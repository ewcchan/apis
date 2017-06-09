---



copyright:

  years: 2017
lastupdated: "2017-06-09"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# {{site.data.keyword.Bluemix_notm}} API management commands
{: #apimgt_cli}

Version: 1.0.0

You can install the {{site.data.keyword.Bluemix_notm}} API management command line interface (CLI) plug-in to complete common management actions to your APIs with scripting. The following information lists the commands that are included with the API management CLI plug-in, including their names, options, usage, prerequisites, descriptions, and examples.
{:shortdesc}

**Note:** **Prerequisites** list which actions are required before using the command. Commands that have no prerequisite actions list **None**. Otherwise, prerequisites might include one or more of the following actions:

**Note:** You can use the short format of bluemix commands; for example, `bx apim` is short for `bluemix apim`.

Use the indexes in the following tables to refer to the frequently used API management commands.

## Commands for API providers
{: #apim_commands_prov}

<table summary="API management provider commands.">
<caption>Table 1. API management provider commands</caption>
 <thead>
 <th colspan="5">API management provider commands</th>
 </thead>
 <tbody>
 <tr>
 <td>[bluemix apim help](apimgt_cli.html#apim_help)</td>
 <td>[bluemix apim api](apimgt_cli.html#apim_api)</td>
 <td>[bluemix apim api-analytics](apimgt_cli.html#apim_api-analytics)</td>
 <td>[bluemix apim api-create](apimgt_cli.html#apim_api-create)</td>
 <td>[bluemix apim api-definition](apimgt_cli.html#apim_api-definition)</td>
 <td>[bluemix apim api-delete](apimgt_cli.html#apim_api-delete)</td>
 <td>[bluemix apim api-expose](apimgt_cli.html#apim_api-expose)</td>
 <td>[bluemix apim api-log](apimgt_cli.html#apim_api-log)</td>
 <td>[bluemix apim api-share](apimgt_cli.html#apim_api-share)</td>
 <td>[bluemix apim api-unexpose](apimgt_cli.html#apim_api-unexpose)</td>
 <td>[bluemix apim api-unshare](apimgt_cli.html#apim_api-unshare)</td>
 <td>[bluemix apim api-update](apimgt_cli.html#apim_api-update)</td>
 <td>[bluemix apim apis](apimgt_cli.html#apim_apis)</td>
 <td>[bluemix apim key](apimgt_cli.html#apim_key)</td>
 <td>[bluemix apim key-create](apimgt_cli.html#apim_key-create)</td>
 <td>[bluemix apim key-delete](apimgt_cli.html#apim_key-delete)</td>
 <td>[bluemix apim key-update](apimgt_cli.html#apim_key-update)</td>
 <td>[bluemix apim keys](apimgt_cli.html#apim_keys)</td>
 </tr>
 </tbody>
 </table>
 
 ## Commands for API consumers
 {: #apim_commands_consum}

<table summary="API management commands that you can use when you are consuming an API.">
<caption>Table 2. Commands for API consumers</caption>
 <thead>
 <th colspan="5">Commands for API consumers</th>
 </thead>
 <tbody>
 <tr>
 <td>[bluemix apim shared-api](apimgt_cli.html#apim_shared-api)</td>
 <td>[bluemix apim shared-apis](apimgt_cli.html#apim_shared-apis)</td>
 </tr>
 </tbody>
 </table>
 
### API management help
{: #apim_help}
Display the general help for first-level built-in commands and supported namespaces of API management CLI, or the help for a specific built-in command or namespace.

<strong>Syntax</strong>

```
bluemix apim help object-action
```
{: codeblock}

<strong>Prerequisites</strong>: None

<strong>Command options</strong>:

   <dl>
   <dt>object-action (optional)</dt>
   <dd>The command for which the help is displayed. If not specified, the general help for the API management CLI is shown.</dd>
   </dl>



<strong>Examples</strong>:

Display general help for API management CLI:

```
bluemix apim help
```

Display help for the `api-create` command:

```
bluemix help api-create
```



### bluemix apim api
{: #apim_api}
Display the properties of a managed API.

<strong>Syntax</strong>
```
bluemix apim api *API_NAME* [--swagger]
```
{: codeblock}

<strong>Prerequisites</strong>: None

<strong>Command options</strong>:
   <dl>
   <dt>--api-name, -n</dt>
   <dd>Specifies the name of the managed API</dd>
   <dt>--swagger (optional)</dt>
   <dd>Displays the information from the Open API definition document in the output</dd>
   </dl>

<strong>Output</strong>

The command outputs a table that lists the following information about the specified API:

   <dl>
     <dt>Name</dt>
	 <dd>The name of the API.</dd>
	 <dt>Type</dt>
	 <dd>The type of API. Valid entries are whisk, cf-apps, or user_defined</dd>
	 <dt>Artifact ID</dt>
	 <dd>The ID that is assigned to the API by the endpoint manager</dd>
	 <dt>Exposed</dt>
	 <dd>Indicates whether the API is exposed (*true*) or not (*false*)
	 <dt>Shared</dt>
	 <dd>Indicates whether the API is shared outside of your Bluemix organization (*true*) or not (*false*)</dd>
	 <dt>Base Path</dt>
	 <dd>Provides the path where the base path of the API is, if available</dd>
	 <dt>Managed URL</dt>
	 <dd>Specifies the location of the shared version of the API</dd>
   </dl>

   
<strong >Examples</strong>:

Display the properties of the API named cloudfound1:

```
bluemix apim api cloudfound1
```

Display the properties and definition file contents for the API named api2:

```
bluemix apim api api2 --swagger
```


### bluemix apim apis
{: #apim_apis}


List the APIs that are available and identified on the identified endpoint server.

```
bluemix apim apis [--api-type *API_TYPE*][--exposed][--unexposed] [--shared] [--unshared]
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-type, -t <i>API_TYPE</i></dt>
   <dd>Only returns the types of APIs that you specify here. Valid options are **whisk** for Openwhisk APIs, **cf-apps** for Cloud Foundry App APIs, and **user_defined** for APIs that are not associated with Openwhisk or Cloud Foundry.</dd>
   <dt>--exposed, -e</dt>
   <dd>Only returns APIs that are exposed.</dd>
   <dt>--unexposed, -u</dt>
   <dd>Only returns APIs that are not exposed.</dd>
   <dt>--shared, -s</dt>
   <dd>Only returns APIs that are shared outside of your Bluemix organization.</dd>
   <dt>--unshared, -n</dt>
   <dd>Only returns APIs that are not shared outside of your Bluemix organization.</dd>
   </dl>

Only one of these options can be specified at a time.

<strong>Output</strong>

The command outputs a table that lists the following information about the specified APIs:

   <dl>
     <dt>Name</dt>
	 <dd>The name of the API.</dd>
	 <dt>Type</dt>
	 <dd>The type of API. Valid entries are whisk, cf-apps, or user_defined.</dd>
	 <dt>Artifact ID</dt>
	 <dd>The ID that is assigned to the API by the endpoint manager.</dd>
	 <dt>Exposed</dt>
	 <dd>Indicates whether the API is exposed (*true*) or not (*false*).
	 <dt>Shared</dt>
	 <dd>Indicates whether the API is shared outside of your Bluemix organization (*true*) or not (*false).</dd>
   </dl>


<strong>Examples</strong>

Return all of the APIs that are available on the endpoint manager:

```
bluemix apim apis 
```

Return all of the OpenWhisk APIs that are available:

```
bluemix apim apis --api-type whisk
```

### bluemix apim api-create
{: #apim_api-create}


Makes an existing unmanaged API into a managed API by importing its Swagger file.

```
bluemix apim api-create *API_NAME* *PATH_TO_OPEN_API_DEFINITION_FILE*
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to manage.</dd>
   <dt>--definition-file, -f</dt>
   <dd>Provides the path to the Open API definition file, which is in YAML or JSON format.</dd>
   </dl>

<strong>Output</strong>

The command outputs the following information:
* Created successfully
* Error (with description of the error)

<strong>Examples</strong>

Manage an OpenWhisk API called apinumber1 that has a yaml definition file called reservations1:

```
bluemix apim api-create apinumber1 ~/dev/apis/reservations1.yaml 
```

Manage a Cloud Foundry app called cfapi that has a json definition file called definition1:

```
bluemix apim api-create cfapi ~/dev/apis/definition1.json
```

### bluemix apim api-delete
{: #apim_api-delete}


Removes a managed API from the database.

```
bluemix apim api-delete *API_NAME* [--confirm]
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to delete. **Important:** Deleting a Cloud Foundry API removes the API from the managed state, but the Cloud Foundry app is not deleted. Deleting an OpenWhisk API deletes the entire API, and must be recreated after it is deleted.</dd>
   <dt>--confirm, -c</dt>
   <dd>Confirms that the command should be completed without providing a confirmation prompt.</dd>
   </dl>

<strong>Output</strong>

The command outputs the following information:
* Deleted successfully
* Error (with description of the error)

<strong>Examples</strong>

Delete an OpenWhisk API called whiskapi1, but confirm with me before it is deleted:

```
bluemix apim api-delete whiskapi1
```

Delete the Cloud Foundry API cloudapi1, and do not request a confirmation before deleting it:

```
bluemix apim api-delete cloudapi1 --confirm
```


### bluemix apim api-expose
{: #apim_api-expose}


Makes a managed API visible to others inside your Bluemix organization.

```
bluemix apim api-expose *API_NAME*
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to expose.</dd>
   </dl>

<strong>Output</strong>

The command outputs the following information:
* Exposed successfully
* Error (with description of the error)

<strong>Example</strong>

Expose a Cloud Foundry API called cloudfound1 with my Bluemix organization:

```
bluemix apim api-expose cloudfound1
```


### bluemix apim keys
{: #apim_api-keys}


Displays the properties of keys that are associated with a managed API.

```
bluemix apim api-keys *API_NAME*
[--key-type *API_KEY_TYPE*]
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to expose.</dd>
   <dt>key_type</dt>
   <dd>The types of API keys that you want to display. Valid entries are <em>inside-bluemix-org</em> and <em>outside-bluemix-org</em>. If this option is not included, all keys for the specified API are displayed.</dd>
   </dl>

Only one of these options can be specified at a time.

<strong>Output</strong>

The command outputs a table that lists the following information about the specified APIs:


   <dl>
     <dt>Key Name</dt>
	 <dd>The name of the API key.</dd>
	 <dt>Key Type</dt>
	 <dd>The type of API key. Valid entries are inside-bluemix-org and outside-bluemix-org.</dd>
	 <dt>Client ID</dt>
	 <dd>The name of the client that is identified with the key.</dd>
	 <dt>Secret Provded</dt>
	 <dd>Indicates whether the API secret is provided for the API. The possible values are true if there is a secret, and false if there is no secret.
   </dl>


<strong>Examples</strong>

Return all of the keys that are associated with the Cloud Foundry API called cloudfound1.

```
bluemix apim api-keys cloudfound1
```

Return the keys that allow people inside of my Bluemix organization to see my API named myapi1.

```
Bluemix apim api-keys myapi1 
--key-type inside-bluemix-org
```
 

### bluemix apim api-share
{: #apim_api-share}


Makes a managed API visible to others outside of your Bluemix organization.

```
bluemix apim api-share *API_NAME*
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to share.</dd>
   </dl>

<strong>Output</strong>

The command outputs the following information:
* Shared successfully
* Error (with description of the error)

<strong>Example</strong>

Share a Cloud Foundry API called cloudfound1 outside of my Bluemix organization:

```
bluemix apim api-share cloudfound1
```



### bluemix apim api-unexpose
{: #apim_api-unexpose}


Makes a managed API that is visible to others inside your Bluemix organization no longer visible to others.

```
bluemix apim api-unexpose *API_NAME*
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to remove from the visibility of others in your Bluemix organization.</dd>
   </dl>

<strong>Output</strong>

The command outputs the following information:
* Unexposed successfully
* Error (with description of the error)

<strong>Example</strong>

Remove an OpenWhisk API called openwhisk1 from view to other members of my Bluemix organization:

```
bluemix apim api-unexpose openwhisk1
```


### bluemix apim api-unshare
{: #apim_api-unshare}


Removes a managed API that is visible to others outside of your Bluemix organization from visibility.

```
bluemix apim api-unshare *API_NAME*
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to stop sharing.</dd>
   </dl>

<strong>Output</strong>

The command outputs the following information:
* Unshared successfully
* Error (with description of the error)

<strong>Example</strong>

Stop sharing a Cloud Foundry API called cloudfound1 outside of my Bluemix organization:

```
bluemix apim api-unshare cloudfound1
```



### bluemix apim api-update
{: #apim_api-update}


Updates the settings of a managed API by replacing its definition file.

```
bluemix apim api-update *API_NAME* *NEW_OPEN_API_DEFINITION_FILE*
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to update.</dd>
   <dt>--definition-file, -f</dt>
   <dd>Provides the path to the replacement Open API definition file, which is in YAML or JSON format.</dd>
   </dl>

<strong>Output</strong>

The command outputs the following information:
* Updated successfully
* Error (with description of the error)


<strong>Example</strong>

Update an OpenWhisk API called whiskapi1 with a definition file with the name definition1.json:

```
bluemix apim api-update --api-name whiskapi1 --definition-file ~/path/definitions/definition1.json
```
