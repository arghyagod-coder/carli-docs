# A Beginner's Guide to the Arch User Repository

Though using an Arch-based distro was pretty straightforward for a seasoned user, there is one striking difference that I felt contrasting with the Debian-like environment: the [Arch User Repository](https://aur.archlinux.org/). This is because Arch Linux separates the official project packages from the software that is contributed by the users themselves in another place completely - thus being called Arch User Repository (AUR).

Unlike other distros, however, *Arch does not even include them in the reach of your package manager*. In Debian or Ubuntu, you might edit `/etc/apt/sources.list` to add nonfree or "universe" repositories or PPAs, and after a cache update, all these packages are automatically manageable from apt. Not so with Arch - the AUR is off-limits to `pacman`, and you must install software from there in a more "manual" way, which confuses many beginners used to a more automatic method.

It took me some time to finally get the way installing from the AUR works, not because it's complicated, but rather because I chose to avoid the unknown until I had no choice. And much like the rest of my experience with Arch, it also turned out to be quite easy, even without helpers (yay, yaourt, paru, etc). That's why I'm summarizing the important findings in this point, so that other beginners may not fear the AUR and learn quickly how to install from there.

Read on!

## How AUR works

The single largest difference between installing stuff from AUR versus contribution repositories in other distros is this: AUR *does not* store binary precompiled packages in a server somewhere - you have to *build them by yourself*.

This is strikingly different from, for example, what you see in Debian. There, you download binaries from the repository server, verify the signature to see if it matches the maintainer's, and if all looks good, copy the binaries into their respective places. Finito. With the AUR, that process is almost reversed, following a build process that resembles that of source-based distributions.

If you look at it from a purely quantitative perspective, the AUR is a much larger repository than the official Arch packages, and this explains why so many times when you search for something via `pacman -Ss package`, you'll find nothing, with the answer on the wiki being "you can install it from the AUR." This is especially true when it comes to games: Arch has a myriad of them, arguably larger than any other distro, but few make it to the official repos. Once again, AUR is the answer.

The overall install process has four major steps that thankfully can be mostly automated using Arch's tools:

1. Clone the AUR git repository of your desired package.
2. Follow the build instructions of the git repo's PKGBUILD file.
3. Install additional dependencies via pacman.
4. Build from source and install the package via pacman.

These steps might sound familiar to you if you've ever compiled a package from the source code on Linux (see my [video on SC-IM](https://diode.zone/videos/watch/22a566fa-464b-4ddd-9e71-38340208bf14) for an example), and that's because it's exactly what you're doing here.

However, unlike the traditional way of building from source, using the AUR allows you to more or less automate most of that process, which greatly facilitates it. That build process also makes use of a "feigned" root environment, that makes it unnecessary to run it as the root user (a-la sudo make install), but requires you to install the `fakeroot` package first:

```
sudo pacman -S fakeroot 
```

Let's look at the process more closely now:

## Installing from AUR

Your starting point to install anything from the AUR is to search for the package you want at the [AUR database](https://aur.archlinux.org/). You have to use your browser for this, as pacman does not search the AUR with the `-Ss` flag.

As you do so, take note of the status and other health indicators of the package; packages in the AUR are not part of the official distribution, and therefore do not get screened for quality or security. Is the package orphaned? Abandoned? Gets regular updates? Do the comments state build errors or difficulties? The more popular packages usually do not suffer from these problems, but it's good to check regardless.

Once you decided on the package to install, find its Git repository link and clone it in the terminal. It's presented on the `https://aur.archlinux.org/package-name.git` format.

git clone https://aur.archlinux.org/package-name.git cd package-name/

You'll find that usually the only thing inside the cloned directory is a script named PKGBUILD. This is the "instructions" on all the steps required to build that package, all the way from installing dependencies, downloading external assets, and compiler flags. Think of it as a Makefile on steroids, which is great since the next step is to simply run the following command to build and install the package:

```
makepkg -si 
```

And that's pretty much it. `makepkg` does its magic handling all the dependencies and compilation for you (it might ask you to install things via pacman along the way), using fakeroot to abstract parts that would require root permissions to proceed. If you find errors along the way (ie. with the configure script), read them and try to understand what dependencies are missing, and fill in those gaps with pacman. Usually after this the build is pretty smooth.

Be warned, though, that since you're compiling everything, it will take much more time compared to pacman. Depending on the package size and your CPU, the build could take anywhere between a few minutes to about an hour. Gentoo users might be used to it, but most others will be quite surprised.

Once the package is built, pacman will offer to install it neatly alongside your other system binaries. Enter your password and that's pretty much it - you have installed your first AUR package!

## Using helpers

As seen in this rather simple guide, using the AUR is not at all a hard task once you know how it works behind the scenes. However, it's still not as convenient as having a package manager to search for install and update packages with short, simple commands. Could there be a way to use the AUR in a similar manner? Surprisingly, there are a few, called **AUR helpers**.

A helper program takes the same (or similar) syntax as pacman and abstracts the work described above to provide an experience similar to using pacman itself. There are still a few caveats that the helpers can't cover completely, and the official way to install from the AUR according to the Arch Linux Project remains the manual process described above. But if you take these in consideration, it's still a very convenient way to use the AUR.

For the longest time, a program called `yaourt` was the go-to helper in Arch Linux. It was, however, deprecated due to lack of maintenance sometime in the mid 2010s, and a spiritual successor called `yay` became the next recommended helper. However, `yay` itself became deprecated by the end of 2019 due to lack of maintenance, and a few other alternatives came along (I hear that `paru` is the new successor to yay).

This anecdote illustrates one important limitation of helpers: *they are as useful as they are maintained.* Because they are not an official part of Arch, the project does not maintain them, and they rely on volunteers to keep evolving together with Arch itself. Using a slightly old helper might not be a problem in the short term, but it might stop working as it falls behind the rolling releases. Keep this in mind as you choose which helper to use.

As they're not part of of Arch Linux, helpers must (not ironically) also be built and installed from the AUR. As we saw before, though, that is not a problem: just follow the same process to build the package manually with git and once you're done, the helper will be available to you, in parallel to pacman.

A full listing [comparing all AUR helper programs](https://wiki.archlinux.org/index.php/AUR_helpers) is available at the Arch Wiki.

## Conclusion

The Arch User Repository is a real treasure trove of community-maintained software that is usually very up-to-date with upstream releases, but requires a slightly different process to install from. Thankfully, it's not complicated, but might require a little more time since it's always built from source.

AUR is not without its warts either, and less popular packages might fall behind in terms of quality or even security, and you should always keep this in mind as you install software from it. You can use helper programs (yay, paru, etc) to ease and speed up the build process when installing from the AUR, but keep in mind their limitations and that the official way to install is still manually.

If you reckon all of these, the AUR is a terrific tool and a source of a myriad of packages, some of which are not even available in other distributions.
