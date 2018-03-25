 
# $Id$
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgbase=breeze
pkgname=(breeze)
pkgver=5.12.3
pkgrel=1.1
arch=(x86_64)
url='https://www.kde.org/workspaces/plasmadesktop/'
license=(LGPL)
makedepends=(extra-cmake-modules frameworkintegration kdelibs automoc4 kdecoration kcmutils plasma-framework python)
source=("https://download.kde.org/stable/plasma/$pkgver/$pkgbase-$pkgver.tar.xz"{,.sig}
001.patch)
sha256sums=('1cbace92ba7548d90c6a74683bceec67a2b86ba7974238c85e3c94fc58577656'
            'SKIP'
            'caed9fda96eae58eaaedfd321db296896edb6710b7025039b1f90e6c4f5ea66d')
validpgpkeys=('2D1D5B0588357787DE9EE225EC94D18F7F05997E'  # Jonathan Riddell
              '0AAC775BB6437A8D9AF7A3ACFE0784117FBCE11D'  # Bhushan Shah <bshah@kde.org>
              'D07BD8662C56CB291B316EB2F5675605C74E02CF'  # David Edmundson
              '1FA881591C26B276D7A5518EEAAF29B42A678C20') # Marco Martin <notmart@gmail.com>

prepare() {
  mkdir -p build
  cd $pkgname-$pkgver
  msg "Transparent menu patch"
  patch -p1 --verbose -i ../001.patch
}

build() {
  cd build
  cmake ../$pkgbase-$pkgver \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DBUILD_TESTING=OFF
  make
}

package_breeze() {
  depends=(frameworkintegration kdecoration breeze-icons kwayland hicolor-icon-theme)
  pkgdesc='Artwork, styles and assets for the Breeze visual style for the Plasma Desktop'
  optdepends=('breeze-kde4: Breeze widget style for KDE4 applications'
		'breeze-gtk: Breeze widget style for GTK applications'
		'kcmutils: for breeze-settings')
  groups=(plasma)

  cd build
  make DESTDIR="$pkgdir" install
}
