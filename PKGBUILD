# Maintainer: Andreas Grapentin <andreas@grapentin.org>
pkgname=vmdebootstrap
pkgver=0.5
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

md5sums=('4a6ca9ac18e9a9b906e74620c3993d16'
         'd472f9f42e356d76dc20d4a46ac2d39f'
         'c9d9f83dd199be54507e52169e1873b2'
         'f6326700d8a7bfbd4cf6460545cff4f6')


prepare() {
  cd "$pkgname-$pkgver"

  patch -p1 < ../python_version.patch
  patch -p1 < ../default_arch.patch
  patch -p1 < ../fix_path.patch
}

package() {
  cd "$pkgname-$pkgver"

  mkdir -p ${pkgdir}/usr/bin
  install -g0 -o0 -m 0755 vmdebootstrap ${pkgdir}/usr/bin/
  mkdir -p ${pkgdir}/usr/local/man/man8
  install -g0 -o0 -m 0644 vmdebootstrap.8.in ${pkgdir}/usr/local/man/man8/vmdebootstrap.8
  gzip ${pkgdir}/usr/local/man/man8/vmdebootstrap.8

  mkdir -p ${pkgdir}/usr/share/doc/$pkgname
  cp COPYING ${pkgdir}/usr/share/doc/$pkgname
  cp README ${pkgdir}/usr/share/doc/$pkgname
  mkdir -p ${pkgdir}/usr/share/licenses/$pkgname
  cd ${pkgdir}/usr/share/licenses/$pkgname
  ln -s ../../doc/$pkgname/COPING COPYING
}
