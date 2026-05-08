pkgname=niceclaw
pkgver=0.9.507
pkgrel=1
pkgdesc="Desktop AI agent for OpenClaw with bundled gateway runtime"
arch=('x86_64' 'aarch64')
url="https://claw.nicerouter.com/"
license=('AGPL-3.0-or-later')
depends=(
  'at-spi2-core'
  'gtk3'
  'libnotify'
  'libsecret'
  'libxss'
  'libxtst'
  'nss'
  'util-linux-libs'
  'xdg-utils'
)
optdepends=('libappindicator-gtk3: tray indicator support on some desktop environments')
options=('!strip')
source_x86_64=(
  "niceclaw-${pkgver}-x86_64.deb::https://pan.feidu.fit/d/%E5%BC%80%E5%8F%91/tmp/NiceClaw-${pkgver}-amd64-linux.deb"
)
source_aarch64=(
  "niceclaw-${pkgver}-aarch64.deb::https://pan.feidu.fit/d/%E5%BC%80%E5%8F%91/tmp/NiceClaw-${pkgver}-arm64-linux.deb"
)
sha512sums_x86_64=(
  'f3cfdc0264094ae689038ef03056ab860c7e87c8f981680d5b73b295afdc278bff4eff709695440d676fd35482ad4de5896e3898cbbdc8fd03c16313bf1a5329'
)
sha512sums_aarch64=(
  'a9e5a5710492d16a3c00f7439212f873babe0087daefee00722bdcd33b6494961f0e549720a1cf98cac83d0d23792ff9d94b0c30953a096b9b3625a20a3c709b'
)

package() {
  local _deb
  local _workdir="$srcdir/deb-extract"

  case "$CARCH" in
    x86_64)
      _deb="niceclaw-${pkgver}-x86_64.deb"
      ;;
    aarch64)
      _deb="niceclaw-${pkgver}-aarch64.deb"
      ;;
  esac

  rm -rf "$_workdir"
  mkdir -p "$_workdir"

  cd "$_workdir"
  ar x "$srcdir/$_deb"
  bsdtar -xf data.tar.xz -C "$pkgdir"

  install -d "$pkgdir/usr/bin"
  ln -sf /opt/NiceClaw/niceclaw "$pkgdir/usr/bin/niceclaw"
}
