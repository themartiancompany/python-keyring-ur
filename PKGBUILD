# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

pkgbase=python-keyring
pkgname=('python-keyring' 'python2-keyring')
pkgver=8.5.1
pkgrel=1
pkgdesc="Store and access your passwords safely."
arch=('any')
url="http://pypi.python.org/pypi/keyring"
license=('PSF' 'MIT')
source=("http://pypi.python.org/packages/source/k/keyring/keyring-$pkgver.tar.gz")
makedepends=('python-setuptools_scm' 'python2-setuptools_scm')
checkdepends=('python-pytest-runner' 'python2-pytest-runner' 'python-mock' 'python2-mock')
md5sums=('f358ae5f121d169424d32fcd7bd309f7')

prepare() {
  cp -a keyring-$pkgver{,-py2}
}

build() {
  cd "$srcdir/keyring-$pkgver"
  python setup.py build

  cd "$srcdir/keyring-$pkgver-py2"
  python2 setup.py build
}

check() {
  cd "$srcdir/keyring-$pkgver"
  python setup.py ptr

  cd "$srcdir/keyring-$pkgver-py2"
  python2 setup.py ptr
}

package_python-keyring() {
  depends=('python-setuptools')
  optdepends=('python-secretstorage: SecretService DBus API (GNOME/KDE)'
              'python-keyrings-alt: Alternative backends')

  cd "$srcdir/keyring-$pkgver"
  python setup.py install --root=$pkgdir --optimize=1
}

package_python2-keyring() {
  depends=('python2-setuptools')
  optdepends=('python2-secretstorage: SecretService DBus API (GNOME/KDE)'
              'python2-keyrings-alt: Alternative backends')

  cd "$srcdir/keyring-$pkgver-py2"
  python2 setup.py install --root=$pkgdir --optimize=1

  mv "$pkgdir"/usr/bin/keyring{,2}
}

# vim:set ts=2 sw=2 et:
