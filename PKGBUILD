# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

pkgbase=python-keyring
pkgname=('python-keyring' 'python2-keyring')
pkgver=10.3.3
pkgrel=1
pkgdesc="Store and access your passwords safely."
arch=('any')
url="http://pypi.python.org/pypi/keyring"
license=('PSF' 'MIT')
source=("https://pypi.io/packages/source/k/keyring/keyring-$pkgver.tar.gz")
makedepends=('python-setuptools_scm' 'python2-setuptools_scm' 'python-secretstorage'
             'python2-secretstorage')
checkdepends=('python-pytest-runner' 'python2-pytest-runner')
sha512sums=('6087b9553d3a8df4abbcc0bacc18d769fda04c092781bd79817ceb5984a2548b5c3a4a2bda15a95040b9db59750a91d8eebbc2420d5f9dbd2fa3d6f10884e26a')

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
  python setup.py ptr

  cd "$srcdir"/keyring-$pkgver-py2
  python2 setup.py ptr
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
