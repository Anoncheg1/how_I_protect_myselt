# Here is my approach to protect PC from common security threats.
1. Replace proprietary BIOS with coreboot or HEADS (https://osresearch.net/).
2. Secure boot with password or locate at USB stick or encrypt boot partition with lightweight LUKS2 encryption + GRUB2.
2. OS Gentoo Linux stable relase only open source licensies. Full recompilation. Non systemd. Non root Xorg.
3. Linux kernel compilation with disabled loadable modules and security hardening, such as:
- Strong Stack Protector
- Randomize kernel things
- Initialize heap memory with zeroes
- Enable debuging kernel data structures
- Other security settings, for ex. Kernel Self Protection Project.
4. Build firmware blobs into the kernel binary, when there is no open alternatives.
5. Full disk encryption with LUKS (Linux Unified Key Setup). Key is a several megabyte file encrypted with AES256 symmetric-key. This key placed at USB stick and used during initramfs loading to decrypt LVM disks with LUKS aes-xts-plain64 algorithm.
6. Hardening /etc/fstab
- proc /proc proc hidepid=2,nosuid,noexec,gid=wheel
- separate partition /home with mount options noexec,nosuid,nodev
7. Simple firewall with iptables or nftables. No log analyzer.
8. Install POSIX Capabilities and active secure computing mode USE="caps seccomp".
9. Logging under root activated, sudo for root deactivated.
10. Separate user for every big application. Firejail with carefully crafted configurations. It prevents from keyloggers and information gathering.

Browser:
- VPN over Tor
- Firefox or TorBrowser
- User-Agent changer
- Hide all fingerprints: Canvas, Fonts, TimeZone
- Disable some of the browser functionality (user.json)
- Disable insecure SSL ciphers, rise up version
- Disable JavaScript whenever it is possible
