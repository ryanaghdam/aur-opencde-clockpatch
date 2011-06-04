# Maintainer: Ryan Aghdam <ryan@aghdam.org>

# Based on original package from Thomas Dziedzic.

pkgname=opencde
pkgver=0.4.4
pkgrel=1
pkgdesc="OpenCDE is a free implementation of the Open Group's Common Desktop Environment. Includes a patch for clock and calendar widgets."
arch=('i686' 'x86_64')
url='http://devio.us/~kpedersen/index.php'
license=('BSD')
depends=('openmotif')
source=("http://devio.us/~kpedersen/releases/${pkgname}-${pkgver}.tar.gz")
md5sums=('1c3a7430b65d9e1e95d464c4a30120a5')

build() {
  cd ${pkgname}/src

  # fix build errors
  unset CFLAGS CXXFLAGS LDFLAGS

  #sed -i "s_PREFIX=/usr/local_PREFIX=${pkgdir}/usr_" config.Mk
  sed -i "s_PREFIX=/usr/local_PREFIX=/usr_" config.Mk

  sed -i 's/$(CC) -c $(CPPFLAGS) $< -o $@/$(CC) -fPIC -c $(CPPFLAGS) $< -o $@/' motifmm/Makefile

  make
}

package() {
  cd ${pkgname}

  # probably need to submit patch to upstream
  #install -d ${pkgdir}/usr/bin

  # removed in 0.4.1 again...
  #make install

  install -d ${pkgdir}/usr
  cp -r bin share etc lib ${pkgdir}/usr
}
