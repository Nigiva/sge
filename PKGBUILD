# Maintainer: Manhong Dai <daimh@umich.edu>
pkgname=sge
pkgver=20190516
pkgrel=1
pkgdesc="Son of Grid Engine/Sun Grid Engine"
arch=('x86_64')
url="https://arc.liv.ac.uk/downloads/SGE/releases/8.1.9/"
license=('GPL')
depends=(
	'awk'
	'binutils'
	'gcc'
	'grep'
	'hwloc'
	'inetutils'
	'libtirpc'
	'libxt'
	'openmotif'
	'tcsh'
)
source=(
	'https://arc.liv.ac.uk/downloads/SGE/releases/8.1.9/sge_8.1.9.tar.xz'
	'sge-8.1.9.patch.xz'
)
md5sums=(
	'a2f03ca8b803ca4da7d2dedadeca74bb'
	'be59af210af77e2ac6efd9fe10d51149'
)
build() {
	patch -s -p0 < sge-8.1.9.patch
	cd sge-8.1.9
	install -d source/MANSBUILD_sge/SEDMAN/man/man1
	install -d source/MANSBUILD_sge/SEDMAN/man/man3
	install -d source/MANSBUILD_sge/SEDMAN/man/man5
	install -d source/MANSBUILD_sge/SEDMAN/man/man8
	cd source
	sh scripts/bootstrap.sh -no-java -no-jni
	./aimk -no-java -no-jni -with-arch-linux
	install -d clients/gui-installer/dist
	touch clients/gui-installer/dist/installer.jar
	rm -f LINUXAMD64/config.status
	rm -f 3rdparty/qtcsh/LINUXAMD64/config.status
	rm -f 3rdparty/qtcsh/LINUXAMD64/atconfig
	rm -f 3rdparty/qmake/LINUXAMD64/config/Makefile
	rm -f 3rdparty/qmake/LINUXAMD64/w32/Makefile
	rm -f 3rdparty/qmake/LINUXAMD64/Makefile
	rm -f 3rdparty/qmake/LINUXAMD64/config.log
	rm -f 3rdparty/qmake/LINUXAMD64/config.status
	rm -f 3rdparty/qmake/LINUXAMD64/glob/Makefile
}
package() {
	install -d $pkgdir/opt/sge
	cp -pr sge-8.1.9 $pkgdir/opt/sge/build
}
install=sge.install
