---

copyright:
  years: 2017,2018
lastupdated: "2018-01-11"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# My APIs
{: #manage_api}

Select **Managed APIs** in the navigation of the **APIs** section to see the overall status of the APIs that you manage and those you have previously managed but are currently unexposed. Select **Shared APIs** to see all of the APIs that have been shared with your {{site.data.keyword.Bluemix_notm}} organization through API management or through the {{site.data.keyword.apiconnect_full}} service. **Pricing** lists and provides the details for the available {{site.data.keyword.apiconnect_service}} service options.

You can view all of the APIs that you manage with API management together by using the APIs dashboard. 

## Viewing managed APIs
{: #view_api}

Here you can view APIs created for Cloud Foundry applications, {{site.data.keyword.openwhisk_short}} actions, and other external sources.

1. From the {{site.data.keyword.Bluemix_notm}} Dashboard, select the **Menu** icon > **APIs**.
2. To select your source, click **Managed APIs**. A list of the APIs that are currently managed is displayed. The types of APIs include the following types:
    * User Defined Endpoints - These entries are APIs that are outside of the {{site.data.keyword.Bluemix_notm}} environment, and tracked by their URL endpoint. 
	* CF Apps - These entries are Cloud Foundry apps that have corresponding API management.
    * {{site.data.keyword.openwhisk_short}} Apps - These entries are {{site.data.keyword.openwhisk_short}} actions that are wrapped inside of an API.

Select the name of an API to view more details about that API.

## Creating managed APIs
{: #create_mgd_api}

You can add an API to the list without leaving the list of managed APIs by selecting **Create Managed API**.

After selecting if you want to create a Cloud Foundry, {{site.data.keyword.openwhisk_short}} action, or API Proxy (external) API, enter the information for your new API.  

This is the only place where you can add an API Proxy, or external API. An external API is one that is not created or stored in the {{site.data.keyword.Bluemix_notm}} organization space. You can manage an external API by specifying the URL of its external endpoint. This is helpful when you are trying API management to see if it meets your needs, or when you already have APIs that are running with existing URLs that you do not want to disrupt. 

See [Manage APIs](manage_apis.html) for additional information about the required settings for creating APIs.

## Working with shared APIs
{: #share_api}

In the **Shared APIs** section, you can view APIs that have been created by others and shared with you. You can also create API keys for the APIs associated with Cloud Foundry apps, {{site.data.keyword.openwhisk_short}} actions, and the {{site.data.keyword.appconserviceshort}} service.

1. From the {{site.data.keyword.Bluemix_notm}} Dashboard, click the **Menu** icon > **APIs**.
2. Select **Shared APIs** in the navigation. All the APIs that you can consume are displayed here.
3. To consume an API, select it to open its Developer Portal, where you can subscribe to a plan in order to use it. 
4. After you select an API to manage, see [Manage APIs](manage_apis.html) for more information about how to complete the following tasks: 
    * View API usage
    * Create API keys
    * Use the API Explorer to view documentation and test the API.
