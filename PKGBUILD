pkgname=niceclaw
pkgver=0.9.10
pkgrel=1
pkgdesc="Desktop AI agent for OpenClaw with bundled gateway runtime"
arch=('x86_64' 'aarch64')
url="https://github.com/NiceAIGC/NiceClaw"
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
  '09709fab3a8a30ba89a39ea29c59c3953e9d401f09b8339f7de455a2e914ab0837d7c32c032d7496af5aec88ad0052ebb1ee0960878516aa1afe40af87f6b857'
)
sha512sums_aarch64=(
  '5c0e247e6b0bb02bcb6b63edc4bfd8913676f5fcb59747ca0c3d173cfe598a050347c26accf2f8005445c6c904f221951f5a3e96d42bfb5ded91eb7216dfb7be'
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
