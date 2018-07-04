# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

pkgname=python-keyring
pkgver=13.2.0
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
sha512sums=('e076cf08b56fdc1af9f1fddb747013daa4cdc592585df877d31a3795d7de9b313141bdd0721be41797473df0ac5620c1d06d5e19927c909079656d7c74431f04')

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
