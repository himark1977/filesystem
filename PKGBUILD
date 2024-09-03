# Maintainer: David Runge <dvzrv@archlinux.org>
# Maintainer: Sébastien Luttringer
# Contributor: Tom Gundersen <teg@jklm.no>

pkgname=filesystem
pkgver=2024.04.07
pkgrel=1
pkgdesc='Base Arch Linux files'
arch=('any')
license=('GPL-3.0-or-later')
url='https://archlinux.org'
depends=('iana-etc')
backup=(
  'etc/crypttab'
  'etc/fstab'
  'etc/group'
  'etc/gshadow'
  'etc/host.conf'
  'etc/hosts'
  'etc/issue'
  'etc/ld.so.conf'
  'etc/nsswitch.conf'
  'etc/passwd'
  'etc/profile'
  'etc/resolv.conf'
  'etc/securetty'
  'etc/shadow'
  'etc/shells'
  'etc/subgid'
  'etc/subuid'
)
source=(
  'arch-release'
  'monadi-logo.png'
  'monadi-logo.svg'
  'archlinux-logo-text.svg'
  'archlinux-logo-text-dark.svg'
  'crypttab'
  'env-generator'
  'fstab'
  'group'
  'gshadow'
  'host.conf'
  'hosts'
  'issue'
  'ld.so.conf'
  'locale.sh'
  'nsswitch.conf'
  'os-release'
  'passwd'
  'profile'
  'resolv.conf'
  'securetty'
  'shadow'
  'shells'
  'sysctl'
  'sysusers'
  'tmpfiles'
  'subgid'
  'subuid'
)
sha256sums=('01ba4719c80b6fe911b091a7c05124b64eeece964e09c058ef8f9805daca546b'
            '3f48779141b68a81e07fee710a42025d4f67b16240295aa4cf148a7ba99cab3c'
            '3ffe8ea4e98db43a3ec4dcca55fd4009cd8b8d220f0996aef7a5b427fdf65234'
            '601069e6e8920309178c397fd8cebe43410827d01899d31777d13212f0dfacf8'
            '96e3cc81623c0537a19799f9eefa966fe46ff5f28a9dc7af1187990973baa127'
            'e03bede3d258d680548696623d5979c6edf03272e801a813c81ba5a5c64f4f82'
            'ed0cb4f1db4021f8c3b5ce78fdf91d2c0624708f58f36c9cf867f4d93c3bc6da'
            'e54626e74ed8fee4173b62a545ab1c3a3a069e4217a0ee8fc398d9933e9c1696'
            '244f0718ee2a9d6862ae59d6c18c1dd1568651eada91a704574fa527fbac2b3a'
            '90d879374f77bac47f132164c1e7fc4892e994ff1d1ac376efa0c1c26ea37273'
            '4d7b647169063dfedbff5e1e22cee77bd1a4183dbcfd5e802e68939da4bbf733'
            'd9cd8a77d9e0aa5e90d7f4ed74c8745c17b525e720e28e4c44364150003c35f9'
            'c18bb80fc718c5e3b82b06c5b12519bf6019b30189e08a4ded79cfd71ebb1594'
            '785c6c3614a27ae6115a27c1ca55bbf333654780997c4ba7e181172b021d1bf3'
            '153d848ed51f2774e5a1578ea08e0c8586ecc63f7562697e035b84247edb2f82'
            'c8ee7a9faf798caab178ec51afae4146f1efd8a716b7acedf28345b6c75f9697'
            '7026b37bd5e38d8af005c9ee7438bc3f48e1c53af6faf1287f11fef6c1db0c5c'
            '13e2783884783ef46b8345fbcdf7880f0414c0a9c42e2b2fc6a2b048cbc2d86e'
            '1979ee468511e65109234d9ab7f26e84f0f5f2a96c3ce18740d145049cfa43f4'
            '5557d8e601b17a80d1ea7de78a9869be69637cb6a02fbfe334e22fdf64e61d4c'
            'd88be2b45b43605ff31dd83d6a138069b6c2e92bc8989b7b9ab9eba8da5f8c7b'
            '6e13705ac4d6f69cdba118c6b70c722346fd3c45224133e6bbfe28aca719563c'
            'ec289c03aa0d150e90e8287f001c8e6552ab9dd54f450bdb5c2d2254e477965b'
            '2905b91729fd252d50064460862ab78c567ac3c103847e5e10c267d1f85928ca'
            '30b97e8f5965744138f7a394e04454db6d509fb89e0a9b615bcd9037df3d6f2a'
            '01d1aeb2cb35965074943bb99a4bb646959e0270a81dcd6af9a7b1c092fb3524'
            'e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855'
            'e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855')

