# Maintainer: Gerad Munsch <gmunsch@unforgivendevelopment.com>
# Contributor: Gero Müller <post@geromueller.de>
#
# adapted from package "dkms-e1000e"
pkgname=e1000e-dkms
_modname=e1000e
pkgver=3.1.0.2
pkgrel=2
pkgdesc="Intel e1000e Ethernet adapter driver (latest version from Intel) (DKMS version)"
license=('GPL')
arch=('i686' 'x86_64')
depends=('dkms')
optdepends=('linux-headers: build the module against Arch kernel [requires at least one set of kernel headers]'
            'linux-ck-headers: build the module against Linux-ck kernel [requires at least one set of kernel headers]'
            'linux-lts-headers: build the module against LTS Arch kernel [requires at least one set of kernel headers]')
install=e1000e-dkms.install
url='http://sourceforge.net/projects/e1000/'
source=("http://downloads.sourceforge.net/project/e1000/${_modname}%20stable/${pkgver}/${_modname}-${pkgver}.tar.gz"
        'dkms.conf.in'
        'e1000e-dkms.install')
sha384sums=('b2b1ccec3299e55b1015e1defd2cef58542bb8f4288df74be7a39feaed4366a806c7144497fad3618034b6f9b99f7e2e'
            '3339c6cfeeb8671bf2b667033d03740bc036c5fb65071ec360a3ecc92f7eda278eedfed2bb6e9d8e20693070b27be30a'
            'fbf65ac0e3120f8accb42e765edc03ac82cf5101ec8d88baa721b9e0ad5775ce0afcdf0132e5f4b23d93714b1edb9f4e')

package() {
  cd ${srcdir}/${_modname}-${pkgver}
  install -dm755 "${pkgdir}/usr/src/${_modname}-${pkgver}/"
  for i in "${srcdir}/${_modname}-${pkgver}/src/"{Makefile,*.c,*.h}; do
    install -D -m644 "${i}" "${pkgdir}/usr/src/${_modname}-${pkgver}/"
  done
  sed "s/#MODULE_VERSION#/${pkgver}/" "${srcdir}/dkms.conf.in" > "${pkgdir}/usr/src/${_modname}-${pkgver}/dkms.conf"
}
