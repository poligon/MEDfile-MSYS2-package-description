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
source=("med-${pkgver}.tar.gz"
	"MEDfileVersionOpen.patch")
sha256sums=('a474e90b5882ce69c5e9f66f6359c53b8b73eb448c5f631fa96e8cd2c14df004'
	'8899d1e3fa7617799438b9cc3fb346c9b5f2dad4c8583a6528f4f9f0a32c0691'
            )

prepare () {
  cd ${srcdir}/${pkgname}-${pkgver}/src
  patch ci/MEDfileVersionOpen.c < ${srcdir}/"MEDfileVersionOpen.patch")
}

build() {
  cd ${srcdir}/med-${pkgver}
  mkdir -p build
  cd build
  cmake -G "MinGW Makefiles" -DCMAKE_SH="CMAKE_SH-NOTFOUND" -DMEDFILE_BUILD_TESTS=OFF -DMEDFILE_INSTALL_DOC=OFF -DCMAKE_BUILD_TYPE="Release" -DCMAKE_C_FLAGS="-O3 -mmmx -msse -msse2 -mfpmath=sse" -DCMAKE_INTERPROCEDURAL_OPTIMIZATION=TRUE -DCMAKE_VERBOSE_MAKEFILE=ON -DCMAKE_INSTALL_PREFIX="$pkgdir/usr/" ../
  cmake --build . -- -j4
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}/build
  cmake --build . --target install
}
