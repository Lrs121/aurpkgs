pkgname=jellyswarrm
_altname=Jellyswarrm
pkgver=0.2.0
pkgrel=1
pkgdesc="Bring all your Jellyfin servers together"
arch=('x86_64' 'aarch64')
license=('GPL-2.0')
url='https://github.com/LLukas22/Jellyswarrm'
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/v${pkgver}.tar.gz")
makedepends=('rustup')
b2sum=()

prepare() {
  rustup default stable
}

build() {
  cd "${altname}-${pkgver}"
  export RUSTUP_TOOLCHAIN=stable
  export CARGO_TARGET_DIR=target
  cargo build --release
}

package() {
  cd "${altname}-${pkgver}"
  install -Dm755 'target/release/jellyroller' -t "$pkgdir/usr/bin"
  install -Dm644 'LICENSE' -t "$pkgdir/usr/share/licenses/$pkgname"
	install -Dm644 'README.md' -t "$pkgdir/usr/share/doc/$pkgname"
}
