pkgname=med
pkgver=4.0.0
pkgrel=1
pkgdesc="MED (Modelisation et Echanges de Donnees, i.e. Data Modelization and Exchanges) file library"
url="http://www.salome-platform.org/user-section/about/med"
license=('LGPL')
depends=('mingw-w64-x86_64-hdf5')
makedepends=('mingw-w64-x86_64-gcc' 
             'mingw-w64-x86_64-cmake')
arch=('x86_64')
source=("med-${pkgver}.tar.gz")
sha256sums=('a474e90b5882ce69c5e9f66f6359c53b8b73eb448c5f631fa96e8cd2c14df004'
            )
build() {
  cd ${srcdir}/med-${pkgver}_SRC
  mkdir -p build
  cd build
  cmake -G "MinGW Makefiles" -DCMAKE_SH="CMAKE_SH-NOTFOUND" -DMEDFILE_BUILD_TESTS=OFF -DMEDFILE_INSTALL_DOC=OFF -DCMAKE_BUILD_TYPE="Release" -DCMAKE_C_FLAGS="-O3 -mmmx -msse -msse2 -mfpmath=sse" -DCMAKE_INTERPROCEDURAL_OPTIMIZATION=TRUE -DCMAKE_VERBOSE_MAKEFILE=ON -DCMAKE_INSTALL_PREFIX="$pkgdir/usr/" ../
  cmake --build . -- -j4
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}_SRC/build
  cmake --build . --target install
}
