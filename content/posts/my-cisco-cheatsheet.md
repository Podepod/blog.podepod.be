+++
date = '2026-01-28T08:11:33Z'
draft = true
title = 'My Cisco Cheatsheet'
author = 'Podepod'
tldr = 'My personal cheatsheet of Cisco commands and other Cisco things'
tags = ['cisco', 'research']
+++

## Cisco Catalyst Switches

### Analyse

Terminal Paging

```cisco
term[inal] l[ength] 0           ! Disables terminal paging
term[inal] l[ength] 20          ! Sets the terminal paging to 20 lines
```

Filter command output

{{< callout type="tip" text="You can use REGEX as a filter instead of plain text" >}}

```cisco
sh[ow] mac address-table | i[nclude] Gi1/0/2 		! Only include the lines that have 'Gi1/0/2' on it
sh[ow] mac address-table | b[egin] Gi1/0/2 			! Start at the first line that has 'Gi1/0/2' on it and show every line after that
sh[ow] mac address-table | e[xclude] Gi1/0/2		! Show all output except the lines that have 'Gi1/0/2' on it
sh[ow] mac address-table | c[ount] Gi1/0/2 			! Count the amount of lines that have 'Gi1/0/2' on it
sh[ow] running-config | s[ection] aaa               ! Only show the AAA section of the running-config
```

Interface Counters

```cisco
sh[ow] int[erface] counters                         ! Show all interface counters
sh[ow] int[erface] counters | i Gi1/0/2             ! Show interface counters for Gi1/0/2
clear counters                                      ! Clear all interface counters
clear counters int Gi1/0/2                          ! Clear interface counters for Gi1/0/2
```

### Hardware

CPU

```cisco
sh[ow] proc[esses] cpu sort[ed]
sh[ow] proc[esses] cpu history
```

Memory

```cisco
sh[ow] memory sum[mary]
sh[ow] proc[esses] mem[ory] sort[ed]
```

Temperature

```cisco
sh[ow] env[irnment] temp[erature] status
```

Power

```cisco
sh[ow] env[ironment] pow[er]                              ! Shows the power supplies of the stack master
sh[ow] env[ironment] pow[er] all                          ! Shows the power supplies of all the stack members
sh[ow] env[ironment] pow[er] switch <stack member nr>     ! Shows the power supplies of a specific stack member
```

### Licensing

### PoE

### SFP

### Switch Stack

### Filesystem


## Cisco Catalyst Wireless Controller