package() {
  local group link mode source_file user
  declare -A directories
  declare -A files
  declare -A symlinks

  # associative array with directories and their assigned mode, user and group
  # all paths are relative to the root directory /
  directories=(
    ["boot"]="755:0:0"
    ["dev"]="755:0:0"
    ["etc"]="755:0:0"
    ["etc/ld.so.conf.d"]="755:0:0"
    ["etc/profile.d"]="755:0:0"
    ["etc/skel"]="755:0:0"
    ["home"]="755:0:0"
    ["mnt"]="755:0:0"
    ["opt"]="755:0:0"
    ["proc"]="555:0:0"
    ["root"]="0750:0:0"
    ["run"]="755:0:0"
    ["srv/http"]="755:0:0"
    ["srv/ftp"]="555:0:11"  # vsftpd won't run with write perms on /srv/ftp
    ["sys"]="555:0:0"
    ["tmp"]="1777:0:0"
    ["usr"]="755:0:0"
    ["usr/bin"]="755:0:0"
    ["usr/include"]="755:0:0"
    ["usr/lib"]="755:0:0"
    ["usr/lib/ld.so.conf.d"]="755:0:0"
    ["usr/local/bin"]="755:0:0"
    ["usr/local/etc"]="755:0:0"
    ["usr/local/games"]="755:0:0"
    ["usr/local/include"]="755:0:0"
    ["usr/local/lib"]="755:0:0"
    ["usr/local/man"]="755:0:0"
    ["usr/local/sbin"]="755:0:0"
    ["usr/local/share"]="755:0:0"
    ["usr/local/src"]="755:0:0"
    ["usr/share/factory/etc"]="755:0:0"
    ["usr/share/man/man1"]="755:0:0"
    ["usr/share/man/man2"]="755:0:0"
    ["usr/share/man/man3"]="755:0:0"
    ["usr/share/man/man4"]="755:0:0"
    ["usr/share/man/man5"]="755:0:0"
    ["usr/share/man/man6"]="755:0:0"
    ["usr/share/man/man7"]="755:0:0"
    ["usr/share/man/man8"]="755:0:0"
    ["usr/share/misc"]="755:0:0"
    ["usr/share/pixmaps"]="755:0:0"
    ["usr/src"]="755:0:0"
    ["var"]="755:0:0"
    ["var/cache"]="755:0:0"
    ["var/empty"]="755:0:0"
    ["var/games"]="775:0:50"  # allow setgid games (gid 50) to write scores
    ["var/lib/misc"]="755:0:0"
    ["var/local"]="755:0:0"
    ["var/log/old"]="755:0:0"
    ["var/opt"]="755:0:0"
    ["var/spool/mail"]="1777:0:0"
    ["var/tmp"]="1777:0:0"
  )

  # associative array with symlink names and their respective targets
  # all paths are relative to the root directory /
  symlinks=(
    ["bin"]="usr/bin"
    ["etc/mtab"]="../proc/self/mounts"
    ["lib"]="usr/lib"
    ["sbin"]="usr/bin"
    ["usr/local/share/man"]="../man"
    ["usr/sbin"]="bin"
    ["var/lock"]="../run/lock"
    ["var/mail"]="spool/mail"
    ["var/run"]="../run"
  )
  [[ $CARCH = 'x86_64' ]] && {
    symlinks["lib64"]="usr/lib"
    symlinks["usr/lib64"]="lib"
  }

  # associative array of target files, their source file, file mode, user and group ownership
  files=(
    ["etc/arch-release"]="arch-release:644:0:0"
    ["etc/crypttab"]="crypttab:600:0:0"
    ["etc/fstab"]="fstab:644:0:0"
    ["etc/group"]="group:644:0:0"
    ["etc/gshadow"]="gshadow:600:0:0"
    ["etc/host.conf"]="host.conf:644:0:0"
    ["etc/hosts"]="hosts:644:0:0"
    ["etc/issue"]="issue:644:0:0"
    ["etc/ld.so.conf"]="ld.so.conf:644:0:0"
    ["etc/nsswitch.conf"]="nsswitch.conf:644:0:0"
    ["etc/passwd"]="passwd:644:0:0"
    ["etc/profile"]="profile:644:0:0"
    ["etc/profile.d/locale.sh"]="locale.sh:644:0:0"
    ["etc/resolv.conf"]="resolv.conf:644:0:0"
    ["etc/securetty"]="securetty:644:0:0"
    ["etc/shells"]="shells:644:0:0"
    ["etc/shadow"]="shadow:600:0:0"
    ["etc/subgid"]="subgid:644:0:0"
    ["etc/subuid"]="subuid:644:0:0"
    ["usr/lib/os-release"]="os-release:644:0:0"
    ["usr/lib/sysctl.d/10-arch.conf"]="sysctl:644:0:0"
    ["usr/lib/sysusers.d/arch.conf"]="sysusers:644:0:0"
    ["usr/lib/tmpfiles.d/arch.conf"]="tmpfiles:644:0:0"
    ["usr/lib/systemd/system-environment-generators/10-arch"]="env-generator:755:0:0"
    ["usr/share/factory/etc/arch-release"]="arch-release:644:0:0"
    ["usr/share/factory/etc/crypttab"]="crypttab:600:0:0"
    ["usr/share/factory/etc/fstab"]="fstab:644:0:0"
    ["usr/share/factory/etc/group"]="group:644:0:0"
    ["usr/share/factory/etc/gshadow"]="gshadow:600:0:0"
    ["usr/share/factory/etc/host.conf"]="host.conf:644:0:0"
    ["usr/share/factory/etc/hosts"]="hosts:644:0:0"
    ["usr/share/factory/etc/issue"]="issue:644:0:0"
    ["usr/share/factory/etc/ld.so.conf"]="ld.so.conf:644:0:0"
    ["usr/share/factory/etc/nsswitch.conf"]="nsswitch.conf:644:0:0"
    ["usr/share/factory/etc/passwd"]="passwd:644:0:0"
    ["usr/share/factory/etc/profile"]="profile:644:0:0"
    ["usr/share/factory/etc/profile.d/locale.sh"]="locale.sh:644:0:0"
    ["usr/share/factory/etc/resolv.conf"]="resolv.conf:644:0:0"
    ["usr/share/factory/etc/securetty"]="securetty:644:0:0"
    ["usr/share/factory/etc/shadow"]="shadow:600:0:0"
    ["usr/share/factory/etc/shells"]="shells:644:0:0"
    ["usr/share/factory/etc/subgid"]="subgid:644:0:0"
    ["usr/share/factory/etc/subuid"]="subuid:644:0:0"
    ["usr/share/pixmaps/monadi-logo.png"]="monadi-logo.png:644:0:0"
    ["usr/share/pixmaps/amonadi-logo.svg"]="monadi-logo.svg:644:0:0"
    ["usr/share/pixmaps/archlinux-logo-text.svg"]="archlinux-logo-text.svg:644:0:0"
    ["usr/share/pixmaps/archlinux-logo-text-dark.svg"]="archlinux-logo-text-dark.svg:644:0:0"
  )

  cd "$pkgdir"

  for dir in "${!directories[@]}"; do
    mode="$(cut -f 1 -d ':' <<< "${directories[$dir]}")"
    user="$(cut -f 2 -d ':' <<< "${directories[$dir]}")"
    group="$(cut -f 3 -d ':' <<< "${directories[$dir]}")"

    install -vdm "$mode" -o "$user" -g "$group" "$dir"
  done

  for link in "${!symlinks[@]}"; do
    ln -sv "${symlinks[$link]}" "$link"
  done

  for target_file in "${!files[@]}"; do
    source_file="$(cut -f 1 -d ':' <<< "${files[$target_file]}")"
    mode="$(cut -f 2 -d ':' <<< "${files[$target_file]}")"
    user="$(cut -f 3 -d ':' <<< "${files[$target_file]}")"
    group="$(cut -f 4 -d ':' <<< "${files[$target_file]}")"

    install -vDm "$mode" -o "$user" -g "$group" "$srcdir/$source_file" "$target_file"
  done
}

# vim:set ts=2 sw=2 et:
