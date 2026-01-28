pkgname=blue-vault
pkgver=0.1.2
pkgrel=1
pkgdesc='A production-quality TUI app to manage Blu-ray cold storage archives on Linux '
url='https://github.com/ChrisLAS/blue-vault'
source=("$pkgname-$pkgver.tar.gz::$url/archive/v$pkgver.tar.gz")
arch=('x86_64' 'aarch64')
license=('GPL-2.0')
depends=('libisoburn' 'dvd+rw-tools')
makedepends=('cargo' 'clang' 'llvm')
optdepends=('qrencode' 'rsync')
b2sums=('b17724927a8b1b540a6967f246c472bdaed857183fdda5fe601dc753344b430ad99271606b179e74505c220e6b60580ca49eed4cc9fd03b5c9ad85c4fd5cfec3')

prepare() {
  cd "$pkgname-$pkgver"
  export RUSTUP_TOOLCHAIN=stable
  cargo fetch --locked --target "$CARCH-unknown-linux-gnu"
}

build() {
  cd "$pkgname-$pkgver"

  export RUSTUP_TOOLCHAIN=stable
  export CARGO_TARGET_DIR=target
  export CC=/sbin/clang
  export CXX=/sbin/clang++
  cargo build --release --frozen
}

package() {
  cd "$pkgname-$pkgver"

  install -Dm 755 target/release/bdarchive -t "$pkgdir/usr/bin"
  install -Dm 644 LICENSE -t "$pkgdir/usr/share/licenses/$pkgname"
}
