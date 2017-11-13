# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

pkgbase=python-keyring
pkgname=('python-keyring' 'python2-keyring')
pkgver=10.5.0
pkgrel=1
pkgdesc="Store and access your passwords safely."
arch=('any')
url="http://pypi.python.org/pypi/keyring"
license=('PSF' 'MIT')
source=("https://pypi.io/packages/source/k/keyring/keyring-$pkgver.tar.gz")
makedepends=('python-setuptools_scm' 'python2-setuptools_scm' 'python-secretstorage'
             'python2-secretstorage')
checkdepends=('python-pytest-runner' 'python2-pytest-runner')
sha512sums=('da1cd064ae896458b1bfc6906a3d40abaa45b6e69f5760fb87d7f7176eab2c909515bbf6e3f01ecd821e340fd1f967ef2aed02053d4211e87533ea4fd6b4e08c')

prepare() {
  cp -a keyring-$pkgver{,-py2}
}

build() {
  cd "$srcdir"/keyring-$pkgver
  python setup.py build

  cd "$srcdir"/keyring-$pkgver-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/keyring-$pkgver
  python setup.py pytest

  cd "$srcdir"/keyring-$pkgver-py2
  python2 setup.py pytest
}

package_python-keyring() {
  depends=('python-setuptools' 'python-secretstorage')
  optdepends=('python-keyrings-alt: Alternative backends')

  cd keyring-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1
}

package_python2-keyring() {
  depends=('python2-setuptools' 'python2-secretstorage')
  optdepends=('python2-keyrings-alt: Alternative backends')

  cd keyring-$pkgver-py2
  python2 setup.py install --root="$pkgdir" --optimize=1

  mv "$pkgdir"/usr/bin/keyring{,2}
}

# vim:set ts=2 sw=2 et:
