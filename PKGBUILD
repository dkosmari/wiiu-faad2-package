pkgname=ppc-faad2
pkgver=2.11.2
pkgrel=1
pkgdesc='Freeware Advanced Audio (AAC) Decoder.'
arch=('any')
url='https://github.com/knik0/faad2'
license=('GPLv2')
options=(!strip libtool staticlibs)
groups=('ppc-portlibs')

source=("$url/archive/refs/tags/$pkgver.tar.gz")

build() {
  cd faad2-$pkgver

  export PORTLIBS_PREFIX=$DEVKITPRO/portlibs/ppc

  CMAKE_C_COMPILER_LAUNCHER=ccache \
  CMAKE_CXX_COMPILER_LAUNCHER=ccache \
  /opt/devkitpro/devkitPPC/bin/powerpc-eabi-cmake \
    -B build \
    -DCMAKE_INSTALL_PREFIX=$PORTLIBS_PREFIX \
    -DCMAKE_BUILD_TYPE=Release \
    -DFAAD_BUILD_CLI=Off \
    -DCMAKE_C_FLAGS_RELEASE="-O2 -mcpu=750 -meabi -mhard-float -ffunction-sections -fdata-sections -DNDEBUG" \
    .

  make -C build VERBOSE=1
}

package() {
  cd faad2-$pkgver/build
  make install DESTDIR="$pkgdir"
}

sha256sums=('3fcbd305e4abd34768c62050e18ca0986f7d9c5eca343fb98275418013065c0e')
