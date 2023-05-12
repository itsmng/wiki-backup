# OCS Inventory NG

This plugin allows you to synchronize OCS Inventory data in your ITSM-NG instance.

`Note: the OCS Inventory TRACE_DELETED option is required.`

## Installation

Installing this plugin is done following the standard process for itsm plugins, simply clone [the git repository](https://github.com/itsmng/ocsinventoryng) or [download a release](https://github.com/itsmng/ocsinventoryng/releases) and place it within ITSM `plugins` folder.

Unzip the plugin archive, set Apache rights and enjoy !

## Features

This plugin bundle a lot of feature in order to import the following data from OCS Inventory :

* Computers information
* Softwares information
* SNMP Scanned devices
* IpDiscover scans
* OCS' plugins information

Supported plugin list :

* Office licences
* Antivirus information
* Windows update status
* Uptime
* Teamviewer
* Windows users
* Proxy configuration
* Extended operating system information
* Services
* Custom installed application
* Network drives
* Process list
* Bitlocker

## Rights management

The OCS plugin rights are available in `Administration > Profiles > {profile_name} > OCSNG`.

![](../img/ocsinventoryng/ocsinventoryng_rights_management.png)

* `Allowed OCSNG servers` : grant access to a configured OCS server data.
* `OCSNG servers` : can modify OCS server configuration.
* `Manually synchronization` : can manually import, synchronize and link OCS equipment.
* `See information` : can see OCS detail information for an imported equipment.
* `Clean links between ITSM-NG and OCSNG` : can clean equipment links.
* `Import computer` : can import computer.
* `Link computer` : can link computer.
* `Rules` : can update import rules.

## Configuration

### OCS server setup

To setup the connection between OCS Inventory database and ITSM-NG, go to `Tools > OCS Inventory NG` and click on `Add a OCSNG server`.

It's also possible to configure a server from `Setup > Plugins > OCS Inventory NG > OCSNG servers`.

![](../img/ocsinventoryng/ocsinventoryng_database_configuration.png)

### Data to import

This tab allows you to define which information from a computer should be imported into ITSM-NG.

![](../img/ocsinventoryng/ocsinventoryng_data_to_import.png)

### Import options

This tab allows you to configure the synchronisation options between OCS and ITSM-NG.

![](../img/ocsinventoryng/ocsinventoryng_import_options.png)

* `Web address of the OCSNG console` : set the OCS Inventory administration console URL. If the address is provided, a link will then be available from the detail page of a computer in ITSM-NG to redirect to the details page on OCS.
* `Limit the import to the following tags (separator $, nothing for all)` : limits the import to the machine with this OCS tag.
* `Exclude the following tags (separator $, nothing for all)` : excludes the import of the machine having this OCS tag.
* `Behavior when disconnecting` : behavior that ITSM-NG must adopt if an element connected to a machine is no longer imported/synchronized by OCS.
* `Use the OCSNG software dictionary` : allows you to synchronize/import software only from the `Dictionary` feature of OCS.
* `Number of items to synchronize via the automatic OCSNG action` : indicates the number of machines that will be synchronized by the automatic action (excluding `Expert` mode).
* `Behavior to the deletion of a computer in OCSNG` : behavior that ITSM-NG must be adopt if a machine is removed from OCS.

### General history

From this tab, you can configure the history for each executed actions.

![](../img/ocsinventoryng/ocsinventoryng_general_history.png)

### Rules

TODO

## Import computer

You will find the computer import actions in `Tools > OCS Inventory NG > Inventory Import`.

![](../img/ocsinventoryng/ocsinventoryng_inventory_import.png)

### Manual actions

#### Import or link new computers

To import computers manually, click on `Import new computers`.

From this page, you will be able to import or link new computers on ITSM-NG.

![](../img/ocsinventoryng/ocsinventoryng_manual_import_computer.png)

`Note: To massively import computers, it is recommended to use the automatic import script. See Massive actions below.`

After import, you will find the `OCS Inventory NG Import informations` on the computer details page.

![](../img/ocsinventoryng/ocsinventoryng_computer_ocs_info.png)

#### Synchronize computers already imported

To synchronize computers manually, click on `Synchronize computers already imported`.

From this page, you will be able to select all computers that you want to synchronize.

![](../img/ocsinventoryng/ocsinventoryng_manual_computer_synchro.png)

#### Clean OCSNG deleted computers

With `Clean OCSNG deleted computers`, you can clean manually the removed OCS computers from ITSM-NG.

![](../img/ocsinventoryng/ocsinventoryng_clean_deleted_computers.png)

`Note: The cleaning action is executed automatically from the moment you click on it.`

#### Clean links between ITSM-NG and OCSNG

This feature allows you to clean broken link between ITSM-NG and OCS.

![](../img/ocsinventoryng/ocsinventoryng_clean_link_computer.png)

A link is broken if a machine is removed from OCS or from ITSM-NG.

### Massive actions

To massively import computers, it is recommended to use automatic import script.

You will found scripts in `itsm-ng/plugins/ocsinventoryng/scripts`.

Below, the list the synchronization/import script arguments :

    sh ocsng_fullsync.sh -h

    Usage:
        ocsng_fullsync.sh [--arg]

    Arguments:
        --thread_nbr=num: number of threads to launch
        --server_id=num: ITSM-NG ID of the OCS server to synchronize from. Default is ALL the servers
        --nolog: output to console
        --debug: run in debug mode

Here, an example to script execution :

    sh ocsng_fullsync.sh --thread_nbr=1 --server_id=2 --nolog --debug

Console output :

    Fri May 12 15:30:13 UTC 2023 ocsng_fullsync.sh started
            Manage delete items in OCS server #2: "OCS-SERVER"
    =====================================================
            Thread #1: starting (1/1)
            Thread #1: import computers from server: 'OCS-SERVER'
            Thread #1: 9 computer(s) found
            Thread #1: 1 computer(s) imported
            Thread #1: 0 computer(s) synchronized
            Thread #1: 0 computer(s) linked
            Thread #1: 8 computer(s) failed import
            Thread #1: 0 computer(s) not updated
            Thread #1: 0 computer(s) not unique
            Thread #1: 0 computer(s) link refused
            Thread #1: done!!
    =====================================================
    cleaning up.
    Fri May 12 15:30:20 UTC 2023 ended

You can configure crontab to run the script regularly :

    */30 * * * * sh /var/www/itsm-ng/plugins/ocsinventoryng/scripts/ocsng_fullsync.sh --thread_nbr=2 --server_id=1

## Import IpDiscover

You will find the IpDiscover import actions in `Tools > OCS Inventory NG > IPDiscover Import`.

### Configuration

To configure IpDiscover import, click on the link `See Setup : IPDiscover Import before`.

![](../img/ocsinventoryng/ocsinventoryng_ipdiscover_import.png)

From this page, you will be able to setup the behavior of the reconciliation between SNMP equipments and IpDiscover equipments, of the IpDiscover non-inventoried equipment and of the IpDiscover identified equipment.

#### Configuring the binding of IpDiscover and SNMP equipments

![](../img/ocsinventoryng/ocsinventoryng_ipdiscover_snmp.png)

* `Merge IpDiscover equipment with SNMP equipment if IP address matches` : enable/disable the merging of IpDiscover devices with SNMP devices if the IP address matches. If an IpDiscover equipment corresponds to an SNMP equipment, it will be automatically filled in as an identified equipment in OCS.
* `Switch the equipment to identified on OCS with type` (required if the option above is enabled) : select the type of OCS network which will be automatically assigned to the IpDiscover equipment on OCS at the time of identification. 

#### IpDiscover Non-Inventoried Equipment configurations

![](../img/ocsinventoryng/ocsinventoryng_ipdiscover_noninventoried.png)

This configuration allows you to link the specific OCS information of the non-identified IpDiscover device to a field of the  ITSM-NG Network Equipment object.

#### IpDiscover Identified Equipment configurations

![](../img/ocsinventoryng/ocsinventoryng_ipdiscover_identified.png)

By default, the identified IpDiscover equipment are imported as Network Equipment like the non-inventoried IpDiscover equipment. 

With this configuration, you will be able to select an OCS network type to be imported as an ITSM-NG object other than a Network Equipment.

### Manual actions

TODO

### Massive actions

TODO

## Import SNMP equipment

You will find the SNMP equipment import actions in `Tools > OCS Inventory NG > SNMP Import`.

### Configuration

TODO

### Manual actions

TODO

### Massive actions

TODO
