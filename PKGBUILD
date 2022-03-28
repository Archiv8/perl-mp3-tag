#!/bin/bash

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: Tooling
# [ToDo]: Add files: User documentation
# [FixMe]: Namcap warnings and errors
# Contributor: Ross Clark <archiv8@artisteducator.com>

# Maintainer: René Wagner <rwagner at rw-net dot de>
# Contributor: John D Jones III AKA jnbek <jnbek1972 -_AT_- g m a i l -_Dot_- com>
# Generator  : CPANPLUS::Dist::Arch 1.32

pkgname="perl-mp3-tag"
pkgver="1.15"
pkgrel="2"
pkgdesc="Module for reading tags of MP3 audio files"
arch=("any")
license=("PerlArtistic" "GPL")
options=("!emptydirs")
depends=(
  "perl"
  )
makedepends=()
url="https://metacpan.org/release/MP3-Tag"
source=(
  "https://cpan.metacpan.org/authors/id/I/IL/ILYAZ/modules/MP3-Tag-1.15.zip"
)
sha256sums=(
  "aaac48f4637edca408fd79381bc0bff0f9b11bd8e1e94de059dae993365f56d1"
)
_distdir="MP3-Tag-1.15"

build() {
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""                 \
      PERL_AUTOINSTALL=--skipdeps                            \
      PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR="$pkgdir""     \
      PERL_MB_OPT="--installdirs vendor --destdir "$pkgdir"" \
      MODULEBUILDRC=/dev/null

    cd "$srcdir/$_distdir"
    /usr/bin/perl Makefile.PL
    make
  )
}

check() {
  cd "$srcdir/$_distdir"
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""
    make test
  )
}

package() {
  cd "$srcdir/$_distdir"
  make install

  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}

# Local Variables:
# mode: shell-script
# sh-basic-offset: 2
# End:
# vim:set ts=2 sw=2 et:
