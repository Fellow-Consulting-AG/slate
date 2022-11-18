---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell


toc_footers:
  - <a href='https://app.polydocs.io'>Sign Up for a Developer Key</a>
 

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Polydocs API
---

# **INTRODUCTION**

Welcome to the Polydocs API! You can use our API to access Polydocs API endpoints, which can get information on various cats, kittens, and breeds in our database.



# **AUTHENTIFICATION**

> To authorize, use this code:



```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "X-API-KEY: meowmeowmeow"
```



> Make sure to replace `meowmeowmeow` with your API key.

Polydocs uses API keys to allow access to the API. You find your  Polydocs API key in our [Seeting Integration](https://app.polydocs.io).

Polydocs expects for the API key to be included in all API requests to the server in a header that looks like the following:

`X-API-KEY: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>


# **MASTER DATA**

## Insert New Master Data 

/master_data_lookup/xml/import_xml_file


```json
{
  "id": "//DataArea/ShippingAddress/ShippingAddressHeader/GeneralInfo/BusinessPartner",
  "Kundennummer": "//DataArea/ShippingAddress/ShippingAddressHeader/GeneralInfo/BusinessPartner",
  "Versandanschrift": "//DataArea/ShippingAddress/ShippingAddressHeader/GeneralInfo/ShippingAddressNumber",
  "Kundenname": "//DataArea/ShippingAddress/ShippingAddressHeader/Address/Name1",
  "Straße": "//DataArea/ShippingAddress/ShippingAddressHeader/Address/Street",
  "ORT": "//DataArea/ShippingAddress/ShippingAddressHeader/Address/CityName",
  "PLZ": "//DataArea/ShippingAddress/ShippingAddressHeader/Address/ZipCode"
}
```

with the Name customer_address

```shell
curl "https://api.polydocs.io/master_data_lookup/xml/import_xml_file" \
  -X POST \
  -H "X-API-KEY:: meowmeowmeow"
  -H 'accept: application/json' \
  -H 'Content-Type: multipart/form-data' \
  -F 'data_type=customer_address' \
  -F 'field_mappings={   "id": "//DataArea/ShippingAddress/ShippingAddressHeader/GeneralInfo/BusinessPartner",   "Kundennummer": "//DataArea/ShippingAddress/ShippingAddressHeader/GeneralInfo/BusinessPartner",   "Versandanschrift": "//DataArea/ShippingAddress/ShippingAddressHeader/GeneralInfo/ShippingAddressNumber",   "Kundenname": "//DataArea/ShippingAddress/ShippingAddressHeader/Address/Name1",   "Straße": "//DataArea/ShippingAddress/ShippingAddressHeader/Address/Street",   "ORT": "//DataArea/ShippingAddress/ShippingAddressHeader/Address/CityName",   "PLZ": "//DataArea/ShippingAddress/ShippingAddressHeader/Address/ZipCode" }' \
  -F 'file=@address_xml_bod.xml;type=text/xml'
```

## Lookup Customer Data

To check the data in the database you can use /master_data_lookup/get_data

```shell
curl -X 'GET' \
  'https://dev.api.polydocs.io/master_data_lookup/get_data?data_type=customer_address' \
  -H 'accept: application/json' \
  -H 'X-API-KEY: meowmeowmeow'
```

# **TEST CLASSIFY**

## Classifier v2

Upload and test direct the classification of a document


```json
{
  "model_name": "visual_classifier",
  "model_version": "1",
  "classification_label": "custom_label",
  "doc_type": null,
  "pages": [
    {
      "page": 1,
      "classification": "email",
      "prob": 0.9810521602630615,
      "model_name": "visual_classifier",
      "model_version": "1",
      "label_doc_type": null,
      "label_priority": 6
    },
    {
      "page": 2,
      "classification": "custom label",
      "prob": 0.9877511262893677,
      "model_name": "visual_classifier",
      "model_version": "1",
      "label_doc_type": null,
      "label_priority": 1
    }
  ],
  "classification_score": 0.9877511262893677

```


```shell
curl -X 'POST' \
  'https://dev.api.polydocs.io/classifier_v2/classify_document' \
  -H 'accept: application/json' \
  -H 'X-API-KEY: meowmeowmeow' \
  -H 'Content-Type: multipart/form-data' \
  -F 'file=@B_47444625_PDF_D52FGM54.PDF;type=application/pdf'
```


test

# **HEALTHZ**
## **HTTP Request: /HEALTHZ** 

**Summary:** This API checks to see if the system is online.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

title: DOC2 - API 

language_tabs: 
   - shell 

toc_footers: 
   - <a href='#'>Sign Up for a Developer Key</a> 
   - <a href='https://github.com/lavkumarv'>Documentation Powered by lav</a> 

includes: 
   - errors 

search: true 

--- 

# **INTRODUCTION** 

DOC2 - API 

**Version:** 2.2.10 

# 
## ***GET*** 

**Summary:** Root

### HTTP Request 
`***GET*** /` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# **LOGTAIL**
## Logtail
### **HTTP Request: /logtail**

**Summary:** This API retrieves logs from the system  

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |


## Logtail Next
### **HTTP Request: /logtail/next**

**Summary:** Get Next Logs 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **USERS**

## Retrieve user
### **HTTP Request: /users/get_users**

**Summary:** This API allows you to retrieve specific users from the system.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Create new user
### **HTTP Request: /users/create**

**Summary:** This API allows you create a new user in the system.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete user
### **HTTP Request: /users/delete/{user_id}**

**Summary:** This API allows you to delete a user from the system.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| user_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update user information
### **HTTP Request: /users/update/{user_id}**

**Summary:** This API allows you to update or change any specific users information.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| user_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve users who can approve
### **HTTP Request: /users/get_users_who_can_approve**

**Summary:** This API retrieves all the users that have the ability to approve changes in the system.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |
| first_approval | query |  | No |  |
| second_approval | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **GROUPS**

## Retrieve groups 
### **HTTP Request: /groups/get_groups**

**Summary:** This API can retrieve a specific group or groups from the system. 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Create new group
### **HTTP Request: /groups/create**

**Summary:** This API allows you to create a new group in the system.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete group
### **HTTP Request: /groups/delete/{group_id}**

**Summary:** This API allows you to delete a group from the system.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| group_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update group information
### **HTTP Request: /groups/update/{group_id}**

**Summary:** This API allows you to update or change any specific groups information.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| group_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Add user to a group
### **HTTP Request: /groups/add_user_to_group**

**Summary:** This API allows you to add a new user to a specific group.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **GROUPS AND USERS**
## Add user to a group
### **HTTP Request: /groups_and_users/add_user_to_group**

**Summary:** This API allows you to add a specific user to a group.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Add multiple users to a group
### **HTTP Request: /groups_and_users/add_users_to_group** 

**Summary:** This API allows you to add multiple users to a group.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Remove user from a group
### **HTTP Request: /groups_and_users/remove_user_from_group** 

**Summary:** This API allows you to remove a specific user from a group.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve users from a group 
### **HTTP Request: /groups_and_users/get_group_users** 

**Summary:** This API allows you to retrieve the users from a specific group.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| group_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **GROUP PERMISSIONS**
## Set group permissions
### **HTTP Request: /group_permission/set_group_permissions**

**Summary:** This API allows you to set what permissions a specific group has enabled.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Set permissions for all groups 
### **HTTP Request: /group_permission/set_all_group_permissions**

**Summary:** This API allows you to set what permissions all groups have enabled.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve permissions of a group 
### **HTTP Request: /group_permission/get_group_permissions** 

**Summary:** This API retrieves the permissions a group has enabled.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Get permissions of all groups
### **HTTP Request: /group_permission/get_all_group_permissions**

**Summary:** This API retireves all the permissions each group has enabled.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrieve user groups and permissions
### **HTTP Request: /group_permission/get_user_groups_and_permissions** 

**Summary:** This API retrieves the groups a specific user belongs too and the permissions that are neabled for these groups.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# **SUB ORGANISATIONS**
## Retrieve sub organisations 
### **HTTP Request: /sub_organisations/get_sub_organisations**

**Summary:** This API retrieves a list of all the sub organizations on the system.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Create new sub organisation
### **HTTP Request: /sub_organisations/create** 

**Summary:** This API allows you to create a new sub organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete sub organisation
### **HTTP Request: /sub_organisations/delete/{sub_org_id}** 

**Summary:** This API allows you to delete a sub organisation.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| sub_org_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update sub organisation
### **HTTP Request: /sub_organisations/update/{sub_org_id}** 

**Summary:** This API allows you to update or change the information of a sub organisation.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| sub_org_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Add new user
### **HTTP Request: /sub_organisation_user/add_user_to_sub_organisation** 

**Summary:** This API allows you to add a new user to a sub organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Remove user
### **HTTP Request: /sub_organisation_user/remove_user_from_sub_organisation**

**Summary:** This API allows you to delete a user from a sub organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve users sub organisations 
### **HTTP Request: /sub_organisation_user/get_user_sub_organisations** 

**Summary:** This API retrieves all the sub organisations where a specific user is added.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| user_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve users organisation and sub organisation
### **HTTP Request: /sub_organisation_user/get_user_organisation_and_sub_organisation** 

**Summary:** This API retrieves the organisation(s) and sub organisation(s) where a specific user is added.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrieve sub organisations with specific users 
### **HTTP Request: /sub_organisation_user/get_sub_organisations_with_users** 

**Summary:** This API retrieves sub organisations that have certain users added to them.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrieve users of a sub organisation 
### **HTTP Request: /sub_organisation_user/get_sub_organisation_users** 

**Summary:** This API retrieves a list of all the users added to a specific sub organisation.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| sub_org_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **CONFIGURATIONS**
## Webhook Export
### **HTTP Request: /CONFIGURE_WEBHOOK_EXPORT**

**Summary:** Allows you to configure a URL where a document will be exported too.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Flow² Export
### **HTTP Request: /CONFIGURATIONS/CONFIGURE_FLOW2_EXPORT**

**Summary:** Configure export for Flow².

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Zugferd Export
### **HTTP Request: /CONFIGURATIONS/CONFIGURE_ZUGFERD_EXPORT** 

**Summary:** Configure export for Zugferd.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Peppol Export 
### **HTTP Request: /CONFIGURATIONS/CONFIGURE_PEPPOL_EXPORT** 

**Summary:** Configure export for Peppol.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## IDM Export
### **HTTP Request: /CONFIGURATIONS/CONFIGURE_IDM_EXPORT** 

**Summary:** Configure export for IDM.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## BOD Export 
### **HTTP Request: /CONFIGURATIONS/CONFIGURE_BOD_EXPORT** 

**Summary:** Configure export for BOD.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## ION Export
### **HTTP Request: /CONFIGURATIONS/CONFIGURE_ION_EXPORT** 

**Summary:**  Configure export for ION.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## INFOR Export
### **HTTP Requet: /CONFIGURATIONS/CONFIGURE_INFOR_EXPORT** 

**Summary:** Configure export for INFOR.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Configuration
### **HTTP Request: /CONFIGURATIONS/GET_CONFIGURATION** 

**Summary:** This API retrieves the oldest configuration of an organisation.

###  
`***POST*** /configurations/get_configuration` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrieve Configurations
### **HTTP Request: /CONFIGURATIONS/GET_CONFIGURATIONS** 

**Summary:** This API retrieves all configurations of an organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Remove configuration
### **HTTP Request: /CONFIGURATIONS/REMOVE_CONFIGURATION** 

**Summary:** This API allows you to remove a configuration.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Visibility
### **HTTP Request: /CONFIGURATIONS/UPDATE_CONFIGURATION_VISIBILITY** 

**Summary:** Activate or deactivate a configuration.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Validation
### **HTTP Request: /CONFIGURATIONS/VALIDATE_EXPORT_CONFIGURATION** 

**Summary:** Validate export Ccnfigurations.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Document Types
### **HTTP Request: /CONFIGURATIONS/DOCUMENT_TYPES** 

**Summary:** Retrieves a list of each document type name.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Document types list
### **HTTP Request: /CONFIGURATIONS/DOCUMENT_TYPES_LIST** 

**Summary:** Retrieves a list of all document types and additional information.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Download 
### **HTTP Request: /CONFIGURATIONS/DOWNLOAD/{ID}** 

**Summary:** Allows you to download mapping files for specific configurations.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |
| type | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **IMPORT**
## Supplier BOD
### **HTTP Request: /IMPORT/SUPPLIER_BOD** 

**Summary:** This API imports a supplier BOD.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Supplier BOD XML
### **HTTP Request: /IMPORT/SUPPLIER_BOD_XML** 

**Summary:** This API imports a supplier BOD XML.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Purchase Order BOD 
### **HTTP Request: /IMPORT/PURCHASE_ORDER_BOD** 

**Summary:** This API imports a purchase order BOD.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Purchase Order BOD XML 
### **HTTP Request: /IMPORT/PURCHASE_ORDER_BOD_XML** 

**Summary:** This API imports a purchase order BOD XML.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## ACK Purchase Order BOD
### **HTTP Request: /IMPORT/ACK_PURCHASE_ORDER_BOD** 

**Summary:** This API imports a ACK purchase order BOD.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## ACK Receive Delivery 
### **HTTP Request: BOD/IMPORT/ACK_RECEIVE_DELIVERY_BOD** 

**Summary:** This API imports a ACK receive delivery BOD

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **EMAIL**
## Retrieve Email
### **HTTP Request: /EMAIL/GET_EMAIL** 

**Summary:** This API retrieves a configured email address and all information associated with it. 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Add Email
### **HTTP Request: /EMAIL/ADD_UPDATE_EMAIL** 

**Summary:** This API allows you to configure a new email address to the system.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Email
### **HTTP Request: /EMAIL/DELETE_EMAIL** 

**Summary:** This API allows you to delete an email address from the system.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Deactivate Email
### **HTTP Request: /EMAIL/(DE)-ACTIVATE_EMAIL** 

**Summary:** This API allows you to deactivate a current email address so that it can be replaced by a new one.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve 
### **HTTP Request: /EMAIL/FETCH_EMAILS** 

**Summary:** Imports PDF attachments sent to a specific configured email address.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Import Log
### **HTTP Request: /EMAIL/GET_IMPORT_LOG** 

**Summary:** Retrieves the log of email imported documents.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Check login 
### **HTTP Request: /EMAIL/CHECK_LOGIN** 

**Summary:** This API checks if the email credentials are valid and can be used to log in.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **ORGANISATION DETAILS**
## Set Details 
### **HTTP Request: /ORG_DETAILS/SET_ORG_DETAILS** 

**Summary:** This API allows you to add the details of a specific organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Details
### **HTTP Request: /ORG_DETAILS/GET_ORG_DETAILS** 

**Summary:** This API retrieves the details of an organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Set Profile 
### **HTTP Request: /ORG_DETAILS/SET_ORG_PROFILE** 

**Summary:** This API allows you to set up a profile for an organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Organisation Profile 
### **HTTP Request: /ORG_DETAILS/GET_ORG_PROFILE** 

**Summary:** This API retrieves the profile of a desired organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## OCR Settings
### **HTTP Request: /ORG_DETAILS/SET_OCR_SETTINGS** 

**Summary:** This API allows you to set the specific OCR settings of an organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve OCR Settings
### **HTTP Request: /ORG_DETAILS/GET_OCR_SETTINGS** 

**Summary:** This API retrieves the OCR settings of a specific organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Check OCR
### **HTTP Request: /ORG_DETAILS/CHECK_OCR** 

**Summary:** 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **EXPORT** 
## Zugferd
### **HTTP Request: /EXPORT_ZUGFERD** 

**Summary:** 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |
| config_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Peppol 
### **HTTP Request: /EXPORT/EXPORT_PEPPOL** 

**Summary:** 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |
| config_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Pending Watch Export Documents 
### **HTTP Request: /EXPORT/GET_PENDING_WATCH_EXPORT_DOCUMENTS** 

**Summary:** This API retrieves all pending watch export documents.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Pending Watch Export Status
### **HTTP Request: /EXPORT/UPDATE_PENDING_WATCH_EXPORT_STATUS** 

**Summary:** This API displays the update status of pending watch export documents. 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Test Process Document 
### **HTTP Request: /EXPORT/TEST_PROCESS_DOC** 

**Summary:** Test Process Doc

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Save Extraction Rules
### **HTTP Request: /EXPORT/SAVE_EXTRACTION_RULES** 

**Summary:** This API sends a command to the system to save all extraction rules.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Data V1
### **HTTP Request: /EXPORT/GET_DATA_V1** 

**Summary:** This API retrieves all V1 data. 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **FUZZY**
## Retrieve Vendor List 
### **HTTP Request: /FUZZY/GET_VENDORS_LIST** 

**Summary:** This API retrieves a list of all the vendors of an organisation.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| keyword | query |  | No |  |
| address_type | query |  | No |  |
| skip | query |  | No |  |
| limit | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Import Vendor CSV 
### **HTTP Request: /FUZZY/IMPORT_VENDORS_CSV** 

**Summary:** This API imports the data of a vendor CSV file.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **VENDORS**
## Retrieve Vendors List 
### **HTTP Request: /VENDORS/GET_VENDORS_LIST** 

**Summary:** This API retrieves a list of all an organisations vendors.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| keyword | query |  | No |  |
| address_type | query |  | No |  |
| skip | query |  | No |  |
| limit | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Import Vendor CSV 
### **HTTP Request: /VENDORS/IMPORT_VENDORS_CSV** 

**Summary:** This API imports a CSV file of a specific vendor.
**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **MIGRATION**
## Retrieve Migration Version 
### **HTTP Request: /MIGRATION/GET_MIGRATION_VERSION** 

**Summary:** This API retrieves a migration version.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# **DOCUMENT CLASSIFICATION RULES** 
## Retrieve Document Classification Rules 
### **HTTP Request: /DOC_CLASSIFICATION_RULES/GET_DOC_CLASSIFICATION_RULES** 

**Summary:** This API retrieves the classification rules for a type of document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Create New Classification Rules 
### **HTTP Request: /DOC_CLASSIFICATION_RULES/CREATE** 

**Summary:** This API allows you to create a new classification rule for a specific type of document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Classification Rules 
### **HTTP Request: /DOC_CLASSIFICATION_RULES/DELETE/{ID}** 

**Summary:** This API allows you to delete a classification rule for a specific type of document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Classification Rules 
### **HTTP Request: /DOC_CLASSIFICATION_RULES/UPDATE/{ID}** 

**Summary:** This API allows you to update existing classification rules for a specific document type.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **DOCUMENTS**
## Classify a Document 
### **HTTP Request: /DOCUMENT/CLASSIFY_DOCUMENT** 

**Summary:** This API allows you to classify a document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Process DOC² Landing Document
### **HTTP Request: /DOCUMENT/PROCESS_DOC2LANDING_DOCUMENT** 

**Summary:** This API allows you to process a landing document for DOC². 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Process Documents 
### **HTTP Request: /DOCUMENT/PROCESS_DOCUMENTS** 

**Summary:** This API allows you to process documents.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Process 
### **HTTP Request: /DOCUMENT/PROCESS** 

**Summary:** 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Process Base64 
### **HTTP Request: /DOCUMENT/PROCESS_BASE64** 

**Summary:** 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Document 
### **HTTP Request: /DOCUMENT/UPDATE/{DOC_ID}** 

**Summary:** This API allows you to update an existing document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Validate and Export 
### **HTTP Request: /DOCUMENT/VALIDATE_AND_EXPORT/{DOC_ID}** 

**Summary:** This API allows you to validate and export a document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve List of Documents 
### **HTTP Request: /DOCUMENT/LIST** 

**Summary:** This API retrieves a list of all existing documents in the system. 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| start_date | query |  | No |  |
| filter | query |  | No |  |
| skip | query |  | No |  |
| limit | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Document Status 
### **HTTP Request: /DOCUMENT/STATUS/{DOC_ID}** 

**Summary:** This API shows the status of a specific document.
 
**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Dashboard 
### **HTTP Request: /DOCUMENT/DASHBOARD** 

**Summary:** 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| keyword | query |  | No |  |
| org_id | query |  | No |  |
| sub_org_id | query |  | No |  |
| assigned_to_me_only | query |  | No |  |
| start_date | query |  | No |  |
| filter | query |  | No |  |
| doc_type | query |  | No |  |
| status | query |  | No |  |
| order_by_field | query |  | No |  |
| order_by_direction | query |  | No |  |
| skip | query |  | No |  |
| limit | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Extraction Result 
### **HTTP Request: /DOCUMENT/EXTRACTION_RESULT** 

**Summary:** This API displays the extraction results of a document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Items from Dictionary 
### **HTTP Request: /DOCUMENT/GET_ITEMS_FROM_DICTIONARY/{ITEM}** 

**Summary:** This API retrieves items from dictionary.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| item | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Restart 
### **HTTP Request: /DOCUMENT/RESTART/{DOC_ID}** 

**Summary:** This API allows you to restart the processing of a specific document. 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |
| improve_quality | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Restart Documents 
### **HTTP Request: /DOCUMENT/RESTART_DOCUMENTS** 

**Summary:** This API restarts the processing of all documents in an organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Approve or Reject 
### **HTTP Request: /DOCUMENT/APPROVE_OR_REJECT/{DOC_ID}** 

**Summary:** This API allows you to either accept or reject a specific document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Document Log 
### **HTTP Request: /DOCUMENT/UPDATE_DOCUMENT_LOG/{DOC_ID}** 

**Summary:** This API updates the document log.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Document Log
### **HTTP Request: /DOCUMENT/GET_DOCUMENT_LOG/{DOC_ID}** 

**Summary:** This API retrieves the log of a specific document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Restart with New Classification 
### *HTTP Request: /DOCUMENT/RESTART_WITH_NEW_CLASSIFICATION/{DOC_ID}** 

**Summary:** 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Restart export 
### **HTTP Request: /DOCUMENT/RESTART_EXPORT/{DOC_ID}** 

**Summary:** Restart Export 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Document ID
### **HTTP Request: /DOCUMENT/{DOC_ID}** 

**Summary:** Get Document ID.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete 
### **HTTP Request: /DOCUMENT/DELETE/{DOC_ID}** 

**Summary:** Delete document.

###  
`***DELETE*** /document/delete/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Documents 
### **HTTP Request: /DOCUMENT/DELETE_DOCUMENTS** 

**Summary:** This API allows you to delete documents.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Assign Specific Document 
### **HTTP Request: /DOCUMENT/ASSIGN/{DOC_ID}** 

**Summary:** 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Assign Documents
### **HTTP Request: /DOCUMENT/ASSIGN_DOCUMENTS** 

**Summary:** 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Assign with Email 
### **HTTP Request: /DOCUMENT/ASSIGN_WITH_EMAIL/{DOC_ID}** 

**Summary:** Assign With Email

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Next Document 
### **HTTP Request: /DOCUMENT/GET_NEXT_DOCUMENT/{DOC_ID}** 

**Summary:** Get Next Document

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |
| doc_type | query |  | No |  |
| status | query |  | No |  |
| sort_attr | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve OCR Data 
### **HTTP Request: /DOCUMENT/GET_OCR_DATA/{DOC_ID}** 

**Summary:** This API retrieves the OCR data of a specific document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Documents in Error Status
### **HTTP Request: /DOCUMENT/DELETE_ERROR_DOCS** 

**Summary:** This API allows you to delete documents that are in error status. 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Split Document 
### **HTTP Request: /DOCUMENT/SPLIT_DOCUMENT** 

**Summary:** This API allows you to split a document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Generate Thumbnails 
### **HTTP Request: /DOCUMENT/GENERATE_THUMBNAILS** 

**Summary:** This API generates a preview image of what the document will look like.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Document Status XML 
### **HTTP Request: /DOCUMENT/GET_DOC_STATUS_XML** 

**Summary:** This API retrieves the status of an XML document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **DOCUMENT LAYOUT TEMPLATES**
## Retrieve Layout Templates 
### **HTTP Request: /DOCUMENT_LAYOUT_TEMPLATE/GET_LAYOUT_TEMPLATES** 

**Summary:** This API retrieves layout templates for a document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type_key | query |  | No |  |
| sub_doc_type_key | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Create 
### **HTTP Request: /DOCUMENT_LAYOUT_TEMPLATE/CREATE** 

**Summary:** This API allows you to create a layout emplate for a document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Layout Template 
### **HTTP Request: /DOCUMENT_LAYOUT_TEMPLATE/{ID}** 

**Summary:** This API retrieves a specific layout template using the ID associated with the layout template.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Layout Template
### **HTTP Request: /DOCUMENT_LAYOUT_TEMPLATE/{ID}** 

**Summary:** This API allows you to update a layout template for a document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Layout template 
### **HTTP Request: /DOCUMENT_LAYOUT_TEMPLATE/{ID}** 

**Summary:** This API allows you to delete a specific layout template.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Upload Template Sample 
### **HTTP Request: /DOCUMENT_LAYOUT_TEMPLATE/UPLOAD_TEMPLATE_SAMPLE** 

**Summary:** This API allows you to upload a sample template. 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **DOCUMENT LOCK**
## Acquire Lock 
### **HTTP Request: /DOCUMENT_LOCK/ACQUIRE_LOCK** 

**Summary:** This API 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Release Lock
### **HTTP Request: /DOCUMENT_LOCK/RELEASE_LOCK** 

**Summary:**  

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Renew Lock 
### **HTTP Request: /DOCUMENT_LOCK/RENEW_LOCK** 

**Summary:** This API

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **TABLE EXTRACTION V3**
## Auto Extract Table 
### **HTTP Request: /TABLE_EXTRACTION_V3/AUTO_EXTRACT_TABLE** 

**Summary:** This API allows you to set that a table will be automatically extracted from a document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Table 
### **HTTP Request: /TABLE_EXTRACTION_V3/GET_TABLE** 

**Summary:** This API will retrieve a specific table froma document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Reformat Table 
### **HTTP Request: /TABLE_EXTRACTION_V3/REFORMAT_TABLE** 

**Summary:** This API allows you to reformat an extracted table.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Compact Table 
### **HTTP Request: /TABLE_EXTRACTION_V3/GET_COMPACT_TABLE** 

**Summary:** This API will retrieve a compact table.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Create Table Column 
### **HTTP Request: /TABLE_EXTRACTION_V3/CREATE_DOCUMENT_TABLE_COLUMN** 

**Summary:** This API allows you to create a table column for a document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Table Rules 
### **HTTP Request: /TABLE_EXTRACTION_V3/DELETE_TABLE_RULES** 

**Summary:** This API allows you to delete table rules.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **BLOCK TABLE EXTRACTION** 
## Blocked List
### **HTTP Request: /BLOCK_TABLE_EXTRACTION/BLOCKED_LIST** 

**Summary:** This API 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Blocked List - Add 
### **HTTP Request: /BLOCK_TABLE_EXTRACTION/BLOCKED_LIST/ADD** 

**Summary:** This API

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Blocked List - Delete 
### **HTTP Request: /BLOCK_TABLE_EXTRACTION/BLOCKED_LIST/{ID}** 

**Summary:** This API 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **FIELD**
## Retrieve Document UI LAYOUT 
### **HTTP Request: /FIELD/GET_DOCUMENT_UI_LAYOUT** 

**Summary:** This API retrieves the document UI layout. 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |
| is_sub_doc_type | query |  | No |  |
| profile | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Field Settings 
### **HTTP Request: /FIELD/GET_FIELD_SETTINGS** 

**Summary:** This API retrieves the field settings for a specific field. 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |
| is_sub_doc_type | query |  | No |  |
| profile | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Clone Document Type 
### **HTTP Request: /FIELD/CLONE_DOC_TYPE** 

**Summary:** This API allows you to clone the fields of a document type to create a clone of a document type.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| copy_from_doc_type | query |  | Yes |  |
| copy_to_doc_type | query |  | Yes |  |
| profile | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Copy Settings from Document Type 
### **HTTP Request: /FIELD/COPY_FIELDS_SETTING_FROM_DOC_TYPE** 

**Summary:** This API lets you copy the field settings of a document type.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| copy_from_doc_type | query |  | Yes |  |
| copy_to_doc_type | query |  | Yes |  |
| profile | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Field Settings of all Document Types 
### **HTTP Request: /FIELD/GET_FIELD_SETTINGS_ALL_DOCUMENT_TYPES** 

**Summary:** This API retrieves a list of all the document types of an organisation as well as the field settings contained within those document types.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| profile | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Restore Default Settings 
### **HTTP Request: /FIELD/SETTINGS_RESTORE_DEFAULTS** 

**Summary:** This API allows you to restore field settings back to the default settings. 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |
| is_sub_doc_type | query |  | No |  |
| profile | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Field Settings 
### **HTTP Request: /FIELD/UPDATE_FIELD_SETTINGS** 

**Summary:** This API allows you to update or change existing field settings. 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |
| is_sub_doc_type | query |  | No |  |
| profile | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Document Layout 
### **HTTP Request: /FIELD/GET_DOCUMENT_LAYOUT** 

**Summary:** This API retrieves the layout fo a specific document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |
| is_sub_doc_type | query |  | No |  |
| profile | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Document Table Validation Rules 
### **HTTP Request: /FIELD/GET_DOCUMENT_TABLE_VALIDATION_RULES** 

**Summary:** This API retrieves the validation rules for all documents table extractions.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| table_name | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Document Table Column 
### **HTTP Request: /FIELD/UPDATE_DOCUMENT_TABLE_COLUMN** 

**Summary:** This API allows you to update or change an existing document table column.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Custom Field Labels 
### **HTTP Request: /FIELD/GET_CUSTOM_FIELD_LABELS** 

**Summary:** This API retrieves a list of the custom field labels. 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |
| profile | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **EXTRACT**
## Retrieve Text 
### **HTTP Request: /EXTRACT/GET_TEXT** 

**Summary:** This API retrieves extracted text from a document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Table Text 
### **HTTP Request: /EXTRACT/GET_TABLE_TEXT** 

**Summary:** This API retrieves text from an extracted table. 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Formatted Amount 
### **HTTP Request: /EXTRACT/GET_FORMATTED_AMOUNT** 

**Summary:** This API retrieves a formatted amount.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Column Headers 
### **HTTP Request: /EXTRACT/GET_COLUMN_HEADERS** 

**Summary:** This API retrieves the column headers from an extracted table.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrieve AI Score 
### **HTTP Request: /EXTRACT/GET_AI_SCORE** 

**Summary:** This API retrieves the AI score from a data extraction of a document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |
| filter_values | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **PURCHASE ORDERS**
## Retrieve Purchase Order List 
### **HTTP Request: /PURCHASE_ORDER/GET_PURCHASE_ORDERS_LIST** 

**Summary:** This API retrieves purchase order lists.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| keyword | query |  | Yes |  |
| skip | query |  | No |  |
| limit | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Lines
### **HTTP Request: /PURCHASE_ORDER/GET_PURCHASE_ORDER_LINES** 

**Summary:** This API retrieves purchase order lines.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| purchase_order_number | query |  | Yes |  |
| amounts_format | query |  | No |  |
| skip | query |  | No |  |
| limit | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Display Columns 
### **HTTP Request: /PURCHASE_ORDER/GET_PURCHASE_ORDER_DISPLAY_COLS** 

**Summary:** This API retrieves ourchase order display columns.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Table from PO Numbers
### **HTTP Request: /PURCHASE_ORDER/GET_TABLE_FROM_PO_NUMBERS** 

**Summary:** This API retreves a table 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Auto PO Match 
### **HTTP Request: /PURCHASE_ORDER/AUTO_PO_MATCH** 

**Summary:** This API allows you to automatically match a purchase order to the PO number.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **SPECIAL RULES** 
## Save
### **HTTP Request: /SPECIAL_RULES/SAVE** 

**Summary:** Save

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **PREFERENCES**
## Retrieve Preferences 
### **HTTP Request: /PREFERENCES/GET_PREFERENCES** 

**Summary:** This API retrieves the preferences

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrieve Preference 
### **HTTP Request: /PREFERENCES/GET_PREFERENCE** 

**Summary:** This API retrieves the preference

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| key | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Set Preference 
### **HTTP Request: /PREFERENCES/SET_PREFERENCE** 

**Summary:** This API allows you to set your preference for

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Remove Preference 
### **HTTP Request: /PREFERENCES/REMOVE_PREFERENCE** 

**Summary:** This API allows you to delete a preference.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| key | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Regex from Document Type 
### **HTTP Request: /PREFERENCES/GET_DOCUMENT_TYPE_REGEXES** 

**Summary:** This API retrieves the regular expressions of a document type.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrieve Supported Barcode Types
### **HTTP Request: /PREFERENCES/GET_SUPPORTED_BARCODE_TYPES** 

**Summary:** This API retrieves all supported barcode types.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Update Organisation Preferences 
### **HTTP Request: /PREFERENCES/UPDATE_ORGANISATION_PREFERENCE** 

**Summary:** This API allows you to update or change the preferences of an organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Organisation Preferences 
### **HTTP Request: /PREFERENCES/GET_ORGANISATION_PREFERENCE** 

**Summary:** This API retrieves a list of all the preferences of an organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update OCR Configuration 
### **HTTP Request: /PREFERENCES/UPDATE_OCR_CONFIGURATION** 

**Summary:** This API allows you to update or change the OCR configuration.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve OCR Configuration 
### **HTTP Request: /PREFERENCES/GET_OCR_CONFIGURATION** 

**Summary:** This API retrieves the OCR Configuration of an organisation.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **RESOURCE**
## Document ID - File Name
### **HTTP Request: /RESOURCE/DOCUMENT/{DOC_ID}/{FILENAME}** 

**Summary:** This API

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |
| filename | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Image ID - Page
### **HTTP Request: /RESOURCE/IMAGE/{DOC_ID}/{PAGE}** 

**Summary:** This API

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |
| page | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Type - ID - Image (Page) 
### **HTTP Request: /RESOURCE/{TYPE}/{ID}/IMAGE/{PAGE}** 

**Summary:** This API

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| type | path |  | Yes |  |
| id | path |  | Yes |  |
| page | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Check S3
### **HTTP Request: /RESOURCE/CHECK_S3** 

**Summary:** S3 Check

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |
| filename | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Mass Check S3
### **HTTP Request: /RESOURCE/MASS_CHECK_S3** 

**Summary:** Mass S3 Check 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Errors
### **HTTP Request: /RESOURCE/GET_ERRORS** 

**Summary:** Gets the error message and the exception cause from the db for the specified doc_ids.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **EPHESOFT**
## Extract Table 
### **HTTP Request: /EPHESOFT/EXTRACT_TABLE** 

**Summary:** Extracts table from the document
Args:
    file: Document from which table should be extracted
    force_ocr ([type]): To re-ocr already ocr-ed document
    format_amount_locale ([type]): Output format for the amounts
    format_date_pattern ([type]): Output format for the dates
    remove_empty_columns: To remove empty columns from the output table
    start_page: Start page (In case there are multiple documents in single pdf)
    end_page: End page (In case there are multiple documents in single pdf)
    output_format: It is useless and never should be passed
Returns:
    [type]: Returns extracted table (Compact) 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| force_ocr | query |  | No |  |
| format_amount_locale | query |  | No |  |
| format_date_pattern | query |  | No |  |
| remove_empty_columns | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Table Train URL 
### **HTTP Request: /EPHESOFT/GET_TABLE_TRAIN_URL** 

**Summary:** Saves a table training record with doc_id and ephesoft_doc_id extracted
             from attached xml. OCRs and copies document from fellowkv storage to doc2 storage.
            Note: This endpoint doesn't extract any table yet. This is done by get_table_train_data endpoint.

Args:
ephesoft_doc_id ([type]): Ephesoft doc id, for which table will be 
                              trained/extracted (e.g. DOC1)
    file: Zip or XML document from Ephesoft. ([BatchInstance]_batch.xml)
    force_ocr ([type]): To re-ocr already ocr-ed document
Returns:
    [type]: id of the saved record

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Table Train Data 
### **HTTP Request: /EPHESOFT/GET_TABLE_TRAIN_DATA** 

**Summary:** Extracts table from the document and return in response.
Args:
    id ([type]): Id for the saved record for EphesoftTableExtractionTraining
Returns:
    [type]: id of the saved record

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Save Extraction Rules 
## **HTTP Request: /EPHESOFT/SAVE_EXTRACTION_RULES/{ID}** 

**Summary:** Saves extraction results, which can be loaded in Ephesoft with 'Reload Data' button
             using get_updated_ephesoft_doc endpoint. Saves table extraction rules for future documents of same supplier.
Args:
    id ([type]): Id for the saved record for EphesoftTableExtractionTraining
Returns:
    [type]: id of the saved record

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve PO Match URL 
### **HTTP Request: /EPHESOFT/GET_PO_MATCH_URL** 

**Summary:** Saves a EphesoftPOMatching record with doc_id and ephesoft_doc_id extracted from attached xml. 
Args:
    ephesoft_doc_id ([type]): Ephesoft doc id, for which table will be 
                              trained/extracted (e.g. DOC1)
    file: Zip or XML document from Ephesoft. ([BatchInstance]_batch.xml)
Returns:
    [type]: id of the saved record

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve PO Match Data 
### **HTTP Request: /EPHESOFT/GET_PO_MATCH_DATA/{ID}** 

**Summary:** Return extracted_data from EphesoftPOMatching. This has same structure as we have for documents extracted_data.

Args:
    id ([type]): EphesoftPOMatching record id
Returns:
    [type]: extracted_data from EphesoftPOMatching

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Save PO Match Data 
### **HTTP Request: /EPHESOFT/SAVE_PO_MATCH_DATA/{ID}** 

**Summary:** Saves updated EphesoftPOMatching record from extracted_data sent in request.

Args:
    id ([type]): EphesoftPOMatching record id
    extracted_data ([type]): extracted_data in the same format we have for documents
Returns:
    [type]: success result 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Updated Ephesoft Document 
### **HTTP Request: /EPHESOFT/GET_UPDATED_EPHESOFT_DOC** 

**Summary:** Return updated ephesoft xml document populated either from extracted table or from PO matching.

Args:
    source ([type]): TableTraining or PO
                     - TableTraining: Result xml should be populated from 
                       table training record
                     - PO Result xml should be populated from po matching
    remove_empty_columns: To remove empty columns from the output table
    ephesoft_doc_id ([type]): Ephesoft doc id, for which table will be updated
    file: Zip or XML document in which table will be updated
Returns:
    [type]: Zip file with updated table

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| source | query |  | No |  |
| remove_empty_columns | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **DOCUMENT TYPE**
## Retrieve Document Type
### **HTTP Request: /DOCUMENT_TYPE/GET_DOCUMENT_TYPES** 

**Summary:** This API retrieves specific document types.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrieve Document Types and Sub Types 
### **HTTP Request: /DOCUMENT_TYPE/GET_DOCUMENT_TYPES_AND_SUB_TYPES** 

**Summary:** This API retrieves specific document types and sub types.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Create Document Type
### **HTTP Request: /DOCUMENT_TYPE/CREATE_DOCUMENT_TYPE** 

**Summary:** This API allows you to create a document type.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Document Type
### **HTTP Request: /DOCUMENT_TYPE/DELETE_DOCUMENT_TYPE/{ID}** 

**Summary:** This API allows you to dlete a document type.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Sub Document Type 
### **HTTP Request: /DOCUMENT_TYPE/GET_SUB_DOCUMENT_TYPES** 

**Summary:** This API retrieves a specific sub document type.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type_key | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Create Sub Document Type 
### **HTTP Request: /DOCUMENT_TYPE/CREATE_SUB_DOCUMENT_TYPE** 

**Summary:** This API allows you to create a sub document type.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Sub Document Type 
### **HTTP Request: /DOCUMENT_TYPE/DELETE_SUB_DOCUMENT_TYPE/{ID}** 

**Summary:** This API allows you to delete a sub document type.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Activate/Deactivate Document Type 
### **HTTP Request: /DOCUMENT_TYPE/ACTIVATE_DEACTIVATE_DOCUMENT_TYPE** 

**Summary:** This API allows you to activate or deactivate a specific document type.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Document Field Groups 
### **HTTP Request: /DOCUMENT_TYPE/GET_DOCUMENT_FIELD_GROUPS** 

**Summary:** This API retrieves document field groups.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type_name | query |  | Yes |  |
| is_sub_doc_type | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Create Document Field Group 
### **HTTP Request: /DOCUMENT_TYPE/CREATE_DOCUMENT_FIELD_GROUP** 

**Summary:** This API allows you to create a document field group.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Document Field Group 
### **HTTP Request: /DOCUMENT_TYPE/DELETE_DOCUMENT_FIELD_GROUP/{ID}** 

**Summary:** This API allows you to delete a document field group.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Create Document Field 
### **HTTP Request: /DOCUMENT_TYPE/CREATE_DOCUMENT_FIELD** 

**Summary:** This API allows you to create a document field.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Document Field 
### **HTTP Request: /DOCUMENT_TYPE/DELETE_DOCUMENT_FIELD/{ID}** 

**Summary:** This API lets you delete a document field.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **DOCUMENT TABLE**
## Retrieve All Document Tables 
### **HTTP Request: /DOCUMENT_TABLE/GET_ALL_DOCUMENT_TABLES** 

**Summary:** This API retrieves all tables that appear in an organisations documents.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrieve Document Tables 
### **HTTP Request: /DOCUMENT_TABLE/GET_DOCUMENT_TABLES** 

**Summary:** This API retrieves document tables.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Document Tables with Columns
### **HTTP Request: /DOCUMENT_TABLE/GET_DOCUMENT_TABLES_WITH_COLUMNS** 

**Summary:** This API retrieves document tables with columns included.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Create Document Table 
### **HTTP Request: /DOCUMENT_TABLE/CREATE_DOCUMENT_TABLE** 

**Summary:** This API allows you to create a document table.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Document Table 
### **HTTP Request: /DOCUMENT_TABLE/DELETE_DOCUMENT_TABLE/{ID}** 

**Summary:** This API allows you to delete a document table.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Document Table Columns 
### **HTTP Request: /DOCUMENT_TABLE/GET_DOCUMENT_TABLE_COLUMNS** 

**Summary:** This API retrieves the columns from a table within a document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| table_name | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Create Document Table Column 
### **HTTP Request: /DOCUMENT_TABLE/CREATE_DOCUMENT_TABLE_COLUMN** 

**Summary:** This API allows you to crteate a document table column.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Document Table Column
### **HTTP Request: /DOCUMENT_TABLE/DELETE_DOCUMENT_TABLE_COLUMN/{ID}** 

**Summary:** This API allows you to dlete a document table column.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Document Table Column 
### **HTTP Request: /DOCUMENT_TABLE/UPDATE_DOCUMENT_TABLE_COLUMN** 

**Summary:** This API allows you to update or change an existing document table column.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **DATA VAULT**
## Create a Record 
### **HTTP Request: /DATA_VAULT/CREATE_RECORD** 

**Summary:** 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **AUTO TEST**
## Add Update Document 
### **HTTP Request: /AUTO_TEST/ADD_UPDATE_DOCUMENT** 

**Summary:** This API duplicates the document into an auto test version of the document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Remove Document 
### **HTTP Request: /AUTO_TEST/REMOVE_DOCUMENT** 

**Summary:** This API deletes an auto test document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Document Data 
### **HTTP Request: /AUTO_TEST/GET_DOCUMENT_DATA** 

**Summary:** This API retrieves data from an auto test document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **REGEX AND PATTERNS**
##  RE Validation 
### **HTTP Request: /REGEX_AND_PATTERNS/RE/IS_VALID** 

**Summary:** Is Re Valid

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Regex Validation 
### **HTTP Request: /REGEX_AND_PATTERNS/REGEX/IS_VALID** 

**Summary:** Is Regex Valid

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## RE Validate Patterns 
### **HTTP Request: /REGEX_AND_PATTERNS/RE/VALIDATE_PATTERNS** 

**Summary:** This API validates Re patterns.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Regex Validate Patterns 
### **HTTP Request: /REGEX_AND_PATTERNS/REGEX/VALIDATE_PATTERNS** 

**Summary:** This API validates Regex patterns.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **FELLOW KV**
## Retrieve Data
### **HTTP Request: /FELLOWKV/GET_DATA/{URL}** 

**Summary:** This API retrieves data that was extracted from the Fellow KV extractor.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| url | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Post Data 
### **HTTP Request: /FELLOWKV/POST_DATA/{URL}** 

**Summary:** This API takes the retrieved Fellow KV data and posts a URL where the data is viewable.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| url | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **DOCUMENT TRAINER**
## Add Sample Document 
### **HTTP Request: /DOCUMENT_TRAINER/ADD_SAMPLE_DOCUMENT** 

**Summary:** This API lets you upload multiple sample documents to the document trainer to test features, etc.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

##  Add One Sample Document
### **HTTP Request: /DOCUMENT_TRAINER/ADD_ONE_SAMPLE_DOCUMENT** 

**Summary:** This API lets you upload one sample document to the document trainer to test features, etc.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrain Model 
### **HTTP Request: /DOCUMENT_TRAINER/RETRAIN_MODEL** 

**Summary:** This API allows you to retrain a model.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrain All Models 
### **HTTP Request: /DOCUMENT_TRAINER/RETRAIN_ALL_MODELS** 

**Summary:** This API allows you to retrain all models at once.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Test Classification 
### **HTTP Request: /DOCUMENT_TRAINER/TEST_CLASSIFICATION** 

**Summary:** This API allows you to test if a document is correctly classified.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Sample Documents 
### **HTTP Request: /DOCUMENT_TRAINER/GET_SAMPLE_DOCUMENTS** 

**Summary:** This API retrieves sample documents.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Sample Document 
### **HTTP Request: /DOCUMENT_TRAINER/DELETE_SAMPLE_DOCUMENT/{ID}** 

**Summary:** This API lets you delete a sample document.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Create Training Files 
### **HTTP Request: /DOCUMENT_TRAINER/CREATE_TRAINING_FILES** 

**Summary:** This APIO lets you create new training files to train documents with.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Test Model 
### **HTTP Request: /DOCUMENT_TRAINER/TEST_MODEL** 

**Summary:** This API lets you test a model.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

<!-- # ** TRIGGERS**
## Retrieve Triggers 
### **HTTP Request: /TRIGGERS/GET_TRIGGERS** 

**Summary:** This API retrieves triggers for work

### 
`***GET*** /triggers/get_triggers` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /TRIGGERS/GET_TRIGGER
## ***GET*** 

**Summary:** Get Trigger

### HTTP Request 
`***GET*** /triggers/get_trigger` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /TRIGGERS/GET_TRIGGER_BY_URL
## ***GET*** 

**Summary:** Get Trigger By Url

### HTTP Request 
`***GET*** /triggers/get_trigger_by_url` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| url | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /TRIGGERS/CREATE_UPDATE_TRIGGER
## ***POST*** 

**Summary:** Create Trigger

### HTTP Request 
`***POST*** /triggers/create_update_trigger` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /TRIGGERS/REMOVE_TRIGGER
## ***DELETE*** 

**Summary:** Remove Trigger

### HTTP Request 
`***DELETE*** /triggers/remove_trigger` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error | -->

# **DOCUMENT STATUS ALERT** 
## Retrieve Document Alert Status
### **HTTP Request: /DOCUMENT_STATUS_ALERT/GET_DOCUMENT_STATUS_ALERT_STATUSES** 

**Summary:** This API retrieves the status of documents for which you have alerts configured.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Retrieve Document Alerts 
### **HTTP Request: /DOCUMENT_STATUS_ALERT/GET_DOCUMENT_STATUS_ALERTS** 

**Summary:** This API retrieves only the alerts for documents which you have alerts configured.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Create Document Status Alert 
### **HTTP Request: /DOCUMENT_STATUS_ALERT/CREATE_DOCUMENT_STATUS_ALERT** 

**Summary:** This API allows you to create a new status alert for a document.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Document Status Alert 
### **HTTP Request: /DOCUMENT_STATUS_ALERT/UPDATE_DOCUMENT_STATUS_ALERT** 

**Summary:** This API allows you to update or change an existing document status alert.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Document Status Alert 
### **HTTP Request: /DOCUMENT_STATUS_ALERT/REMOVE_DOCUMENT_STATUS_ALERT** 

**Summary:** This API allows you to delte a document status alert.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **CUSTOM CLASSIFIER** 
## Test Classification
### **HTTP Request: /CUSTOM_CLASSIFIER/TEST_CLASSIFICATION** 

**Summary:** This API allows you to test the cutom classification rule you created.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Train Document 
### **HTTP Request: /CUSTOM_CLASSIFIER/TRAIN_DOCUMENT** 

**Summary:** This API lets you train documents using your custom classification rule.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **CUSTOM MODEL**
## List 
### **HTTP Request: /CUSTOM_MODEL/LIST** 

**Summary:** This API retrieves a list of custom models.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Create Model 
### **HTTP Request: /CUSTOM_MODEL/CREATE** 

**Summary:** This API allows you to create custom model layouts.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Custom Model 
### **HTTP Request: /CUSTOM_MODEL/{ID}** 

**Summary:** This API retrieves a custom model according to its ID.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Custom Model
### **HTTP Request: /CUSTOM_MODEL/{ID}** 

**Summary:** This API allows you to update or change an existing custom model layout.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Custom Model
### **HTTP Request: /CUSTOM_MODEL/{ID}**

**Summary:** This API lets you delete a custom model layout.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **CUSTOM MODEL LABEL**
## Retrieve Custom Model Label List 
### **HTTP Request: /CUSTOM_MODEL_LABEL/LIST** 

**Summary:** This API retrieves a list of all custom model labels.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| model_name | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Create Custom Model Label 
### **HTTP Request: /CUSTOM_MODEL_LABEL/CREATE** 

**Summary:** This API allows you to create a custom model label.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| model_name | query |  | Yes |  |
| label_name | query |  | Yes |  |
| associated_doc_type | query |  | No |  |
| associated_sub_doc_type | query |  | No |  |
| further_classification_model | query |  | No |  |
| further_classification_model_version | query |  | No |  |
| priority | query |  | No |  |
| is_default | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Specific Custom Model Label 
### **HTTP Request: /CUSTOM_MODEL_LABEL/{ID}** 

**Summary:** This API retrieves a specific custom model label according to its ID.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Update Custom Model Label 
### **HTTP Request: /CUSTOM_MODEL_LABEL/{ID}** 

**Summary:** This API lets you update or change an existing custom model label.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |
| model_name | query |  | No |  |
| label_name | query |  | No |  |
| associated_doc_type | query |  | No |  |
| associated_sub_doc_type | query |  | No |  |
| further_classification_model | query |  | No |  |
| further_classification_model_version | query |  | No |  |
| priority | query |  | No |  |
| is_default | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Delete Custom Model Label 
### **HTTP Request: /CUSTOM_MODEL_LABEL/{ID}** 

**Summary:** This API lets you delete a custom model label.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# **OCR CONFIGURATIONS**
## Retrieve OCR Server Types 
### **HTTP Request: /OCR_CONFIGURATIONS/GET_OCR_SERVER_TYPES** 

**Summary:** This API retrieves all OCR server types.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Update OCR Configuration 
### **HTTP Request: /OCR_CONFIGURATIONS/UPDATE_OCR_CONFIGURATION** 

**Summary:** This API allows you to update or change the existing OCR configurations.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Retrieve Specific OCR Configuration 
### **HTTP Request: /OCR_CONFIGURATIONS/GET_OCR_CONFIGURATION** 

**Summary:** This API Allows you to retrieve a specific OCR configuration.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## Enable/Disable Etext function 
### **HTTP Request: /OCR_CONFIGURATIONS/UPDATE_ETEXT_ENABLE_STATUS** 

**Summary:** This API allows you to activate or deactivate the Etext function.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## Check if Etext is Enabled 
### **HTTP Request: /OCR_CONFIGURATIONS/IS_ETEXT_ENABLED** 

**Summary:** This API retrieves the status of the Etext activation (whether it is turned on or not).

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# **API**
## API Health 
### **HTTP Request: /API/HEALTH/** 

**Summary:** This API checks if an API is still online.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## API Health - Services 
### **HTTP Request: /API/HEALTH/SERVICES** 

**Summary:** This API retrieves the full list of services the API offers and displays whether they are online or not.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /FLOW/GET_DOCUMENT_FLOW/{DOC_ID}
## ***GET*** 

**Summary:** Documents Status

### HTTP Request 
`***GET*** /flow/get_document_flow/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /FLOW/TEST_FLOW/{DOC_ID}
## ***GET*** 

**Summary:** Test Flow

### HTTP Request 
`***GET*** /flow/test_flow/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /MASTER_DATA_LOOKUP/GET_DATASET_TYPES
## ***GET*** 

**Summary:** Get Dataset Types

### HTTP Request 
`***GET*** /master_data_lookup/get_dataset_types` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /MASTER_DATA_LOOKUP/GET_DATASET_FIELDS
## ***GET*** 

**Summary:** Get Dataset Types

### HTTP Request 
`***GET*** /master_data_lookup/get_dataset_fields` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| dataset_name | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /MASTER_DATA_LOOKUP/GET_DATA
## ***GET*** 

**Summary:** Get Data

### HTTP Request 
`***GET*** /master_data_lookup/get_data` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| data_type | query |  | Yes |  |
| filter_data_json | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /MASTER_DATA_LOOKUP/DOWNLOAD_CSV
## ***GET*** 

**Summary:** Get Data

### HTTP Request 
`***GET*** /master_data_lookup/download_csv` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| data_type | query |  | Yes |  |
| delimiter | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /MASTER_DATA_LOOKUP/CREATE_RECORDS
## ***POST*** 

**Summary:** Create Records

### HTTP Request 
`***POST*** /master_data_lookup/create_records` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /MASTER_DATA_LOOKUP/UPDATE_RECORD
## ***POST*** 

**Summary:** Update Record

### HTTP Request 
`***POST*** /master_data_lookup/update_record` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /MASTER_DATA_LOOKUP/DELETE_RECORD
## ***POST*** 

**Summary:** Delete Record

### HTTP Request 
`***POST*** /master_data_lookup/delete_record` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /MASTER_DATA_LOOKUP/IMPORT_DATA
## ***POST*** 

**Summary:** Import Data

### HTTP Request 
`***POST*** /master_data_lookup/import_data` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /HEALTHZ
## ***GET*** 

**Summary:** This API checks to see if the system is online.

### HTTP Request 
`***GET*** /healthz` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |



