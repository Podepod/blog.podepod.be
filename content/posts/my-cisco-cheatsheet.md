+++
date = '2026-01-28T08:11:33Z'
draft = true
title = 'My Cisco Cheatsheet'
author = 'Podepod'
tldr = 'My personal cheatsheet of Cisco commands and other Cisco things'
tags = ['cisco', 'research', 'networking']
toc = false
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

Licensing information

```cisco
sh[ow] license all
sh[ow] license sum[mary]
```

Add switch to smart account

```cisco
conf t
 ip name-server <dns-server(s)>
 call-home
  http resolve-hostname ipv4-first
  contact-email-addr <contact email>
  profile CiscoTAC-1
   active
  exit
 exit
 ip http client source-interface vlan <management vlan>
 no license smart privacy hostname
 license smart transport callhome
 service call-home
end

license smart trust idtoken <token> all force
```

Change the bootlevel of the switch (to network-advantage with addon dna-advantage)

```cisco
configure terminal
 license boot level network-advantage addon dna-advantage
end
```

### PoE

PoE Port status

```cisco
sh[ow] power inline
```

PoE port config auto

```cisco
conf[igure] term[inal]
 int[erface] <interface>
  power inline auto
end
```

PoE port config static

```cisco
conf[igure] term[inal]
 int[erface] <interface>
  power inline static
  power inline static max <4000-30000 (milli-watts)>
end
```

Activate PoE High Availability (keeps PoE enabled even when the switch is rebooting, as long as the switch has power)

```cisco
conf[igure] term[inal]
 int[erface] <interface>
  power inline port perpetual-poe-ha
end
```

### SFP



### Switch Stack

### Filesystem

### Macro / script

## Cisco Catalyst Wireless Controller

### WLC 

#### Health Checks

```cisco
show redundancy
show redundancy switchover history

show chassis
show chassis rmi

show processes cpu sorted
show processes cpu history

show memory
show processes memory
```

#### Redunancy

```cisco
show redundancy
show redundancy switchover history
show chassis
show chassis rmi
```

#### Change primary node

```cisco
redundancy force-switchover
```

#### Radio Active (RA) Traces

GUI only?

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

#### Exclude Client MAC

CLI

```cisco
conf t
 [no] wireless exclusionlist <MAC address> <description, max 32 characters>
end
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

### Access Points

#### AP config

CLI

```cisco
show ap name <AP name> config general
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

#### Reboot AP

CLI

```cisco
ap name <AP name> reset
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

#### Show AP tags

CLI

```cisco
ap name <AP name> tag info
ap name <AP name> tag detail
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

#### Change AP tags

CLI

```cisco
conf[igure] term[inal]
 ap <eth mac>
  policy-tag <policy-tag name>
  rf-tag <rf-tag name>
  site-tag <site-tag name>
end
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

#### Change AP primary controller

CLI

```cisco
ap name <AP name> controller primary <controller name> <controller IP>
ap name <AP name> reset                                                     ! AP needs to be restarted after changing primary controller
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

#### Change AP name

CLI

```cisco
ap name <current AP name> name <new AP name>
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

#### AP LED

CLI

Show status

```cisco
show ap name <AP name> config general | i LED
```

Change LED Status

```cisco
ap name <AP name> [no] led
```

Flash LED

```cisco
ap name <AP name> led flash start duration <seconds 0-3600>
ap name <AP name> led flash stop
```

Brightness LED

```cisco
ap name <AP name> led-brightness-level <level 1-8>
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

#### Show AP Image

CLI

```cisco
show ap name <AP name> image
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

#### Show AP CDP neighbours

CLI

```cisco
show ap name <AP name> cdp neighbors
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}

#### RLAN

CLI

```cisco
show ap name <AP name> lan port summary
```

GUI

{{< callout type="custom" emoji="📋" title="TODO" text="I should still add this part" style="background-color: #ffffd9; border: 3px solid #ffff00;" >}}
