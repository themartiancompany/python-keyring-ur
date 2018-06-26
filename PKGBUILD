# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

pkgname=python-keyring
pkgver=13.1.0
pkgrel=1
pkgdesc="Store and access your passwords safely."
arch=('any')
url="http://pypi.python.org/pypi/keyring"
license=('PSF' 'MIT')
source=("https://pypi.io/packages/source/k/keyring/keyring-$pkgver.tar.gz")
depends=('python-entrypoints' 'python-secretstorage')
optdepends=('python-keyrings-alt: Alternative backends')
makedepends=('python-setuptools-scm')
checkdepends=('python-pytest-flake8' 'python-pytest-runner')
sha512sums=('06dc9f27692b4ebaa1592d500135d4dad7358ebc53d3b1e1cc733e9aa6610136f9b7224ffd5426324ee5d405fcf0c0b836de776ab304d2395e7491655afd98ca')

prepare() {
  cd keyring-$pkgver
  echo -e '\nflake8-ignore = W191 W503 W504' >> pytest.ini
}

build() {
  cd keyring-$pkgver
  python setup.py build
}

check() {
  cd keyring-$pkgver
  python setup.py pytest
}

package() {
  cd keyring-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
}

# vim:set ts=2 sw=2 et:
