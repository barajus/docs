---
title: Troubleshooting the etc Directory
author: Cumulus Networks
weight: 1010
aliases:
 - /display/DOCS/Troubleshooting+the+etc+Directory
 - /pages/viewpage.action?pageId=8366322
toc: 4
---
The `{{<link url="Understanding-the-cl-support-Output-File" text="cl-support">}}` script replicates the /`etc` directory, however, it deliberately excludes certain files, such as `/etc/nologin`, which prevents unprivileged users from logging into the system.

This is the alphabetical list of the output from running `ls -l` on the `/etc` directory structure created by `cl-support`.

| **File**                  |
| ------------------------- |
| acpi |
| adduser.conf |
| alternatives |
| apparmor.d |
| apt |
| audisp |
| audit |
| bash.bashrc |
| bash_completion |
| bash_completion.d |
| bcm.d |
| bindresvport.blacklist |
| binfmt.d |
| ca-certificates |
| ca-certificates.conf |
| calendar |
| console-setup |
| cron.d |
| cron.daily |
| cron.hourly |
| cron.monthly |
| crontab |
| cron.weekly |
| cruft |
| cumulus |
| dbus-1 |
| debconf.conf |
| debian_version |
| debsums-ignore |
| default |
| deluser.conf |
| dhcp |
| discover.conf.d |
| discover-modprobe.conf |
| dnsmasq.conf |
| dnsmasq.d |
| dpkg |
| e2fsck.conf |
| emacs |
| environment |
| etckeeper |
| ethertypes |
| fonts |
| freeipmi |
| frr |
| fstab |
| gai.conf |
| groff |
| grub.d |
| gshadow |
| gshadow- |
| gss |
| gunicorn.conf.py |
| hostapd |
| hostapd.conf |
| host.conf |
| hostname |
| hsflowd |
| hsflowd.conf |
| hw_init.d |
| image-release |
| init |
| init.d |
| initramfs-tools |
| inputrc |
| insserv |
| insserv.conf |
| insserv.conf.d |
| iproute2 |
| issue |
| issue.net |
| kernel |
| ldap |
| ld.so.cache |
| ld.so.conf |
| ld.so.conf.d |
| libaudit.conf |
| libnl |
| linuxptp |
| lldpd.d |
| locale.alias |
| locale.gen |
| localtime |
| logcheck |
| login.defs |
| login.defs.cumulus |
| login.defs.cumulus-orig |
| logrotate.conf |
| logrotate.conf.cumulus |
| logrotate.conf.cumulus-orig |
| logrotate.d |
| lsb-release |
| lvm |
| machine-id |
| magic |
| magic.mime |
| mailcap |
| mailcap.order |
| manpath.config |
| mime.types |
| mke2fs.conf |
| modprobe.d |
| modules |
| modules-load.d |
| motd |
| motd.distrib |
| mtab |
| mysql |
| nanorc |
| netd.conf |
| netq |
| network |
| networks |
| nginx |
| nsswitch.conf |
| ntp.conf |
| openvswitch |
| opt |
| os-release |
| perl |
| profile |
| profile.cumulus |
| profile.cumulus-orig |
| profile.d |
| protocols |
| ptm.d |
| ptp4l.conf |
| python |
| python2.7 |
| python3 |
| python3.7 |
| ras |
| rc0.d |
| rc1.d |
| rc2.d |
| rc3.d |
| rc4.d |
| rc5.d |
| rc6.d |
| rcS.d |
| rdnbrd.conf |
| resolv.conf |
| resolvconf |
| resolv.conf.bak |
| restapi.conf |
| rmt |
| rpc |
| rsyslog.conf |
| rsyslog.conf.cumulus |
| rsyslog.conf.cumulus-orig |
| rsyslog.d |
| runit |
| screenrc |
| securetty |
| security |
| selinux |
| sensors3.conf |
| sensors.d |
| services |
| sgml |
| shells |
| skel |
| smartd.conf |
| smartmontools |
| snmp |
| ssh |
| subgid |
| subgid- |
| subuid |
| subuid- |
| sv |
| sysctl.conf |
| sysctl.d |
| systemd |
| terminfo |
| timezone |
| tmpfiles.d |
| ucf.conf |
| udev |
| ufw |
| update-motd.d |
| vim |
| vrf |
| watchdog.conf |
| wgetrc |
| X11 |
| xattr.conf |
| xdg |
| xml |