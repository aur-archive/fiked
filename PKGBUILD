# Archtrack maintainer: Evan Teitelman <teitelmanevan at gmail dot com>
# Contributor: Jens Pranaitis <jens@chaox.net>
pkgname=fiked
pkgver=0.0.5
pkgrel=1
pkgdesc="fake IDE daemon"
arch=("i686" "x86_64")
url="http://www.roe.ch/FakeIKEd"
updateurl="http://www.roe.ch/FakeIKEd=>fiked-"
license=('GPL')
depends=("libgcrypt" "libdnet")
source=(http://mirror.roe.ch/rel/$pkgname/$pkgname-$pkgver.tar.bz2)
md5sums=('2313cf2e13c0d516caea72bf4b57a7e4')

groups=(archtrack archtrack-sniffing-spoofing)

build() {
  cd "$srcdir/$pkgname-$pkgver"
  sed -i "s|libnet11-config|libnet-config|g" GNUmakefile || return 1
  sed -i "s|/usr/local|/usr|g" GNUmakefile || return 1
  sed -i "s|man/man1|share/man/man1|g" GNUmakefile || return 1
  sed -i "s|CFLAGS?=.*|CFLAGS=$CFLAGS|" GNUmakefile || return 1
  PREFIX="/usr" make || return 1
  install -D -m755 $pkgname "$pkgdir"/usr/bin/$pkgname || return 1
  install -D -m644 $pkgname.1 "$pkgdir"/usr/share/man/man1/$pkgname.1 || return 1
}

