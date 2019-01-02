# Maintainer: Filipe Laíns (FFY00) <lains@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

pkgbase=python-keyring
_pkgname=${pkgbase#python-}
pkgname=(python-$_pkgname python2-$_pkgname)
pkgver=17.1.1
pkgrel=1
pkgdesc="Store and access your passwords safely."
arch=('any')
url="https://github.com/jaraco/keyring"
license=('PSF' 'MIT')
optdepends=('python-keyrings-alt: Alternative backends')
makedepends=('python-setuptools-scm' 'python2-setuptools-scm' 'python-entrypoints'
             'python2-entrypoints' 'python-secretstorage' 'python2-secretstorage')
checkdepends=('python-pytest-flake8' 'python-pytest-runner' 'python2-pytest-flake8'
              'python2-pytest-runner' 'python-dbus' 'python2-dbus')
source=("https://pypi.io/packages/source/${_pkgname:0:1}/$_pkgname/$_pkgname-$pkgver.tar.gz")
sha512sums=('19fb785376db8e1e7a87917b29e8094e14d689ac60cd299047c4e8fa3ecdb029c377df0b77bd2c89a463ddaa9eae165b5355d8d7e7d758fd367dd50cd0d06f1a')

prepare() {
  cp -a $_pkgname-$pkgver{,-py2}
}

build() {
  echo "Building python-$_pkgname $pkgver"
  cd "$srcdir"/$_pkgname-$pkgver
  python setup.py build

  echo "Building python2-$_pkgname $pkgver"
  cd "$srcdir"/$_pkgname-$pkgver-py2
  python2 setup.py build
}

check() {
  echo "Running tests on python-$_pkgname $pkgver"
  cd "$srcdir"/$_pkgname-$pkgver
  python setup.py pytest

  echo "Running tests on python2-$_pkgname $pkgver"
  cd "$srcdir"/$_pkgname-$pkgver-py2
  python2 setup.py pytest
}

package_python-keyring() {
  depends=('python-entrypoints' 'python-secretstorage')
  optdepends=('python-dbus: for kwallet backend')
  cd $_pkgname-$pkgver

  python setup.py install --root="$pkgdir" --optimize=1 --skip-build
  install -Dm 644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

package_python2-keyring() {
  depends=('python2-entrypoints' 'python2-secretstorage')
  optdepends=('python2-dbus: for kwallet backend')
  cd $_pkgname-$pkgver-py2

  python2 setup.py install --root="$pkgdir" --optimize=1 --skip-build
  mv "$pkgdir"/usr/bin/keyring "$pkgdir"/usr/bin/keyring2 # Fix the binary name
  install -Dm 644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

# vim:set ts=2 sw=2 et:
