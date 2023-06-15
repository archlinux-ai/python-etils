# Maintainer: Luis Martinez <luis dot martinez at disroot dot org>
# Contributor: Chih-Hsuan Yen <yan12125@archlinux.org>
# Contributor: Daniel Bershatsky <bepshatsky@yandex.ru>

pkgname=python-etils
_pkg="${pkgname#python-}"
pkgver=1.0.0
pkgrel=2
pkgdesc='Collection of eclectic utils for python'
url='https://github.com/google/etils'
license=('Apache')
arch=('any')
depends=('python-typing_extensions')
makedepends=('python-build' 'python-flit-core' 'python-installer')
# Not including python-jax as build fails
# (https://github.com/google/jax/issues/7712)
checkdepends=(
  'python-chex'
  'python-pylint'
  'python-pytest'
  'python-pytest-subtests'
  'python-pytest-xdist'
  'python-pytorch'
)
# See https://github.com/google/etils/blob/main/pyproject.toml for optional
# dependencies
optdepends=(
  'ipython: for etils.ecolab'
  'python-absl: for etils.eap, etils.etqdm'
  'python-dm-tree: for etils.etree.tree'
  'python-importlib_resources: for epath'
  'python-jax: for etils.etree.jax'
  'python-mediapy: for etils.ecolab'
  'python-numpy: for etils.array_types, etils.ecolab, etils.enp'
  'python-simple-parsing: for etils.eap'
  'python-tensorflow: for etils.etree.nest'
  'python-tqdm: for etils.etqdm'
  'python-zipp: for etils.epath'
)
source=("$pkgname-$pkgver.tar.gz::https://files.pythonhosted.org/packages/source/e/$_pkg/$_pkg-$pkgver.tar.gz")
sha256sums=('d10982f7702422bea8635d5284b8bed629f51919fc122ac1e1e4abf45ec8f785')

build() {
	cd etils-$pkgver
	python -m build --wheel --no-isolation
}

check() {
    cd etils-$pkgver
    # etils/eapp: needs simple_parsing
    # etils/enp, etils/etree/tree_utils_test.py: needs jax
    # etils/ecolab: needs mediapy
    # etils/edc/frozen_utils_test.py: needs chex
    pytest \
        --ignore etils/eapp \
        --ignore etils/ecolab \
        --ignore etils/edc/frozen_utils_test.py \
        --ignore etils/enp \
        --ignore etils/etree/tree_utils_test.py
}

package() {
    cd etils-$pkgver
    python -m installer --destdir="$pkgdir" dist/*.whl
}
