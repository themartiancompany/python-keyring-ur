# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer:  Truocolo <truocolo@aol.com>
# Maintainer:  Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer:  Filipe Laíns (FFY00) <lains@archlinux.org>
# Contributor: Johannes Dewender  arch at JonnyJD dot net
# Contributor: Ivan Sichmann Freitas <ivansichfreitas@gmail.com>
# Contributor: Brice Maron <brice@bmaron.net>
# Contributor: Nuno Araujo <nuno.araujo at russo79.com>
# Contributor: Steven Allen <steven {at} stebalien {dot} com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=keyring
pkgname="${_py}-${_pkg}"
pkgver=25.2.1
pkgrel=1
pkgdesc='Store and access your passwords safely'
arch=(
  'any'
)
_http="https://github.com"
_ns="jaraco"
url="${_http}/${_ns}/${_pkg}"
license=(
  'PSF-2.0'
  'MIT'
)
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
  "${_py}-jaraco.classes"
  "${_py}-secretstorage"
  "${_py}-jaraco.functools"
  "${_py}-jaraco.context"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-setuptools-scm"
  "${_py}-wheel"
)
checkdepends=(
  "${_py}-pytest"
)
optdepends=(
  "${_py}-keyrings-alt: Alternative backends"
  "${_py}-dbus: kwallet backend"
)
_pypa="https://files.pythonhosted.org/packages/source"
source=(
  "${_pypa}/${_pkg::1}/${_pkg}/${_pkg}-${pkgver}.tar.gz"
)
sha512sums=(
  '4512c79a1f0c05cd5d28919f55f19c142488d69d9bf7a27e9d7b3aace36535cf43a4522a4ea4b4738f21c82a6980932bd9d1c7ae62592242c333161e791cdb2e'
)
b2sums=(
  '706eb0cb1cb5e7f22e603df3b2ab9c95421a389d5bec8034ac452d37e754564379d6133a195e7c7fcbb1f96a8f964e5de505a39dce1da72090daad01d144c213'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  rm \
    "tests/backends/test_"{"Windows","macOS"}".py"
  "${_py}" \
    -m \
      pytest \
    --deselect \
      tests/backends/test_chainer.py
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm 644 \
    LICENSE \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  local \
    site_packages=$( \
      python \
        -c \
        "import site; print(site.getsitepackages()[0])")
  rm \
    -rf \
    "${pkgdir}/${site_packages}/${_name}/tests"
}

# vim:set ts=2 sw=2 et:
