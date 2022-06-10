#!/bin/bash

# Based on the original PKGBUILD by René Wagner <rwagner at rw-net dot de> and John D Jones III AKA jnbek <jnbek1972 -_AT_- g m a i l -_Dot_- com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/perl-mp3-tag/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/perl-mp3-tag/discussions>

_relname="MP3-Tag"

pkgname="perl-mp3-tag"
pkgver="1.15"
pkgrel="3"
pkgdesc="Module for reading tags of MP3 audio files"
arch=(
  "any"
)
license=(
  "PerlArtistic"
  "GPL"
)
options=(
  "!emptydirs"
)
depends=(
  "perl"
)
url="https://metacpan.org/release/MP3-Tag"
_zipname="${_relname}-${pkgver}"
source=(
  "https://cpan.metacpan.org/authors/id/I/IL/ILYAZ/modules/${_zipname}.zip"
)
sha512sums=(
  "e0361e34583dc8d1742b40d2922e66de8d43180d99e52f8e34166c432619ca4611b8589c6acc0498384f9f0dd2e30189351c18e0bfe2a4ca96df60809683cbb3"
)

build() {
  (
    export PERL_MM_USE_DEFAULT=1 PERL5LIB="" \
      PERL_AUTOINSTALL=--skipdeps \
      PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR="${pkgdir}"" \
      PERL_MB_OPT="--installdirs vendor --destdir "${pkgdir}"" \
      MODULEBUILDRC=/dev/null

    cd "$srcdir/${_zipname}"
    /usr/bin/perl Makefile.PL
    make
  )
}

check() {
  cd "$srcdir/${_zipname}"
  (
    export PERL_MM_USE_DEFAULT=1 PERL5LIB=""
    make test
  )
}

package() {

  cd "$srcdir/${_zipname}"

  make install

  find "${pkgdir}" -name .packlist -o -name perllocal.pod -delete
}
