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
}

```


```shell
curl -X 'POST' \
  'https://dev.api.polydocs.io/classifier_v2/classify_document' \
  -H 'accept: application/json' \
  -H 'X-API-KEY: meowmeowmeow' \
  -H 'Content-Type: multipart/form-data' \
  -F 'file=@B_47444625_PDF_D52FGM54.PDF;type=application/pdf'
```


# /HEALTHZ
## ***GET*** 

**Summary:** Healthz

### HTTP Request 
`***GET*** /healthz` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Successful Response |


