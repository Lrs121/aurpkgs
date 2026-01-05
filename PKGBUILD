pkgname=jellyroller
_altname=JellyRoller
pkgver=1.0.0
pkgrel=1
pkgdesc="CLI Jellyfin Controller Utility for Linux and Windows"
arch=('x86_64' 'aarch64')
license=('GPL')
url='https://github.com/LSchallot/JellyRoller'
depends=()
makedepends=('rustup')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/v${pkgver}.tar.gz")
b2sum=(SKIP)

prepare() {
  rustup default stable
}

build() {
  cd "${_altname}-${pkgver}"
  export RUSTUP_TOOLCHAIN=stable
  export CARGO_TARGET_DIR=target
  cargo build --release
}

package() {
  cd "${_altname}-${pkgver}"
  install -Dm755 'target/release/jellyroller' -t "$pkgdir/usr/bin"
  install -Dm644 'LICENSE' -t "$pkgdir/usr/share/licenses/$pkgname"
	install -Dm644 'README.md' -t "$pkgdir/usr/share/doc/$pkgname"
}
