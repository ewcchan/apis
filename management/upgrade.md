---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-10"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Accessing more API management features
{: #upgrade}

The API management function that is provided with your {{site.data.keyword.Bluemix}} API allows you limited control of call rates, OAuth, and view analytics. You can have greater management control over APIs by upgrading to the {{site.data.keyword.apiconnect_full}} service. The {{site.data.keyword.apiconnect_short}} service provides more choices of security policies and greater control over rate limits. In addition to this, you'll be able to configure a fully customizable Developer Portal so that you can socialize your APIs and engage with the developer community. Other benefits include:
* Lifecycle management
* Composite APIs
* Web services integration
* Protocol mediation
* API generation from schema
* Micro services development

Migrating to the {{site.data.keyword.apiconnect_short}} service is easy, and you do not have to recreate any of the APIs that you are managing with API management. You can migrate your APIs automatically or manually.

## Automatically migrating APIs to {{site.data.keyword.apiconnect_short}}
{: #auto_migrate_api}

If you decide to upgrade to {{site.data.keyword.apiconnect_short}}, you'll need to migrate your APIs from API management to the {{site.data.keyword.apiconnect_short}} service by selecting and completing the following procedure for the type of API that you are migrating.

### Cloud Functions API

1. Select **Functions** in your {{site.data.keyword.Bluemix_notm}} menu to view your Cloud Functions.

2. In the Functions list, select **APIs** in the navigation.

3. Select the name of the Function API that you want to migrate.

4. Select **Definition** in the navigation.

5. Select **API definition file** > **Export to API Connect** > **Export API** in the *API definition file* section. If you already have an existing {{site.data.keyword.apiconnect_short}} service, then it automatically migrates the API to the existing service. If you do not already have an {{site.data.keyword.apiconnect_short}} service configured, it automatically adds the service with a free Lite plan and migrates the API. If your instance failed to provision, complete the steps in [Manually migrating APIs to {{site.data.keyword.apiconnect_short}}](#man_migrate_api) to manually migrate it to the new service. 

6. Before closing the screen of the original API, disable the slider for **Expose Managed API** . This prevents anyone from acting on the endpoint of the old version.

### Cloud Foundry API

1. Open your existing Cloud Foundry API source in the {{site.data.keyword.Bluemix_notm}} Dashboard. 

2. Select **API Management** in the navigation menu.

3. Select **Definition** in the navigation.

4. Select **API definition file** > **Export to API Connect** > **Export API**. If you already have an existing {{site.data.keyword.apiconnect_short}} service, then it automatically migrates the API to the existing service. If you do not already have an {{site.data.keyword.apiconnect_short}} service configured, it automatically adds the service with a free Lite plan and migrates the API. If your instance failed to provision, complete the steps in [Manually migrating APIs to {{site.data.keyword.apiconnect_short}}](#man_migrate_api) to manually migrate it to the new service.
   
5. After the content has been migrated to the {{site.data.keyword.apiconnect_short}} instance, select the link that is provided to access the migrated version.
    **Important:** To prevent issues with multiple instances of the API running, make sure that you disable the *Manage the API* slider in the original version of the API.

6. Select the **APIs** tab in the navigation.

7. Select **Drafts** to view your new API.

## Manually migrating APIs to {{site.data.keyword.apiconnect_short}}
{: #man_migrate_api}

If the process to migrate your API to the {{site.data.keyword.apiconnect_short}} service did not finish correctly, complete the following steps to manually migrate it:

1. Open your API.
	1. Sign in to {{site.data.keyword.Bluemix_notm}}.
	2. For a Cloud Foundry app: 
		1. Select **Dashboard** in the Menu.
		2. Select the name of the Cloud Foundry app that you want to migrate.
		3. Select **API Management** in the navigation.
	3. For a Cloud Functions action: 
		1. Select **Functions** in the Menu.
		2. Select **APIs** in the navigation.
		3. Select the name of the API that you want to migrate.
2. Download the Swagger document for the API from API management.
    1. Select **Definition** in the navigation.
	2. Select **API definition file**.
    3. Select **Export YAML** or **Export JSON**, depending on your file type, to download the definition of the API. The file downloads to your downloads folder.
3. Create and prepare the {{site.data.keyword.apiconnect_short}} instance. 
	1. Go to **APIs** in the navigation to filter the services.
	2. Select the API Connect service. 
    3. Create an instance of the {{site.data.keyword.apiconnect_short}} service from the {{site.data.keyword.Bluemix_notm}} catalog.
	4. Select your plan. The Lite plan is the free option.
	5. Select **Create** to create the instance.
4. Import the Swagger document to your {{site.data.keyword.apiconnect_short}} instance by completing the following steps:
	1. From the {{site.data.keyword.apiconnect_short}} service dashboard, select **Navigate to... (>>)** > **Drafts** in the menu.
	2. Select the APIs tab.
	3. Select **+Add** > **Import API from a file or URL**.
	4. Find and select the Swagger file that you downloaded from API management. Select **Open**.
	5. Select **Import** to import your API into the {{site.data.keyword.apiconnect_short}} service.
5. To prevent issues that result from running multiple instances of the API, make sure that you disable the *Manage the API* slider in the original version of the API.

Your API is available in the {{site.data.keyword.apiconnect_short}} service instance. 

## Publish the API

You can continue to publish the API by completing the following steps:

1. Create a Catalog.
	1. Select **+Add** to create a catalog.
	2. Enter a Display name and name for your catalog, and select **Add**.
	3. Select the catalog that you created.
2. Specify settings for your API.
    1. Select **Create product**.
	2. Specify a name for the product.
	2. Select the product that you created to view its settings.
	3. Set the rate limit for the API.
	4. Set the tier for the API.
3. Add the endpoint for the API, if necessary.
    1. Select the API.
	2. Select the Assembly tab.
	3. Add the endpoint, if it is not already specified.
	
 After you migrate your APIs, you can access all of the API management features by opening the {{site.data.keyword.apiconnect_short}} service tile and through the {{site.data.keyword.Bluemix_notm}} Dashboard. 

