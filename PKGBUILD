# Mantainer: Rogof <rogof /at/ gmx /dot/ com>
# Contributor: Felix Hanley <felix /at/ seconddrawer /dot/ com /dot/ au>

pkgname=multimarkdown
pkgver=4.7.1
pkgrel=1
pkgdesc="C implementation of MultiMarkdown"
url="http://fletcherpenney.net/multimarkdown/"
license=('GPL2' 'MIT')
arch=('i686' 'x86_64')
depends=('bash')
makedepends=('glib2' 'git')
optdepends=('texlive-most: latex and PDF output support')
options=(!buildflags)
source=("multimarkdown::git+https://github.com/fletcher/MultiMarkdown-4.git#tag=${pkgver}")
sha1sums=('SKIP')

prepare() {
    cd "$srcdir/multimarkdown"
    git submodule init && git submodule update
    touch greg/greg.c
}

build() {
    cd "$srcdir/multimarkdown"
    make
}

package() {
    cd "$srcdir/multimarkdown"

    install -dm755 "$pkgdir/usr/bin"
    install -Dm755 multimarkdown \
        scripts/mmd2tex \
        scripts/mmd2pdf \
        scripts/mmd2opml \
        scripts/mmd2odf \
        scripts/mmd2all \
        "$pkgdir/usr/bin/"

    install -dm755 "$pkgdir/usr/share/doc/$pkgname"
    cp -a documentation/* "$pkgdir/usr/share/doc/$pkgname"

    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
