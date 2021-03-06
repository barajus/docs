---
title: Adding and Updating Packages
author: Cumulus Networks
weight: 147
aliases:
 - /display/RMP31/Adding+and+Updating+Packages
 - /pages/viewpage.action?pageId=5122746
pageID: 5122746
product: Cumulus RMP
version: 3.1.2
imgData: cumulus-rmp-31
siteSlug: cumulus-rmp-31
---
You use the Advanced Packaging Tool (APT) to manage additional
applications (in the form of packages) and to install the latest
updates.

## Commands</span>

  - apt-get

  - apt-cache

  - dpkg

## Updating the Package Cache</span>

To work properly, APT relies on a local cache of the available packages.
You must populate the cache initially, and then periodically update it
with `apt-get update`:

    cumulus@switch:~$ sudo apt-get update
    Get:1 http://repo3.cumulusnetworks.com CumulusRMP-3 InRelease [7,624 B]
    Get:2 http://repo3.cumulusnetworks.com CumulusRMP-3-security-updates InRelease [7,555 B]
    Get:3 http://repo3.cumulusnetworks.com CumulusRMP-3-updates InRelease [7,660 B]
    Get:4 http://repo3.cumulusnetworks.com CumulusRMP-3/cumulus Sources [20 B]
    Get:5 http://repo3.cumulusnetworks.com CumulusRMP-3/upstream Sources [20 B]
    Get:6 http://repo3.cumulusnetworks.com CumulusRMP-3/cumulus amd64 Packages [38.4 kB]
    Get:7 http://repo3.cumulusnetworks.com CumulusRMP-3/upstream amd64 Packages [445 kB]
    Get:8 http://repo3.cumulusnetworks.com CumulusRMP-3-security-updates/cumulus Sources [20 B]
    Get:9 http://repo3.cumulusnetworks.com CumulusRMP-3-security-updates/upstream Sources [11.8 kB]
    Get:10 http://repo3.cumulusnetworks.com CumulusRMP-3-security-updates/cumulus amd64 Packages [20 B]
    Get:11 http://repo3.cumulusnetworks.com CumulusRMP-3-security-updates/upstream amd64 Packages [8,941 B]
    Get:12 http://repo3.cumulusnetworks.com CumulusRMP-3-updates/cumulus Sources [20 B]
    Get:13 http://repo3.cumulusnetworks.com CumulusRMP-3-updates/upstream Sources [776 B]
    Get:14 http://repo3.cumulusnetworks.com CumulusRMP-3-updates/cumulus amd64 Packages [38.4 kB]
    Get:15 http://repo3.cumulusnetworks.com CumulusRMP-3-updates/upstream amd64 Packages [444 kB]
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3/cumulus Translation-en_US
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3/cumulus Translation-en
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3/upstream Translation-en_US
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3/upstream Translation-en
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3-security-updates/cumulus Translation-en_US
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3-security-updates/cumulus Translation-en
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3-security-updates/upstream Translation-en_US
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3-security-updates/upstream Translation-en
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3-updates/cumulus Translation-en_US
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3-updates/cumulus Translation-en
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3-updates/upstream Translation-en_US
    Ign http://repo3.cumulusnetworks.com CumulusRMP-3-updates/upstream Translation-en
    Fetched 1,011 kB in 1s (797 kB/s)
    Reading package lists... Done

## Listing Available Packages</span>

Once the cache is populated, use `apt-cache` to search the cache to find
the packages you are interested in or to get information about an
available package. Here are examples of the `search` and `show`
sub-commands:

    cumulus@switch:~$ apt-cache search tcp
    fakeroot - tool for simulating superuser privileges
    libwrap0 - Wietse Venema's TCP wrappers library
    libwrap0-dev - Wietse Venema's TCP wrappers library, development files
    netbase - Basic TCP/IP networking system
    nmap - The Network Mapper
    openbsd-inetd - OpenBSD Internet Superserver
    openssh-client - secure shell (SSH) client, for secure access to remote machines
    openssh-server - secure shell (SSH) server, for secure access from remote machines
    rsyslog - reliable system and kernel logging daemon
    socat - multipurpose relay for bidirectional data transfer
    tcpd - Wietse Venema's TCP wrapper utilities
    tcpdump - command-line network traffic analyzer
    tcpreplay - Tool to replay saved tcpdump files at arbitrary speeds
    tcpstat - network interface statistics reporting tool
    tcptrace - Tool for analyzing tcpdump output
    tcpxtract - extracts files from network traffic based on file signatures

    cumulus@switch:~$ apt-cache show tcpdump
    Package: tcpdump
    Status: install ok installed
    Priority: optional
    Section: net
    Installed-Size: 1092
    Maintainer: Romain Francoise <rfrancoise@debian.org>
    Architecture: amd64
    Multi-Arch: foreign
    Version: 4.6.2-5+deb8u1
    Depends: libc6 (>= 2.14), libpcap0.8 (>= 1.5.1), libssl1.0.0 (>= 1.0.0)
    Description: command-line network traffic analyzer
     This program allows you to dump the traffic on a network. tcpdump
     is able to examine IPv4, ICMPv4, IPv6, ICMPv6, UDP, TCP, SNMP, AFS
     BGP, RIP, PIM, DVMRP, IGMP, SMB, OSPF, NFS and many other packet
     types.
     .
     It can be used to print out the headers of packets on a network
     interface, filter packets that match a certain expression. You can
     use this tool to track down network problems, to detect attacks
     or to monitor network activities.
    Description-md5: f01841bfda357d116d7ff7b7a47e8782
    Homepage: http://www.tcpdump.org/

