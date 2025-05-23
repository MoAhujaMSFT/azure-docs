---
title: "[Recommended] Infoblox SOC Insight Data Connector via AMA connector for Microsoft Sentinel"
description: "Learn how to install the connector [Recommended] Infoblox SOC Insight Data Connector via AMA to connect your data source to Microsoft Sentinel."
author: cwatson-cat
ms.topic: generated-reference
ms.date: 10/15/2024
ms.service: microsoft-sentinel
ms.author: cwatson
ms.collection: sentinel-data-connector
---

# [Recommended] Infoblox SOC Insight Data Connector via AMA connector for Microsoft Sentinel

The Infoblox SOC Insight Data Connector allows you to easily connect your Infoblox BloxOne SOC Insight data with Microsoft Sentinel. By connecting your logs to Microsoft Sentinel, you can take advantage of search & correlation, alerting, and threat intelligence enrichment for each log. 

This data connector ingests Infoblox SOC Insight CDC logs into your Log Analytics Workspace using the new Azure Monitor Agent. Learn more about ingesting using the new Azure Monitor Agent [here](/azure/sentinel/connect-cef-ama). **Microsoft recommends using this Data Connector.**

This is autogenerated content. For changes, contact the solution provider.

## Connector attributes

| Connector attribute | Description |
| --- | --- |
| **Log Analytics table(s)** | CommonSecurityLog (InfobloxCDC_SOCInsights)<br/> |
| **Data collection rules support** | [Workspace transform DCR](/azure/azure-monitor/logs/tutorial-workspace-transformations-portal) |
| **Supported by** | [Infoblox](https://support.infoblox.com/) |

## Query samples

**Return all logs involving DNS Tunneling**

   ```kusto
InfobloxCDC_SOCInsights

   | where ThreatType == "DNS Tunneling"
   ```

**Return all logs involving a configuration issue**

   ```kusto
InfobloxCDC_SOCInsights

   | where ThreatClass == "TI-CONFIGURATIONISSUE"
   ```

**Return all high threat level logs**

   ```kusto
InfobloxCDC_SOCInsights

   | where ThreatLevel == "High"
   ```

**Return raised status logs**

   ```kusto
InfobloxCDC_SOCInsights

   | where Status == "RAISED"
   ```

**Return logs involving a high amount of unblocked DNS hits**

   ```kusto
InfobloxCDC_SOCInsights

   | where NotBlockedCount >= 100
   ```

**Return each Insight by ThreatFamily**

   ```kusto
InfobloxCDC_SOCInsights

   | summarize dcount(InfobloxInsightID) by ThreatFamily
   ```



## Prerequisites

To integrate with [Recommended] Infoblox SOC Insight Data Connector via AMA make sure you have: 

- ****: To collect data from non-Azure VMs, they must have Azure Arc installed and enabled. [Learn more](/azure/azure-monitor/agents/azure-monitor-agent-install?tabs=ARMAgentPowerShell,PowerShellWindows,PowerShellWindowsArc,CLIWindows,CLIWindowsArc)
- ****: Common Event Format (CEF) via AMA and Syslog via AMA data connectors must be installed. [Learn more](/azure/sentinel/connect-cef-ama#open-the-connector-page-and-create-the-dcr)


## Vendor installation instructions

Workspace Keys

In order to use the playbooks as part of this solution, find your **Workspace ID** and **Workspace Primary Key** below for your convenience.


   Workspace Key

Parsers

>This data connector depends on a parser based on a Kusto Function to work as expected called [**InfobloxCDC_SOCInsights**](https://github.com/Azure/Azure-Sentinel/blob/master/Solutions/Infoblox%20SOC%20Insights/Parsers/InfobloxCDC_SOCInsights.yaml) which is deployed with the Microsoft Sentinel Solution.

SOC Insights

>This data connector assumes you have access to Infoblox BloxOne Threat Defense SOC Insights. You can find more information about SOC Insights [**here**](https://docs.infoblox.com/space/BloxOneThreatDefense/501514252/SOC+Insights).

Infoblox Cloud Data Connector

>This data connector assumes an Infoblox Data Connector host has already been created and configured in the Infoblox Cloud Services Portal (CSP). As the [**Infoblox Data Connector**](https://docs.infoblox.com/display/BloxOneThreatDefense/Deploying+the+Data+Connector+Solution) is a feature of BloxOne Threat Defense, access to an appropriate BloxOne Threat Defense subscription is required. See this [**quick-start guide**](https://www.infoblox.com/wp-content/uploads/infoblox-deployment-guide-data-connector.pdf) for more information and licensing requirements.


2. Secure your machine 

Make sure to configure the machine's security according to your organization's security policy


[Learn more >](https://aka.ms/SecureCEF)



## Next steps

For more information, go to the [related solution](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/infoblox.infoblox-app-for-microsoft-sentinel?tab=Overview) in the Azure Marketplace.
