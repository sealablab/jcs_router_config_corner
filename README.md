# jcs_router_config_corner
Johnnys (public) router configuration templates.

Welome to my (public) router configuration template repo

Before we continue any further, let me describe the exact hardware/software revisions these templates were created from.

Although we will see these configurations grow in complexity over time, the following presumptions can be made throughout this repo

All running configs were generated from OPNSense 24.01 community edition, running on an official [DEC 2752](https://shop.opnsense.com/product/dec2752-opnsense-rack-security-appliance/)


## [Decisio DEC 2752 ](https://shop.opnsense.com/product/dec2752-opnsense-rack-security-appliance/) running [OPNSense](https://docs.opnsense.org/releases/CE_24.7.html#october-23-2024)

Although all of the baseline configurations were generated with the 2752 specifically, you really only need to know the following to follow along

* `igc0` (the rightmost) is dedicated to the **CORE MGMT** subnet
* `igc1` (next rightost) will be our WAN / uplink port **WAN**
* `ax0`  (the rightmost SFP+) will be our **LAN** / data-plane


## Mikrotik [CRS-326](https://mikrotik.com/product/CRS326-24G-2SplusRM) running [SwOS](https://help.mikrotik.com/docs/spaces/SWOS/pages/328415/SwOS)

* `MGMT` (the dedicated MGMT port) connects to the **CORE MGMT** subnet.
* `SFP+10` will be the TRUNK port that connects directly to the OPNSense.`ax0`

## CORE-MGMT
The **CORE-MGMT** subnet is used exclusively for management of CORE NETWORK infrastructure. You can use any old ethernet switch for it. Attached should be:
* CRS-326.`MGMT` 
* OPNSense.`igc0` (OPT)
* Your core-network administrators laptop


# Configuration file formats:
## OPNSense : [config.xml](https://github.com/mihakralj/opnsense-cli)
OPNsense maintains its entire configuration in a [single xml file](https://forum.opnsense.org/index.php?topic=18193.0) named `config.xml` 
For reference, you can find a link to my __Factory defaults__ [here](configs/OPNSense-config-factory.xml)



## SwOS ; `css326q_2.17.swb`
**SwOS** configuration files appear to be plaintext
For reference, you can find a link to my __Factory defaults__ [here](configs/CSS326Q-config-factory.txt)

# The Baseline config 

*** OPNsense.localdomain: OPNsense 24.10 ***

 LAN (ax0)       -> v4: 10.40.0.1/24
 OPT1 (igc0)     -> v4: 10.19.99.1/24
 WAN (igc1)      -> 

