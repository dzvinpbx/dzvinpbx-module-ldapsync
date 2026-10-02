# LDAP/AD user sync module for Dzvin PBX

[![GitHub release](https://img.shields.io/github/v/release/dzvinpbx/dzvinpbx-module-ldapsync)](https://github.com/dzvinpbx/dzvinpbx-module-ldapsync/releases)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

**[Українською](README.uk.md)** | **English**

Synchronises employees from Active Directory and other LDAP servers into Dzvin PBX, creating user
accounts automatically. After an internal extension number is assigned, extension details can be
written back to the directory.

> This is a Dzvin PBX fork of the MikoPBX **ModuleLdapSync** module - see [Attribution](#attribution).

## Features

- Import of users from Active Directory, OpenLDAP, 389 Directory Server and FreeIPA
- LDAP, LDAP + STARTTLS and LDAPS, with optional server certificate validation and a custom CA bundle
- Attribute mapping: name, mobile number, extension, e-mail, photo, account state
- Optional two-way sync: extension, mobile number, e-mail, avatar and SIP password are written back to the directory
- Organizational unit and extra user filters
- Periodic background sync (hourly, every 5 minutes while changes are detected) and manual sync
- Conflict log for records that could not be synchronised
- Test of the LDAP bind and of the user list before enabling the sync

## Requirements

- Dzvin PBX 2025.1.1 or higher (PHP 8.4)

## Installation

1. Open **Modules** -> **Marketplace** in the Dzvin PBX admin panel
2. Find **LDAP/AD sync**
3. Click **Install**

Or from a GitHub release: download the `.zip`, then **Modules** -> **Install module**.

## Usage

1. Add a server: address, port, transport mode, the bind account and the domain root (Base DN).
2. Set the attribute names used in your directory on the **Sync fields** tab.
3. Run **Test bind** and the user list test, then enable the server.

## License

GPL-3.0-or-later - see [LICENSE](LICENSE). The upstream repository ships no LICENSE file; its
`composer.json` declares GPL-3.0-or-later and the source files carry the GPL-3.0 header, so the
GPL-3.0 text was added here. Bundled PHP libraries (`directorytree/ldaprecord`, Carbon and their
dependencies) are MIT-licensed.

## Attribution

This is a Dzvin PBX fork of [`mikopbx/ModuleLdapSync`](https://github.com/mikopbx/ModuleLdapSync)
(from tag `v1.41`, commit `8a1c038`), © 2017-2023 Alexey Portnov and Nikolay Beketov, licensed
under GPL-3.0-or-later. The fork renames the PBX core namespace (`MikoPBX\` -> `DzvinPBX\`),
removes the commercial licence binding of the original module, completes the Ukrainian
translation and adapts links and the release process to this repository. The original copyright
and licence headers are kept in every source file; the core this module is built for is
[MikoPBX Core](https://github.com/mikopbx/Core).
