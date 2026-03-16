pkgname=vlmcsd
pkgver=2602
pkgrel=1
pkgdesc="KMS Emulator in C"
arch=('i686' 'x86_64' 'armv6h' 'armv7h' 'aarch64')
url="https://github.com/tfslabs/vlmcsd"
license=('unknown')
makedepends=('git')
conflicts=('vlmcsd-git' 'vlmcsd-svn')
provides=('vlmcsd')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/${pkgver}/${pkgver}.tar.gz"
        "${pkgname}.service"
        "${pkgname}.socket")
b2sums=('978975a03dd067ac74b6b7d1ba4421413581766e8c8a0a82923c686cec0ee5fb53ad61232b7dd0e50efbb4dc8a7fb6b9aa5732e3bf2bd7e3dede2607ad9f214c'
        '33d35d9ace1ae72a86a17ad682b134f9e28215260a05f3411382facaee8f25d7d1d415d3ae8cc03f412da16049928a70d9dffac013868f09686c739bab3fe724'
        'cbdba12f65042db734e89029f83c538b226473943a953f879651cc9db9d53ebcbe264c5f364c2776d129544d75e4fb6aa1057e819e5aa31a6ab0b4d5530f3365')

#prepare() {
#  cd "${pkgname}-${pkgver}"
#  git submodule update --init
#}

build() {
  cd "${pkgname}-${pkgver}"
  make
  cd man
  gzip -fk *.[0-9]
}

package() {
  for unit in vlmcsd.service vlmcsd.socket; do
    install -Dm644 "${srcdir}"/${unit} "${pkgdir}"/usr/lib/systemd/system/${unit}
  done

  cd "${pkgname}-${pkgver}"

  for bin in vlmcs{d,}; do
    install -Dm755 "bin/${bin}" "${pkgdir}"/usr/bin/${bin}
  done

  cd man
  for manpage in *.[0-9]; do
    section=${manpage##*.}
    install -Dm644 ${manpage}.gz "${pkgdir}"/usr/share/man/man${section}/${manpage}.gz
  done
}
