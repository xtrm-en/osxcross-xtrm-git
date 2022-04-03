# Maintainer: xtrm <oss@xtrm.me>
pkgname=osxcross-latest-git
_pkgname=osxcross
_sdkver=11.3
pkgver=0.14
pkgrel=1
pkgdesc="OS X cross toolchain for Linux, FreeBSD and NetBSD"
arch=('x86_64')
url="https://github.com/tpoechtrager/osxcross"
license=('MIT')
depends=()
makedepends=('clang>=3.2' 'patch' 'libxml2' 'bash')
optdepends=(
	'llvm: for Link Time Optimization support and ld64 -bitcode_bundle support'
	'uuid: for ld64 -random_uuid support'
	'xar: for ld64 -bitcode_bundle support'
)
provides=("$_pkgname")
conflicts=("$_pkgname")
source=('git+https://github.com/tpoechtrager/osxcross.git' 'https://github.com/phracker/MacOSX-SDKs/releases/download/$_sdkver/MacOSX$_sdkver.tar.xz')
md5sums=('SKIP' 'SKIP')
noextract=('MacOSX$_sdkver.sdk.tar.xz')
options=('!strip')

build() {
	cd "$srcdir/$_pkgname"

	mv ../MacOSX$_sdkver.sdk.tar.xz tarballs/
	sed -i -e 's|-march=native||g' build_clang.sh wrapper/build.sh
	UNATTENDED=yes OSX_VERSION_MIN=$_sdkver ./build_wrapper.sh
}

package() {
	cd "$srcdir/$_pkgname"

	mkdir -p $pkgdir/usr/local
	mv target $pkgdir/usr/local/osx-ndk-x86
}
