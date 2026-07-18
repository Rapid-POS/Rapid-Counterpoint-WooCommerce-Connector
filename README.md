# Rapid POS WooCommerce Connector - Version 2.01.00
Updated 7/17/2026

---

## Overview

The **Rapid POS WooCommerce Connector** seamlessly integrates your Counterpoint POS system with your WooCommerce online store. This connection keeps your items, customers, and orders synchronized automatically — helping you manage your ecommerce operations efficiently without duplicate data entry.

---

## Minimum System Requirements:
- Minimum Counterpoint version: **8.5.6.2**  
- Minimum SQL Server version: **2016**  
- Minimum Supported Operating System version: **Windows Server 2016** or **Windows 11 Pro** 
- Minimum PowerShell version: **5.1**  

If you would like the WooCommerce connector but your system does not meet these minimum requirements, please consult your Care Team Lead (vCIO) for an upgrade quote.

> [!WARNING]
> Your environment must meet our [CI/CD Connector Requirements](https://github.com/Rapid-POS/Miscellaneous-Documents/blob/main/CICD-Connector-Requirements.md) (server access, firewall rules, etc.) before any install or upgrade. Troubleshooting, manual installs, or follow-up work resulting from unmet requirements will be billed at standard T&M rates.

---

## Section 1: Data Flow Summary

The Rapid POS WooCommerce Connector allows you to:

- Sync **inventory data** between Counterpoint and WooCommerce, keeping pricing and quantity information consistent across systems.  
- Automatically import **online orders** and **customers** from WooCommerce into Counterpoint.

### Items (Products)
- Flow **from Counterpoint → WooCommerce**  
- Includes both standard and gridded items.  

### Orders & Customers
- Flow **from WooCommerce → Counterpoint**  
- New online orders and customer updates are imported every 15 minutes.  

---

**Note:** Rapid POS does not provide website design or hosting services. We recommend working with a qualified ecommerce professional to build and maintain your WooCommerce storefront.
