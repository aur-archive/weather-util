# Maintainer: Michael P <ptchinster@archlinux.us>
pkgname=weather-util
pkgver=2.0
pkgrel=3
pkgdesc="provides quick command line access to current weather conditions and forecasts"
arch=('any')
url="http://fungi.yuggoth.org/weather/"
license=('ISC')
groups=()
depends=('python')
makedepends=('unzip')
optdepends=()
provides=()
conflicts=("expect")
replaces=()
backup=('etc/weatherrc')
options=()
install='weather.install'
changelog=
source=( http://fungi.yuggoth.org/weather/src/weather-$pkgver.tar.gz )
noextract=()
md5sums=('be49f38f2da59dfc4716e2370f029a65')

package() {
	name=${pkgname//-util}
	pyversion=`pacman -Q python | cut -d. - -f1,2 | sed 's/ //'`

	mkdir -p $pkgdir/usr/bin
	mkdir -p $pkgdir/usr/lib/${pyversion}
	mkdir -p $pkgdir/usr/share/man/man{1,5}
	mkdir -p $pkgdir/usr/share/licenses/$pkgname
	mkdir -p $pkgdir/etc

	cd "$name-$pkgver"

	cp "$name" "$pkgdir/usr/bin"
	cp "${name}.py" "$pkgdir/usr/lib/${pyversion}"
	cp "${name}.1" "$pkgdir/usr/share/man/man1"
	cp "${name}rc.5" "$pkgdir/usr/share/man/man5"
	cp "LICENSE" $pkgdir/usr/share/licenses/$pkgname
	cp "${name}rc" "$pkgdir/etc"

    #weather-utils-data portion
    for f in *.zip; do unzip $f -d "$pkgdir/usr/share/$pkgname/"; done;
}

