# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

pkgbase=python-keyring
pkgname=('python-keyring' 'python2-keyring')
pkgver=10.5.1
pkgrel=1
pkgdesc="Store and access your passwords safely."
arch=('any')
url="http://pypi.python.org/pypi/keyring"
license=('PSF' 'MIT')
source=("https://pypi.io/packages/source/k/keyring/keyring-$pkgver.tar.gz")
makedepends=('python-setuptools_scm' 'python2-setuptools_scm' 'python-secretstorage'
             'python2-secretstorage')
checkdepends=('python-pytest-runner' 'python2-pytest-runner')
sha512sums=('2e18487c061d67b866390e4f2f740ceb281b75e9ead01c00e2851aec9f56cffb6268334b35d64b498eaa719639fceceb29cf6adf46c6930e3506c04f672e897c')

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
