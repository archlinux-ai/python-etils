# Maintainer: Luis Martinez <luis dot martinez at disroot dot org>
# Contributor: Chih-Hsuan Yen <yan12125@archlinux.org>
# Contributor: Daniel Bershatsky <archlinux-ai@daskol.xyz>

pkgname=python-etils
_pkgname="${pkgname#python-}"
pkgver=1.3.0
pkgrel=1
pkgdesc='Collection of eclectic utils for python'
url='https://github.com/google/etils'
license=('Apache')
arch=('any')
depends=('python-typing_extensions')
makedepends=('python-build' 'python-flit-core' 'python-installer')
# NOTE Do not run tests. Assume that it is tested well since we does not have
# binary dependencies here.
# checkdepends=(
#   'python-chex'
#   'python-jax'
#   'python-pylint'
#   'python-pytest'
#   'python-pytest-subtests'
#   'python-pytest-xdist'
#   'python-pytorch'
#   'python-tensorflow'
# )
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
source=("$pkgname-$pkgver.tar.gz::https://github.com/google/${_pkgname}/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('9316f84d6d94716ce4260f02d812dadc36ea9e5a1b2ff4ab542b9069b547904a')

build() {
	python -m build -nw $_pkgname-$pkgver
}

package() {
    python -m installer \
        --compile-bytecode 1 \
        --destdir $pkgdir \
        $_pkgname-$pkgver/dist/$_pkgname-*.whl
}
