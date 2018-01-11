# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
_php=php5
pkgname=$_php-redis
_pkgrealname=redis
pkgver=3.1.5
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

sha512sums="9d19d8ff2af92ef4da5c8d82daec6307c66db7c3f5171f8ad7d834b01f77ac488b66bd74e6223e76ea7bc6936188341f347756e2f0bbb63ce4a149341c3d6a92  redis-3.1.5.tgz"
