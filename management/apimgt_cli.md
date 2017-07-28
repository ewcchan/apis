---



copyright:

  years: 2017
lastupdated: "2017-06-26"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# Bluemix API management commands
{: #apimgt_cli}

Version: 1.0.0

You can install the {{site.data.keyword.Bluemix_notm}} API management command line interface (CLI) plug-in to complete common management actions to your APIs with scripting. The following information lists the commands that are included with the API management CLI plug-in, including their names, options, usage, prerequisites, descriptions, and examples.
{:shortdesc}

**Note:** **Prerequisites** list which actions are required before using the command. Commands that have no prerequisite actions list **None**. Otherwise, prerequisites might include one or more of the following actions:

**Note:** You can use the short format of bluemix commands; for example, `bx apim` is short for `bluemix apim`.

Use the indexes in the following table to refer to the frequently used API management commands.

<table summary="API management commands.">
<caption>Table 1. API management commands</caption>
 <thead>
 <th colspan="5">API management commands</th>
 </thead>
 <tbody>
 <tr>
 <td>[bluemix apim help](apimgt_cli.html#apim_help)</td>
 <td>[bluemix apim api](apimgt_cli.html#apim_api)</td>
 <td>[bluemix apim apis](apimgt_cli.html#apim_apis)</td>
 <td>[bluemix apim api-create](apimgt_cli.html#apim_api-create)</td>
 <td>[bluemix apim api-delete](apimgt_cli.html#apim_api-delete)</td>
 <td>[bluemix apim api-expose](apimgt_cli.html#apim_api-expose)</td>
 <td>[bluemix apim api-share](apimgt_cli.html#apim_api-share)</td>
 <td>[bluemix apim api-unexpose](apimgt_cli.html#apim_api-unexpose)</td>
 <td>[bluemix apim api-unshare](apimgt_cli.html#apim_api-unshare)</td>
 <td>[bluemix apim api-update](apimgt_cli.html#apim_api-update)</td>
 <td>[bluemix apim keys](apimgt_cli.html#apim_keys)</td>
 </tr>
 </tbody>
 </table>
 
  
## API management help
{: #apim_help}
Display the general help for first-level built-in commands and supported namespaces of API management CLI, or the help for a specific built-in command or namespace.

### Syntax

```
bluemix apim help <object-action>
```
{: codeblock}

### Command options

   <dl>
   <dt>object-action (optional)</dt>
   <dd>The command for which the help is displayed. If not specified, the general help for the API management CLI is shown.</dd>
   </dl>

### Examples

Display general help for API management CLI:

```
bluemix apim help
```

Display help for the `api-create` command:

```
bluemix apim help api-create
```



## bluemix apim api
{: #apim_api}
Display the properties of a managed API.

### Syntax
```
bluemix apim api --name <API_NAME> [--swagger]
```
{: codeblock}

### Required flag
   <dl>
   <dt>--name</dt>
   <dd>Specifies the name of the managed API</dd>
   </dl>


### Command options
   <dl>
   <dt>--swagger</dt>
   <dd>Displays the information from the Open API definition document in the output</dd>
   </dl>

### Output

The command outputs a table that lists the following information about the specified API:

   <dl>
     <dt>Name</dt>
	 <dd>The name of the API.</dd>
	 <dt>Type</dt>
	 <dd>The type of API. Valid entries are <em>whisk</em>, <em>cf-apps</em>, or <em>user-defined</em></dd>
	 <dt>Managed</dt>
	 <dd>If the value is true, indicates that the endpoint is discovered but not exposed on the gateway.</dd>
	 <dt>Exposed</dt>
	 <dd>Indicates whether the API is live on the gateway (<em>true</em>), or not (<em>false</em>).
	 <dt>Shared</dt>
	 <dd>Indicates whether the API is shared outside of your Bluemix organization (<em>true</em>) or not (<em>true</em>).</dd>
	 <dt>Managed URL</dt>
	 <dd>Specifies the location of the shared version of the API.</dd>
   </dl>

   
### Examples

Display the properties of the API named cloudfound1:

```
bluemix apim api cloudfound1
```

Display the properties and definition file contents for the API named api2:

```
bluemix apim api api2 --swagger
```


## bluemix apim apis
{: #apim_apis}


List the APIs that are available and identified on the identified endpoint server.

### Syntax
```
bluemix apim apis [--api-provider <API_PROVIDER>][--exposed][--shared]
```
{: codeblock}

### Command options

Note: If no options are specified, the information for all APIs is returned.
   <dl>
   <dt>--api-provider </dt>
   <dd>Only returns the types of APIs that you specify here. Valid options are <em>whisk</em> for Openwhisk APIs, <em>cf-apps</em> for Cloud Foundry App APIs, and <em>user-defined</em> for APIs that are not associated with Openwhisk or Cloud Foundry.</dd>
   <dt>--exposed</dt>
   <dd>Only returns APIs that are exposed.</dd>
   <dt>--shared</dt>
   <dd>Only returns APIs that are shared outside of your {{site.data.keyword.Bluemix_notm}} organization.</dd>
   </dl>

### Output

The command outputs a table that lists the following information about the specified APIs:

   <dl>
     <dt>Name</dt>
	 <dd>The name of the API.</dd>
	 <dt>Type</dt>
	 <dd>The type of API. Valid entries are <em>whisk</em>, <em>cf-apps</em>, or <em>user-defined</em></dd>
	 <dt>Managed</dt>
	 <dd>If the value is true, indicates that the endpoint is discovered but not exposed on the gateway.</dd>
	 <dt>Exposed</dt>
	 <dd>Indicates whether the API is live on the gateway (<em>true</em>), or not (<em>false</em>).
	 <dt>Shared</dt>
	 <dd>Indicates whether the API is shared outside of your Bluemix organization (<em>true</em>) or not (<em>false</em>).</dd>
	 <dt>Managed URL</dt>
	 <dd>Specifies the location of the shared version of the API if the API is exposed. Value is <em>undefined</em> when the API is not exposed. </dd>
   </dl>


### Examples

Return all of the APIs that are available on the endpoint manager:

```
bluemix apim apis 
```

Return all of the OpenWhisk APIs that are available:

```
bluemix apim apis --api-provider whisk
```

## bluemix apim api-create
{: #apim_api-create}


Makes an existing unmanaged API into a managed API by importing its Swagger file.

### Syntax

```
bluemix apim api-create --name <API_NAME> --file <PATH_TO_OPEN_API_DEFINITION_FILE> --provider cf-apps [--expose]
```
{: codeblock}

### Required flags

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifies the name of the API that you want to manage.</dd>
   <dt>--file</dt>
   <dd>Provides the path to the Open API definition file, which is in YAML or JSON format.</dd>
   <dt>--provider</dt>
   <dd>Specifies the type of API that you are creating. Note: The only valid entry for this is <em>cf-apps</em>.
   </dl>

### Command option

   <dl>
   <dt>--expose</dt>
   <dd>Expose the endpoint automatically after creating it.</dd>
   </dl>

### Output

The command outputs the following information:
* Created successfully
* Error (with description of the error)

### Examples

Manage an Cloud Foundry API named apinumber1 that has a yaml definition file called reservations1:

```
bluemix apim api-create --name apinumber1 --file ~/dev/apis/reservations1.yaml --provider cf-apps
```

Manage a Cloud Foundry app called cfapi that has a json definition file called definition1:

```
bluemix apim api-create --name cfapi --file ~/dev/apis/definition1.json --provider cf-apps
```

## bluemix apim api-delete
{: #apim_api-delete}

Removes a managed API from the database.

### Syntax

```
bluemix apim api-delete --name <API_NAME> --confirm
```
{: codeblock}

### Required flags

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifies the name of the API that you want to delete. **Important:** Deleting a Cloud Foundry API removes the API from the managed state, but the Cloud Foundry app is not deleted. Deleting an OpenWhisk API deletes the entire API, and must be recreated after it is deleted.</dd>
   <dt>--confirm</dt>
   <dd>Confirms that the command should be completed without providing a confirmation prompt.</dd>
   </dl>


### Output

The command outputs the following information:
* Deleted successfully
* Error (with description of the error)

### Examples

Delete the Cloud Foundry API cloudapi1:

```
bluemix apim api-delete --name cloudapi1 --confirm
```


## bluemix apim api-expose
{: #apim_api-expose}

Makes a managed API visible to others inside my {{site.data.keyword.Bluemix_notm}} organization.

### Syntax
```
bluemix apim api-expose --name <API_NAME>
```
{: codeblock}

### Required flag

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifies the name of the API that you want to expose.</dd>
   </dl>

### Output

The command outputs the following information:
* Exposed successfully
* Error (with description of the error)

### Example

Expose a Cloud Foundry API called cloudfound1 with my {{site.data.keyword.Bluemix_notm}} organization:

```
bluemix apim api-expose --name cloudfound1
```


## bluemix apim api-share
{: #apim_api-share}


Makes a managed API visible to others outside of my {{site.data.keyword.Bluemix_notm}} organization.

### Syntax
```
bluemix apim api-share --name <API_NAME>
```
{: codeblock}

### Required flag

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifies the name of the API that you want to share.</dd>
   </dl>

### Output

The command outputs the following information:
* Shared successfully
* Error (with description of the error)

### Example

Share a Cloud Foundry API called cloudfound1 outside of my {{site.data.keyword.Bluemix_notm}} organization:
```
bluemix apim api-share --name cloudfound1
```


## bluemix apim api-unexpose
{: #apim_api-unexpose}


Makes a managed API that is visible to others inside your {{site.data.keyword.Bluemix_notm}} organization no longer visible to others.

### Syntax
```
bluemix apim api-unexpose --name <API_NAME>
```
{: codeblock}

### Required flag

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifies the name of the API that you want to remove from the visibility of others in your {{site.data.keyword.Bluemix_notm}} organization.</dd>
   </dl>

### Output

The command outputs the following information:
* Unexposed successfully
* Error (with description of the error)

### Example

Remove an OpenWhisk API called openwhisk1 from view to other members of my {{site.data.keyword.Bluemix_notm}} organization:

```
bluemix apim api-unexpose --name openwhisk1
```


## bluemix apim api-unshare
{: #apim_api-unshare}


Removes a managed API that is visible to others outside of my {{site.data.keyword.Bluemix_notm}} organization from visibility.

### Syntax
```
bluemix apim api-unshare --name <API_NAME>
```
{: codeblock}

<strong>Required flag</strong>:

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifies the name of the API that you want to stop sharing.</dd>
   </dl>

### Output

The command outputs the following information:
* Unshared successfully
* Error (with description of the error)

### Example

Stop sharing a Cloud Foundry API called cloudfound1 outside of my {{site.data.keyword.Bluemix_notm}} organization:

```
bluemix apim api-unshare --name cloudfound1
```



## bluemix apim api-update
{: #apim_api-update}


Updates the settings of a managed API by replacing its definition file. Important: This is a complete replacement of the existing definitions in the API with the definitions in the new file. Any empty or missing entries in the new file that exist in the existing file are removed from the definition.

### Syntax
```
bluemix apim api-update --name <API_NAME> --file <NEW_OPEN_API_DEFINITION_FILE>
```
{: codeblock}

### Required flags

   <dl>
   <dt>--name <API_NAME></dt>
   <dd>Specifies the name of the API that you want to update.</dd>
   <dt>--file</dt>
   <dd>Provides the path to the replacement Open API definition file, which is in YAML or JSON format.</dd>
   </dl>

### Output

The command outputs the following information:
* Updated successfully
* Error (with description of the error)


### Example

Update an OpenWhisk API called whiskapi1 with a definition file with the name definition1.json:

```
bluemix apim api-update --name whiskapi1 --filePath ~/path/definitions/definition1.json
```


## bluemix apim keys
{: #apim_api-keys}


Displays the properties of keys that are associated with a managed API.

### Syntax
```
bluemix apim api-keys --name <API_NAME> --bluemix|--external
```
{: codeblock}

### Required flags

   <dl>
   <dt>--name <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to expose.</dd>
   <dt>--bluemix</dt>
   <dd>Lists the {{site.data.keyword.Bluemix_notm}} API keys for the specified API.</dd>
   <dt>--external</dt>
   <dd>Lists the external API keys for the specified API.</dd>
   </dl>

### Output

The command outputs a table that lists the following information about the specified APIs:


   <dl>
     <dt>Key Name</dt>
	 <dd>The name of the API key.</dd>
	 <dt>Key Type</dt>
	 <dd>The type of API key. Valid entries are <em>bluemix</em> and <em>external</em>.</dd>
	 <dt>Client ID</dt>
	 <dd>The name of the client that is identified with the key.</dd>
	 <dt>Secret Provided</dt>
	 <dd>Indicates whether the API secret is provided for the API. The possible values are <em>true</em> if there is a secret, and <em>false</em> if there is no secret.
   </dl>


### Examples

Return all of the external keys that are associated with the API named cloudfound1.

```
bluemix apim --name cloudfound1 --external
```

Return the keys that allow people inside of my {{site.data.keyword.Bluemix_notm}} organization to see my API named myapi1.

```
bluemix apim --name myapi1 --bluemix 
```
 
