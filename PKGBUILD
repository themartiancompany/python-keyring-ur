# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

pkgbase=python-keyring
pkgname=('python-keyring' 'python2-keyring')
pkgver=5.3
pkgrel=1
pkgdesc="Store and access your passwords safely."
arch=('any')
url="http://pypi.python.org/pypi/keyring"
license=('PSF' 'MIT')
source=("http://pypi.python.org/packages/source/k/keyring/keyring-$pkgver.zip")
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-pytest' 'python2-pytest' 'python-mock' 'python2-mock' 'python-crypto' 'python2-crypto'
              'python-secretstorage' 'python2-secretstorage' 'python-gobject' 'python2-gobject' 'libgnome-keyring'
              'kdebindings-python' 'kdebindings-python2' 'python2-gdata')
md5sums=('fd50a2be4a44a78efb09a7c046b6410d')

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
  py.test

  cd "$srcdir/keyring-$pkgver-py2"
  py.test2
}

package_python-keyring() {
  depends=('python-setuptools')
  optdepends=('libgnome-keyring: Gnome integration'
            'python-gobject: Gnome integration'
            'kdebindings-python: Kde integration'
            'python-crypto: CLI keyring'
            'python-secretstorage: SecretService DBus API (GNOME/KDE)')

  cd "$srcdir/keyring-$pkgver"
  python setup.py install --root=$pkgdir --optimize=1
}

package_python2-keyring() {
  depends=('python2-setuptools')
  optdepends=('libgnome-keyring: Gnome integration'
            'python2-gobject: Gnome integration'
            'kdebindings-python2: Kde integration'
            'python2-crypto: CLI keyring'
            'python2-secretstorage: SecretService DBus API (GNOME/KDE)')

  cd "$srcdir/keyring-$pkgver-py2"
  python2 setup.py install --root=$pkgdir --optimize=1

  mv "$pkgdir"/usr/bin/keyring{,2}
}

# vim:set ts=2 sw=2 et:
