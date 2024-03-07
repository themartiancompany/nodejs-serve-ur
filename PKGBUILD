# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Filipe Bertelli <filipebertelli@tutanota.com>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>

_pkgbase=serve
pkgname=nodejs-$_pkgbase
pkgdesc='Quick HTTP server'
pkgver=14.2.1
pkgrel=1
arch=('any')
url='https://github.com/zeit/serve'
license=(
  'MIT'
)
depends=(
  'nodejs'
  'nodejs-inherits'
)
makedepends=(
  'npm'
)
_npm="http://registry.npmjs.org"
source=(
  "${_npm}/${_pkgbase}/-/${_pkgbase}-${pkgver}.tgz"
)
noextract=(
  "${_pkgbase}-${pkgver}.tgz"
)

package() {
  local \
    _npm_options=()
  _npm_options=(
    -g 
    # --user 
    #   root 
    --prefix 
      "$pkgdir"/usr
  )
  npm \
    install \
    "${_npm_options[@]}" \
    "${srcdir}/${_pkgbase}-${pkgver}.tgz"
  rm \
    -fr \
      "${pkgdir}/usr/etc"
  # Fix npm derp
  find \
    "${pkgdir}/usr" \
    -type \
      d \
    -exec \
      chmod \
        755 \
	'{}' \
	+
}

sha512sums=(
  'e3c7abe5fcc787b1824a12e73723c144f123b3623a401a33786af4da069a7113a2c92ffc011003963e7de63dfd8995c0a816c91c7fe2bc92723d1598f6c41664'
)

# vim:set sw=2 sts=-1 et:
