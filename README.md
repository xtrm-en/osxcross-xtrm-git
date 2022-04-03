# osxcross-latest-git

a properly maintained AUR package for the
[osxcross](https://github.com/tpoechtrager/osxcross/) toolchain.

this version is built with the 11.3 OSX SDK

# how to build

if this package **isn't in the AUR** yet, do the following:

```bash
git clone https://github.com/xtrm-en/osxcross-latest-git
cd osxcross-latest-git
sudo makepkg -si
```

# how to install

if by any chance i'm not lazy and put this on the AUR:

```bash
# using your favorite AUR helper
yay -S osxcross-latest-git
paru osxcross-latest-git
pamac install osxcross-latest-git
```

or

```bash
# cloning directly from the AUR
git clone https://aur.archlinux.org/osxcross-latest-git.git
cd osxcross-latest-git
sudo makepkg -si
```

