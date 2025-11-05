# Template for Digital Stock Management

The Digital Stock Management Template is created by the [510 Data & Digital team](https://510.global/) of [the Netherlands Red Cross](https://rodekruis.nl/en). It is designed to help Red Cross Red Crescent National Societies strengthen their management of stock and warehouse activities by having a systematic reporting way using familiar tools Kobo Toolbox and PowerBI.

---

## Table of Contents

- [What is Digital Stock Management?](#what-is-digital-stock-management)
- [Features](#features)
- [Requirements](#requirements)
- [Setup](#setup)
- [How to Use](#how-to-use)
- [Read more](#read-more)

---

## What is Digital Stock Management?

Digital Stock Management is a centralised stock management tool that collect, summarize and displays stocking activity information in warehouses. The tool makes use of [Kobo Toolbox](https://www.kobotoolbox.org/) and [PowerBI](https://www.microsoft.com/en-us/power-platform/products/power-bi) which are commonly used among Red Cross Red Crescent National Societies in their operations.

Standardized but highly customised:
- It is set with standard questions in stock and warehouse management, so organisations can easily adapt it to their own needs and contexts.
- The [data model](guides/data-model.md) is kept as simple as possible. All calculations and consolidations are done within Power BI queries.
- This combination makes the system easy to understand, maintain, and use, even as teams make their own custom changes.

Therefore, this template is designed so anyone with basic to intermediate skills of Data and Information Management can deploy and lead the implementation with ease.

---

## Features

- **Centralise registration of receivals & issuance** with simple and consistent data entry
- **Overview of the current inventory and values** to see all inventory, consolidations and activities at a glance
- **Support decision making** based on all latest information about items in one place
- **Integration** with:
   - Commonly used data collection tool Kobo Toolbox
   - Power BI dashboard for visualisation and reporting

- **Notify users via email about inventory and activities[^1]** to timely act on these items

[^1]: Additional feature, see [email notification](guides/optional-feature.md)

---

## Requirements

**Hard Requirements**

- A KoboToolbox account: those affiliated with National Society a free account can be created at [Kobo IFRC server](https://kobo.ifrc.org/)
- Install [Power BI desktop](https://www.microsoft.com/en-us/download/details.aspx?id=58494)

**Recommendations**

- A [workspace](https://learn.microsoft.com/en-us/power-bi/collaborate-share/service-new-workspaces) in Power BI service for better managing published Power BI dashboard and user roles.
- Have an admin role in the workspace.

---

## Setup

The tool template comsists of 2 Kobo forms and a Power BI dashboard:
- [Form 1 - New registration.xlsx](kobo-forms/Form%201%20-%20New%20registration.xlsx)
- [Form 2 - Warehouse management.xlsx](kobo-forms/Form%202%20-%20Warehouse%20management.xlsx)
- [Stocking Warehouses.pbix](pbi/Stocking%20Warehouses.pbix)

Basic contents in this tool is already made use in various cases. It is ready to be connected and deployed as is. Follow [Deploy](#deploy) to do so. 

Of course, the contents can be customised to your own local context, such as currency of goods. Follow first [Customizations](#customizations) for these adjustments, then [deploy](#deploy).

### Customizations

- Add local currency to data collection forms:
  
  Open Form 1 xls file, go to question name `currency` (type `calculate`) in sheet `survey`, change the value in `calculation` column to the local currentcy name ISO code e.g. `"EUR"` question in the 2 Kobo xls forms

- Populate item category options:
  
  In Form 1 xls file, go to sheet `choices` edit or add more options for item category to your need. Make sure to use the exact same `list_name` value in all options : `item_category`.

- Dashboard
  
  Open the Power BI dashboard template project file with Power BI desktop, add NS logo in the dashboard (by inserting image) on the upper left corner in <ins>all</ins> dashboard pages.

### Deploy

**1. Deploy forms**
1. In Kobo platform, create 2 new projects by [uploading the 2 xls form](https://support.kobotoolbox.org/getting_started_xlsform.html#uploading-and-previewing-the-xlsform-in-kobotoolbox), rename the project titles if needed
2. Data from Form 1 - New registration linked with Form 2 - Warehouse management using [Dynamic Data Attachment](https://support.kobotoolbox.org/dynamic_data_attachment.html). Follow [instructions](https://support.kobotoolbox.org/dynamic_data_attachment.html#setting-up-projects-for-dynamic-linking) to link Form 1 (parent) to Form 2 (children).
3. Deploy the 2 forms
4. Generate [named exports](https://support.kobotoolbox.org/synchronous_exports.html#generating-a-named-export) of the 2 forms then get their [synchronous export links](https://support.kobotoolbox.org/synchronous_exports.html#retrieving-the-synchronous-export-link)

**2. Deploy dashboard**

On your computer:

5. Open the Power BI dashboard template project file. In Transform data, select in the Queries panel a query e.g. "Form 1 - New registration", and replace the link in `FileURL` with the synchronous export link of the corresponding Kobo form.
6. Do the same for the other query e.g. "Form 2 - Warehouse management".
7. Make sure the query steps are valid after the replacement.
8. [Publish](https://learn.microsoft.com/en-us/power-bi/create-reports/desktop-upload-desktop-files) the dashboard to your workspace in the Power BI service

In the Power BI workspace:

9. [Verify data source credentials](https://connectorly.io/blog/update-data-source-credentials-power-bi/) of the published dashboard
10. Enable [auto-refresh](https://learn.microsoft.com/en-us/power-bi/connect-data/refresh-scheduled-refresh#scheduled-refresh)
11. Share the published dashboard by [giving people access to the workspace](https://learn.microsoft.com/en-us/power-bi/collaborate-share/service-give-access-new-workspaces).

---

## How to Use

1. When there are new items, or new warehouses, or new donor/project that are not known before, use Form 1 - New registration to register them.
   
   Ideally, this should be done at Logistics/Produrement at HQ level who has all overviews.

2. When reporting an activity at a warehouse, use Form 2 - Warehouse management to register goods in or out. Form 2 also include possibility to take photos relevant document which can be displayed in the dashboard.
   
   This form should be used at warehouses by store manager.

3. The dashboard's queries will perform all set calculation and visualise automatically.

For more in-depth guides for specific scenarios, see the Guides section.

---
