#
#

pkgname=backupd
pkgdesc="Compressed and encrypted backups with 7zip and GPG"
pkgver=0.1
pkgrel=1
arch=('any')
url="https://github.com/gustawho/backupd"
license=("GPL3")
makedepends=('git')
depends=('p7zip')
source=("git://github.com/gustawho/${pkgname}.git")
md5sums=('SKIP')

package() {
  cd "$srcdir/${pkgname}"
  mkdir -p $pkgdir/usr/lib/systemd/user/ $pkgdir/usr/bin/
  install -m644 backupd "$pkgdir/usr/bin/"
  install -m644 backupd-daemon "$pkgdir/usr/bin/"
  install -m644 backupd.service "$pkgdir/usr/lib/systemd/user/"
  install -m644 backupd.timer "$pkgdir/usr/lib/systemd/user/"
}