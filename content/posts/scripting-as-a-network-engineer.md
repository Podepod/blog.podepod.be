+++
title = 'Scripting as a network engineer'
author = 'Podepod'
date = '2026-02-12T09:02:54Z'
tldr = "Some stuff I've automated and some thoughts on scripting"
tags = ['networking', 'cisco', 'thoughts']
toc = false
draft = false
+++

Recently I've been scripting a lot more. I like to automate things that I have to do more than once every day (or at least most of the days). So most of my scripting is network related which is interesting to figure out. Mostly because I try to keep it within powershell without any downloaded modules. It's fun to just figure out how things work without a module which does it al for you in a single function.

For example: we would like to automatically update our inventory tool with up to date data about our access switches. We only use Cisco switches and have a Cisco Catalyst Center running. So I can use the API of Catalyst Center to request a lot of data about the switches without having to SSH to each individual switch. We also do this for our wireless access points so we can put these in our inventory system as well.

Now I just started another script which will take data out of inventory system and use them to generate a custom motd banner on all our access switches. I had already rolled out this banner to all access switches about a year ago but I have to update them manually every time something changes (which isn't a lot so I forget most of the time..). The banner is used to quickly display some useful information about the switch without having to look it up or run commands to find the information. 

```text 
                 ___   ___   __  __  ___    _    _  _ __   __
                / __| / _ \ |  \/  || _ \  /_\  | \| |\ \ / /
               | (__ | (_) || |\/| ||  _/ / _ \ | .\ | \ V /
                \___| \___/ |_|  |_||_|  /_/ \_\|_|\_|  |_|

=================================================================================

SWITCH NAME:        <switch name>
MGMT IP:            <mgmt IP>
SOFTWARE VERSION:   <IOS-XE version>
UPS:                <UPS IP>
TYPE:               <switch type>

LOCATION:           <physical location where the datarack is located>
DEPARTMENT:         <involved departments which are impacted by this switch>
TO CONTACT:         <people who should be contacted for update windows etc.>
UPDATE WINDOW:      <previous update window>

OTHER:              <special warnings for critical switches or just other usefull info>

=================================================================================

```

The banner has come in clutch when I wasn't paying too much attention and suddenly realised I was about to reconfigure the wrong trunk port. Sometimes when you have so much ssh sessions open, you're working in the wrong one...

Other small, fun and usefull scripts I've written are:

- A script to format MAC addresses every possible format. It outputs all the formats I've set up and also copies the given type to the clipboard.

```shell
$> mac -t dhcp AA:BB:CC:DD:EE:FF

ise       : AA:BB:CC:DD:EE:FF
dhcp_c    : aa-bb-cc-dd-ee-ff
dhcp_u    : AABBCCDDEEFF
cisco     : aabb.ccdd.eeff
windows   : AA:BB:CC:DD:EE:FF

Formatted MAC (dhcp): aabbccddeeff
```

- An easy script that's basically a normal ping but with the time printed before every ping. That way I can see how much time has passed when one ping is missed or when the thing I pinged went down or came back up again.

```shell
$> tp -t 8.8.8.8

Pinging 8.8.8.8 with 32 bytes of data:
✓ 02/12/2026 10:39:07: Reply from 8.8.8.8: time=8ms TTL=117
✓ 02/12/2026 10:39:08: Reply from 8.8.8.8: time=7ms TTL=117
✓ 02/12/2026 10:39:09: Reply from 8.8.8.8: time=7ms TTL=117
✓ 02/12/2026 10:39:10: Reply from 8.8.8.8: time=10ms TTL=117
✓ 02/12/2026 10:39:11: Reply from 8.8.8.8: time=10ms TTL=117
```

- A script that generates the md5 hash of a file and verifies it against a given hash
- A script that parses Cisco Catalyst logs by severity level

Some smaller functions I added to my powershell profile

- A function that generates a psk of a given length and copies it to my clipboard
- A function to disable or enable a given network adapter
- some aliases of the ping command: `pt` equals `ping -t`, `p4` equals `ping -4`, `pc` equals `ping '$($Get-Clipboard)'` etc
- I have a few infrastructure devices that also get a ping alias, so I don't have to know the ip or type the hostname right xD
- a COM-port function which displays the active COM port (`Write-Host ([System.IO.Ports.SerialPort]::GetPortNames())`) when I try to connect to the console of a device
- a function that keeps my screen active for when I'm patching stuff and don't touch my laptop but still need the screen to be on. I know this can also be done with powertoys, but as I said before, I like to figure things out myself :)

Most of my scripts also have one or more aliases in my powershell profile. I like to use short aliases so I can use the scripts and functions as easy as possible. But this made my Powershell profile quite cluttered. Recently I cleaned it up and split my profile up in two files: the profile file (`Microsoft.PowerShell_profile.ps`) is the place where all the aliases are defined. The `profileFunctions.ps1` file is where all the smaller functions are defined and this file gets imported by the profile file.

It's fun to try and automate as much as possible, especially the repetitive stuff, like converting a mac adress to all the formats used by different applications... These are small improvements in my workflow but I'd like to think they saved me more cost than I've spend writing the code for it.
