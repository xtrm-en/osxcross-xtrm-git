# osxcross-xtrm-git

a properly maintained AUR package for the
[osxcross](https://github.com/tpoechtrager/osxcross/) toolchain.

this version is built with the 11.3 OSX SDK

# how to build

if this package **isn't in the AUR** yet, do the following:

```bash
git clone https://github.com/xtrm-en/osxcross-xtrm-git
cd osxcross-xtrm-git
makepkg -si
```

# how to install

if by any chance i'm not lazy and put this on the AUR:

```bash
# using your favorite AUR helper
yay -S osxcross-xtrm-git
paru osxcross-xtrm-git
pamac install osxcross-latest-git
```

or

```bash
# cloning directly from the AUR
git clone https://aur.archlinux.org/osxcross-xtrm-git.git
cd osxcross-xtrm-git
makepkg -si
```