{{%notice note%}}

The search commands look for the search terms not only in the package
name but in other parts of the package information. Consequently, it
will match on more packages than you would expect.

{{%/notice%}}

## Adding a Package</span>

In order to add a new package, first ensure the package is not already
installed in the system:

    cumulus@switch:~$ dpkg -l | grep {name of package}

If the package is installed already, ensure it's the version you need.
If it's an older version, then update the package from the Cumulus RMP
repository:

    cumulus@switch:~$ sudo apt-get update

If the package is not already on the system, add it by running `apt-get
install`. This retrieves the package from the Cumulus RMP repository and
installs it on your system together with any other packages that this
package might depend on.

For example, the following adds the package `tcpreplay` to the system:

    cumulus@switch:~$ sudo apt-get install tcpreplay
    cumulus@switch:~$ sudo apt-get install tcpreplay
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    The following NEW packages will be installed:
    tcpreplay
    0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
    Need to get 436 kB of archives.
    After this operation, 1008 kB of additional disk space will be used.
    Get:1 https://repo.cumulusnetworks.com/ CumulusLinux-1.5/main tcpreplay amd64 4.6.2-5+deb8u1 [436 kB]
    Fetched 436 kB in 0s (1501 kB/s)
    Selecting previously unselected package tcpreplay.
    (Reading database ... 15930 files and directories currently installed.)
    Unpacking tcpreplay (from .../tcpreplay_4.6.2-5+deb8u1_amd64.deb) ...
    Processing triggers for man-db ...
    Setting up tcpreplay (4.6.2-5+deb8u1) ...
    cumulus@switch:~$ 

## Listing Installed Packages</span>

The APT cache contains information about all the packages available on
the repository. To see which packages are actually installed on your
system, use `dpkg`. The following example lists all the packages on the
system that have "tcp" in their package names:

``` 
cumulus@switch:~$ dpkg -l \*tcp\*
  Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                  Version             Architecture        Description
+++-=====================-===================-===================-=====================================
un  tcpd                  <none>              <none>              (no description available)
ii  tcpdump               4.6.2-5+deb8u1      amd64               command-line network traffic analyzer  
```

## Upgrading to Newer Versions of Installed Packages</span>

### Upgrading a Single Package</span>

A single package can be upgraded by simply installing that package again
with `apt-get install`. You should perform an update first so that the
APT cache is populated with the latest information about the packages.

To see if a package needs to be upgraded, use `apt-cache show <pkgname>`
to show the latest version number of the package. Use `dpkg -l
<pkgname>` to show the version number of the installed package.

### Upgrading All Packages</span>

You can update all packages on the system with `apt-get update`. This
upgrades all installed versions with their latest versions but will not
install any new packages.

## Adding Packages from Another Repository</span>

As shipped, Cumulus RMP searches the Cumulus RMP repository for
available packages. You can add additional repositories to search by
adding them to the list of sources that `apt-get` consults. See `man
sources.list` for more information.

{{%notice tip%}}

For several packages, Cumulus Networks has added features or made bug
fixes and these packages must not be replaced with versions from other
repositories. Cumulus RMP has been configured to ensure that the
packages from the Cumulus RMP repository are always preferred over
packages from other repositories.

{{%/notice%}}

If you want to install packages that are not in the Cumulus RMP
repository, the procedure is the same as above with one additional step.

{{%notice note%}}

Packages not part of the Cumulus RMP repository have generally not been
tested, and may not be supported by Cumulus RMP support.

{{%/notice%}}

Installing packages outside of the Cumulus RMP repository requires the
use of `apt-get`, but, depending on the package, `easy-install` and
other commands can also be used.

To install a new package, please complete the following steps:

1.  First, ensure package is not already installed in the system. Use
    the `dpkg` command:
    
        cumulus@switch:~$ dpkg -l | grep {name of package}

2.  If the package is installed already, ensure it's the version you
    need. If it's an older version, then update the package from the
    Cumulus RMP repository:
    
        cumulus@switch:~$ sudo apt-get update
        cumulus@switch:~$ sudo apt-get install {name of package}

3.  If the package is not on the system, then most likely the package
    source location is also **not** in the `/etc/apt/sources.list` file.
    If the source for the new package is **not** in `sources.list`,
    please edit and add the appropriate source to the file. For example,
    add the following if you wanted a package from the Debian repository
    that is **not** in the Cumulus RMP repository:
    
        deb http://http.us.debian.org/debian jessie main
        deb http://security.debian.org/ jessie/updates main
    
    Otherwise, the repository may be listed in `/etc/apt/sources.list`
    but is commented out, as can be the case with the testing
    repository:
    
        #deb http://repo.cumulusnetworks.com CumulusRMP-VERSION testing
    
    To uncomment the repository, remove the \# at the start of the line,
    then save the file:
    
        deb http://repo.cumulusnetworks.com CumulusRMP-VERSION testing

4.  Run `apt-get update` then install the package:
    
        cumulus@switch:~$ sudo apt-get update
        cumulus@switch:~$ sudo apt-get install {name of package}

## Configuration Files</span>

  - /etc/apt/apt.conf

  - /etc/apt/preferences

  - /etc/apt/sources.list

## Useful Links</span>

  - [Debian GNU/Linux FAQ, Ch 8 Package management
    tools](http://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html)

  - man pages for `apt-get`, `dpkg`, `sources.list`, `apt_preferences`

