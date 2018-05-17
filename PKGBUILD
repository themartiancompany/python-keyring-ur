# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

pkgname=python-keyring
pkgver=12.2.1
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
sha512sums=('8806b4433bc9085ae133300e68bc614281beea70de547f75afafdf6de2ee1b436f3a4cd13d7684cb6e4d5aef0a2eb9119d9cebbaf239a9ee1997ece4a56a7371')

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
