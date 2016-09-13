# Maintainer: Andreas Grapentin <andreas@grapentin.org>
pkgname=vmdebootstrap
pkgver=1.4
pkgrel=1
pkgdesc="Create Debian disk images"
arch=('i686' 'x86_64')

url="http://git.liw.fi/cgi-bin/cgit/cgit.cgi/vmdebootstrap/"
license=('GPL3')

depends=('debootstrap'
         'syslinux'
         'qemu'
         'parted'
         'multipath-tools'
         'python2-cliapp'
	 'python2-setuptools'
         'distro-info')

source=("http://git.liw.fi/cgi-bin/cgit/cgit.cgi/$pkgname/snapshot/$pkgname-$pkgver.tar.gz"
        'python_version.patch'
        'default_arch.patch'
        'fix_path.patch')

md5sums=('5eb3152436c64957eb61299f1cd495d2'
         '7a15de579dcecaaba83554dbb3760780'
         '3c3d9df067faa0d742011ad0943427e9'
         '806fd64966193e9ae0fb4ab56ab7f3f9')


prepare() {
  cd "$pkgname-$pkgver"

  patch -p1 < ../python_version.patch
  patch -p1 < ../default_arch.patch
  patch -p1 < ../fix_path.patch
}

package() {
	cd "$pkgname-$pkgver"

  python2 setup.py install --root="${pkgdir}/" --optimize=1
  mkdir -p ${pkgdir}/usr/share/doc/$pkgname
  cp COPYING ${pkgdir}/usr/share/doc/$pkgname
  cp README ${pkgdir}/usr/share/doc/$pkgname
  mkdir -p ${pkgdir}/usr/share/licenses/$pkgname
  cd ${pkgdir}/usr/share/licenses/$pkgname
  ln -s ../../doc/$pkgname/COPING COPYING
}
