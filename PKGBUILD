# Maintainer: xtrm <oss@xtrm.me>
pkgname=osxcross-latest-git
_pkgname=osxcross
_sdkver=11.3
_sdkname=MacOSX$_sdkver.sdk
_prefix=/opt/osxcross
pkgver=0.14
pkgrel=1
pkgdesc="OS X cross toolchain for Linux, FreeBSD and NetBSD"
arch=('x86_64')
url="https://github.com/tpoechtrager/osxcross"
license=('MIT')
depends=()
makedepends=('clang>=3.2' 'patch' 'libxml2' 'llvm' 'bash')
optdepends=(
	'uuid: for ld64 -random_uuid support'
	'xar: for ld64 -bitcode_bundle support'
)
provides=("$_pkgname")
conflicts=("$_pkgname")
source=('git+https://github.com/tpoechtrager/osxcross.git'
        "https://github.com/phracker/MacOSX-SDKs/releases/download/$_sdkver/$_sdkname.tar.xz")
md5sums=('SKIP' 'SKIP')
noextract=("$_sdkname.tar.xz")
options=('!strip')

prepare() {
	cd "$srcdir/$_pkgname"
	
	msg2 'Prepare SDK'
	mv ../$_sdkname.tar.xz tarballs/

  	msg2 'Prepare osxcross'
	sed -i -e 's|-march=native||g' build_clang.sh wrapper/build.sh
}

build() {
	cd "$srcdir/$_pkgname"

	export UNATTENDED=yes
	export OSX_VERSION_MIN=$_sdkver

	./build_wrapper.sh
}

package() {
	cd "$srcdir/$_pkgname"

	mkdir -p "$pkgdir/${_prefix%/*}"
	cp -r target "$pkgdir/${_prefix}"
	install -d "${pkgdir}/${_prefix}/share/apple-darwin"
}
