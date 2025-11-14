pkgbase='podsync'
pkgname='gpodsync'
pkgrel=1
pkgver=0.1.11
pkgdesc='A minimal podcast sync server, using the same API as GPodder, compatible with AntennaPod.'
url='https://github.com/bobrippling/podsync'
arch=(x86_64)
makedepends=('cargo')
conflicts=('podsync' 'podsync-git' 'podsync-bin')
source=("${pkgbase}-${pkgver}.tar.gz::${url}/archive/refs/tags/v${pkgver}.tar.gz")
b2sums=('f8ef9fa384075dbd4921e869d7fee4db4d23117fb2e010e2ab4b56679db4a9e9')

build() {
  cd "${srcdir}/${pkgbase}-${pkgver}"
  cargo build --release
}

package() {
  cd "${srcdir}/${pkgbase}-${pkgver}"
  install -d 
}
