# Maintainer: Evan Greenup <_>

_name=shellcheck
pkgname=hx-$_name
pkgver=0.9.0
pkgrel=1
pkgdesc="Shell script analysis tool"
url="https://www.shellcheck.net/"
license=("GPL-3.0-only")
arch=('x86_64')
provides=("shellcheck")
conflicts=("shellcheck")
replaces=("shellcheck")
depends=()
makedepends=('stack')
source=("${_name}-${pkgver}.tar.gz::https://github.com/koalaman/${_name}/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('3cec1fec786feee79dacdabf9de784a117b7f82388dbcca97ba56a5c9ff7d148')

build() {
  cd "$srcdir/$_name-$pkgver"

  stack build ShellCheck:exe:shellcheck
}

check() {
  cd "$srcdir/$_name-$pkgver"

  stack test ShellCheck:exe:shellcheck
}

package() {
  cd "$srcdir/$_name-$pkgver"
  mkdir -m755 -p "${pkgdir}/usr/bin/"
  install -m755 "$(stack path --local-install-root)/bin/shellcheck" "${pkgdir}/usr/bin/shellcheck"
  install -D -m644 LICENSE -t "$pkgdir"/usr/share/licenses/$pkgname/
}
