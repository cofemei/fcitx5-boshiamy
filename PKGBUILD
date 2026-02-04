# Maintainer: hhschen <hhschen820@gmail.com>
pkgname=fcitx5-boshiamy
pkgver=1.0.0
pkgrel=1
pkgdesc="A Boshiamy (嘸蝦米) input method engine for Fcitx 5."
arch=(x86_64)
url="https://github.com/cofemei/fcitx5-boshiamy"
license=('GPL')
depends=('fcitx5' 'fcitx5-chinese-addons')
makedepends=('boost' 'extra-cmake-modules')
conflicts=('fcitx5-table-extra')
source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('fa91875f6b922938294d8690b5de3c0183e91ffc67aa0fba8490152a1311f432')

prepare() {
  cd "$srcdir/$pkgname-$pkgver"
  mkdir -p build
}

build() {
  cd "$srcdir/$pkgname-$pkgver/build"
  cmake .. \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_C_FLAGS="-march=znver5 -mtune=znver5 -O3" \
    -DCMAKE_CXX_FLAGS="-march=znver5 -mtune=znver5 -O3"
  cmake --build .
}

package() {
  cd "$srcdir/$pkgname-$pkgver/build"
  make DESTDIR="$pkgdir/" install
}
