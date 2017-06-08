---



copyright:

  years: 2017
lastupdated: "2017-06-08"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}

# {{site.data.keyword.Bluemix_notm}} API management commands
{: #apimgt_cli}

Version: 1.0.0

You can install the {{site.data.keyword.Bluemix_notm}} API management command line interface (CLI) plugin to complete some common management actions to your APIs with scripting. The following information lists the commands that are included with the API management CLI plug-in, and includes their names, options, usage, prerequisites, descriptions, and examples.
{:shortdesc}

**Note:** *Prerequisites* list which actions are required before using the command. Commands that have no prerequisite actions list **None**. Otherwise, prerequisites might include one or more of the following actions:

**Note:** You can use the short format of bluemix commands; for example, `bx api` is short for `bluemix api`.

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
bluemix help apim [COMMAND|NAMESPACE]
```
{: codeblock}
or
```
bluemix apim help object-action
```
{: codeblock}

<strong>Prerequisites</strong>: None

<strong>Command options</strong>:

   <dl>
   <dt>COMMAND|NAMESPACE (optional)</dt>
   <dd>The command or namespace that help is displayed for. If not specified, the general help for the API management CLI is shown.</dd>
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
bluemix apim api [--api-name *API_NAME*] [--api-type *API_TYPE*]
```
{: codeblock}

<strong>Prerequisites</strong>: None

<strong>Command options</strong>:
   <dl>
   <dt>--api-name, -n (optional)</dt>
   <dd>The name of the managed API.</dd>
   <dt>--api-type, -t (optional)</dt>
   <dd>Type of API (whisk, cf-apps, user-defined)</dd>
   </dl>
   
<strong >Examples</strong>:

Display the properties of the following API:

```
bluemix apim api api.chinabluemix.net
```

### bluemix apim apis
{: #apim_apis}


List the APIs that are available and identified on the identified endpoint server.

```
bluemix apim apis [--api-type *API_TYPE*] [--exposed][--unexposed] [--shared] [--unshared]
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
bluemix apim api-create [--api-name *API_NAME*][--api-type *API_TYPE*][--app *CF_APP_NAME*][--definition-file *OPEN_API_DEFINITION_FILE*]
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to manage.</dd>
   <dt>--api-type, -t <i>API_TYPE</i></dt>
   <dd>Specifies the type of the API that you want to create. Valid options are **whisk** for Openwhisk APIs, **cf-apps** for Cloud Foundry App APIs, and **user_defined** for APIs that are not associated with Openwhisk or Cloud Foundry.</dd>
   <dt>--app, -a</dt>
   <dd>Specifies the name of the Cloud Foundry application that is associated with this API. Note: This entry is required when *cf-apps* is specified as the type.</dd>
   <dt>--definition-file, -f</dt>
   <dd>Provides the path to the Open API definition file, which is in YAML or JSON format.</dd>
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

Manage an OpenWhisk API called apinumber1 that has a yaml definition file called reservations1:

```
bluemix apim api-create --api-name apinumber1 --api-type whisk
 --definition-file ~/dev/apis/reservations1.yaml 
```

Manage a Cloud Foundry app called cfapi that has a json definition file called definition1:

```
bluemix apim api-create --api-name cfapi --api-type cf-apps  --app cfapi 
 --definition-file ~/dev/apis/definition1.json
```

### bluemix apim api-delete
{: #apim_api-delete}


Removes a managed API from the database.

```
bluemix apim api-delete [--api-name *API_NAME*][--api-type *API_TYPE*][--confirm]
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to delete. **Important:** Deleting a Cloud Foundry API removes the API from the managed state, but the Cloud Foundry app is not deleted. Deleting an OpenWhisk API deletes the entire API, and must be recreated after it is deleted.</dd>
   <dt>--api-type, -t <i>API_TYPE</i></dt>
   <dd>Specifies the type of the API that you want to create. Valid options are **whisk** for Openwhisk APIs, **cf-apps** for Cloud Foundry App APIs, and **user_defined** for APIs that are not associated with Openwhisk or Cloud Foundry.</dd>
   <dt>--confirm, -c</dt>
   <dd>Confirms that the command should be completed without providing a confirmation prompt.</dd>
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

Delete an OpenWhisk API called whiskapi1, but confirm with me before it is deleted:

```
bluemix apim api-delete --api-name whiskapi1
```

Delete the Cloud Foundry API cloudapi1, and do not request a confirmation before deleting it:

```
bluemix apim api-delete --api-name cloudapi1 --confirm
```


### bluemix apim api-expose
{: #apim_api-expose}


Makes a managed API visible to others inside your Bluemix organization.

```
bluemix apim api-expose [--api-name *API_NAME*]
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to expose.</dd>
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

<strong>Example</strong>

Expose a Cloud Foundry API called cloudfound1 with my Bluemix organization:

```
bluemix apim api-expose --api-name cloudfound1
```



### bluemix apim keys
{: #apim_api-keys}


Displays the properties of keys that are associated with a managed API.

```
bluemix apim api-keys [--api-name *API_NAME*][--api-type *API_TYPE*]
[--key-type *API_KEY_TYPE*]
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to expose.</dd>
   <dt>Type</dt>
   <dd>The type of API. Valid entries are whisk, cf-apps, or user_defined.</dd>
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
bluemix apim api-keys --api-name cloudfound1
```

Return the keys that allow people inside of my Bluemix organization to see my API named myapi1.

```
Bluemix apim api-keys --apiname myapi1 
--key-type inside-bluemix-org
```
 

### bluemix apim api-share
{: #apim_api-share}


Makes a managed API visible to others outside of your Bluemix organization.

```
bluemix apim api-share [--api-name *API_NAME*]
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to share.</dd>
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


<strong>Example</strong>

Share a Cloud Foundry API called cloudfound1 outside of my Bluemix organization:

```
bluemix apim api-share --api-name cloudfound1
```



### bluemix apim api-unexpose
{: #apim_api-unexpose}


Makes a managed API that is visible to others inside your Bluemix organization no longer visible to others.

```
bluemix apim api-unexpose [--api-name *API_NAME*]
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to remove from the visibility of others in your Bluemix organization.</dd>
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


<strong>Example</strong>

Remove an OpenWhisk API called openwhisk1 from view to other members of my Bluemix organization:

```
bluemix apim api-unexpose --api-name openwhisk1
```


### bluemix apim api-unshare
{: #apim_api-unshare}


Removes a managed API that is visible to others outside of your Bluemix organization from visibility.

```
bluemix apim api-unshare [--api-name *API_NAME*]
```
{: codeblock}

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>--api-name, -n <i>API_NAME</i></dt>
   <dd>Specifies the name of the API that you want to stop sharing.</dd>
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


<strong>Example</strong>

Stop sharing a Cloud Foundry API called cloudfound1 outside of my Bluemix organization:

```
bluemix apim api-unshare --api-name cloudfound1
```



### bluemix apim api-update
{: #apim_api-update}


Updates the settings of a managed API by replacing its definition file.

```
bluemix apim api-update [--api-name *API_NAME*]
[--definition-file *OPEN_API_DEFINITION_FILE*]
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


<strong>Example</strong>

Update an OpenWhisk API called whiskapi1 with a definition file with the name definition1.json:

```
bluemix apim api-update --api-name whiskapi1 --definition-file ~/path/definitions/definition1.json
```


### bluemix login
{: #bluemix_login}

Log in user. 

```
bluemix login [OPTIONS...]
```

<strong>Prerequisites</strong>:  None

<!-- staging comment for Atlas 45: might need prereq for federated ID/SSO option unless we expect them to just view the details from the cf login command -->

<strong>Command options</strong>:
<dl>
  <dt>-a <i>API_ENDPOINT</i> (optional)</dt>
  <dd> API endpoint (For example: api.ng.bluemix.net)</dd>
  <dt> --apikey <i>API_KEY or @API_KEY_FILE_PATH</i>
  <dd> API key content or the path of an API key file indicated by @</dd>
  <dt> --sso (optional) </dt>
  <dd> use one time passcode to login </dd>
  <dt> -u <i>USERNAME</i> (optional)</dt>
  <dd> Username</dd>
  <dt> -p <i>PASSWORD</i> (optional)</dt>
  <dd> Password</dd>
  <dt> -c <i>ACCOUNT_ID</i> (optional) </dt>
  <dd> ID of the target account</dd>
  <dt> -o <i>ORG_NAME</i> (optional) </dt>
  <dd> Name of the target organization </dd>
  <dt> -s <i>SPACE_NAME</i> (optional) </dt>
  <dd> Name of the target space</dd>
  <dt> --skip-ssl-validation (optional) </dt>
  <dd> Bypass SSL validation of HTTP requests. This option is not recommended.</dd>
</dl>

<strong>Examples</strong>:

Interactive login:

```
bluemix login
```

Log in with user name and password, and set target account, org and space:

```
bluemix login -u username -p password -c MyAccountID -o MyOrg -s MySpace
```

Log in with one time passcode and set target account, org and space

```
bluemix login --sso -c MyAccountID -o MyOrg -s MySpace
```

Log in with API key and set targets:

* API key has account associated

```
bluemix login --apikey api-key-string -o MyOrg -s MySpace
```

```
bluemix login --apikey @filename -o MyOrg -s MySpace
```

* API key has no account associated

```
bluemix login --apikey api-key-string -c MyAccountID -o MyOrg -s MySpace
```

```
bluemix login --apikey @fileName -c MyAccountID -o MyOrg -s MySpace
```

<strong>Note:</strong> If the API Key has an associated account, switching to another account is not allowed.


### bluemix plugin install
{: #bluemix_plugin_install}

Install the specific version of plugin to {{site.data.keyword.Bluemix_notm}} CLI from the specified path or repository.

```
bluemix plugin install PLUGIN_PATH|PLUGIN_NAME [-r REPO_NAME] [-v VERSION]
```

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>PLUGIN_PATH|PLUGIN_NAME (required)</dt>
   <dd>If -r <i>REPO_NAME</i> is not specified, plugin is installed from the specified local path or remote URL.</dd>
   <dt>-r <i>REPO_NAME</i> (optional)</dt>
   <dd>The name of the repository where the plugin binary is located.</dd>
   <dt>-v <i>VERSION</i> (optional)</dt>
   <dd>The version of the plugin to be installed. If not provided, the latest version of the plugin is installed. This option is valid only when you install the plugin from the repository.</dd>
    </dl>

<strong>Examples</strong>:

Install a plugin from the local file:

```
bluemix plugin install /downloads/new_plugin
```

Install a plugin from the remote URL:

```
bluemix plugin install http://plugins.ng.bluemix.net/downloads/new_plugin
```

Install the `IBM-Containers` plugin of the latest version from the `bluemix-repo` repository:

```
bluemix plugin install IBM-Containers -r bluemix-repo
```
Install the `IBM-Containers` plugin with the  version `0.5.800` from the `bluemix-repo` repository:

```
bluemix plugin install IBM-Containers -r bluemix-repo -v 0.5.800
```

### bluemix plugin update
{: #bluemix_plugin_update}

Upgrade the plug-in from a repository

```
bluemix plugin update -r REPO_NAME [PLUGIN NAME [-v VERSION]]
```

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:
<dl>
 <dt>-r REPO_NAME (required)</dt>
 <dd>The name of the repository where the plugin binary is located.</dd>
 <dt><i>PLUGIN_NAME</i> (optional)</dt>
 <dd>If not specified, all plug-ins available for update in the given repository are listed for selection.</dd>
 <dt>-v <i>VERSION</i> (optional)</dt>
 <dd>The version of the plugin to be updated to. If not provided, update the plugin to the the latest available version.</dd>
</dl>

<strong>Examples</strong>:

check for all available upgrade in plugin repository "My-Repo":

```
bluemix plugin update -r My-Repo
```

Upgrade plugin "plugin-echo" in repository "My-Repo" to the latest:

```
bluemix plugin update -r My-Repo plugin-echo
```

Update plugin "plugin-echo" in repository "My-Repo" to version "1.0.1":

```
bluemix plugin update -r My-Repo plugin-echo -v 1.0.1
```

### bluemix plugin uninstall
{: #bluemix_plugin_uninstall}

Uninstall the specified plugin from {{site.data.keyword.Bluemix_notm}} CLI.

```
bluemix plugin uninstall PLUGIN_NAME
```

<strong>Prerequisites</strong>:  None

<strong>Command options</strong>:

   <dl>
   <dt>PLUGIN_NAME (required)</dt>
   <dd>The name of the plugin to be uninstalled.</dd>
    </dl>

<strong>Examples</strong>:

Uninstall the `IBM-Containers` plugin that was previously installed:

```
bluemix plugin uninstall IBM-Containers
```
