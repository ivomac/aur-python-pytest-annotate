# Maintainer: Ivo Maceira <ivomaceira at gmail dot com>
_base=pytest-annotate
pkgname="python-${_base}"
pkgver=1.0.5
pkgrel=1
pkgdesc="PyAnnotate as a pytest plugin."
arch=(any)
license=("Apache-2.0")
url="https://github.com/kensho-technologies/pytest-annotate"
depends=(python)
makedepends=(python-build python-installer python-setuptools python-wheel)
checkdepends=(python-pytest pyannotate)
source=("https://files.pythonhosted.org/packages/36/1b/bcc0d62ced8190773b2b0c778632e0806ede6d0fa2651af87661d3b66d12/${_base}-${pkgver}.tar.gz")
sha512sums=("d87c62a37ce2d0704466a83ca527513c1333525f38c4eeec31213ac75d03e8c84ebc51235f73882a32bc5495cd5a3696f2cd667320e048d8b7a827869c2f37ee")


build() {
  cd ${_base}-${pkgver}
  python -m build --wheel --skip-dependency-check --no-isolation
}

check() {
  cd ${_base}-${pkgver}
  python -m venv --system-site-packages test-env
  test-env/bin/python -m installer dist/*.whl
}

package() {
  cd ${_base}-${pkgver}
  PYTHONPYCACHEPREFIX="${PWD}/.cache/cpython/" python -m installer --destdir="${pkgdir}" dist/*.whl
  install -Dm644 README.md -t "$pkgdir/usr/share/doc/${pkgname}"
  install -Dm644 LICENSE.txt -t "$pkgdir/usr/share/licenses/${pkgname}"
}
