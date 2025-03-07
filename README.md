facterdb
========

[![License](https://img.shields.io/github/license/voxpupuli/facterdb.svg)](https://github.com/voxpupuli/facterdb/blob/master/LICENSE)
[![Test](https://github.com/voxpupuli/facterdb/actions/workflows/test.yml/badge.svg)](https://github.com/voxpupuli/facterdb/actions/workflows/test.yml)
[![Release](https://github.com/voxpupuli/facterdb/actions/workflows/release.yml/badge.svg)](https://github.com/voxpupuli/facterdb/actions/workflows/release.yml)
[![RubyGem Version](https://img.shields.io/gem/v/facterdb.svg)](https://rubygems.org/gems/facterdb)
[![RubyGem Downloads](https://img.shields.io/gem/dt/facterdb.svg)](https://rubygems.org/gems/facterdb)
[![Donated by Camptocamp](https://img.shields.io/badge/donated%20by-camptocamp-fb7047.svg)](#transfer-notice)

A Gem that contains a lot of facts for a lot of Operating Systems.

![FacterDB](images/facterdb.png)

# Usage

## CLI

```shell
facterdb 'facterversion=/^2.4\./ and (operatingsystem=Debian and operatingsystemrelease>=7 or operatingsystem=RedHat and operatingsystemrelease=/^7/)'
```

Will return a JSON containing the facts for Debian 7, Debian 8 and RedHat 7 generated by Facter 2.4.

## Ruby

```ruby
require 'facterdb'
FacterDB::get_facts()
```

Returns an Array of Hash containing the whole facts database.

## Filtering by Facter version and fact values

### With an Array filter

```ruby
require 'facterdb'

FacterDB.get_facts([{:osfamily => 'Debian'}])
```

### With an Hash filter

```ruby
require 'facterdb'

FacterDB.get_facts({:osfamily => 'Debian'})
```

### With a String filter

```ruby
require 'facterdb'

FacterDB::get_facts('osfamily=Debian')
```

## Facter version and Operating System coverage

|      operating system       | 1.6 | 1.7 | 2.0 | 2.1 | 2.2 | 2.3 | 2.4 | 2.5 | 3.0 | 3.1 | 3.2 | 3.3 | 3.4 | 3.5 | 3.6 | 3.7 | 3.8 | 3.9 | 3.10 | 3.11 | 3.12 | 3.13 | 3.14 | 4.0 | 4.1 | 4.2 | 4.3 | 4.4 |
| --------------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| AIX 5300                    |     |     |     |     |     |     |     |     |     |     |  1  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| AIX 6100                    |     |     |     |     |     |     |     |     |     |     |  1  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| AIX 7100                    |     |     |     |     |     |     |     |     |     |     |  1  |     |     |     |     |     |     |  1  |     |     |     |     |     |     |     |     |     |     |
| AlmaLinux 8                 |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |
| AlmaLinux 9                 |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |
| Amazon                      |  3  |     |     |     |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Amazon 2                    |     |     |     |     |     |     |     |  1  |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |
| Amazon 4                    |     |  3  |  3  |  3  |     |     |     |     |  1  |  1  |     |  1  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Amazon 2016                 |     |     |     |     |  1  |  1  |  1  |  1  |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |
| Amazon 2017                 |     |     |     |     |  1  |  1  |  1  |     |     |     |     |     |     |     |  1  |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Amazon 2022                 |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |  1  |     |     |
| Archlinux                   |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  1  |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |     |     |  1  |     |     |
| CentOS 5                    |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |
| CentOS 6                    |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  1  |  1  |     |     |     |     |     |
| CentOS 7                    |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  2  |  2  |     |  2  |  1  |  1  |  2  |  1  |  1  |  1  |  1  |  2  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |
| CentOS 8                    |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |  1  |     |     |
| CentOS 9                    |     |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |  1  |     |     |
| Darwin                      |     |     |  4  |  4  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Darwin 14                   |     |     |  2  |  2  |  2  |  2  |  2  |  1  |     |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |
| Darwin 15                   |     |     |     |     |  1  |  1  |  1  |  1  |     |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |
| Darwin 16                   |     |     |     |     |  1  |  1  |  1  |  1  |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |
| Darwin 17                   |     |     |     |     |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |
| Darwin 18                   |     |     |     |     |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |  1  |     |  1  |  1  |     |     |     |     |     |
| Darwin 19                   |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |     |     |     |
| Darwin 20                   |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |  1  |     |     |
| Debian 6                    |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Debian 7                    |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |
| Debian 8                    |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |
| Debian 9                    |  1  |  1  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |  2  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |  1  |     |     |
| Debian 10                   |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |
| Debian 11                   |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |
| Fedora 19                   |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Fedora 22                   |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Fedora 23                   |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Fedora 24                   |  1  |  1  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |
| Fedora 25                   |     |     |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |
| Fedora 26                   |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |     |     |     |     |     |     |     |     |
| Fedora 27                   |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |  1  |     |     |     |     |  1  |     |     |     |     |     |     |     |     |
| Fedora 28                   |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |     |     |     |
| Fedora 29                   |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |     |     |     |
| Fedora 30                   |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |  1  |     |     |     |     |     |
| Fedora 32                   |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |
| Fedora 33                   |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |
| Fedora 34                   |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |
| Fedora 35                   |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |     |     |
| Fedora 36                   |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |  1  |  1  |  1  |
| Fedora 37                   |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |
| FreeBSD 9                   |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| FreeBSD 10                  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  1  |     |     |     |     |     |     |     |     |     |  1  |     |     |     |     |     |     |     |     |     |     |
| FreeBSD 11                  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  2  |  1  |  1  |  1  |     |     |
| FreeBSD 12                  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  2  |  1  |  1  |  1  |     |     |
| FreeBSD 13                  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |
| Gentoo                      |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |  1  |     |     |     |     |     |
| LinuxMint 18                |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |  1  |     |  1  |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |
| LinuxMint 19                |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |     |     |     |
| OpenBSD 5.7                 |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| OpenBSD 5.8                 |     |     |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| OpenBSD 5.9                 |     |     |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| OpenBSD 6.0                 |     |     |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| OpenBSD 6.2                 |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |  2  |     |     |     |     |     |     |     |     |     |     |     |
| OpenBSD 6.3                 |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |  2  |     |     |     |     |     |     |     |     |     |
| OpenBSD 6.4                 |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |     |     |     |     |     |
| OpenSuSE 12                 |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| OpenSuSE 13                 |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| OpenSuSE 15                 |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |     |     |     |
| OpenSuSE 42                 |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |
| OracleLinux 5               |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |
| OracleLinux 6               |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  1  |  2  |  1  |  1  |  1  |     |     |  1  |     |     |
| OracleLinux 7               |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  2  |  2  |     |  2  |  1  |  1  |  2  |  1  |  1  |  1  |  1  |  2  |  1  |  1  |  1  |  1  |     |  1  |     |     |
| OracleLinux 8               |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |  1  |     |     |
| OracleLinux 9               |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |
| Pop!_OS 21.10               |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |
| Raspbian 9                  |     |     |     |     |     |     |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Raspbian 10                 |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  2  |     |     |     |     |     |     |     |     |
| RedHat 5                    |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |
| RedHat 6                    |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  3  |  2  |  2  |  2  |  2  |  2  |  1  |  1  |  1  |     |     |     |     |     |
| RedHat 7                    |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  2  |  2  |     |  2  |  1  |  1  |  2  |  1  |  1  |  1  |  1  |  2  |  1  |  1  |  1  |  1  |     |  1  |     |     |
| RedHat 8                    |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |
| RedHat 9                    |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |
| Rocky 8                     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |
| Rocky 9                     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |
| SLES 11                     |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  1  |  1  |     |     |     |     |     |
| SLES 12                     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |  1  |  1  |  1  |
| SLES 15                     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |  1  |     |     |
| Scientific 5                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |
| Scientific 6                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  1  |  1  |     |     |     |     |     |
| Scientific 7                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  2  |  2  |     |  2  |  1  |  1  |  2  |  1  |  1  |  1  |  1  |  2  |  1  |  1  |  1  |  1  |     |  1  |     |     |
| Solaris 10                  |     |     |     |     |     |     |     |  1  |     |     |     |     |     |     |     |     |     |  1  |     |  1  |     |     |     |     |     |     |     |     |
| Solaris 11                  |  1  |  1  |  1  |  1  |  1  |  2  |  2  |  1  |     |     |     |     |     |     |     |     |     |     |     |  2  |     |     |  2  |  1  |     |     |     |     |
| Ubuntu 10.04                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Ubuntu 12.04                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Ubuntu 14.04                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |
| Ubuntu 14.10                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Ubuntu 15.04                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Ubuntu 15.10                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |     |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Ubuntu 16.04                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |
| Ubuntu 16.10                |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  2  |     |     |     |     |     |     |     |     |     |     |     |     |     |
| Ubuntu 18.04                |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |
| Ubuntu 20.04                |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |
| Ubuntu 21.04                |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |
| Ubuntu 21.10                |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |     |     |
| Ubuntu 22.04                |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |  1  |  1  |  1  |
| Ubuntu 22.10                |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |  1  |     |     |
| VirtuozzoLinux 7            |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |     |     |     |
| Windows 7                   |     |     |     |  1  |  1  |  1  |  2  |  1  |  2  |  2  |     |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |
| Windows 8.1                 |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |
| Windows 10                  |     |     |     |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |  2  |     |     |  1  |     |     |
| Windows Server 2008         |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |
| Windows Server 2008 R2      |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |     |     |     |     |     |     |
| Windows Server 2012         |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |  1  |     |     |
| Windows Server 2012 R2      |     |     |     |  1  |  1  |  1  |  2  |  1  |  1  |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |  1  |     |     |
| Windows Server 2012 R2 Core |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |     |     |     |
| Windows Server 2016         |     |     |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |  1  |     |     |
| Windows Server 2016 Core    |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |
| Windows Server 2019         |     |     |     |     |     |     |     |  1  |  1  |  1  |     |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |  1  |     |     |  1  |     |     |
| Windows Server 2019 Core    |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |
| Windows Server 2022 Core    |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |
| openSUSE 15                 |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |  1  |  1  |  1  |  1  |
| windows 11                  |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |
| windows 2022                |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |  1  |     |     |

Where the number (1, 2 etc.) are the number of factsets for that OS and facter combination (e.g., x86_64 and i386 architectures).

## Add new Operating System support

There is `Vagrantfile` to automagically populate `facts` directory by spawning a new VM and launches a provisioning scripts.

```
$ cd facts
$ vagrant up --provision
```

Create i386 facts from x86_64's ones

```
for file in facts/*/*-x86_64.facts; do cat $file | sed -e 's/x86_64/i386/' -e 's/amd64/i386/' > $(echo $file | sed 's/x86_64/i386/'); done
```
Create RedHat, Scientific, OracleLinux facts from CentOS's ones

```
$ bundle exec rake rhel_alts
```

Then update the table in this README by running `bundle exec rake table`

*NOTE*: When using Facter version 4, by default some "legacy facts" are hidden from the output.
To generate a fact set with the legacy facts use the command `puppet facts show --show-legacy`

## Supplying custom external facts

The default facts are great for many things but there will be times when you need to have facterdb search custom
fact sets that only make sense in your environment or might contain sensitive information.

This can be useful when combined with [rspec_puppet_facts](https://github.com/mcanevet/rspec-puppet-facts) or the [puppet-debugger](https://github.com/nwops/puppet-debugger) which both use this gem.

To supply external facts to facterdb just set the `FACTERDB_SEARCH_PATHS` environment variable with one or more
paths to your facts.  Do this any time facterdb is used directly or indirectly.

When separating paths please use the default path separator character supported by your OS.
* Unix/Linux/OSX = `:`
* Windows = `;`

Each fact set you create must meet the following requirements:
1. A JSON serialized file containing a single Hash of all the facts.
2. The facts file must end in `.facts`
3. Must be placed inside some directory.  You can organize this directory however you like.

Facterdb is smart enough the search your supplied directories for files ending with '.facts'.  You can even supply
multiple directories.

Example:

`FACTERDB_SEARCH_PATHS="/var/opt/lib/custom_facts"`

or

`FACTERDB_SEARCH_PATHS="/var/opt/lib/custom_facts:/tmp/custom_facts:/home/user1/custom_facts"`

We still highly encourage you to create pull requests with new fact sets over of using external facts.

You can create these files via many methods.

* `puppet facts | jq '.values' > /tmp/custom_facts/datacenter_a/2.4/os_x.facts`  # must have jq command
* Via puppetdb queries
* hand crafted


Additionally you can skip the default FacterDB facts completely by setting the environment variable `FACTERDB_SKIP_DEFAULTDB`.
This will instruct facterdb to not look at its built-in facts which can be useful should you need to completely replace which facts are used.


Setting the variable `FACTERDB_SKIP_DEFAULTDB` to anything will disable the internal facts used by facterdb.  You would most likely use this in combination
with the `FACTERDB_SEARCH_PATHS` environment variable.

Example:

```
FACTERDB_SEARCH_PATHS="/var/opt/lib/custom_facts:/tmp/custom_facts:/home/user1/custom_facts"
FACTERDB_SKIP_DEFAULTDB='yes'
```

## Debugging fact sets

By setting the environment variable `FACTERDB_INJECT_SOURCE` the following facts are injected into all fact sets:

`_facterdb_path` : The base name of the file used to load this fact set e.g. `centos-5-i386.facts`

`_facterdb_filename` : The full path of the file used to load this fact set e.g. `/project/facter-db/centos-5-i386.facts`


``` json
{
  "_facterdb_path": "centos-5-i386.facts",
  "_facterdb_filename": "/project/facter-db/centos-5-i386.facts",
  "aio_agent_version": "1.8.3",
  "architecture": "i386",
  "augeas": {
    "version": "1.4.0"
  },
  "augeasversion": "1.4.0",
  "bios_release_date": "07/30/2013",
  "bios_vendor": "Phoenix Technologies LTD",
  "bios_version": "6.00",
  "blockdevice_fd0_size": 4096,
  "blockdevice_hdc_size": 4294965248,
  "blockdevice_sda_model": "Virtual disk",
  ...
```

To set the environment variable use;

``` bash
bash> FACTERDB_INJECT_SOURCE='true'
```
or on Windows
``` powershell
powershell> $ENV:FACTERDB_INJECT_SOURCE = 'true'
```

# Contributing

Please submit issues at https://github.com/camptocamp/facterdb/issues or PRs in the same repository.

## Release process

* Update the version in `lib/facterdb/version.rb`
* Run `rake changelog`
* Commit and PR the results.


## Transfer Notice

This plugin was originally authored by [Camptocamp](http://www.camptocamp.com).
The maintainer preferred that Puppet Community take ownership of the module for future improvement and maintenance.
Existing pull requests and issues were transferred over, please fork and continue to contribute here instead of Camptocamp.

Previously: https://github.com/camptocamp/facterdb
