# Maintainer: loathingkernel <username ta gmail tod com>
# Contributor: Mikołaj Chwalisz <m.chwalisz@gmail.com>
# Contributor: archlinux.info:tdy

pkgname=vitables
pkgver=3.0.2
pkgrel=3
pkgdesc="A GUI browser and editor for PyTables/HDF5 files"
arch=(any)
url=http://vitables.org
license=(GPL3)
depends=(
  'python-pyqt5'
  'python-qtpy'
  'python-pytables'
)
makedepends=(
  'python-sphinx'
)
source=(
  "$pkgname-$pkgver.tar.gz::https://github.com/uvemas/ViTables/archive/v$pkgver.tar.gz"
  "vitables.desktop"
  "vitables.svg"
  "python310.patch"
)
sha256sums=(
  '43a965a08124fe0e1974aed27a7149cdeaf75e8ae833e95a18a94d7d5bd506c8'
  'dd793f85d81591edd837a5fb94642dbf3ba488c69c605cbc2c87f74baea8676c'
  '0be6fdeb2c1f40fe2c478b0a6b9f99bad170d69f1210300d736bb98a5b9edcd8'
  '60cf7529f4095f4a3a86648ab95388b43c1d5e7cb23f482d98c4b395c4f800fc'
)

prepare() {
  cd ViTables-"$pkgver"
  patch --forward --strip=1 --input=$srcdir/python310.patch

}

build() {
  cd ViTables-"$pkgver"
  python setup.py build
}

package() {
  cd ViTables-"$pkgver"
  python setup.py install --root="$pkgdir" --optimize=1
  install -d "$pkgdir"/usr/share/{applications,pixmaps}
  install -m644 "$srcdir"/vitables.desktop "$pkgdir"/usr/share/applications/
  install -m644 "$srcdir"/vitables.svg "$pkgdir"/usr/share/pixmaps/
}
