pkgname='perl-memory-usage'
pkgver='0.201'
pkgrel='1'
pkgdesc="Memory::Usage - Tools to determine actual memory usage"
arch=('any')
license=('PerlArtistic' 'GPL')
options=('!emptydirs')
depends=('perl')
makedepends=()
url='http://search.cpan.org/perldoc?Memory::Usage'
source=("http://search.cpan.org/CPAN/authors/id/D/DO/DONEILL/Memory-Usage-$pkgver.tar.gz")
md5sums=('8a71930b4ed847508b1dd35b79f76a5c')

build() {
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""                 \
      PERL_AUTOINSTALL=--skipdeps                            \
      PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'"     \
      PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
      MODULEBUILDRC=/dev/null

    cd "${srcdir}/Memory-Usage-$pkgver" 
    /usr/bin/perl Makefile.PL
    make
  )
}

check() {
  cd "${srcdir}/Memory-Usage-$pkgver"
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""
    make test
  )
}

package() {
  cd "${srcdir}/Memory-Usage-$pkgver"
  make install
  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}
