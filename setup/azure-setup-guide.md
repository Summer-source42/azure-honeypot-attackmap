# Project Setup Guide

This guide will walk you through the steps to replicate the Azure Sentinel Honeypot Project with a focus on setting up the Azure environment and visualizing attack maps.

## Prerequisites

Before you begin, ensure you have the following:
- An **Azure Subscription** (can be a free trial or a paid account)
- Access to **Azure Sentinel** and **Log Analytics Workspace**
- Basic understanding of **Azure VM**, **KQL (Kusto Query Language)**, and **Azure Sentinel Workbooks**

## Step 1: Create an Azure Subscription

1. Sign up for a free Azure subscription: [Azure Free Account](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account)
2. After signing up, log in to the Azure Portal: [Azure Portal](https://portal.azure.com)

## Step 2: Set Up a Virtual Machine

1. Go to **Azure Portal > Virtual Machines** and create a new Windows Virtual Machine (VM).
2. Configure your VM with the appropriate settings (OS, size, etc.).
3. Set up a **Network Security Group** to allow all inbound traffic.
4. Log in to the VM, then disable the firewall by running:
   ```bash
   wf.msc

