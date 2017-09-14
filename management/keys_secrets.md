---

copyright:
  years: 2017
lastupdated: "2017-08-09"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Manage keys and secrets
{: #keys_secrets}

When your APIs are managed by API management, you can use keys and secrets to control access to the APIs.

## Creating a key and secret
{: #create_key_secret}

To add a key to your API, complete the following steps:

1. Open your Cloud Foundry Application or OpenWhisk API, if it is not already open.

2. Select *API management* in the navigation.

3. Select the Sharing tab to access the keys for that application or API. 

4. Ensure that the **Expose Managed API** slider is set to the *on* position. Your API must be exposed before you can assign keys.

5. Create a key for a customer who has access to your {{site.data.keyword.Bluemix_notm}} organization.
  1. Select **Create API Key +** in the *Sharing within {{site.data.keyword.Bluemix_notm}} Organization* section. A key and secret are automatically created and entered in the correct fields. You cannot update the key or the secret for this type of key. 
  2. Enter a name for your key and secret to help you identify it. For example, the name of the customer who will use it.
  3. Select **Save** to save the new key.
  4. You can repeat steps *a* through *c* for additional keys, if necessary. You can have a maximum of 5 keys in this section per API.

6. Create a key for a customer who is not a member of your {{site.data.keyword.Bluemix_notm}} Organization.
  1. Select **Create API Key +** in the *Sharing Outside of {{site.data.keyword.Bluemix_notm}} Organization* section. A key is automatically created and entered in the correct field. There is no secret that is displayed initially for this type of key. You cannot update the key. 
  2. Enter a name for your key to help you identify it. For example, the name of the customer who will use it.
  3. Optional: If you want to add a secret to the key, select the **API Portal Link** for the key that you want to add the secret to and select **Set API Secret**.
  4. Select **Save** to save the new key.
  5. You can repeat steps *a* through *d* for additional keys, if necessary. You can have a maximum of 5 keys in this section per API.
Your keys are listed for the API when the *Sharing* tab is selected.

## Specifying a key and secret in an API call
{: #spec_key_secret}

Your customers can only call your API if they include the correct key, secret, or both in the header of the call. To call the API, they must include the key and secret in the API call as shown in the following example:
```
curl --request PUT \
  --url https://appidtest.mybluemix.net/ \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --header 'x-ibm-client-secret: add_secret_here' \
  --data '{"id":999999999999999}'
```
{: codeblock}
Where *add_secret_here* is replaced with the secret for the correct key. 

## Deleting an API key
{: #delete_key}

At some point, you will want to remove a key. Maybe a customer that used your API creates its own API and no longer needs yours. To ensure that none of their customers are still using your API, you can delete the key. To delete a key from service, complete the following steps:

1. Open your Cloud Foundry Application or OpenWhisk API, if it is not already open.

2. Select *API management* in the navigation.

3. Select the *Sharing* tab.

4. Find the key that you want to delete. Tip: This is when it is helpful to name the keys so they are easily identified.

5. Select the options icon, which is three vertical dots, beside the key that you want to delete. 

6. Select **Delete key**.

7. Confirm the deletion to remove the key.
