# Securing Linux

## System audit

Lynis scans the system configuration and creates an overview of system information
and security issues usable by professional auditors.

https://cisofy.com/lynis

```sudo apt install lynis```

Run it from System > Lynis or type ```sudo lynis audit system``` from the terminal.

You'll see some initial info about the system under test, e.g.:

```
  Program version:           3.1.4
  Operating system:          Linux
  Operating system name:     Debian
  Operating system version:  13
  Kernel version:            6.12.96+deb13
  Hardware platform:         x86_64
```

This is followed by a list of _all_ running services Lynis found, and whether it deems the service or its configuration as secure. A sample (much more fun and chill-inducing if reading it in the default color mode):

```
    - ModemManager.service (value=6.3)                        [ MEDIUM ]
    - NetworkManager.service (value=7.8)                      [ EXPOSED ]
    - accounts-daemon.service (value=5.5)                     [ MEDIUM ]
    - alsa-state.service (value=9.6)                          [ UNSAFE ]
    - anacron.service (value=9.6)                             [ UNSAFE ]
    - avahi-daemon.service (value=9.6)                        [ UNSAFE ]
    - bluetooth.service (value=6.0)                           [ MEDIUM ]
    - colord.service (value=3.5)                              [ PROTECTED ]
    - cron.service (value=9.6)                                [ UNSAFE ]
```

This list can go on for a long time, but is categorized for ease (?) of parsing. After the list, it gets to an actionable list of recommendations:

```
================================================================================

  -[ Lynis 3.1.4 Results ]-

  Warnings (3):
  ----------------------------
  ! Reboot of system is most likely needed [KRNL-5830] 
    - Solution : reboot
      https://cisofy.com/lynis/controls/KRNL-5830/

  ! apt-get check returned a non successful exit code. [PKGS-7390] 
      https://cisofy.com/lynis/controls/PKGS-7390/

  ! Found one or more vulnerable packages. [PKGS-7392] 
      https://cisofy.com/lynis/controls/PKGS-7392/

  Suggestions (44):
  ----------------------------
  * Install libpam-tmpdir to set $TMP and $TMPDIR for PAM sessions [DEB-0280] 
    - Related resources
      * Website: https://cisofy.com/lynis/controls/DEB-0280/

  * Install apt-listbugs to display a list of critical bugs prior to each APT installation. [DEB-0810] 
    - Related resources
      * Website: https://cisofy.com/lynis/controls/DEB-0810/
```

A number of these recommendations assume you want to harden your system to enterprise-server-class levels. If this is a laptop that never leaves your home LAN (and you trust that your teenager isn't trying to extract your credit card info the fun way rather than just raiding your wallet), you probably don't need to ```Install fail2ban to automatically ban hosts that commit multiple authentication errors```, for example. (As always, YMMV.)

Each recommendation is followed by a URL to greater detail on Lynis's site explaining the risk and what to do about it.

Finally, the report gives an overall score and what it actually did:

```
  Lynis security scan details:

  Hardening index : 60 [############        ]
  Tests performed : 251
  Plugins enabled : 1

  Components:
  - Firewall               [V]
  - Malware scanner        [X]

  Scan mode:
  Normal [V]  Forensics [ ]  Integration [ ]  Pentest [ ]

  Lynis modules:
  - Compliance status      [?]
  - Security audit         [V]
  - Vulnerability scan     [V]

  Files:
  - Test and debug information      : /var/log/lynis.log
  - Report data                     : /var/log/lynis-report.dat
```


## Vulnerability scanning

### OpenVAS / Greenbone

OpenVAS scans a host or subnet for known vulnerabilities (CVEs). 

[Documentation](https://greenbone.github.io/docs/latest/index.html)

#### Installation



#### Running

When it first runs, OpenVAS takes a considerable amount of time downloading vuln data. You'll see "Please wait while the feed is syncing. Scans are not available during this time." at the top of the screen. Be patient, and if at all possible, don't close the container if you want to run scans in the next hour.


