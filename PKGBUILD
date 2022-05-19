#!/bin/bash

# Created from the original PKGBUILD by ValHue <vhuelamo at gmail dot com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/fontfinder/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/fontfinder/discussions>


pkgname="fontfinder"
pkgver="1.4.1"
pkgrel="1"
pkgdesc="A Google font browser for your GTK desktop, written in Rust"
arch=(
    "x86_64"
    )
url="https://gitlab.com/mmstick/fontfinder"
license=(
    "MIT"
    )
depends=(
    "webkit2gtk" 
    "openssl-1.0"
    )
makedepends=(
    "rust"
    )
options=(
    "!emptydirs"
    )
provides=(
    "${pkgname}"
    )
source=(
    "${pkgname}-${pkgver}.tar.gz::${url}/-/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz"
    )
sha512sums=(
    "5684fde581d80db49f93652992b7aca63560f50d4ac35e4e7c017bed1b9da70feb16313aa3ee6d29f2f1fd02b8b5ca96920336a7341e800f852afe543b8821a1"
    )

build() {

    cd "${pkgname}-${pkgver}"

    sed -i "s|usr/local|usr|g" Makefile

    export OPENSSL_INCLUDE_DIR=/usr/include/openssl-1.0
    export OPENSSL_LIB_DIR=/usr/lib/openssl-1.0

    make
}

package() {

    cd "${pkgname}-${pkgver}"

    make DESTDIR=${pkgdir} install

    install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
