# Setup Guide for Azure Sentinel Honeypot Project

Follow these instructions to set up the **Azure Sentinel Honeypot** project.

## Prerequisites

Before you begin, ensure you have the following:

- **Azure Account**: Create a free Azure account [here](https://azure.microsoft.com/en-us/free/) or use a paid subscription.
- **Basic Azure Knowledge**: Familiarity with Azure Virtual Machines (VMs), networking, and Azure Sentinel.
- **KQL Knowledge**: Basic understanding of Kusto Query Language (KQL) is helpful.

## Step 1: Create Azure Subscription

1. Sign up for a **free Azure account** or use a **paid Azure subscription**.
2. After signing up, log in to the [Azure Portal](https://portal.azure.com/).

## Step 2: Set Up Virtual Machine

1. In the Azure Portal, search for **Virtual Machines** and create a **new Windows 10 VM**.
2. Choose an appropriate size for the VM (e.g., **Standard B1s** for testing).
3. Set up credentials (username and password) for the VM.
4. In the **Network Security Group** (NSG) settings, create an inbound rule that allows all traffic to the VM.
5. **Important**: Turn off the **Windows Firewall** on the VM by opening **wf.msc** and setting the firewall state to "Off".

## Step 3: Set Up Azure Sentinel

1. In the **Azure Portal**, create a **Log Analytics Workspace** (LAW).
2. After creating the LAW, go to **Azure Sentinel** and link the LAW to Sentinel.
3. Set up data connectors to collect **Windows Security Events** from the VM.

## Step 4: Import GeoIP Watchlist

1. Download the **GeoIP Watchlist** file from the **watchlist/geoip-summarized.csv** folder in this repo.
2. In **Azure Sentinel**, go to **Watchlist** under the **Configuration** section.
3. Import the **geoip-summarized.csv** file to enrich logs with geographic data.

## Step 5: Visualize Attack Map

1. Use the **Attack Map Workbook** located in the **sentinel-workbook/attack-map.json** file.
2. Import this file into **Azure Sentinel** under **Workbooks**.
3. This workbook will create a map visualization of failed login attempts and their geographic locations.

## Step 6: Monitor and Query Logs

1. Use **KQL (Kusto Query Language)** to query the logs and identify failed login attempts (Event ID: 4625).
2. Use the provided **KQL query** in the **README.md** to start analyzing the logs.

## Conclusion

After following the steps, you'll have a **Honeypot** running on **Azure** with **Azure Sentinel** monitoring and visualizing failed login attempts, along with geographical data enriched through the **GeoIP Watchlist**.

---
