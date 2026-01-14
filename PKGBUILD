# Maintainer: Ewout van Mansom <ewout@vanmansom.name>
pkgname=smfc
pkgver=4.2.1
pkgrel=1
pkgdesc="Supermicro Fan Control"
arch=(any)
install=smfc.install
backup=('etc/default/smfc' 'opt/smfc/smfc.conf')
url="https://github.com/petersulyok/smfc"
license=('GPL3')
depends=('python' 'syslog-ng' 'pacman-hook-reload-modules')
optdepends=('nvidia-utils' 'smartmontools')
checkdepends=('flake8' 'python-coverage' 'python-pylint' 'python-pytest' 'python-pytest-cov')
source=(
  "${pkgname}-v${pkgver}.tar.gz::${url}/archive/refs/tags/v${pkgver}.tar.gz"
  "modules-load.conf"
  "smfc.install"
)
b2sums=('bd6f0118fb819f88eebace63f6a5533c8de272437da6a097ccfe8a6923be3e79bdba235c99b34a7d374f4941a8c9842f64e75deb879f643b7efb89e629590b05'
        'da0f37c6575fd3710af4ec15ca63979a15486cea69c929ecbd1c687aab066b60fb4f90df834112b391f86a0498844fa688c870a904658362be8b2c165d37c5d4'
        'b085d9d1d133ff163774d59370a64ffb56d94e581301312202bb4cb468b54965fcb88643af942d6618d15b98aa29c7b45f2433a3bb0a29bf91bb4cfe8b52bf53')

check() {
  cd "${pkgname}-${pkgver}"
  pytest
}

package() {
  install -o root -g root -Dm644 modules-load.conf "${pkgdir}/usr/lib/modules-load.d/smfc.conf"

  cd "${pkgname}-${pkgver}"

  install -o root -g root -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"

  cd src
  install -o root -g root -Dm755 smfc.py "${pkgdir}/opt/smfc/smfc.py"
  install -o root -g root -Dm644 smfc.conf "${pkgdir}/opt/smfc/smfc.conf"
  install -o root -g root -Dm644 smfc "${pkgdir}/etc/default/smfc"
  install -o root -g root -Dm644 smfc.service "${pkgdir}/usr/lib/systemd/system/smfc.service"
}
