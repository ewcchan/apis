---

copyright:
  years: 2017
lastupdated: "2017-06-09"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Running commands with the API management CLI
{: #apim-cli-over}

You can use the IBM Bluemix API management CLI to complete some of the same tasks with the command line that you can complete with the Bluemix graphical user interface. The commands can be entered individually in a terminal window or called in a sequence in a script. 
{:shortdesc}

## Prerequisites
{: #apim-cli-script-prereq}

Before you can use the API management CLI, you must have completed the following steps:

* Obtain a [Bluemix ID](../../admin/adminpublic.html#signing-up-for-bluemix){: new_window}. 
* Download and install the [Bluemix command line](../../cli/reference/bluemix_cli/index.html#getting-started){: new_window}.
* Install the Bluemix [API management command line plug-in](../../cli/reference/bluemix_cli/index.html#install_plug-in){: new_window}.
* [Log in](../../cli/reference/bluemix_cli/bx_cli.html){: new_window} to the Bluemix command line.

## Sample script

The following sample script demonstrates a complete cycle of API management commands from adding a gateway to an API to removing the gateway from the API:

```
bluemix login -a https://api.ng.bluemix.net -c account_ID (1) -u username
 -p password
rem Logs you into your default Bluemix organization with the command-line interface.

pause

bluemix apim apis
rem  Displays the APIs in your default organization.

pause

bluemix apim api-create apimclitest downloads/helloWorld.json
rem Uses the helloWorld.json file to create a managed API from the apimclitest API 
rem that is in your Bluemix organization.

pause

bluemix apim api-update apimclitest downloads/newhelloWorld.json
rem Replaces the existing json definition of the apimclitest with the 
rem newhelloWorld.json definition.

pause

bluemix apim api-expose apimclitest
rem Exposes the API.

pause

bluemix apim api-share apimclitest
rem Shares the API with others outside of your Bluemix organization.

pause

bluemix apim api-unshare apimclitest
rem Stops sharing the API outside of your Bluemix organization.

pause

bluemix apim keys apimclitest
rem Displays the keys that are associated with your API, if there are any.

pause

bluemix apim api-unshare apimclitest
rem Stops sharing the API.

pause

bluemix apim api-delete apimclitest
rem Removes the gateway from the API. It is no longer managed. 
rem Important: If you delete a Cloud Foundry API, the base Cloud 
rem Foundry app remains in the Bluemix service, but it is no longer 
rem managed. An OpenWhisk API that is deleted removes all
rem interactions between the individual OpenWhisk actions. After
rem the OpenWhisk API is deleted, it must be recreated if 
rem you want to use it again.
```
{:codeblock}

See [Command-line interface commands](apimgt_cli.html) for the list of available commands.

