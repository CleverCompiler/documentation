---
title: "Managing Network Global Configurations"
description: "Provides instructions on configuring or managing global configuration settings."
weight: 20
tags:
- network
---

Use the **Global Configuration Settings** screen to manage existing general network settings like the default gateway and DNS servers. Set DHCP to assign the IP address or to set a static IP address, add IP address aliases, and set up services to allow external communication.

{{< hint type=warning >}}
**Disruptive Change**

You can lose your TrueNAS connection if you change the network interface that the web interface uses!  
You might need command line knowledge or physical access to the TrueNAS system to fix misconfigured network settings.
{{< /hint >}}

{{< expand "Tutorial Video" "v" >}}

{{< embed-video name="scaleangelfishstaticipglobalnetworking" >}}

{{< /expand >}}

{{< expand "Can I configure these options elsewhere?" "v" >}}
Users can configure many of these interface, DNS, and gateway options in the [Console Setup menu]({{< relref "ConsoleSetupMenuSCALE.md" >}}).
Be sure to check both locations when troubleshooting network connectivity issues.
{{< /expand >}}

## Setting Up External Communication for Services
Use the **Global Configuration Outbound Network** radio buttons to set up services for external communication capability.

These services use external communication:
* ACME DNS-Authenticators
* Anonymous usage statistics
* Catalog(s) information exchanges
* Cloud sync
* KMIP
* Mail (email service)
* Replication
* Rsync
* Support
* TrueCommand iX portal
* Updates
* VMWare snapshots

Select **Allow All** to permit all the above services to communicate externally. This is the default setting.

Select **Deny All** to prevent all the above services from communicating externally.

Select **Allow Specific** to permit external communication for the services you select.
**Allow Specific** displays a dropdown list of the services you can select.
Click on all that apply. A checkmark displays next to a selected service, and these services display in the field separated by a comma (,).

Click **Save** when finished.

## Setting Up Netwait
Use Netwait to prevent starting all network services until the network is ready.
Netwait sends a [ping](https://manpages.debian.org/unstable/inetutils-ping/ping.1.en.html) to each of the IP addresses you specify until one responds, and after receiving the response then services can start.

To set up Netwait, from the **Network** screen:

1. Click on **Settings** in the **Global Configuration** widget to open the **Global Configuration** screen.

2. Select **Enable Netwait Feature**. The **Netwait IP List** field displays.

3. Enter your list of IP addresses to ping. Press <kbd>Enter</kbd> after entering each IP address.

4. Click **Save** when finished.
