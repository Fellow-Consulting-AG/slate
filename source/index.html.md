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

# Introduction

Welcome to the Polydocs API! You can use our API to access Polydocs API endpoints, which can get information on various cats, kittens, and breeds in our database.



# Authentication

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


# MasterData

## Insert new Master Data 

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

# Test Classify

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

# /HEALTHZ
## ***GET*** 

**Summary:** This API checks to see if the system is online.

### HTTP Request 
`***GET*** /healthz` 

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

# Introduction 

DOC2 - API 

**Version:** 2.2.10 

# /
## ***GET*** 

**Summary:** Root

### HTTP Request 
`***GET*** /` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# LOGTAIL
## ***POST*** 

**Summary:** This API retrieves logs from the system

### HTTP Request 
`***POST*** /logtail/` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /LOGTAIL/NEXT
## ***POST*** 

**Summary:** Get Next Logs

### HTTP Request 
`***POST*** /logtail/next` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /USERS/GET_USERS
## ***GET*** 

**Summary:** This API allows you to retrieve specific users from the system.

### HTTP Request 
`***GET*** /users/get_users` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /USERS/CREATE
## ***POST*** 

**Summary:** This API allows you create a new user in the system.

### HTTP Request 
`***POST*** /users/create` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /USERS/DELETE/{USER_ID}
## ***DELETE*** 

**Summary:** This API allows you to delete a user from the system.

