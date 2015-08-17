# Maintainer: speps <speps dot aur dot archlinux dot org>

pkgname=pumpa-qt4
pkgver=0.9
pkgrel=2
pkgdesc="A simple pump.io client written in C++ and Qt4"
arch=('i686' 'x86_64')
url="http://gitorious.org/pumpa"
license=('GPL3')
depends=('qjson' 'aspell' 'tidyhtml')
provides=('pumpa')
install="pumpa.install"
source=("$url/pumpa/archive/v$pkgver.tar.gz")
md5sums=('2fc740b6063ad0a46a520489ba1f9117')

prepare() {
  cd pumpa-pumpa

  # qt4 reference
  sed -i 's|pumpa|&-qt4|;s|Pumpa|& (Qt4)|' pumpa.desktop
}

build() {
  cd pumpa-pumpa
  qmake-qt4 PREFIX=/usr
  make
}

package() {
  cd pumpa-pumpa

  # bin
  install -Dm755 pumpa \
    "$pkgdir/usr/bin/$pkgname"

  # desktop file
  install -Dm644 pumpa.desktop \
    "$pkgdir/usr/share/applications/$pkgname.desktop"

  # icon
  install -Dm644 images/pumpa.png \
    "$pkgdir/usr/share/icons/hicolor/32x32/apps/$pkgname.png"
}
