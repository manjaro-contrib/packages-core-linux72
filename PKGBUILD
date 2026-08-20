# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Contributor: Bernhard Landauer <bernhard@manjaro.org>
# Contributor: Jan Alexander Steffens (heftig) <heftig@archlinux.org>

_basekernel=7.2
_basever=${_basekernel//.}
_kernelname=-MANJARO
_commit=
_rc=
pkgbase=linux${_basever}
pkgver=7.2.0
pkgrel=2
arch=('x86_64')
url="https://www.kernel.org/"
license=(GPL-2.0-only)
makedepends=(
  bc
  binutils
  cpio
  gettext
  glibc
  libelf
  libgcc
  openssl
  pahole
  perl
  python
  rust
  rust-bindgen
  rust-src
  tar
  xxhash
  xz
  zlib
  zstd
)
options=(
  !debug
  !strip
)
source=(https://www.kernel.org/pub/linux/kernel/v7.x/linux-${_basekernel}.tar.xz
        #https://github.com/torvalds/linux/archive/refs/tags/v${_basekernel}.tar.gz
        #https://git.kernel.org/torvalds/t/linux-${_basekernel}-${_rc}.tar.gz
        #linux-${_basekernel}-${_rc}.tar.gz::https://github.com/torvalds/linux/archive/${_commit}.tar.gz
        #https://www.kernel.org/pub/linux/kernel/v7.x/patch-${pkgver}.xz
        config
        # ARCH Patches
        0001-add-sysctl-to-disallow-unprivileged-CLONE_NEWUSER-by.patch
        0002-drivers-firmware-skip-simpledrm-if-nvidia-drm.modese.patch
        # Upstream Patches
        0000-drm-amdgpu-fix-race-condition-in-amdgpu_vm_wait_idle-during-process-kill.patch
        # Turn off custom brightness-curve when nonsense is found in BIOS
        0001-drm-amd-Sanity-check-custom-brightness-curve-data-po.patch
        # From Valve for Upstream (fixes suspend on deck target in inputplumber)
        0000-usb-vhci-hcd-Unconditionally-allow-system-suspend.patch
        # Manjaro Patches
        # Realtek patch
        0999-patch_realtek.patch
        # ROG ALLY Patches
        # https://github.com/OpenGamingCollective/linux/pull/11
        0001-FOR-UPSTREAM-hid-asus-ally-Add-joystick-LED-ring-sup.patch
        0002-FOR-UPSTREAM-hid-asus-ally-do-MCY-FW-validation-in-h.patch
        0003-FOR-UPSTREAM-hid-asus-ally-initial-Ally-X-gamepad-br.patch
        0004-FOR-UPSTREAM-hid-asus-ally-initial-gamepad-configura.patch
        0005-FOR-UPSTREAM-hid-asus-ally-add-button-remap-attribut.patch
        0006-FOR-UPSTREAM-hid-asus-ally-add-gamepad-mode-selectio.patch
        0007-FOR-UPSTREAM-hid-asus-ally-Turbo-settings-for-button.patch
        0008-FOR-UPSTREAM-hid-asus-ally-add-vibration-intensity-s.patch
        0009-FOR-UPSTREAM-hid-asus-ally-add-JS-deadzones.patch
        0010-FOR-UPSTREAM-hid-asus-ally-add-trigger-deadzones.patch
        0011-FOR-UPSTREAM-hid-asus-ally-add-anti-deadzones.patch
        0012-FOR-UPSTREAM-hid-asus-ally-add-JS-response-curves.patch
        0013-FOR-UPSTREAM-hid-asus-ally-mcu_version-attribute.patch
        0014-FOR-UPSTREAM-hid-asus-ally-add-calibrations-wip.patch
        0015-FOR-UPSTREAM-debug-by-default.patch
        0016-FOR-UPSTREAM-hid-asus-ally-grab-short-press-QAM-on-R.patch
        0017-FOR-UPSTREAM-hid-asus-ally-disable-wakeup-attribute-.patch
        # OrangePi Neo patches
        0001-iio-imu-bmi270-Match-PNP-ID-found-on-newer-OrangePi-NEO-firmware.patch
        # Zotac Zone patches
        0001-zotac-zone-hid-initial-impl.patch
        0002-xpad-gate-the-zotac-zone-PID-behind-if-IS_REACHABLE-.patch
        0003-tmp-apply-zotac-screen-quirk.patch
        0005-zone-fix-6.15-rename-del_timer-to-timer_delete.patch
        # Steamdeck (OLED)
        0001-steam-deck.patch
        #iwlwifi: Fix firmware version handling
        0000-iwlwifi-fix.patch
)

if [[ ! -z "$_commit" ]]; then
  _srcdir="linux-${_commit}"
elif [[ ! -z "$_rc" ]]; then
  _srcdir="linux-${_basekernel}-${_rc}"
else
  _srcdir="linux-${_basekernel}"
fi

sha256sums=('f9fef3d14c0df53819026f4be74459835c2a0b0dcbf5b5bbd9ea19f0829402b3'
            'd258dcf30a3cd66f75691f71a10243b6769967cc06212f406cf818c24b1fa6e5'
            'e5e98d62b63704cecdf32dbe6a9bafea6e70b23fa8e01fe96ca220ac6036392e'
            'c21170eba77438abb8b8ab02aeccf16bfb2467a01303509945aa6b3a0fd16d31'
            '37f3222fafbe67dec3740933be37867e0c378468f71e9a6d5d6a07c2a2a568fe'
            'cacb08b2f43a9fd09053bffaacc4b7bdf8381772f26e61825fb696ded100af57'
            '512032c6b93fce24254da6cace7bf101c8f7c824761a0f99deed4b7724ac6f3e'
            '103688f3fceff664c919d94faab7a6948880710641110eaa71fe107ee06c37e9'
            'fdb4994534e896bcfa83a4f5764c8e2039f77c708f04cd1e4fc0ec1fc824c15e'
            'a1e9a20dc86c2ea5ed5736336656f74e789f2c6c12704896c9f7e32729988500'
            '82252a10edeb5848fb3ad6f79211b669894ebe07ebdb7c8f2ad72f1b0bd91364'
            '2844e5b8e34da0b48020d3bb0e57724848f5f01683a29ec63019d1b164ecf509'
            '4dca4da1dc5b21da4ebafe6c5072c0596eb530ab9e5603ddf0ccad2208146cac'
            '755083d2f4093b2faa7a8ac0fee53fbc6b527a076af1698e97bf94b717891abd'
            '68d500aab543edff8c5e3298d3be6fa0b78f700fb490ca52d14cb84051ffda15'
            '0b4eeafdeddfd00938584f6e8e31f0316aa0245ada5db7d1492c455175ad7076'
            '0e078d413f5c10fb39fb45608e49b3c58b3154df9c3cc79f0a5a21296a92f535'
            '651dc8efc28cd03b145342db5a6446a80a7aa4bd7064e3ab1832292181951614'
            'f7cabd28d1c7e4492c9c685d41676a16d0887221c76b3257dc4653e8cbbd0239'
            '4dd33735647768755c07ca55f7c9aa0ead9a20ae2d929b2ade840a992d5fe08e'
            '8bdcf5f00387d93086dde4748f5155a21b90b87e0fd562a127c365df6395b3eb'
            '1dc1f5cc60e7f1298b4f3deea12dd9e6c47454fecee55b5f46888f22aec09b03'
            '7cd498aab2ec929315848366ca07b379315db7c081bf463f6590146534fb651c'
            '54841d11451eaea6eab712184a84fe3f119c1b5365fbca0c927129ebde3c16e8'
            '73ed3550e05774836772418418a5089d43709b1796c42141e75dbe78584369d8'
            'fc358dd3b574e4f47d25952417107ca0e743d33125ed93866697a266cde9b76e'
            'b67f25c13e946b51712b0e828ebbf8bea980d339bd6effab17869f6a62e428df'
            'f53e0ad0892ab4bd85f55b4cbb829481eba28865cf835a46c80bc237e0771981'
            '138684588665b8f651dffb4e75c265a2b81f6bd7a606f75f8fc6814a4a63d3fd'
            '3d37e1f54290bad1b7a4c5c45046341dc4c1bfc2f8648b7754bf0bd9705b3a35'
            'f8cf8ad3e17857b51c3f7dd954eb5ac7ba44bfe0302a40e70b2c496573407edf'
            '9628a67ac23beaf2de7194d2934386944adc64cb2a4a90e4c38b867b868654b4')

export KBUILD_BUILD_HOST=manjaro
export KBUILD_BUILD_USER=$pkgbase
export KBUILD_BUILD_TIMESTAMP="$(date -Ru${SOURCE_DATE_EPOCH:+d @$SOURCE_DATE_EPOCH})"

prepare() {
  cd $_srcdir

  #msg "set PATCHLEVEL to 2"
  #sed -ri "s|^(PATCHLEVEL =).*|\1 2|" Makefile

  #msg "set EXTRAVERSION to ${_rc}"
  #sed -ri "s|^(EXTRAVERSION =).*|\1 -${_rc}|" Makefile

  echo "Setting version..."
  echo "-$pkgrel" > localversion.10-pkgrel

  # add upstream patch
  if [[ -z "$_rc" ]] && [[ -e "../patch-${pkgver}" ]]; then
    msg "add upstream patch"
    patch -p1 -i "../patch-${pkgver}"
  fi

  local src
  for src in "${source[@]}"; do
    src="${src%%::*}"
    src="${src##*/}"
    src="${src%.zst}"
    [[ $src = *.patch ]] || continue
    echo "Applying patch $src..."
    patch -Np1 < "../$src"
  done

  echo "Setting config..."
  cp ../config .config
  make olddefconfig
  diff -u ../config .config || :

  make -s kernelrelease > version
  msg "Prepared $pkgbase version $(<version)"
}

build() {
  cd $_srcdir
  make ${MAKEFLAGS} bzImage modules
  make -C tools/bpf/bpftool vmlinux.h feature-clang-bpf-co-re=1
}

_package() {
  pkgdesc="The Linux $_basekernel kernel and modules"
  depends=(
    'coreutils'
    'initramfs'
    'kmod'
  )
  optdepends=(
    'linux-headers: headers and scripts for building modules'
    'linux-firmware: firmware images needed for some devices'
    'scx-scheds: to use sched-ext schedulers'
    'wireless-regdb: to set the correct wireless channels of your country'
  )
  provides=(
    "linux=${pkgver}"
    KSMBD-MODULE
    NTSYNC-MODULE
    VIRTUALBOX-GUEST-MODULES
    WIREGUARD-MODULE
  )
  replaces=(
    virtualbox-guest-modules
    wireguard
  )

  cd $_srcdir
  local modulesdir="$pkgdir/usr/lib/modules/$(<version)"

  echo "Installing boot image..."
  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  install -Dm644 "$(make -s image_name)" "$modulesdir/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "$pkgbase" | install -Dm644 /dev/stdin "$modulesdir/pkgbase"
  echo "${_basekernel}-${CARCH}" | install -Dm644 /dev/stdin "$modulesdir/kernelbase"

  # add kernel version
  mkdir -p "${pkgdir}/boot"
  echo "$(<version) x64" > "${pkgdir}/boot/${pkgbase}-${CARCH}.kver"

  echo "Installing modules..."
  ZSTD_CLEVEL=19 make INSTALL_MOD_PATH="$pkgdir/usr" INSTALL_MOD_STRIP=1 \
    DEPMOD=/doesnt/exist modules_install  # Suppress depmod

  # remove build link
  rm "$modulesdir"/build

  # now we call depmod...
  depmod -b "${pkgdir}/usr" -F System.map "$(<version)"
}

_package-headers() {
  pkgdesc="Headers and scripts for building modules for the Linux $_basekernel kernel"
  depends=(
    binutils
    glibc
    libelf
    libgcc
    openssl
    pahole
    xxhash
    zlib
    zstd
  )
  provides=('LINUX-HEADERS' "linux-headers=$pkgver")

  cd $_srcdir
  local builddir="$pkgdir/usr/lib/modules/$(<version)/build"

  echo "Installing build files..."
  install -Dt "$builddir" -m644 .config Makefile Module.symvers System.map \
    localversion.* version vmlinux tools/bpf/bpftool/vmlinux.h
  install -Dt "$builddir/kernel" -m644 kernel/Makefile
  install -Dt "$builddir/arch/x86" -m644 arch/x86/Makefile
  cp -t "$builddir" -a scripts
  ln -srt "$builddir" "$builddir/scripts/gdb/vmlinux-gdb.py"

  # required when STACK_VALIDATION is enabled
  install -Dt "$builddir/tools/objtool" tools/objtool/objtool

  # required when DEBUG_INFO_BTF_MODULES is enabled
  install -Dt "$builddir/tools/bpf/resolve_btfids" tools/bpf/resolve_btfids/resolve_btfids

  echo "Installing headers..."
  cp -t "$builddir" -a include
  cp -t "$builddir/arch/x86" -a arch/x86/include
  install -Dt "$builddir/arch/x86/kernel" -m644 arch/x86/kernel/asm-offsets.s

  install -Dt "$builddir/drivers/md" -m644 drivers/md/*.h
  install -Dt "$builddir/net/mac80211" -m644 net/mac80211/*.h

  # https://bugs.archlinux.org/task/13146
  install -Dt "$builddir/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # https://bugs.archlinux.org/task/20402
  install -Dt "$builddir/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "$builddir/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "$builddir/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # https://bugs.archlinux.org/task/71392
  install -Dt "$builddir/drivers/iio/common/hid-sensors" -m644 drivers/iio/common/hid-sensors/*.h

  echo "Installing KConfig files..."
  find . -name 'Kconfig*' -exec install -Dm644 {} "$builddir/{}" \;

  echo "Removing unneeded architectures..."
  local arch
  for arch in "$builddir"/arch/*/; do
    [[ $arch = */x86/ ]] && continue
    echo "Removing $(basename "$arch")"
    rm -r "$arch"
  done

  echo "Removing documentation..."
  rm -r "$builddir/Documentation"

  echo "Removing broken symlinks..."
  find -L "$builddir" -type l -printf 'Removing %P\n' -delete

  echo "Removing loose objects..."
  find "$builddir" -type f -name '*.o' -printf 'Removing %P\n' -delete

  echo "Stripping build tools..."
  local file
  while read -rd '' file; do
    case "$(file -Sib "$file")" in
      application/x-sharedlib\;*)      # Libraries (.so)
        strip -v $STRIP_SHARED "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip -v $STRIP_STATIC "$file" ;;
      application/x-executable\;*)     # Binaries
        strip -v $STRIP_BINARIES "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip -v $STRIP_SHARED "$file" ;;
    esac
  done < <(find "$builddir" -type f -perm -u+x ! -name vmlinux -print0)

  echo "Stripping vmlinux..."
  strip -v $STRIP_STATIC "$builddir/vmlinux"

  echo "Adding symlink..."
  mkdir -p "$pkgdir/usr/src"
  ln -sr "$builddir" "$pkgdir/usr/src/$pkgbase"
}

pkgname=(
  "$pkgbase"
  "$pkgbase-headers"
)
for _p in "${pkgname[@]}"; do
  eval "package_$_p() {
    $(declare -f "_package${_p#$pkgbase}")
    _package${_p#$pkgbase}
  }"
done