### HTTP Request 
`***DELETE*** /users/delete/{user_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| user_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /USERS/UPDATE/{USER_ID}
## ***PUT*** 

**Summary:** This API allows you to update or change any specific users information.

### HTTP Request 
`***PUT*** /users/update/{user_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| user_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /USERS/GET_USERS_WHO_CAN_APPROVE
## ***GET*** 

**Summary:** This API retrieves all the users that have the ability to approve certain changes in the system.

### HTTP Request 
`***GET*** /users/get_users_who_can_approve` 

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

# /GROUPS/GET_GROUPS
## ***GET*** 

**Summary:** This API allows you to retrieve a specific group or groups from the system.

### HTTP Request 
`***GET*** /groups/get_groups` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /GROUPS/CREATE
## ***POST*** 

**Summary:** This API allows you to create a new group in the system.

### HTTP Request 
`***POST*** /groups/create` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUPS/DELETE/{GROUP_ID}
## ***DELETE*** 

**Summary:** This API allows you to delete a group from the system.

### HTTP Request 
`***DELETE*** /groups/delete/{group_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| group_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUPS/UPDATE/{GROUP_ID}
## ***PUT*** 

**Summary:** This API allows you to update or change any specific groups information.

### HTTP Request 
`***PUT*** /groups/update/{group_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| group_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUPS/ADD_USER_TO_GROUP
## ***POST*** 

**Summary:** This API allows you to add a new user to a specific group.

### HTTP Request 
`***POST*** /groups/add_user_to_group` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUPS_AND_USERS/ADD_USER_TO_GROUP
## ***POST*** 

**Summary:** This API allows you to add a specific user to a group.

### HTTP Request 
`***POST*** /groups_and_users/add_user_to_group` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUPS_AND_USERS/ADD_USERS_TO_GROUP
## ***POST*** 

**Summary:** This API allows you to add multiple users to a group.

### HTTP Request 
`***POST*** /groups_and_users/add_users_to_group` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUPS_AND_USERS/REMOVE_USER_FROM_GROUP
## ***DELETE*** 

**Summary:** This API allows you to remove a specific user from a group.

### HTTP Request 
`***DELETE*** /groups_and_users/remove_user_from_group` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUPS_AND_USERS/GET_GROUP_USERS
## ***GET*** 

**Summary:** This API allows you to retrieve the users from a specific group.

### HTTP Request 
`***GET*** /groups_and_users/get_group_users` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| group_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUP_PERMISSION/SET_GROUP_PERMISSIONS
## ***POST*** 

**Summary:** This API allows you to set what permissions a specific group has enabled.

### HTTP Request 
`***POST*** /group_permission/set_group_permissions` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUP_PERMISSION/SET_ALL_GROUPS_PERMISSIONS
## ***POST*** 

**Summary:** This API allows you to set what permissions all groups have enabled.

### HTTP Request 
`***POST*** /group_permission/set_all_groups_permissions` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUP_PERMISSION/GET_GROUP_PERMISSIONS
## ***GET*** 

**Summary:** This API retrieves the permissions a group has enabled.

### HTTP Request 
`***GET*** /group_permission/get_group_permissions` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## ***POST*** 

**Summary:** Set Group Permissions

### HTTP Request 
`***POST*** /group_permission/get_group_permissions` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /GROUP_PERMISSION/GET_ALL_GROUPS_PERMISSIONS
## ***GET*** 

**Summary:** Set Group Permissions

### HTTP Request 
`***GET*** /group_permission/get_all_groups_permissions` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## ***POST*** 

**Summary:** Set Group Permissions

### HTTP Request 
`***POST*** /group_permission/get_all_groups_permissions` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /GROUP_PERMISSION/GET_USER_GROUPS_AND_PERMISSIONS
## ***GET*** 

**Summary:** Set Group Permissions

### HTTP Request 
`***GET*** /group_permission/get_user_groups_and_permissions` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

## ***POST*** 

**Summary:** Set Group Permissions

### HTTP Request 
`***POST*** /group_permission/get_user_groups_and_permissions` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /SUB_ORGANISATIONS/GET_SUB_ORGANISATIONS
## ***GET*** 

**Summary:** Get Sub Organisations

### HTTP Request 
`***GET*** /sub_organisations/get_sub_organisations` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /SUB_ORGANISATIONS/CREATE
## ***POST*** 

**Summary:** Create Sub Organization

### HTTP Request 
`***POST*** /sub_organisations/create` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /SUB_ORGANISATIONS/DELETE/{SUB_ORG_ID}
## ***DELETE*** 

**Summary:** Delete Group

### HTTP Request 
`***DELETE*** /sub_organisations/delete/{sub_org_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| sub_org_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /SUB_ORGANISATIONS/UPDATE/{SUB_ORG_ID}
## ***PUT*** 

**Summary:** Update Group

### HTTP Request 
`***PUT*** /sub_organisations/update/{sub_org_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| sub_org_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /SUB_ORGANISATION_USER/ADD_USER_TO_SUB_ORGANISATION
## ***POST*** 

**Summary:** Add User To Sub Organisation

### HTTP Request 
`***POST*** /sub_organisation_user/add_user_to_sub_organisation` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /SUB_ORGANISATION_USER/REMOVE_USER_FROM_SUB_ORGANISATION
## ***DELETE*** 

**Summary:** Remove User From Sub Organisation

### HTTP Request 
`***DELETE*** /sub_organisation_user/remove_user_from_sub_organisation` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /SUB_ORGANISATION_USER/GET_USER_SUB_ORGANISATIONS
## ***GET*** 

**Summary:** Get User Sub Organisations

### HTTP Request 
`***GET*** /sub_organisation_user/get_user_sub_organisations` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| user_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /SUB_ORGANISATION_USER/GET_USER_ORGANISATION_AND_SUB_ORGANISATION
## ***GET*** 

**Summary:** Get User Organisation And Sub Organisation

### HTTP Request 
`***GET*** /sub_organisation_user/get_user_organisation_and_sub_organisation` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /SUB_ORGANISATION_USER/GET_SUB_ORGANISATIONS_WITH_USERS
## ***GET*** 

**Summary:** Get User Organisation And Sub Organisation

### HTTP Request 
`***GET*** /sub_organisation_user/get_sub_organisations_with_users` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /SUB_ORGANISATION_USER/GET_SUB_ORGANISATION_USERS
## ***GET*** 

**Summary:** Get Sub Organisation Users

### HTTP Request 
`***GET*** /sub_organisation_user/get_sub_organisation_users` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| sub_org_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/CONFIGURE_WEBHOOK_EXPORT
## ***POST*** 

**Summary:** Webhook Configurations

### HTTP Request 
`***POST*** /configurations/configure_webhook_export` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/CONFIGURE_FLOW2_EXPORT
## ***POST*** 

**Summary:** Flow2 Configurations

### HTTP Request 
`***POST*** /configurations/configure_flow2_export` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/CONFIGURE_ZUGFERD_EXPORT
## ***POST*** 

**Summary:** Zugferd Configuration

### HTTP Request 
`***POST*** /configurations/configure_zugferd_export` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/CONFIGURE_PEPPOL_EXPORT
## ***POST*** 

**Summary:** Peppol Configuration

### HTTP Request 
`***POST*** /configurations/configure_peppol_export` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/CONFIGURE_IDM_EXPORT
## ***POST*** 

**Summary:** Idm Export Configurations

### HTTP Request 
`***POST*** /configurations/configure_idm_export` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/CONFIGURE_BOD_EXPORT
## ***POST*** 

**Summary:** Bod Export Configurations

### HTTP Request 
`***POST*** /configurations/configure_bod_export` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/CONFIGURE_ION_EXPORT
## ***POST*** 

**Summary:** Ion Export Configurations

### HTTP Request 
`***POST*** /configurations/configure_ion_export` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/CONFIGURE_INFOR_EXPORT
## ***POST*** 

**Summary:** Infor Export Configurations

### HTTP Request 
`***POST*** /configurations/configure_infor_export` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/GET_CONFIGURATION
## ***POST*** 

**Summary:** Get Configurations

### HTTP Request 
`***POST*** /configurations/get_configuration` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /CONFIGURATIONS/GET_CONFIGURATIONS
## ***POST*** 

**Summary:** Get Export Configurations

### HTTP Request 
`***POST*** /configurations/get_configurations` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /CONFIGURATIONS/REMOVE_CONFIGURATION
## ***POST*** 

**Summary:** Remove Configuration

### HTTP Request 
`***POST*** /configurations/remove_configuration` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/UPDATE_CONFIGURATION_VISIBILITY
## ***POST*** 

**Summary:** Update Configuration Visibility

### HTTP Request 
`***POST*** /configurations/update_configuration_visibility` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/VALIDATE_EXPORT_CONFIGURATION
## ***POST*** 

**Summary:** Validate Export Configurations

### HTTP Request 
`***POST*** /configurations/validate_export_configuration` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CONFIGURATIONS/DOCUMENT_TYPES
## ***GET*** 

**Summary:** Get Document Types

### HTTP Request 
`***GET*** /configurations/document_types` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /CONFIGURATIONS/DOCUMENT_TYPES_LIST
## ***GET*** 

**Summary:** Get Document Types List

### HTTP Request 
`***GET*** /configurations/document_types_list` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /CONFIGURATIONS/DOWNLOAD/{ID}
## ***GET*** 

**Summary:** Downlod File

### HTTP Request 
`***GET*** /configurations/download/{id}` 

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

# /IMPORT/SUPPLIER_BOD
## ***POST*** 

**Summary:** Import Supplier Bod

### HTTP Request 
`***POST*** /import/supplier_bod` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /IMPORT/SUPPLIER_BOD_XML
## ***POST*** 

**Summary:** Import Supplier Bod Xml

### HTTP Request 
`***POST*** /import/supplier_bod_xml` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /IMPORT/PURCHASE_ORDER_BOD
## ***POST*** 

**Summary:** Import Purchase Order Bod

### HTTP Request 
`***POST*** /import/purchase_order_bod` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /IMPORT/PURCHASE_ORDER_BOD_XML
## ***POST*** 

**Summary:** Import Purchase Order Bod Xml

### HTTP Request 
`***POST*** /import/purchase_order_bod_xml` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /IMPORT/ACK_PURCHASE_ORDER_BOD
## ***POST*** 

**Summary:** Import Ack Purchase Order Bod

### HTTP Request 
`***POST*** /import/ack_purchase_order_bod` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /IMPORT/ACK_RECEIVE_DELIVERY_BOD
## ***POST*** 

**Summary:** Import Ack Receive Delivery Bod

### HTTP Request 
`***POST*** /import/ack_receive_delivery_bod` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EMAIL/GET_EMAIL
## ***GET*** 

**Summary:** Get Email

### HTTP Request 
`***GET*** /email/get_email` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /EMAIL/ADD_UPDATE_EMAIL
## ***POST*** 

**Summary:** Add Update Email

### HTTP Request 
`***POST*** /email/add_update_email` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EMAIL/DELETE_EMAIL
## ***DELETE*** 

**Summary:** Delete Email

### HTTP Request 
`***DELETE*** /email/delete_email` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /EMAIL/(DE)-ACTIVATE_EMAIL
## ***POST*** 

**Summary:** Switch Email

### HTTP Request 
`***POST*** /email/(de)-activate_email` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EMAIL/FETCH_EMAILS
## ***GET*** 

**Summary:** Fetch Emails

### HTTP Request 
`***GET*** /email/fetch_emails` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /EMAIL/GET_IMPORT_LOG
## ***GET*** 

**Summary:** Get Log

### HTTP Request 
`***GET*** /email/get_import_log` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /EMAIL/CHECK_LOGIN
## ***POST*** 

**Summary:** Check Login

### HTTP Request 
`***POST*** /email/check_login` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /ORG_DETAILS/SET_ORG_DETAILS
## ***POST*** 

**Summary:** Set Org Details

### HTTP Request 
`***POST*** /org_details/set_org_details` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /ORG_DETAILS/GET_ORG_DETAILS
## ***GET*** 

**Summary:** Get Org Details

### HTTP Request 
`***GET*** /org_details/get_org_details` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /ORG_DETAILS/SET_ORG_PROFILE
## ***POST*** 

**Summary:** Set Org Profile

### HTTP Request 
`***POST*** /org_details/set_org_profile` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /ORG_DETAILS/GET_ORG_PROFILE
## ***GET*** 

**Summary:** Get Org Profile

### HTTP Request 
`***GET*** /org_details/get_org_profile` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /ORG_DETAILS/SET_OCR_SETTINGS
## ***POST*** 

**Summary:** Set Ocr Settings

### HTTP Request 
`***POST*** /org_details/set_ocr_settings` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /ORG_DETAILS/GET_OCR_SETTINGS
## ***GET*** 

**Summary:** Get Ocr Settings

### HTTP Request 
`***GET*** /org_details/get_ocr_settings` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /ORG_DETAILS/CHECK_OCR
## ***POST*** 

**Summary:** Check Ocr

### HTTP Request 
`***POST*** /org_details/check_ocr` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EXPORT/EXPORT_ZUGFERD
## ***GET*** 

**Summary:** Export Zugferd

### HTTP Request 
`***GET*** /export/export_zugferd` 

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

# /EXPORT/EXPORT_PEPPOL
## ***GET*** 

**Summary:** Export Peppol

### HTTP Request 
`***GET*** /export/export_peppol` 

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

# /EXPORT/GET_PENDING_WATCH_EXPORT_DOCUMENTS
## ***GET*** 

**Summary:** Get Pending Watch Export Documents

### HTTP Request 
`***GET*** /export/get_pending_watch_export_documents` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EXPORT/UPDATE_PENDING_WATCH_EXPORT_STATUS
## ***GET*** 

**Summary:** Update Pending Watch Export Status

### HTTP Request 
`***GET*** /export/update_pending_watch_export_status` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EXPORT/TEST_PROCESS_DOC
## ***GET*** 

**Summary:** Test Process Doc

### HTTP Request 
`***GET*** /export/test_process_doc` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EXPORT/SAVE_EXTRACTION_RULES
## ***POST*** 

**Summary:** Save Extraction Rules

### HTTP Request 
`***POST*** /export/save_extraction_rules` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EXPORT/GET_DATA_V1
## ***GET*** 

**Summary:** Get Data V1

### HTTP Request 
`***GET*** /export/get_data_v1` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /FUZZY/GET_VENDORS_LIST
## ***POST*** 

**Summary:** Get Vendors List

### HTTP Request 
`***POST*** /fuzzy/get_vendors_list` 

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

# /FUZZY/IMPORT_VENDORS_CSV
## ***POST*** 

**Summary:** Import Vendors Csv

### HTTP Request 
`***POST*** /fuzzy/import_vendors_csv` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /VENDORS/GET_VENDORS_LIST
## ***GET*** 

**Summary:** Get Vendors List

### HTTP Request 
`***GET*** /vendors/get_vendors_list` 

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

# /VENDORS/IMPORT_VENDORS_CSV
## ***POST*** 

**Summary:** Import Vendors Csv

### HTTP Request 
`***POST*** /vendors/import_vendors_csv` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /MIGRATION/GET_MIGRATION_VERSION
## ***GET*** 

**Summary:** Get Migration Version

### HTTP Request 
`***GET*** /migration/get_migration_version` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /DOC_CLASSIFICATION_RULES/GET_DOC_CLASSIFICATION_RULES
## ***GET*** 

**Summary:** Get Groups

### HTTP Request 
`***GET*** /doc_classification_rules/get_doc_classification_rules` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /DOC_CLASSIFICATION_RULES/CREATE
## ***POST*** 

**Summary:** Create Rule

### HTTP Request 
`***POST*** /doc_classification_rules/create` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOC_CLASSIFICATION_RULES/DELETE/{ID}
## ***DELETE*** 

**Summary:** Delete Group

### HTTP Request 
`***DELETE*** /doc_classification_rules/delete/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOC_CLASSIFICATION_RULES/UPDATE/{ID}
## ***PUT*** 

**Summary:** Update

### HTTP Request 
`***PUT*** /doc_classification_rules/update/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/CLASSIFY_DOCUMENT
## ***POST*** 

**Summary:** Process Doc2Landing Document

### HTTP Request 
`***POST*** /document/classify_document` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/PROCESS_DOC2LANDING_DOCUMENT
## ***POST*** 

**Summary:** Process Doc2Landing Document

### HTTP Request 
`***POST*** /document/process_doc2landing_document` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/PROCESS_DOCUMENTS
## ***POST*** 

**Summary:** Process Documents

### HTTP Request 
`***POST*** /document/process_documents` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/PROCESS
## ***POST*** 

**Summary:** Process

### HTTP Request 
`***POST*** /document/process` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/PROCESS_BASE64
## ***POST*** 

**Summary:** Process Base64

### HTTP Request 
`***POST*** /document/process_base64` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/UPDATE/{DOC_ID}
## ***POST*** 

**Summary:** Update

### HTTP Request 
`***POST*** /document/update/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/VALIDATE_AND_EXPORT/{DOC_ID}
## ***POST*** 

**Summary:** Validate And Export

### HTTP Request 
`***POST*** /document/validate_and_export/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/LIST
## ***GET*** 

**Summary:** Documents List

### HTTP Request 
`***GET*** /document/list` 

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

# /DOCUMENT/STATUS/{DOC_ID}
## ***GET*** 

**Summary:** Documents Status

### HTTP Request 
`***GET*** /document/status/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/DASHBOARD
## ***GET*** 

**Summary:** Dashboard

### HTTP Request 
`***GET*** /document/dashboard` 

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

# /DOCUMENT/EXTRACTION_RESULT
## ***POST*** 

**Summary:** Extraction Result

### HTTP Request 
`***POST*** /document/extraction_result` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/GET_ITEMS_FROM_DICTIONARY/{ITEM}
## ***GET*** 

**Summary:** Get Items From Dictionary

### HTTP Request 
`***GET*** /document/get_items_from_dictionary/{item}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| item | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/RESTART/{DOC_ID}
## ***GET*** 

**Summary:** Restart

### HTTP Request 
`***GET*** /document/restart/{doc_id}` 

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

# /DOCUMENT/RESTART_DOCUMENTS
## ***POST*** 

**Summary:** Restart Documents

### HTTP Request 
`***POST*** /document/restart_documents` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/APPROVE_OR_REJECT/{DOC_ID}
## ***POST*** 

**Summary:** Approve Or Reject

### HTTP Request 
`***POST*** /document/approve_or_reject/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/UPDATE_DOCUMENT_LOG/{DOC_ID}
## ***POST*** 

**Summary:** Update Document Log

### HTTP Request 
`***POST*** /document/update_document_log/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/GET_DOCUMENT_LOG/{DOC_ID}
## ***POST*** 

**Summary:** Get Document Log

### HTTP Request 
`***POST*** /document/get_document_log/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/RESTART_WITH_NEW_CLASSIFICATION/{DOC_ID}
## ***POST*** 

**Summary:** Restart With New Classification

### HTTP Request 
`***POST*** /document/restart_with_new_classification/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/RESTART_EXPORT/{DOC_ID}
## ***GET*** 

**Summary:** Restart Export

### HTTP Request 
`***GET*** /document/restart_export/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/{DOC_ID}
## ***GET*** 

**Summary:** Get Document

### HTTP Request 
`***GET*** /document/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/DELETE/{DOC_ID}
## ***DELETE*** 

**Summary:** Delete Document

### HTTP Request 
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

# /DOCUMENT/DELETE_DOCUMENTS
## ***DELETE*** 

**Summary:** Delete Documents

### HTTP Request 
`***DELETE*** /document/delete_documents` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/ASSIGN/{DOC_ID}
## ***POST*** 

**Summary:** Assign

### HTTP Request 
`***POST*** /document/assign/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/ASSIGN_DOCUMENTS
## ***POST*** 

**Summary:** Assign Documents

### HTTP Request 
`***POST*** /document/assign_documents` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/ASSIGN_WITH_EMAIL/{DOC_ID}
## ***POST*** 

**Summary:** Assign With Email

### HTTP Request 
`***POST*** /document/assign_with_email/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/GET_NEXT_DOCUMENT/{DOC_ID}
## ***GET*** 

**Summary:** Get Next Document

### HTTP Request 
`***GET*** /document/get_next_document/{doc_id}` 

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

# /DOCUMENT/GET_OCR_DATA/{DOC_ID}
## ***POST*** 

**Summary:** Get Ocr Data

### HTTP Request 
`***POST*** /document/get_ocr_data/{doc_id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/DELETE_ERROR_DOCS
## ***DELETE*** 

**Summary:** Delete Error Docs

### HTTP Request 
`***DELETE*** /document/delete_error_docs` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /DOCUMENT/SPLIT_DOCUMENT
## ***POST*** 

**Summary:** Split Document

### HTTP Request 
`***POST*** /document/split_document` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/GENERATE_THUMBNAILS
## ***POST*** 

**Summary:** Generate Thumbnails

### HTTP Request 
`***POST*** /document/generate_thumbnails` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT/GET_DOC_STATUS_XML
## ***POST*** 

**Summary:** Get Doc Status Xml

### HTTP Request 
`***POST*** /document/get_doc_status_xml` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_LAYOUT_TEMPLATE/GET_LAYOUT_TEMPLATES
## ***GET*** 

**Summary:** Get Layout Templates

### HTTP Request 
`***GET*** /document_layout_template/get_layout_templates` 

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

# /DOCUMENT_LAYOUT_TEMPLATE/CREATE
## ***POST*** 

**Summary:** Create Layout Templates

### HTTP Request 
`***POST*** /document_layout_template/create` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_LAYOUT_TEMPLATE/{ID}
## ***GET*** 

**Summary:** Get Layout Templates

### HTTP Request 
`***GET*** /document_layout_template/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## ***PUT*** 

**Summary:** Update Layout Templates

### HTTP Request 
`***PUT*** /document_layout_template/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## ***DELETE*** 

**Summary:** Delete Layout Templates

### HTTP Request 
`***DELETE*** /document_layout_template/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_LAYOUT_TEMPLATE/UPLOAD_TEMPLATE_SAMPLE
## ***POST*** 

**Summary:** Upload Template Sample

### HTTP Request 
`***POST*** /document_layout_template/upload_template_sample` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_LOCK/ACQUIRE_LOCK
## ***POST*** 

**Summary:** Acquire Lock

### HTTP Request 
`***POST*** /document_lock/acquire_lock` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_LOCK/RELEASE_LOCK
## ***POST*** 

**Summary:** Release Lock

### HTTP Request 
`***POST*** /document_lock/release_lock` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_LOCK/RENEW_LOCK
## ***POST*** 

**Summary:** Renew Lock

### HTTP Request 
`***POST*** /document_lock/renew_lock` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /TABLE_EXTRACTION_V3/AUTO_EXTRACT_TABLE
## ***POST*** 

**Summary:** Auto Extract Table V3

### HTTP Request 
`***POST*** /table_extraction_v3/auto_extract_table` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /TABLE_EXTRACTION_V3/GET_TABLE
## ***POST*** 

**Summary:** Get Table

### HTTP Request 
`***POST*** /table_extraction_v3/get_table` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /TABLE_EXTRACTION_V3/REFORMAT_TABLE
## ***POST*** 

**Summary:** Reformat Table

### HTTP Request 
`***POST*** /table_extraction_v3/reformat_table` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /TABLE_EXTRACTION_V3/GET_COMPACT_TABLE
## ***POST*** 

**Summary:** Get Compact Table

### HTTP Request 
`***POST*** /table_extraction_v3/get_compact_table` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /TABLE_EXTRACTION_V3/CREATE_DOCUMENT_TABLE_COLUMN
## ***POST*** 

**Summary:** Create Document Type

### HTTP Request 
`***POST*** /table_extraction_v3/create_document_table_column` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /TABLE_EXTRACTION_V3/DELETE_TABLE_RULES
## ***POST*** 

**Summary:** Delete Table Rules

### HTTP Request 
`***POST*** /table_extraction_v3/delete_table_rules` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /BLOCK_TABLE_EXTRACTION/BLOCKED_LIST
## ***GET*** 

**Summary:** Blocked List

### HTTP Request 
`***GET*** /block_table_extraction/blocked_list` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /BLOCK_TABLE_EXTRACTION/BLOCKED_LIST/ADD
## ***POST*** 

**Summary:** Blocked List Add

### HTTP Request 
`***POST*** /block_table_extraction/blocked_list/add` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /BLOCK_TABLE_EXTRACTION/BLOCKED_LIST/{ID}
## ***DELETE*** 

**Summary:** Delete From Blocked List

### HTTP Request 
`***DELETE*** /block_table_extraction/blocked_list/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /FIELD/GET_DOCUMENT_UI_LAYOUT
## ***GET*** 

**Summary:** Get Document Ui Layout

### HTTP Request 
`***GET*** /field/get_document_ui_layout` 

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

# /FIELD/GET_FIELD_SETTINGS
## ***GET*** 

**Summary:** Get Field Settings

### HTTP Request 
`***GET*** /field/get_field_settings` 

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

# /FIELD/CLONE_DOC_TYPE
## ***GET*** 

**Summary:** Clone Doc Type

### HTTP Request 
`***GET*** /field/clone_doc_type` 

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

# /FIELD/COPY_FIELDS_SETTING_FROM_DOC_TYPE
## ***GET*** 

**Summary:** Copy Fields Setting From Doc Type

### HTTP Request 
`***GET*** /field/copy_fields_setting_from_doc_type` 

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

# /FIELD/GET_FIELD_SETTINGS_ALL_DOCUMENT_TYPES
## ***GET*** 

**Summary:** Get All Documents Field Settings

### HTTP Request 
`***GET*** /field/get_field_settings_all_document_types` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| profile | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /FIELD/SETTINGS_RESTORE_DEFAULTS
## ***POST*** 

**Summary:** Reset Field Rules

### HTTP Request 
`***POST*** /field/settings_restore_defaults` 

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

# /FIELD/UPDATE_FIELD_SETTINGS
## ***POST*** 

**Summary:** Get Field Rules

### HTTP Request 
`***POST*** /field/update_field_settings` 

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

# /FIELD/GET_DOCUMENT_LAYOUT
## ***POST*** 

**Summary:** Get Document Layout

### HTTP Request 
`***POST*** /field/get_document_layout` 

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

# /FIELD/GET_DOCUMENT_TABLE_VALIDATION_RULES
## ***GET*** 

**Summary:** Get Document Table Validation Rules

### HTTP Request 
`***GET*** /field/get_document_table_validation_rules` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| table_name | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /FIELD/UPDATE_DOCUMENT_TABLE_COLUMN
## ***POST*** 

**Summary:** Update Document Table Column

### HTTP Request 
`***POST*** /field/update_document_table_column` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /FIELD/GET_CUSTOM_FIELD_LABELS
## ***GET*** 

**Summary:** Get Custom Field Labels

### HTTP Request 
`***GET*** /field/get_custom_field_labels` 

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

# /EXTRACT/GET_TEXT
## ***POST*** 

**Summary:** Get Text

### HTTP Request 
`***POST*** /extract/get_text` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EXTRACT/GET_TABLE_TEXT
## ***POST*** 

**Summary:** Get Table Text

### HTTP Request 
`***POST*** /extract/get_table_text` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EXTRACT/GET_FORMATTED_AMOUNT
## ***POST*** 

**Summary:** Get Formatted Amount

### HTTP Request 
`***POST*** /extract/get_formatted_amount` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EXTRACT/GET_COLUMN_HEADERS
## ***GET*** 

**Summary:** Get Document Types

### HTTP Request 
`***GET*** /extract/get_column_headers` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /EXTRACT/GET_AI_SCORE
## ***POST*** 

**Summary:** Get Ai Score

### HTTP Request 
`***POST*** /extract/get_ai_score` 

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

# /PURCHASE_ORDER/GET_PURCHASE_ORDERS_LIST
## ***GET*** 

**Summary:** Get Purchase Orders List

### HTTP Request 
`***GET*** /purchase_order/get_purchase_orders_list` 

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

# /PURCHASE_ORDER/GET_PURCHASE_ORDER_LINES
## ***GET*** 

**Summary:** Get Purchase Order Lines

### HTTP Request 
`***GET*** /purchase_order/get_purchase_order_lines` 

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

# /PURCHASE_ORDER/GET_PURCHASE_ORDER_DISPLAY_COLS
## ***GET*** 

**Summary:** Get Purchase Orders List

### HTTP Request 
`***GET*** /purchase_order/get_purchase_order_display_cols` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /PURCHASE_ORDER/GET_TABLE_FROM_PO_NUMBERS
## ***POST*** 

**Summary:** Get Table From Po Numbers

### HTTP Request 
`***POST*** /purchase_order/get_table_from_po_numbers` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /PURCHASE_ORDER/AUTO_PO_MATCH
## ***POST*** 

**Summary:** Get Table From Po Numbers

### HTTP Request 
`***POST*** /purchase_order/auto_po_match` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /SPECIAL_RULES/SAVE
## ***POST*** 

**Summary:** Save

### HTTP Request 
`***POST*** /special_rules/save` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /PREFERENCES/GET_PREFERENCES
## ***GET*** 

**Summary:** Get Preferences

### HTTP Request 
`***GET*** /preferences/get_preferences` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /PREFERENCES/GET_PREFERENCE
## ***GET*** 

**Summary:** Get Preference

### HTTP Request 
`***GET*** /preferences/get_preference` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| key | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /PREFERENCES/SET_PREFERENCE
## ***PUT*** 

**Summary:** Set Preference

### HTTP Request 
`***PUT*** /preferences/set_preference` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /PREFERENCES/REMOVE_PREFERENCE
## ***DELETE*** 

**Summary:** Remove Preferences

### HTTP Request 
`***DELETE*** /preferences/remove_preference` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| key | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /PREFERENCES/GET_DOCUMENT_TYPE_REGEXES
## ***GET*** 

**Summary:** Get Document Type Regexes

### HTTP Request 
`***GET*** /preferences/get_document_type_regexes` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /PREFERENCES/GET_SUPPORTED_BARCODE_TYPES
## ***GET*** 

**Summary:** Get Supported Barcode Types

### HTTP Request 
`***GET*** /preferences/get_supported_barcode_types` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /PREFERENCES/UPDATE_ORGANISATION_PREFERENCE
## ***POST*** 

**Summary:** Update Organisation Preference

### HTTP Request 
`***POST*** /preferences/update_organisation_preference` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /PREFERENCES/GET_ORGANISATION_PREFERENCE
## ***POST*** 

**Summary:** Get Organisation Preference

### HTTP Request 
`***POST*** /preferences/get_organisation_preference` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /PREFERENCES/UPDATE_OCR_CONFIGURATION
## ***POST*** 

**Summary:** Update Ocr Configuration

### HTTP Request 
`***POST*** /preferences/update_ocr_configuration` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /PREFERENCES/GET_OCR_CONFIGURATION
## ***POST*** 

**Summary:** Get Ocr Configuration

### HTTP Request 
`***POST*** /preferences/get_ocr_configuration` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /RESOURCE/DOCUMENT/{DOC_ID}/{FILENAME}
## ***GET*** 

**Summary:** Document

### HTTP Request 
`***GET*** /resource/document/{doc_id}/{filename}` 

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

# /RESOURCE/IMAGE/{DOC_ID}/{PAGE}
## ***GET*** 

**Summary:** Document

### HTTP Request 
`***GET*** /resource/image/{doc_id}/{page}` 

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

# /RESOURCE/{TYPE}/{ID}/IMAGE/{PAGE}
## ***GET*** 

**Summary:** Document

### HTTP Request 
`***GET*** /resource/{type}/{id}/image/{page}` 

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

# /RESOURCE/CHECK_S3
## ***GET*** 

**Summary:** S3 Check

### HTTP Request 
`***GET*** /resource/check_S3` 

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

# /RESOURCE/MASS_CHECK_S3
## ***POST*** 

**Summary:** Mass S3 Check

### HTTP Request 
`***POST*** /resource/mass_check_S3` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /RESOURCE/GET_ERRORS
## ***GET*** 

**Summary:** Get Error From Db

**Description:** Gets the error message and the exception cause from the db for the specified doc_ids

### HTTP Request 
`***GET*** /resource/get_errors` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EPHESOFT/EXTRACT_TABLE
## ***POST*** 

**Summary:** Extract Table

**Description:** Extracts table from the document
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

### HTTP Request 
`***POST*** /ephesoft/extract_table` 

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

# /EPHESOFT/GET_TABLE_TRAIN_URL
## ***POST*** 

**Summary:** Get Table Train Url

**Description:** Saves a table training record with doc_id and ephesoft_doc_id extracted
    from attached xml.
    OCRs and copies document from fellowkv storage to doc2 storage.
    Note: This endpoint doesn't extract any table yet. This is done by 
          get_table_train_data endpoint.
Args:
    ephesoft_doc_id ([type]): Ephesoft doc id, for which table will be 
                              trained/extracted (e.g. DOC1)
    file: Zip or XML document from Ephesoft. ([BatchInstance]_batch.xml)
    force_ocr ([type]): To re-ocr already ocr-ed document
Returns:
    [type]: id of the saved record

### HTTP Request 
`***POST*** /ephesoft/get_table_train_url` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EPHESOFT/GET_TABLE_TRAIN_DATA
## ***GET*** 

**Summary:** Get Table Train Data

**Description:** Extracts table from the document and return in response
Args:
    id ([type]): Id for the saved record for EphesoftTableExtractionTraining
Returns:
    [type]: id of the saved record

### HTTP Request 
`***GET*** /ephesoft/get_table_train_data` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EPHESOFT/SAVE_EXTRACTION_RULES/{ID}
## ***POST*** 

**Summary:** Save Extraction Rules2

**Description:** Saves extraction results, which can be loaded in Ephesoft with 'Reload Data' button
    using get_updated_ephesoft_doc endpoint.
    Saves table extraction rules for future documents of same supplier.
Args:
    id ([type]): Id for the saved record for EphesoftTableExtractionTraining
Returns:
    [type]: id of the saved record

### HTTP Request 
`***POST*** /ephesoft/save_extraction_rules/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EPHESOFT/GET_PO_MATCH_URL
## ***POST*** 

**Summary:** Get Po Match Url

**Description:** Saves a EphesoftPOMatching record with doc_id and ephesoft_doc_id extracted
    from attached xml.
    Extract table from xml
    Populates po_items (po line match with table line)
Args:
    ephesoft_doc_id ([type]): Ephesoft doc id, for which table will be 
                              trained/extracted (e.g. DOC1)
    file: Zip or XML document from Ephesoft. ([BatchInstance]_batch.xml)
Returns:
    [type]: id of the saved record

### HTTP Request 
`***POST*** /ephesoft/get_po_match_url` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EPHESOFT/GET_PO_MATCH_DATA/{ID}
## ***GET*** 

**Summary:** Get Po Match Data

**Description:** Return extracted_data from EphesoftPOMatching. This has same structure
    as we have for documents extracted_data
Args:
    id ([type]): EphesoftPOMatching record id
Returns:
    [type]: extracted_data from EphesoftPOMatching

### HTTP Request 
`***GET*** /ephesoft/get_po_match_data/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EPHESOFT/SAVE_PO_MATCH_DATA/{ID}
## ***POST*** 

**Summary:** Save Po Match Data

**Description:** Saves updated EphesoftPOMatching record from extracted_data sent in request.
Args:
    id ([type]): EphesoftPOMatching record id
    extracted_data ([type]): extracted_data in the same format we have for documents
Returns:
    [type]: success result

### HTTP Request 
`***POST*** /ephesoft/save_po_match_data/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /EPHESOFT/GET_UPDATED_EPHESOFT_DOC
## ***POST*** 

**Summary:** Get Updated Ephesoft Doc

**Description:** Return updated ephesoft xml document populated either from extracted table
    or from PO matching
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

### HTTP Request 
`***POST*** /ephesoft/get_updated_ephesoft_doc` 

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

# /DOCUMENT_TYPE/GET_DOCUMENT_TYPES
## ***GET*** 

**Summary:** Get Document Types

### HTTP Request 
`***GET*** /document_type/get_document_types` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /DOCUMENT_TYPE/GET_DOCUMENT_TYPES_AND_SUB_TYPES
## ***GET*** 

**Summary:** Get Document Types And Sub Types

### HTTP Request 
`***GET*** /document_type/get_document_types_and_sub_types` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /DOCUMENT_TYPE/CREATE_DOCUMENT_TYPE
## ***POST*** 

**Summary:** Create Document Type

### HTTP Request 
`***POST*** /document_type/create_document_type` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TYPE/DELETE_DOCUMENT_TYPE/{ID}
## ***DELETE*** 

**Summary:** Delete Document Type

### HTTP Request 
`***DELETE*** /document_type/delete_document_type/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TYPE/GET_SUB_DOCUMENT_TYPES
## ***GET*** 

**Summary:** Get Sub Document Types

### HTTP Request 
`***GET*** /document_type/get_sub_document_types` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type_key | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TYPE/CREATE_SUB_DOCUMENT_TYPE
## ***POST*** 

**Summary:** Create Sub Document Type

### HTTP Request 
`***POST*** /document_type/create_sub_document_type` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TYPE/DELETE_SUB_DOCUMENT_TYPE/{ID}
## ***DELETE*** 

**Summary:** Delete Sub Document Type

### HTTP Request 
`***DELETE*** /document_type/delete_sub_document_type/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TYPE/ACTIVATE_DEACTIVATE_DOCUMENT_TYPE
## ***POST*** 

**Summary:** Activate Deactivate Document Type

### HTTP Request 
`***POST*** /document_type/activate_deactivate_document_type` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TYPE/GET_DOCUMENT_FIELD_GROUPS
## ***GET*** 

**Summary:** Get Document Field Groups

### HTTP Request 
`***GET*** /document_type/get_document_field_groups` 

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

# /DOCUMENT_TYPE/CREATE_DOCUMENT_FIELD_GROUP
## ***POST*** 

**Summary:** Create Document Field Group

### HTTP Request 
`***POST*** /document_type/create_document_field_group` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TYPE/DELETE_DOCUMENT_FIELD_GROUP/{ID}
## ***DELETE*** 

**Summary:** Delete Document Field Group

### HTTP Request 
`***DELETE*** /document_type/delete_document_field_group/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TYPE/CREATE_DOCUMENT_FIELD
## ***POST*** 

**Summary:** Create Document Field

### HTTP Request 
`***POST*** /document_type/create_document_field` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TYPE/DELETE_DOCUMENT_FIELD/{ID}
## ***DELETE*** 

**Summary:** Delete Document Field

### HTTP Request 
`***DELETE*** /document_type/delete_document_field/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TABLE/GET_ALL_DOCUMENT_TABLES
## ***GET*** 

**Summary:** Get Document Types

### HTTP Request 
`***GET*** /document_table/get_all_document_tables` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /DOCUMENT_TABLE/GET_DOCUMENT_TABLES
## ***GET*** 

**Summary:** Get Document Types

### HTTP Request 
`***GET*** /document_table/get_document_tables` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TABLE/GET_DOCUMENT_TABLES_WITH_COLUMNS
## ***GET*** 

**Summary:** Get Document Tables With Columns

### HTTP Request 
`***GET*** /document_table/get_document_tables_with_columns` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_type | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TABLE/CREATE_DOCUMENT_TABLE
## ***POST*** 

**Summary:** Create Document Table

### HTTP Request 
`***POST*** /document_table/create_document_table` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TABLE/DELETE_DOCUMENT_TABLE/{ID}
## ***DELETE*** 

**Summary:** Delete Document Table

### HTTP Request 
`***DELETE*** /document_table/delete_document_table/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TABLE/GET_DOCUMENT_TABLE_COLUMNS
## ***GET*** 

**Summary:** Get Document Table Columns

### HTTP Request 
`***GET*** /document_table/get_document_table_columns` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| table_name | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TABLE/CREATE_DOCUMENT_TABLE_COLUMN
## ***POST*** 

**Summary:** Create Document Table Column

### HTTP Request 
`***POST*** /document_table/create_document_table_column` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TABLE/DELETE_DOCUMENT_TABLE_COLUMN/{ID}
## ***DELETE*** 

**Summary:** Delete Document Table Column

### HTTP Request 
`***DELETE*** /document_table/delete_document_table_column/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TABLE/UPDATE_DOCUMENT_TABLE_COLUMN
## ***POST*** 

**Summary:** Update Document Table Column

### HTTP Request 
`***POST*** /document_table/update_document_table_column` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DATA_VAULT/CREATE_RECORD
## ***POST*** 

**Summary:** Create Document Type

### HTTP Request 
`***POST*** /data_vault/create_record` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /AUTO_TEST/ADD_UPDATE_DOCUMENT
## ***POST*** 

**Summary:** Add Update Document

### HTTP Request 
`***POST*** /auto_test/add_update_document` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /AUTO_TEST/REMOVE_DOCUMENT
## ***DELETE*** 

**Summary:** Remove Document

### HTTP Request 
`***DELETE*** /auto_test/remove_document` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /AUTO_TEST/GET_DOCUMENT_DATA
## ***GET*** 

**Summary:** Get Document Data

### HTTP Request 
`***GET*** /auto_test/get_document_data` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| doc_id | query |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /AUTO_TEST/AUTO_PROCESS_DOCUMENTS
## ***POST*** 

**Summary:** Auto Process Documents

### HTTP Request 
`***POST*** /auto_test/auto_process_documents` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /REGEX_AND_PATTERNS/RE/IS_VALID
## ***POST*** 

**Summary:** Is Re Valid

### HTTP Request 
`***POST*** /regex_and_patterns/re/is_valid` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /REGEX_AND_PATTERNS/REGEX/IS_VALID
## ***POST*** 

**Summary:** Is Regex Valid

### HTTP Request 
`***POST*** /regex_and_patterns/regex/is_valid` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /REGEX_AND_PATTERNS/RE/VALIDATE_PATTERNS
## ***POST*** 

**Summary:** Validate Re Patterns

### HTTP Request 
`***POST*** /regex_and_patterns/re/validate_patterns` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /REGEX_AND_PATTERNS/REGEX/VALIDATE_PATTERNS
## ***POST*** 

**Summary:** Validate Regex Patterns

### HTTP Request 
`***POST*** /regex_and_patterns/regex/validate_patterns` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /FELLOWKV/GET_DATA/{URL}
## ***GET*** 

**Summary:** Get Data

### HTTP Request 
`***GET*** /fellowkv/get_data/{url}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| url | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /FELLOWKV/POST_DATA/{URL}
## ***POST*** 

**Summary:** Post Data

### HTTP Request 
`***POST*** /fellowkv/post_data/{url}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| url | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /FELLOWKV/POST_ASAD_DATA/{URL}
## ***POST*** 

**Summary:** Post Asad Data

### HTTP Request 
`***POST*** /fellowkv/post_asad_data/{url}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| url | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DB/EXPORT
## ***POST*** 

**Summary:** Db Export

### HTTP Request 
`***POST*** /db/export` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| as_file | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DB/IMPORT
## ***POST*** 

**Summary:** Db Import

### HTTP Request 
`***POST*** /db/import` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DB/FILE_IMPORT/
## ***POST*** 

**Summary:** Db File Import

### HTTP Request 
`***POST*** /db/file_import/` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TRAINER/ADD_SAMPLE_DOCUMENT
## ***POST*** 

**Summary:** Add Sample Document

### HTTP Request 
`***POST*** /document_trainer/add_sample_document` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TRAINER/ADD_ONE_SAMPLE_DOCUMENT
## ***POST*** 

**Summary:** Add One Sample Document

### HTTP Request 
`***POST*** /document_trainer/add_one_sample_document` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TRAINER/RETRAIN_MODEL
## ***POST*** 

**Summary:** Retrain Model

### HTTP Request 
`***POST*** /document_trainer/retrain_model` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /DOCUMENT_TRAINER/RETRAIN_ALL_MODELS
## ***POST*** 

**Summary:** Retrain Model

### HTTP Request 
`***POST*** /document_trainer/retrain_all_models` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /DOCUMENT_TRAINER/TEST_CLASSIFICATION
## ***POST*** 

**Summary:** Test Classification

### HTTP Request 
`***POST*** /document_trainer/test_classification` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TRAINER/GET_SAMPLE_DOCUMENTS
## ***POST*** 

**Summary:** Get Sample Documents

### HTTP Request 
`***POST*** /document_trainer/get_sample_documents` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TRAINER/DELETE_SAMPLE_DOCUMENT/{ID}
## ***DELETE*** 

**Summary:** Delete Document Field

### HTTP Request 
`***DELETE*** /document_trainer/delete_sample_document/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TRAINER/CREATE_TRAINING_FILES
## ***POST*** 

**Summary:** Create Training Files

### HTTP Request 
`***POST*** /document_trainer/create_training_files` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_TRAINER/TEST_MODEL
## ***POST*** 

**Summary:** Test Model

### HTTP Request 
`***POST*** /document_trainer/test_model` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /TRIGGERS/GET_TRIGGERS
## ***GET*** 

**Summary:** Get Triggers

### HTTP Request 
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
| 422 | Validation Error |

# /DOCUMENT_STATUS_ALERT/GET_DOCUMENT_STATUS_ALERT_STATUSES
## ***GET*** 

**Summary:** Get Document Status Alert Statuses

### HTTP Request 
`***GET*** /document_status_alert/get_document_status_alert_statuses` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /DOCUMENT_STATUS_ALERT/GET_DOCUMENT_STATUS_ALERTS
## ***GET*** 

**Summary:** Get Document Status Alerts

### HTTP Request 
`***GET*** /document_status_alert/get_document_status_alerts` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /DOCUMENT_STATUS_ALERT/CREATE_DOCUMENT_STATUS_ALERT
## ***POST*** 

**Summary:** Create Group

### HTTP Request 
`***POST*** /document_status_alert/create_document_status_alert` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_STATUS_ALERT/UPDATE_DOCUMENT_STATUS_ALERT
## ***POST*** 

**Summary:** Update Document Status Alert

### HTTP Request 
`***POST*** /document_status_alert/update_document_status_alert` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /DOCUMENT_STATUS_ALERT/REMOVE_DOCUMENT_STATUS_ALERT
## ***DELETE*** 

**Summary:** Remove Document Status Alert

### HTTP Request 
`***DELETE*** /document_status_alert/remove_document_status_alert` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CUSTOM_CLASSIFIER/TEST_CLASSIFICATION
## ***POST*** 

**Summary:** Test Classification

### HTTP Request 
`***POST*** /custom_classifier/test_classification` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CUSTOM_CLASSIFIER/TRAIN_DOCUMENT
## ***POST*** 

**Summary:** Train Document

### HTTP Request 
`***POST*** /custom_classifier/train_document` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CUSTOM_MODEL/LIST
## ***GET*** 

**Summary:** Get List

### HTTP Request 
`***GET*** /custom_model/list` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /CUSTOM_MODEL/CREATE
## ***POST*** 

**Summary:** Create Layout Templates

### HTTP Request 
`***POST*** /custom_model/create` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CUSTOM_MODEL/{ID}
## ***GET*** 

**Summary:** Get Model

### HTTP Request 
`***GET*** /custom_model/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## ***PUT*** 

**Summary:** Update Model

### HTTP Request 
`***PUT*** /custom_model/{id}` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## ***DELETE*** 

**Summary:** Delete Model

### HTTP Request 
`***DELETE*** /custom_model/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CUSTOM_MODEL_LABEL/LIST
## ***GET*** 

**Summary:** Get List

### HTTP Request 
`***GET*** /custom_model_label/list` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| model_name | query |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /CUSTOM_MODEL_LABEL/CREATE
## ***POST*** 

**Summary:** Create Layout Templates

### HTTP Request 
`***POST*** /custom_model_label/create` 

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

# /CUSTOM_MODEL_LABEL/{ID}
## ***GET*** 

**Summary:** Get Model

### HTTP Request 
`***GET*** /custom_model_label/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

## ***PUT*** 

**Summary:** Update Model

### HTTP Request 
`***PUT*** /custom_model_label/{id}` 

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

## ***DELETE*** 

**Summary:** Delete Model

### HTTP Request 
`***DELETE*** /custom_model_label/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /OCR_CONFIGURATIONS/GET_OCR_SERVER_TYPES
## ***GET*** 

**Summary:** Get Ocr Server Types

### HTTP Request 
`***GET*** /ocr_configurations/get_ocr_server_types` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /OCR_CONFIGURATIONS/UPDATE_OCR_CONFIGURATION
## ***POST*** 

**Summary:** Update Ocr Configuration

### HTTP Request 
`***POST*** /ocr_configurations/update_ocr_configuration` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /OCR_CONFIGURATIONS/GET_OCR_CONFIGURATION
## ***GET*** 

**Summary:** Get Ocr Configuration

### HTTP Request 
`***GET*** /ocr_configurations/get_ocr_configuration` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /OCR_CONFIGURATIONS/UPDATE_ETEXT_ENABLE_STATUS
## ***POST*** 

**Summary:** Update Etext Enable Status

### HTTP Request 
`***POST*** /ocr_configurations/update_etext_enable_status` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |
| 422 | Validation Error |

# /OCR_CONFIGURATIONS/IS_ETEXT_ENABLED
## ***GET*** 

**Summary:** Is Etext Enabled

### HTTP Request 
`***GET*** /ocr_configurations/is_etext_enabled` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /API/HEALTH/
## ***GET*** 

**Summary:** Check All

### HTTP Request 
`***GET*** /api/health/` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |

# /API/HEALTH/SERVICES
## ***GET*** 

**Summary:** Services

### HTTP Request 
`***GET*** /api/health/services` 

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



