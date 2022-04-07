# Maintainer: xtrm <oss@xtrm.me>
pkgname=osxcross-xtrm-git
_pkgname=osxcross
_sdkver=11.3
_sdkname=MacOSX$_sdkver.sdk
pkgver=0.14
pkgrel=1
pkgdesc="OS X cross toolchain for Linux, FreeBSD and NetBSD"
arch=('x86_64')
url="https://github.com/tpoechtrager/osxcross"
license=('MIT')
depends=('llvm')
makedepends=('clang>=3.2' 'patch' 'libxml2' 'cmake' 'bash')
optdepends=('uuid: ld64 -random_uuid support'
			'xar: ld64 -bitcode_bundle support' )
provides=("$_pkgname")
conflicts=("$_pkgname")
source=('git+https://github.com/tpoechtrager/osxcross.git'
        "https://github.com/joseluisq/macosx-sdks/releases/download/$_sdkver/$_sdkname.tar.xz")
md5sums=('SKIP' 'SKIP') # yes
options=('!strip')

prepare() {
	msg2 'Prepare SDK'
	cd "$srcdir"

	cp -r /usr/include/c++/v1 "$_sdkname/usr/include/c++"
	bsdtar cJf "$srcdir/$_pkgname/tarballs/$_sdkname.tar.xz" "$_sdkname"

	msg2 'Prepare osxcross'
	cd "$srcdir/$_pkgname"
	sed -i -e 's|-march=native||g' build_clang.sh wrapper/build_wrapper.sh
}

build() {
	cd "$srcdir/$_pkgname"

	export UNATTENDED=yes
	export OSX_VERSION_MIN=10.7
	export CFLAGS='-U_GLIBCXX_ASSERTIONS'
	export CXXFLAGS='-U_GLIBCXX_ASSERTIONS'

	./build.sh
}

package() {
	cd "$srcdir/$_pkgname"

	mkdir -p "$pkgdir/opt/$_pkgname"
	cp -r "$srcdir/$_pkgname/target/"* "$pkgdir/opt/$_pkgname/"

	mkdir -p "$pkgdir/etc/ld.so.conf.d/"
	echo /opt/$_pkgname/lib | sudo tee $pkgdir/etc/ld.so.conf.d/$_pkgname.conf
}
