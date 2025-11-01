# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.


# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
#   Filipe Bertelli
#     <filipebertelli@tutanota.com>

_os="$( \
  uname \
    -o)"
_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_node="nodejs"
if [[ "${_os}" == "Android" ]]; then
  _node="nodejs-lts"
fi
if [[ ! -v "_npm" ]]; then
  _npm="true"
fi
if [[ ! -v "_git_http" ]]; then
  _git_http="github"
fi
_archive_format="tgz"
if [[ ! -v "${_archive_format}" ]]; then
  if [[ "${_npm}" == "false" ]]; then
    if [[ "${_git_http}" == "github" ]]; then
      _archive_format="zip"
    fi
  fi
fi
_pkg=serve
pkgbase="${_node}-${_pkg}"
pkgname=(
  "${pkgbase}"
)
_pkgdesc=(
  'Quick HTTP server'
)
pkgdesc="${_pkgdesc[*]}"
pkgver=14.2.5
pkgrel=1
arch=(
  'any'
)
_http="https://${_git_http}.com"
_ns="vercel"
url="${_http}/${_ns}/${_pkg}"
license=(
  'MIT'
)
depends=(
  "${_node}"
  "${_node}-inherits"
)
makedepends=(
)
if [[ "${_npm}" == "true" ]]; then
  makedepends+=(
    "npm"
  )
fi
_tarname="${_pkg}-${pkgver}"
_tarfile="${_tarname}.${_archive_format}"
_sum="c0d39ad4cb5b5991b3860eeeba64d8d4f1aeb8f28035b08e12fb86182ca7456f"
_sig_sum="1266c50d81a552dea0ba6ad4f435c83efb107bf056ceeaaddfb236f711f1be65"
# Dvorak
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
# Truocolo
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_uri="${_evmfs_dir}/${_sum}"
_evmfs_src="${_tarfile}::${_evmfs_uri}"
_sig_uri="${_evmfs_dir}/${_sig_sum}"
_sig_src="${_tarfile}.sig::${_sig_uri}"
_npm_http="http://registry.npmjs.org"
source=()
sha256sums=()
if [[ "${_evmfs}" == "true" ]]; then
  _uri="${_evmfs_uri}"
  source+=(
    "${_sig_src}"
  )
  sha256sums+=(
    "${_sig_sum}"
  )
elif [[ "${_evmfs}" == "true" ]]; then
  if [[ "${_npm}" == "true" ]]; then
    _uri="${_npm_http}/${_pkg}/-/${_tarfile}"
  fi
fi
_src="${_tarfile}::${_uri}"
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
noextract=(
  "${_tarfile}"
)

package_nodejs-serve() {
  local \
    _npm_options=() \
    _find_opts=()
  _npm_options=(
    -g 
    # --user 
    #   root 
    --prefix 
      "${pkgdir}/usr"
  )
  find_opts+=(
    -type
      "d"
    -exec
      chmod
        755
        '{}'
        +
  )
  npm \
    install \
    "${_npm_options[@]}" \
    "${srcdir}/${_pkg}-${pkgver}.tgz"
  rm \
    -fr \
      "${pkgdir}/usr/etc"
  # Fix npm derp
  find \
    "${pkgdir}/usr" \
    "${_find_opts[@]}"
}


# vim:set sw=2 sts=-1 et:
