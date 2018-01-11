# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
_php=php5
pkgname=$_php-redis
_pkgrealname=redis
pkgver=3.1.6
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

sha512sums="4263d150c93f11dd06587925ad9a3cd8fbba2e4a18b2f23e6adfaeb25d566a1c2d256551a50ae1b9c770fd0f9bc4c92f483c46d60be9d4f5b5ba056231b7d527  redis-3.1.6.tgz"
