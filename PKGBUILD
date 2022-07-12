# Merged with official ABS kwallet PKGBUILD by João, 2021/03/05 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwallet-git
pkgver=5.80.0_r1047.g41a76c3
pkgrel=1
pkgdesc='Secure and unified container for user passwords'
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(LGPL)
depends=(knotifications-git kiconthemes-git kservice-git gpgme)
makedepends=(git extra-cmake-modules-git kdoctools-git boost doxygen qt5-tools qt5-doc qca-qt5-git)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
optdepends=('kwalletmanager-git: Configuration GUI')
groups=(kf5-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
