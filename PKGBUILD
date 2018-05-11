# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

pkgname=python-keyring
pkgver=12.2.0
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
sha512sums=('1bdec1d9775157c47710280cb95ac1419f357840ca0b1aba5bdb48f4851ceb04c9ef56f74e5ab564b1365ce2ec45a3ff15d1ae23360bb9b9e098b3684a06e80f')

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
