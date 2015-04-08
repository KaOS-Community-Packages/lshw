pkgname=lshw
pkgver=B.02.17
pkgrel=1
pkgdesc="A small tool to provide detailed information on the hardware configuration of the machine."
url="http://ezix.org/project/wiki/HardwareLiSter"
license=('GPL')
arch=('x86_64')
depends=('gcc-libs' 'hwids')
optdepends=('gtk2')
makedepends=('gcc' 'gtk2' 'sqlite')
source=(http://ezix.org/software/files/lshw-$pkgver.tar.gz)
md5sums=('a5feb796cb302850eaf5b4530888e3ed')

build() {
  cd $srcdir/$pkgname-$pkgver
  sed -i 's|/usr/bin/gtk-lshw|/usr/sbin/gtk-lshw|' src/gui/integration/gtk-lshw.desktop
  make SBINDIR=/usr/bin
  make SBINDIR=/usr/bin gui
}

package() {
  cd $srcdir/$pkgname-$pkgver
  make DESTDIR=$pkgdir/ SBINDIR=/usr/bin install
  make DESTDIR=$pkgdir/ SBINDIR=/usr/bin install-gui
  install -Dm0644 src/gui/integration/gtk-lshw.desktop $pkgdir/usr/share/applications/gtk-lshw.desktop
  install -Dm0644 src/gui/integration/gtk-lshw.pam $pkgdir/usr/share/doc/$pkgname/gtk-lshw.pam
  install -Dm0644 src/gui/integration/console.apps $pkgdir/usr/share/doc/$pkgname/console.apps
  rm -f $pkgdir/usr/share/lshw/{pci,usb}.ids
}
