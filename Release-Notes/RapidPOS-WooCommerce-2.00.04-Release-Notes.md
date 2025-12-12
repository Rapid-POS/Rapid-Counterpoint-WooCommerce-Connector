# Rapid POS WooCommerce Connector v2.00.04 Release Notes  
_Release Date: Coming soon!_

---
  
## Bug Fixes and Performance Enhancements  
  
### Optimized Product Attribute Term Handling  
  
- Previously, when syncing an item, the connector retrieved all existing terms for each product attribute before determining whether a term already existed.  
  - If the term existed, it was assigned to the product.  
  - If the term did not exist, it was created and then assigned.  
  
- The connector now attempts to assign the term immediately without pre-loading the full term list.  
  - If the term already exists (the most common scenario), processing immediately continues to the next attribute, significantly improving performance.  
  - If the term does not exist, the connector creates the missing term in WooCommerce and assigns it accordingly. 
  
**Note:** Fields in Counterpoint can be synced to Product Attribute fields in WooCommerce using the **WooCommerce Custom Field Mapping** table. This improvement specifically affects how the connector sets the **term (value)** for a product attribute in WooCommerce.  
  
### Adjusted Install Script for WooCommerce Item Field Placement and Visibility  
  
- Updated the install script to correctly control whether the **WooCommerce Item** checkbox is shown on the *Items* custom tab based on the `UseWooCommerceFlag` configuration value.  
  - When `UseWooCommerceFlag` is set to **false**, the **WooCommerce Item** checkbox is hidden.  
  - When `UseWooCommerceFlag` is set to **true**, the checkbox is displayed and positioned directly below the **WooCommerce ID** field.

### Corrected Cell Description Population for Gridded Items on WooCommerce Order Imports 
 
- Fixed an issue where WooCommerce orders imported into Counterpoint were not populating the **Cell Description field** for gridded items.  
- The connector now correctly derives and sets `PS_DOC_LIN.CELL_DESCR` based on the item’s grid dimensions or cell count when downloading WooCommerce orders.  
- This ensures that line items for gridded products display the expected cell description values in Counterpoint, matching native Counterpoint behavior.
