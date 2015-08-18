# Maintainer: kevku <kevku@gmx.com>
# Contributor: Ole Roeßler <ole.roessler@gmail.com>
pkgname=yaph
pkgver=0.91
pkgrel=3
arch=('i686' 'x86_64')
pkgdesc="Yet Another Proxy Hunter - scans and validates lists of SOCKS 4/5 or HTTP proxies"
url="http://yaph.sourceforge.net/"
license="GPL"
depends=('nmap')
optdepends=('proxychains: stealth proxy checking')
backup=('etc/yaph.conf')
source=("http://downloads.sourceforge.net/yaph/yaph/$pkgname-${pkgver}.tar.gz"
        "yaph.patch")
md5sums=('f09edd5ba42c671f2d62760bf58604ec'
         '998733e496f8e77e8b74a6c8a7540a3e')
         
build() {
	cd "$srcdir/$pkgname-$pkgver"
	patch -Np1 -i "$srcdir/yaph.patch"
	mv configure.in configure.ac
	echo "AC_PROG_CC" >> configure.ac
	aclocal
	autoconf
        automake --add-missing
	./configure --prefix=/usr --sysconfdir=/etc
	make 
}

package(){
	cd "$srcdir/$pkgname-$pkgver"
	make DESTDIR=$pkgdir install
}
