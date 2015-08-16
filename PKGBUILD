
# Maintainer: Antonis Geralis 

pkgname=libtmdbqt-git
pkgver=r21.19c5bd9
pkgrel=1
pkgdesc='This library can retrieve information about movies from the Tmdb web service.'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kde/kde-workspace'
license=('GPL')
depends=('qt5-base')
makedepends=('git' 'qt5-tools')
optdepends=()
conflicts=('libtmdbqt')
provides=('libtmdbqt')
source=("git://anongit.kde.org/libtmdbqt.git")
#install=$pkgname.install
sha256sums=('SKIP')

pkgver() {
  cd libtmdbqt
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() { 
  cd build
  cmake ../libtmdbqt \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DLIB_INSTALL_DIR=lib \
    -DLIBEXEC_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DSYSCONF_INSTALL_DIR=/etc \
    -DBUILD_TESTING=OFF
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
