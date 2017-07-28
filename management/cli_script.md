---

copyright:
  years: 2017
lastupdated: "2017-07-25"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Run commands with the API management CLI
{: #apim-cli-over}

You can use the {{site.data.keyword.Bluemix_notm}} API management CLI to complete some of the same tasks with the command line that you can complete with the {{site.data.keyword.Bluemix_notm}} graphical user interface. The commands can be entered individually in a terminal window or called in a sequence in a script. 
{:shortdesc}

## Prerequisites
{: #apim-cli-script-prereq}

Before you can use the API management CLI, you must have completed the following steps:

* Obtain a [Bluemix ID](../../admin/adminpublic.html#signing-up-for-bluemix){: new_window}. 
* Download and install the [Bluemix command line](../../cli/reference/bluemix_cli/index.html#getting-started){: new_window}.
* Install the {{site.data.keyword.Bluemix_notm}} [API management command line plug-in](../../cli/reference/bluemix_cli/index.html#install_plug-in){: new_window}.
* [Log in](../../cli/reference/bluemix_cli/bx_cli.html){: new_window} to the {{site.data.keyword.Bluemix_notm}} command line.

## Sample CLI sequence of commands for an API

The following steps demonstrate a complete cycle of API management commands from adding a gateway to an API to removing the gateway from the API:

1. Log in to {{site.data.keyword.Bluemix_notm}} 
    ```
    bluemix login -a https://api.ng.bluemix.net -c account_ID (1) -u username -p password
    ```
    {:codeblock}
    Logs you into your default {{site.data.keyword.Bluemix_notm}} organization with the command-line interface.

2. Display your APIs
    ```
    bluemix apim apis
    ```
    {:codeblock}
    Displays the APIs in your default organization.

3. Create an API
    ```
    bluemix apim api-create --name <API_NAME> --file <path_to_Swagger_file>
    ```
    {:codeblock}
    Uses the Swagger file to create a managed API from the API that you specify in your {{site.data.keyword.Bluemix_notm}} organization.

4. Update an existing API definition
    ```
    bluemix apim api-update --name <API_NAME> --file <path_to_new_Swagger_file>
    ```
    {:codeblock}
    Replaces the existing definition of the API that you specify with the new Swagger file definition.

5. Expose the API
    ```
    bluemix apim api-expose --name <API_NAME>
    ```
    {:codeblock}
    Exposes the API.

6. Share the API
    ```
    bluemix apim api-share --name <API_NAME>
    ```
    {:codeblock}
    Shares the API with others outside of your {{site.data.keyword.Bluemix_notm}} organization.

7. Stop exposing the API
    ```
    bluemix apim api-unexpose --name <API_NAME>
    ```
    {:codeblock}
    Stops sharing the API outside of your {{site.data.keyword.Bluemix_notm}} organization.

8. Display the keys for your API
    ```
    bluemix apim keys --name <API_NAME>
    ```
    {:codeblock}
    Displays the keys that are associated with your API, if there are any.

9. Stop sharing the API
    ```
    bluemix apim api-unshare --name <API_NAME>
    ```
    {:codeblock}
    Stops sharing the API.
	
10. Remove the API
    ```
    bluemix apim api-delete --name <API_NAME>
    ```
    {:codeblock}
    Removes the gateway from the API. It is no longer managed. 
    Important: If you delete a Cloud Foundry API, the base Cloud Foundry app remains in the {{site.data.keyword.Bluemix_notm}} service, but it is no longer managed. An OpenWhisk API that is deleted removes all interactions between the individual OpenWhisk actions. After the OpenWhisk API is deleted, it must be recreated if you want to use it again.
    
See [Command-line interface commands](../../cli/plugins/api-management-cliplugin/index.html) for the complete list of API management commands and their options.

