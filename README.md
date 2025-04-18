# Azure Sentinel Honeypot Project

## 🚀 Overview

Welcome to the **Azure Sentinel Honeypot Project**! This project aims to simulate a real-world cyberattack scenario using **Microsoft Azure** and **Azure Sentinel** to capture and analyze malicious activities. By setting up a vulnerable **Windows VM** in Azure, we can monitor and visualize cyberattacks using **Azure Sentinel** for security monitoring and log analysis.

Through this project, you'll learn how to deploy a honeypot, collect and analyze logs, query those logs using **Kusto Query Language (KQL)**, and create an interactive **attack map** for visualizing attack sources.

## 🛠️ Key Features

- **Honeypot Deployment**: Create an intentionally vulnerable **Windows VM** in **Azure** to act as a honeypot.
- **Security Monitoring with Sentinel**: Set up **Azure Sentinel** for log collection, aggregation, and threat detection.
- **Advanced Log Queries**: Use **KQL** to query logs for suspicious activities (e.g., failed login attempts).
- **Geo-location Enrichment**: Enhance logs with geographic data to visualize the location of attacks.
- **Attack Map Creation**: Build and display an interactive attack map in **Sentinel Workbooks**.

## 💻 Technologies Used

- **Microsoft Azure** - Cloud platform for deploying and managing virtual machines and other services.
- **Azure Sentinel** - Cloud-native SIEM (Security Information and Event Management) solution for security monitoring.
- **Kusto Query Language (KQL)** - Language for querying data in Azure Sentinel.
- **GeoIP Watchlist** - For enriching logs with geolocation information.
- **Sentinel Workbooks** - For data visualization and creating custom reports.

## 📂 Project Structure

```plaintext
Azure-Sentinel-Honeypot-Project/
├── README.md               # Project overview, instructions, and setup guide
├── sentinel-workbook/       # Contains JSON file for creating the Attack Map in Azure Sentinel
│   └── attack-map.json      # JSON configuration for the Attack Map Workbook
├── watchlist/               # Watchlist data for geo-location enrichment in Azure Sentinel
│   └── geoip-summarized.csv # GeoIP watchlist to enrich event logs with geographic data
├── screenshots/             # Visual representations of the project setup and results
│   └── attack-map-sample.png # Screenshot of the generated Attack Map in Azure Sentinel
└── setup-guide/             # Detailed instructions for setting up and replicating the project
    └── steps.md             # Step-by-step guide for deploying and configuring the honeypot
```


## Result

### Attack Map Visualization

One of the key outcomes of this project is the **Attack Map** created within **Azure Sentinel Workbooks**. This interactive map provides a geographical representation of the attack origins, showcasing where the attempted breaches are coming from.

The **Attack Map** not only displays locations but can also be drilled down to understand the attack behavior, such as login attempts and their corresponding times. By enriching the attack logs with **GeoIP** data, it adds contextual information that is crucial for incident response teams.

### Key Insights

- **Geo-location Insights**: The **GeoIP enrichment** allows for precise identification of the geographical regions from which attacks originate, helping security teams focus on specific threat vectors.
- **Security Monitoring**: The setup of this honeypot and its integration with **Azure Sentinel** provides continuous monitoring of suspicious activities, making it a useful tool for security operations in real-world environments.
- **Actionable Data**: With **KQL queries**, you can further drill into the logs, filter results, and identify suspicious patterns, making this project a learning tool for analyzing and responding to security threats.

---

## Getting Started

### Prerequisites

Before setting up the project, ensure that you have the following:

- **Azure Account**: Create a free [Azure account](https://azure.microsoft.com/en-us/free/) or use a paid subscription.
- **Basic Azure Knowledge**: Familiarity with Azure Virtual Machines (VMs) and **Azure Sentinel**.
- **KQL Knowledge**: Basic understanding of **Kusto Query Language (KQL)** will be helpful.

### Setup Instructions

To replicate this project, follow the setup guide detailed in `setup-guide/steps.md`. Below is a summary:

1. **Create an Azure Subscription**:
   - Sign up for a free [Azure account](https://azure.microsoft.com/en-us/free/).
   - If Azure doesn't allow creating a free account, you can use a paid subscription or join the Cyber Range.

2. **Create a Virtual Machine**:
   - Set up a **Windows 10** virtual machine in Azure (configure VM size and credentials).
   - Allow all inbound traffic by modifying the **Network Security Group** for the VM.

3. **Disable Windows Firewall**:
   - Log into the VM and turn off the firewall to allow inbound attacks (Windows -> `wf.msc` -> turn off firewall).

4. **Set Up Azure Sentinel**:
   - Create a **Log Analytics Workspace (LAW)** in Azure Sentinel.
   - Connect the VM to **Azure Sentinel** and configure it to send **Windows Security Events** logs to Sentinel.

5. **Enrich Logs with GeoIP Data**:
   - Import the **GeoIP Watchlist** into Azure Sentinel to add location data to your attack logs.

6. **Visualize Attack Locations**:
   - Use the **Attack Map Workbook** (`sentinel-workbook/attack-map.json`) to visualize attacks geographically in **Azure Sentinel**.

---

## Sentinel Attack Map Query

This KQL query detects failed login attempts on your Azure Sentinel workspace and visualizes them using a geographic map based on GeoIP data. The query helps you identify patterns in login attempts across various locations globally.

### Query Breakdown
- **Failed Logins**: The query tracks failed login attempts (EventID 4625) from various IP addresses.
- **GeoIP Enrichment**: The IP addresses are enriched with geographic data using the GeoIP watchlist, allowing the visualization of attack origins on the map.
- **Map Visualization**: The final result is displayed on a map, using geographic coordinates (latitude and longitude) derived from the enriched data.

### How to Use

1. Navigate to **Azure Sentinel Workbooks** in your Azure Portal.
2. Click on **+ New** to create a new **Workbook**.
3. Add a **Query** to the workbook and paste the following KQL query from the `workbooks/attack-map.json` file.
4. Configure the **Map Visualization**:
   - Set the **Latitude** and **Longitude** fields from the query results.
   - Adjust settings like **opacity**, **size settings**, and **color settings** as necessary.
5. Save the workbook with an appropriate name.

