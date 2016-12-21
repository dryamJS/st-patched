# Maintainer: mar77i <mar77i at mar77i dot ch>
# Past Maintainer: Gaetan Bisson <bisson@archlinux.org>
# Contributor: Scytrin dai Kinthra <scytrin@gmail.com>

pkgname=st-terminal
_pkgname=st
pkgver=0.7
pkgrel=1
pkgdesc='Simple virtual terminal emulator for X with official patches'

url='http://st.suckless.org/'
arch=('i686' 'x86_64')
license=('MIT')
options=('zipman')
depends=('libxft')
makedepends=('ncurses' 'libxext' 'git')

provides=("${_pkgname}")
conflicts=("${_pkgname}")

# include config.h and any patches you want to have applied here
source=('http://dl.suckless.org/st/st-0.7.tar.gz'	
	'config.h'
	'http://st.suckless.org/patches/st-clipboard-20160727-308bfbf.diff'
	'http://st.suckless.org/patches/st-delkey-20160727-308bfbf.diff'
	'http://st.suckless.org/patches/st-externalpipe-20160727-308bfbf.diff'
	'http://st.suckless.org/patches/st-hidecursor-20160727-308bfbf.diff'
	'http://st.suckless.org/patches/st-no_bold_colors-20160727-308bfbf.diff'
	'http://st.suckless.org/patches/st-solarized-both-20160727-308bfbf.diff'
	'http://st.suckless.org/patches/st-spoiler-20160727-308bfbf.diff'
	'http://st.suckless.org/patches/st-visualbell-20160727-308bfbf.diff'
	'http://st.suckless.org/patches/st-vertcenter-20160819-023225e.diff'
)


prepare() {	
	cd "${_pkgname}-${pkgver}"	
	for file in "${source[@]}"; do
		if [[ "$file" == "config.h" ]]; then
			# add config.h if present in source array
			# Note: this supersedes the above sed to config.def.h
			cp "$srcdir/$file" .
		elif [[ "$file" == *.diff || "$file" == *.patch ]]; then
			# add all patches present in source array
			patch -Np1 <"$srcdir/$(basename ${file})"

	
		fi
	done
}

build() {
	cd "${_pkgname}-${pkgver}"
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
	cd "${_pkgname}-${pkgver}"
	make PREFIX=/usr DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
	install -Dm644 README "${pkgdir}/usr/share/doc/${pkgname}/README"
}
md5sums=('29b2a599cf1511c8062ed8f025c84c63'
         'SKIP'
         '831b8bdc34b48a3290e39ac9aca2906f'
         '3bff87125eaf696f56230fb618d6eb90'
         '47d628501defd776efd0d4fbb1968895'
         '8ff8a77b34dfc09a4dd0d2cf876d68e7'
         '635b29fb7cb085ba445e909d7499f98e'
         'b7219cf14d214086c9bb573cc87d1465'
         '84941105ecbd96cf6db0f67a76696481'
         'e8d28e10e9b2a2d2a86e8de294eaa4c4'
         'bef82e822d8a02963fb8ede5829e04c6')
