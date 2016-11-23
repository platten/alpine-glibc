# Maintainer: Glider Labs <team@gliderlabs.com>

pkgname="glibc"
pkgver="2.24"
_pkgrel="0"
pkgrel="3"
pkgdesc="GNU C Library compatibility layer"
arch="x86_64"
url="https://github.com/platten/alpine-glibc"
license="GPL"
source="https://github.com/platten/alpine-glibc/raw/master/glibc-bin-$pkgver-$_pkgrel-x86_64.tar.gz
nsswitch.conf
ld.so.conf"
subpackages="$pkgname-bin $pkgname-i18n"
triggers="$pkgname-bin.trigger=/lib:/usr/lib:/usr/glibc-compat/lib"

package() {
  mkdir -p "$pkgdir/lib64" "$pkgdir/usr/glibc-compat/lib/locale" "$pkgdir"/etc
  cp -a "$srcdir"/usr "$pkgdir"
  cp "$srcdir"/nsswitch.conf "$pkgdir"/etc/nsswitch.conf
  cp "$srcdir"/ld.so.conf "$pkgdir"/usr/glibc-compat/etc/ld.so.conf
  rm "$pkgdir"/usr/glibc-compat/etc/rpc
  rm -rf "$pkgdir"/usr/glibc-compat/bin
  rm -rf "$pkgdir"/usr/glibc-compat/sbin
  rm -rf "$pkgdir"/usr/glibc-compat/lib/gconv
  rm -rf "$pkgdir"/usr/glibc-compat/lib/getconf
  rm -rf "$pkgdir"/usr/glibc-compat/lib/audit
  rm -rf "$pkgdir"/usr/glibc-compat/lib/*.a
  rm -rf "$pkgdir"/usr/glibc-compat/include
  rm -rf "$pkgdir"/usr/glibc-compat/share
  rm -rf "$pkgdir"/usr/glibc-compat/var
  ln -s /usr/glibc-compat/lib/ld-linux-x86-64.so.2 ${pkgdir}/lib64/ld-linux-x86-64.so.2
  ln -s /usr/glibc-compat/etc/ld.so.cache ${pkgdir}/etc/ld.so.cache
}

bin() {
  depends="$pkgname libgcc"
  mkdir -p "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/glibc-compat/bin "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/glibc-compat/sbin "$subpkgdir"/usr/glibc-compat
}

i18n() {
  depends="$pkgname-bin"
  arch="noarch"
  mkdir -p "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/glibc-compat/share "$subpkgdir"/usr/glibc-compat
}

md5sums="9f95d81da94350ac4944ec5283ef37bf  glibc-bin-2.24-0-x86_64.tar.gz
5be984273de4203318c9c3fb0d4e9d2b  nsswitch.conf
b4a846d17bde75e47976d972c4e067a5  ld.so.conf"
sha256sums="d59b56a1db881b7d4d069c32f755b0598ed29bae5062cda42b4cfe09ff17374a  glibc-bin-2.24-0-x86_64.tar.gz
3be94785355b4b363d1268f133e198323441eafa6017b2b1fed32ae279d685c7  nsswitch.conf
c758b7c31c4d4f1f60b94bc1220adfb6d65b3614ea4b7aa277d7ded101da5772  ld.so.conf"
sha512sums="774ed3555eb112dd9979979ff7558cd219b11ec79a58fd48a9f07d7f6004302d1a8b47f644bbc92d2b0b0663845ba1290c3a70570d53582e87f354c9a4c69747  glibc-bin-2.24-0-x86_64.tar.gz
478bdd9f7da9e6453cca91ce0bd20eec031e7424e967696eb3947e3f21aa86067aaf614784b89a117279d8a939174498210eaaa2f277d3942d1ca7b4809d4b7e  nsswitch.conf
509dd981fb0cce9fcb257dfef40982d268b552de435a008b35d9e75b1df4648291061fd40d60bdaf370adb7076e2095767f9986663c3de4c4f0b21a092fd0716  ld.so.conf"
