# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
_php=php5
pkgname=$_php-redis
_pkgrealname=redis
pkgver=3.1.4
pkgrel=0
pkgdesc="PHP extension for interfacing with Redis"
url="http://pecl.php.net/redis"
arch="all"
license="PHP"
depends=""
depends_dev="$_php-dev"
makedepends="$depends_dev autoconf"
install=""
subpackages="$pkgname-dev $pkgname-doc"
source="http://pecl.php.net/get/$_pkgrealname-$pkgver.tgz"

builddir="$srcdir"/$_pkgrealname-$pkgver

build() {
	cd "$builddir"
	phpize5 || return 1
	./configure --prefix=/usr \
		--disable-redis-sasl \
		--with-php-config=/usr/bin/php-config5 \
	|| return 1
	make || return 1
}

package() {
	cd "$builddir"
	make INSTALL_ROOT="$pkgdir"/ install || return 1
	install -d "$pkgdir"/etc/$_php/conf.d || return 1
	echo "extension=$_pkgrealname.so" > "$pkgdir"/etc/$_php/conf.d/$_pkgrealname.ini
	for _dev in *.h; do
		install -Dm644 $_dev $pkgdir/usr/include/$pkgname/$_dev
	done
	for _doc in COPYING CREDITS; do
		install -Dm644 $_doc $pkgdir/usr/share/doc/$pkgname/$_doc
	done
}

md5sums="7af20e191c486c458b5a8e421c024c3d  redis-3.1.4.tgz"
sha256sums="adebdfd52e8227a4da5d381d325b6eaccd29fd233bcc1b877517b9e8706ef265  redis-3.1.4.tgz"
sha512sums="dbf3eecfa761d0d3e97781968378d8bcc74e79bf4a0f85d6c2e8338180755e503179bc78b03ae6ee26a5619f439ead77068db3ab18d1b2dbf58e1643bea3a49f  redis-3.1.4.tgz"
