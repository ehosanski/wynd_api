---
layout: default
title: Documentation 👨‍💻
permalink: /documentation
---

----------

<!-- TOC depthFrom:1 depthTo:1 withLinks:1 updateOnSave:1 orderedList:0 -->
# Sommaire

- [ENTITY](#entity)
- [CATEGORY](#category)
- [PRODUCT](#product)
- [CUSTOMER](#customer)
- [USER](#user)
- [MENU](#menu)
- [SIPS](#sips)
- [ORDER](#order)
- [BASKET](#basket)
- [WYND_TERMINAL](#wyndterminal)
- [TAG](#tag)
- [FACEBOOK CONNECT (Work In Progress)](#facebook-connect-work-in-progress)
- [EVENT GLOSSARY](#event-glossary)

-----------


# Basics

Our API is REST based.
* It make use of standard HTTP verbs like GET, POST, PUT and PATCH
* Uses standard HTTP error responses to describe errors
* Authentication and authorization are based on the OAuth 2.0 standard
* All communication with our servers must be over SSL (https://)
* POST data should be encoded as standard application/x-www-form-urlencoded
* All our responses are in JSON format
* Accessible using apidemo.wynd.eu as domain

[*Retour en haut*](#sommaire)


# Responses

The Stuart API uses HTTP status codes to indicate the status of your requests. This includes successful and unsuccessful responses.Responses will also include JSON formatted details for further details.
* `200` - OK: Everything went as planned.
* `201` - Created.
* `204` - OK but no content
* `304` - Not Modified: Resource hasn't been updated since the date provided.
* `400` - Bad Request: Something went wrong with your request, most likey a missing argument or parameter.
* `401` - Unauthorized: Authentication was incorrect.
* `403` - Forbidden: You don't have the necessary permissions for the resource.
* `404` - Not Found
* `422` - We coudln't process your request. Review the parameters
* `500` - Internal Server Error: We had a problem processing the request.
* `503` - Service Unavailable: Try again later.

[*Retour en haut*](#sommaire)

# ENTITY


The “ENTITY” account indistinctly for the point of sale (relate to the eshop), the master entity (relate to the marketplace, encompassing several eshops)

## `SPEC_TECH_ENTITY_001_GET` - Select available site
This route let you select all entities existing on the marketplace (no filters)

### GET  /api/entities.{_format}

* DB storage : `llx_entity`

* JSON template :

```json
{
  "data": [
    {
      "id": 4,
      "wynd_id": "",
      "external_id": null,
      "name": "",
      "label": "PAUL",
      "description": "",
      "town": null,
      "zipcode": null,
      "address": null,
      "address_additional": null,
      "phone": null,
      "mail": null,
      "website": null,
      "photo": null,
      "logo": null,
      "capital": null,
      "code_rcs": null,
      "code_siret": null,
      "code_siren": null,
      "code_ape": null,
      "vat_number": null,
      "legal_form": null,
      "latitude": null,
      "longitude": null,
      "created_at": "2016-12-08T17:06:10+0100",
      "updated_at": "2016-12-08T17:07:04+0100",
      "is_visible": true,
      "is_active": true,
      "created_by": 1
    },
    {
      "id": 3,
      "wynd_id": "",
      "external_id": null,
      "name": "",
      "label": "PAUL Gare du Nord - RER",
      "description": "",
      "town": null,
      "zipcode": null,
      "address": null,
      "address_additional": null,
      "phone": null,
      "mail": null,
      "website": null,
      "photo": null,
      "logo": null,
      "capital": null,
      "code_rcs": null,
      "code_siret": null,
      "code_siren": null,
      "code_ape": null,
      "vat_number": null,
      "legal_form": null,
      "latitude": null,
      "longitude": null,
      "created_at": "2016-06-28T15:21:45+0200",
      "updated_at": "2016-09-01T10:10:48+0200",
      "is_visible": true,
      "is_active": true,
      "created_by": 1
    },
    {
      "id": 1,
      "wynd_id": "",
      "external_id": 292,
      "name": "",
      "label": "Entité maître",
      "description": "Entité maître, ne peut pas être supprimée",
      "town": null,
      "zipcode": null,
      "address": null,
      "address_additional": null,
      "phone": null,
      "mail": null,
      "website": null,
      "photo": null,
      "logo": null,
      "capital": null,
      "code_rcs": null,
      "code_siret": null,
      "code_siren": null,
      "code_ape": null,
      "vat_number": null,
      "legal_form": null,
      "latitude": null,
      "longitude": null,
      "created_at": "2015-11-22T21:56:02+0100",
      "updated_at": "2016-09-01T08:30:09+0200",
      "is_visible": true,
      "is_active": true,
      "created_by": 1
    },
    {
      "id": 2,
      "wynd_id": "",
      "external_id": null,
      "name": "",
      "label": "PAUL Gare du Nord - Parvis",
      "description": "",
      "town": null,
      "zipcode": null,
      "address": null,
      "address_additional": null,
      "phone": null,
      "mail": null,
      "website": null,
      "photo": null,
      "logo": null,
      "capital": null,
      "code_rcs": null,
      "code_siret": null,
      "code_siren": null,
      "code_ape": null,
      "vat_number": null,
      "legal_form": null,
      "latitude": null,
      "longitude": null,
      "created_at": "2016-03-31T15:43:43+0200",
      "updated_at": "2016-09-01T10:10:42+0200",
      "is_visible": true,
      "is_active": true,
      "created_by": 1
    }
  ]
}
```



## `SPEC_TECH_ENTITY_002_GET` - Select / display a site

### GET  /api/entities/{id}.{_format}

This route let you select a site with its technical ID and retrieve the following information :


**API attribute name**|**DB + Attribute Name**|**Description**
:-----:|:-----:|:-----:
openTimes|`llx_entity`|opening time
is\_open| |The site is open
open| |
schedule|`llx_takeaway_hours_plan`|Slots available for delivery
today_slots| |Slot of the day available for taking orders
next_slot| |Next available slot for ordering
distance| |Calculated field
latlong| |calculated field (not used)
id| |Entity ID
wynd_id| |not used
external_id| |
name| |not used
label| |Entity name
description| |Entity description / point of sale
tags|`llx_tags_entities`|Tags related to the entity




* DB storage : `llx_entity`

```json
{
  "data": {
    "openTimes": {
      "open": null,
      "close": null,
      "is_open": false
    },
    "today_slots": {
      "slots": []
    },
    "next_slot": false,
    "distance": null,
    "latlong": null,
    "id": 1,
    "wynd_id": "",
    "external_id": 292,
    "name": "",
    "label": "Entité maître",
    "description": "Entité maître, ne peut pas être supprimée",
    "town": null,
    "zipcode": null,
    "address": null,
    "address_additional": null,
    "phone": null,
    "mail": null,
    "website": null,
    "photo": null,
    "logo": null,
    "capital": null,
    "code_rcs": null,
    "code_siret": null,
    "code_siren": null,
    "code_ape": null,
    "vat_number": null,
    "legal_form": null,
    "latitude": null,
    "longitude": null,
    "created_at": "2015-11-22T21:56:02+0100",
    "updated_at": "2016-09-01T08:30:09+0200",
    "is_visible": true,
    "is_active": true,
    "created_by": 1,
    "extrafields": {
      "id": 20,
      "phone": null,
      "latitude": null,
      "longitude": null,
      "monday_open_time": null,
      "monday_close_time": null,
      "tuesday_open_time": null,
      "tuesday_close_time": null,
      "wednesday_open_time": null,
      "wednesday_close_time": null,
      "thursday_open_time": null,
      "thursday_close_time": null,
      "friday_open_time": null,
      "friday_close_time": null,
      "saturday_open_time": null,
      "saturday_close_time": null,
      "sunday_open_time": null,
      "sunday_close_time": null,
      "slogan": null,
      "diet": null,
      "parent": null,
      "updated_at": "2016-12-16T11:52:51+0100",
      "id_restaurant": "6292",
      "pubnub_channel": null,
      "wyndt_api_url": null,
      "merchant_id": ""
    },
    "consts": [
      {
        "name": "MAIN_INFO_SOCIETE_LOGO_MINI",
        "value": "logo-quick-1_mini.png"
      },
      {
        "name": "MAIN_INFO_SOCIETE_LOGO",
        "value": "logo-quick-1.png"
      },
      {
        "name": "MAIN_INFO_SOCIETE_LOGO_SMALL",
        "value": "logo-quick-1_small.png"
      },
      {
        "name": "MAIN_INFO_SOCIETE_COUNTRY",
        "value": "1:FR:France"
      },
      {
        "name": "MAIN_INFO_SOCIETE_NOM",
        "value": "Elior WIIISH"
      },
      {
        "name": "MAIN_INFO_SOCIETE_ADDRESS",
        "value": "Gare du nord"
      },
      {
        "name": "MAIN_INFO_SOCIETE_TOWN",
        "value": "Paris"
      },
      {
        "name": "MAIN_INFO_SOCIETE_ZIP",
        "value": "75009"
      },
      {
        "name": "MAIN_INFO_SOCIETE_STATE",
        "value": "0"
      },
      {
        "name": "MAIN_MONNAIE",
        "value": "EUR"
      },
      {
        "name": "MAIN_INFO_SOCIETE_WEB",
        "value": "elior.com"
      },
      {
        "name": "MAIN_INFO_SOCIETE_FORME_JURIDIQUE",
        "value": "0"
      }
    ],
    "schedule": [],
    "tags": [
  	{
    	  "id": 4,
    	  "label": "ligne_4",
    	  "type": {
      	    "id": 2,
      	    "label": "location"
    	},
    	  "entities": [
      	    null
    	  ]
  	},
  	{
    	  "id": 5,
    	  "label": "ligne_5",
    	  "type": {
      	    "id": 2,
      	    "label": "location"
    	  },
    	  "entities": [
      	     null
    	  ]
  	}
    ]
  }
}
```

## `SPEC_TECH_ENTITY_006_GET` - Select / display an entity and sister entity
This route lets you select an entity via its technical ID and return its sister entities.

### GET  /api/entities/{id}/children

### GET /api/entities?parent={parentId}

* DB storage : `llx_entity`

## `SPEC_TECH_ENTITY_003_GET` - Select entity using GPS Position
This route allows for entity selection using its gps coordinates.

### GET /api/entities/search/geoloc

* DB storage : `llx_entity`

## `SPEC_TECH_ENTITY_004_GET` - Select slot for coming days

This route allows for available slots in the coming N days

### GET /api/entity/{entityId}/next-days-slots/{length}
* Table Dolibarr : `llx_entity`

### GET  /api/entity/{entityId}/next-days-slots/{length}.{_format}

entityID : Entity ID
lenght : number of days (5 by default)
remaining_orders : numbers of orders remaining on the selected slot

```json
{
  "2016-12-20T16:19:26+01:00": {
    "slots": [
      {
        "day": "Mardi",
        "is_selectable": false,
        "remaining_orders": 0,
        "start": {
          "timestamp": 1482220800,
          "time": "09:00",
          "full": "2016-12-20 09:00:00"
        },
        "end": {
          "timestamp": 1482222600,
          "time": "09:30",
          "full": "2016-12-20 09:30:00"
        }
      },
      {
        "day": "Mardi",
        "is_selectable": false,
        "remaining_orders": 1,
        "start": {
          "timestamp": 1482222600,
          "time": "09:30",
          "full": "2016-12-20 09:30:00"
        },
        "end": {
          "timestamp": 1482224400,
          "time": "10:00",
          "full": "2016-12-20 10:00:00"
        }
      },
      {
        "day": "Mardi",
        "is_selectable": false,
        "remaining_orders": 1,
        "start": {
          "timestamp": 1482224400,
          "time": "10:00",
          "full": "2016-12-20 10:00:00"
        },
        "end": {
          "timestamp": 1482226200,
          "time": "10:30",
          "full": "2016-12-20 10:30:00"
        }
      },
      {
        "day": "Mardi",
        "is_selectable": false,
        "remaining_orders": 0,
        "start": {
          "timestamp": 1482226200,
          "time": "10:30",
          "full": "2016-12-20 10:30:00"
        },
        "end": {
          "timestamp": 1482228000,
          "time": "11:00",
          "full": "2016-12-20 11:00:00"
        }
      },
      {
        "day": "Mardi",
        "is_selectable": false,
        "remaining_orders": 1,
        "start": {
          "timestamp": 1482228000,
          "time": "11:00",
          "full": "2016-12-20 11:00:00"
        },
        "end": {
          "timestamp": 1482229800,
          "time": "11:30",
          "full": "2016-12-20 11:30:00"
        }
      },
      {
        "day": "Mardi",
        "is_selectable": false,
        "remaining_orders": 0,
        "start": {
          "timestamp": 1482229800,
          "time": "11:30",
          "full": "2016-12-20 11:30:00"
        },
        "end": {
          "timestamp": 1482231600,
          "time": "12:00",
          "full": "2016-12-20 12:00:00"
        }
      },
      {
        "day": "Mardi",
        "is_selectable": false,
        "remaining_orders": 0,
        "start": {
          "timestamp": 1482231600,
          "time": "12:00",
          "full": "2016-12-20 12:00:00"
        },
        "end": {
          "timestamp": 1482233400,
          "time": "12:30",
          "full": "2016-12-20 12:30:00"
        }
      },
      {
        "day": "Mardi",
        "is_selectable": false,
        "remaining_orders": 1,
        "start": {
          "timestamp": 1482233400,
          "time": "12:30",
          "full": "2016-12-20 12:30:00"
        },
        "end": {
          "timestamp": 1482235200,
          "time": "13:00",
          "full": "2016-12-20 13:00:00"
        }
      }

```

## `SPEC_TECH_ENTITY_005_GET` - Select slot on a given day
This route allows for selecting available slots for the day

### GET /api/entity/{entityId}/one-day-slots/{day} ou day = YYYY-mm-dd

* DB storage: `llx_entity`

### GET  /api/entity/{entityId}/one-day-slots/{day}.{_format}

```json
{
  "slots": [
    {
      "day": "Mardi",
      "is_selectable": false,
      "remaining_orders": 0,
      "start": {
        "timestamp": 1482220800,
        "time": "09:00",
        "full": "2016-12-20 09:00:00"
      },
      "end": {
        "timestamp": 1482222600,
        "time": "09:30",
        "full": "2016-12-20 09:30:00"
      }
    },
    {
      "day": "Mardi",
      "is_selectable": false,
      "remaining_orders": 1,
      "start": {
        "timestamp": 1482222600,
        "time": "09:30",
        "full": "2016-12-20 09:30:00"
      },
      "end": {
        "timestamp": 1482224400,
        "time": "10:00",
        "full": "2016-12-20 10:00:00"
      }
    },
    {
      "day": "Mardi",
      "is_selectable": false,
      "remaining_orders": 1,
      "start": {
        "timestamp": 1482224400,
        "time": "10:00",
        "full": "2016-12-20 10:00:00"
      },
      "end": {
        "timestamp": 1482226200,
        "time": "10:30",
        "full": "2016-12-20 10:30:00"
      }
    },
    {
      "day": "Mardi",
      "is_selectable": false,
      "remaining_orders": 0,
      "start": {
        "timestamp": 1482226200,
        "time": "10:30",
        "full": "2016-12-20 10:30:00"
      },
      "end": {
        "timestamp": 1482228000,
        "time": "11:00",
        "full": "2016-12-20 11:00:00"
      }
    },
    {
      "day": "Mardi",
      "is_selectable": false,
      "remaining_orders": 1,
      "start": {
        "timestamp": 1482228000,
        "time": "11:00",
        "full": "2016-12-20 11:00:00"
      },
      "end": {
        "timestamp": 1482229800,
        "time": "11:30",
        "full": "2016-12-20 11:30:00"
      }
    }
]
```

[*Retour en haut*](#sommaire)


# CATEGORY

## `SPEC_TECH_CATEGORY_001_GET` - Select categories for an Entity

### GET  /api/{entity}/{channel}/categories.{_format}
This route retrieves existing categories of an entity for a given Channel

#### Output :
Example: Get /api/1/website/categories

```json
[
   {
     "position": false,
     "height": false,
     "width": false,
     "background": false,
     "icon": false,
     "color": false,
     "isDefault": false,
     "id": 2,
     "label": "Boissons et Cave à vins",
     "description": null
   },
   {
     "position": false,
     "height": false,
     "width": false,
     "background": false,
     "icon": false,
     "color": false,
     "isDefault": false,
     "id": 3,
     "label": "Colas et boissons gazeuses",
     "description": null
   },
   {
     "position": false,
     "height": false,
     "width": false,
     "background": false,
     "icon": false,
     "color": false,
     "isDefault": false,
     "id": 4,
     "label": "Sodas",
     "description": null
   }
]
```

* DB Storage: `llx_categorie`

## `SPEC_TECH_CATEGORY_001_GET` - Select categories for an entity (hierachical tree view)
This route retrieves existing categories of an entity for a given Channel. Results as structure Tree view.

entity : entity id
channel : distribution channel (website / pos)

### GET  /api/{entity}/{channel}/categories/tree.{_format}

```json
{
   "id": 1,
   "title": "website",
   "parent": false,
   "external_id": null,
   "count_products": 0,
   "product_limit": null,
   "image": null,
   "depth": 0,
   "children": [
     {
       "id": 425,
       "title": "Fruits et Légumes",
       "parent": 1,
       "external_id": "R01",
       "count_products": 144,
       "product_limit": null,
       "image": "https://marketplace.test.local:8890/img/categories/R01.jpg",
       "depth": 1,
       "children": []
     },
     {
       "id": 409,
       "title": "Viandes et Poissons",
       "parent": 1,
       "external_id": "R02",
       "count_products": 55,
       "product_limit": null,
       "image": "https://marketplace.test.local:8890/img/categories/R02.jpg",
       "depth": 1,
       "children": []
     },
     {
       "id": 442,
       "title": "Pains et Pâtisserie",
       "parent": 1,
       "external_id": "R03",
       "count_products": 11,
       "product_limit": null,
       "image": "https://marketplace.test.local:8890/img/categories/R03.jpg",
       "depth": 1,
       "children": []
     },
     {
       "id": 367,
       "title": "Crémerie",
       "parent": 1,
       "external_id": "R04",
       "count_products": 299,
       "product_limit": null,
       "image": "https://marketplace.test.local:8890/img/categories/R04.jpg",
       "depth": 1,
       "children": []
     },
     {
       "id": 339,
       "title": "Charcuterie Traiteur",
       "parent": 1,
       "external_id": "R05",
       "count_products": 217,
       "product_limit": null,
       "image": "https://marketplace.test.local:8890/img/categories/R05.jpg",
       "depth": 1,
       "children": []
     },
     {
       "id": 263,
       "title": "Epicerie Salée",
       "parent": 1,
       "external_id": "R07",
       "count_products": 359,
       "product_limit": null,
       "image": "https://marketplace.test.local:8890/img/categories/R07.jpg",
       "depth": 1,
       "children": []
     },
     {
       "id": 328,
       "title": "Animaux",
       "parent": 1,
       "external_id": "R14",
       "count_products": 16,
       "product_limit": null,
       "image": "https://marketplace.test.local:8890/img/categories/R14.jpg",
       "depth": 1,
       "children": []
     }
   ],
   "maximum_default": 10
}
```

[*Retour en haut*](#sommaire)


# PRODUCT
The “PRODUCT” object is a product sold.

## `SPEC_TECH_PRODUCT_001_GET` - Select available product for an entity

### GET /api/{entity}/{channel}/products
* DB storage : `llx_product`

## `SPEC_TECH_PRODUCT_002_GET` - Select a product using its ID

### GET  /api/product/{id}.{_format}

* DB storage : `llx_product`


```json
{
  "externalId": 1,
  "externalRef": "Salade Paul",
  "featured": false,
  "picture": null,
  "type": "Salade",
  "categoryKvs": "3",
  "tvaTx": "3.000",
  "priceTtc": "7.00400000",
  "priceHt": "6.80000000",
  "prices": {
    "1": {
      "price_ttc": 7.004,
      "price_ht": 6.8,
      "price_per_unit": 0,
      "unit_ratio": false,
      "tva_tx": 3,
      "to_sell": true
    }
  },
  "product_origin": null,
  "extra_data_image": false,
  "extra_data_weight": 0,
  "extra_data_weight_unit": false,
  "root_category_id": false,
  "root_category_label": false,
  "category_limit": false,
  "extra_data_packaging": false,
  "extra_categories": [],
  "extra_data": [],
  "children": null,
  "id": 363,
  "ref": "SALADE_PAUL",
  "label": "Salade Paul",
  "description": "Filets de poulet, copeaux de parmesan, sauce Caesar, cro&ucirc;tons aill&eacute;s, salade, ciboulette.",
  "barcode": null,
  "tags": [
   {
    "id": 1
    "label": "petit_dejeuner"
    },

    "id": 2
    "label": "gluten_free"
    }
  ]
}
```

## `SPEC_TECH_PRODUCT_002_GET` - Select list of product for a given entity.

### GET  /api/{entity}/{channel}/products.{_format}

#### Input :
Channel : Distribution channel (website / pos)
Entity : entity ID de l’entité (point of sale)
#### Output :
Products table

```json
{
  "externalId": 1,
  "externalRef": "Salade Paul",
  "featured": false,
  "picture": null,
  "type": "Salade",
  "categoryKvs": "3",
  "tvaTx": "3.000",
  "priceTtc": "7.00400000",
  "priceHt": "6.80000000",
  "prices": {
    "1": {
      "price_ttc": 7.004,
      "price_ht": 6.8,
      "price_per_unit": 0,
      "unit_ratio": false,
      "tva_tx": 3,
      "to_sell": true
    }
  },
  "product_origin": null,
  "extra_data_image": false,
  "extra_data_weight": 0,
  "extra_data_weight_unit": false,
  "root_category_id": false,
  "root_category_label": false,
  "category_limit": false,
  "extra_data_packaging": false,
  "extra_categories": [],
  "extra_data": [],
  "children": null,
  "id": 363,
  "ref": "SALADE_PAUL",
  "label": "Salade Paul",
  "description": "Filets de poulet, copeaux de parmesan, sauce Caesar, cro&ucirc;tons aill&eacute;s, salade, ciboulette.",
  "barcode": null,
  "tags": [
   {
    "id": 1
    "label": "petit_dejeuner"
    },

    "id": 2
    "label": "gluten_free"
    }
  ]
}
```



[*Retour en haut*](#sommaire)



# CUSTOMER

The “CUSTOMER” object is a customer.

## `SPEC_TECH_CUSTOMER_001_POST` - Customer account creation

### POST  /api/customers.{_format}


# USER

The “USER” object is the user accessing the API.

## `SPEC_TECH_USER_001_PUT` - Customer Information and preferences update

### PUT /api/customer/{id}
* DB storage : `llx_user`

## `SPEC_TECH_USER_002_POST` - Authentification
This route is made for user (customer) authentification

### POST /api/user/authenticate.{_format}

* DB storage : `llx_user`

# MENU
The object “MENU” is made of products belonging to the category.

## `SPEC_TECH_MENU_001_GET` - Retrieve the list of entity menus

### GET /api/menu.{_format}

Retrieve cartes and menus.

Carte structure
The carte is structure according to the following JSON on the POS 1.4.

```json
[
  {
    "result": "string",
    "code": 0,
    "message": "string",
    "data": {
      "mainRootCategory": "string",
      "rootCategories": [
        {
          "id": 0,
          "label": "string",
          "parent": 0,
          "description": "string",
          "position": 0,
          "height": 0,
          "width": 0,
          "background": "string",
          "icon": "string",
          "color": "string",
          "is_default": 0,
          "type": "string",
          "path": "string"
        }
      ],
      "products": [
        {
          "product_id": 0,
          "ref": "string",
          "external_id": 0,
          "external_ref": "string",
          "label": "string",
          "type": "string",
          "division": "string",
          "category_kvs": "string",
          "description": "string",
          "barcode": "string",
          "priceCenter": "string"
        }
      ],
      "map": [
        {
          "id": 0,
          "label": "string",
          "parent": 0,
          "description": "string",
          "position": 0,
          "height": 0,
          "width": 0,
          "background": "string",
          "icon": "string",
          "color": "string",
          "is_default": 0,
          "type": "string",
          "path": "string",
          "sub": {}
        }
      ]
    }
  }
]
```


Contrairement à ce que le nom de la route pourrait laisser entendre, la route /api/menu permet de récupérer l'ensemble des produits et non seulement les menus.
La route /api/menu permet de récupérer :

* La liste des catégories
* La liste des produits
* La map des catégories, produits et produits fils

#### Input
Il est possible de filtrer le retour de la route /api/menu par :
Entité (entity) : numéro du point de vente
Destination (channelId) : numéro de la destination
Exemple

```Get /api/menu?entityId=1&channelId=2```


#### Output
Le retour de la route /api/menu est structurée ainsi :
MainRootCategory : l'id de la catégorie racine
rootCategories : la liste "à plat" des catégories
products : la liste "à plat" des produits
map : les liens entre catégories & produits et produits & produits fils
Exemple

```json
{
  "result": "success",
  "code": 2001,
  "message": "Pos Menu",
  "data": {
    "mainRootCategory": "1_103005370", // ID de la catégorie qui sert de point d'entrée dans l'arborescence
    "rootCategories": { // Liste des catégories primaires (Enfants direct de la categorie principale
       "10_103005374": { // Ordre_ID-Categorie
        "id": "103005374", // ID de la catégorie
        "label": { // Label center, liste des libellés (Default + locales)
          "default": "Desserts"
        },
        "parent": "103005370", // Categorie parente de la catégorie
        "description": null, // Description de la catégorie
        "position": "10", // Ordre d'affichage de la catégorie
        "height": "1", // Hauteur du bouton de la catégorie
        "width": "1", // Largeur du bouton de la catégorie
        "background": "", // Image de fond de la catégorie
        "icon": "", // Icone du bouton de la catégorie
        "color": "#999", // Couleur du bouton de la catégorie
        "is_default": "0", // Booléen de catégorie par défaut
        "type": "category", // Type de l'élément
        "path": "1_103005370,10_103005374" // Chemin pour accèder à cette catégorie dans la map
      }
    },
    "products": { // Référentiel produits
      "1": {
        "id": "1", // ID du produit
        "ref": "MEGA_BBQ_BC", // Référence (Unique) du produit)
        "external_id": "1133414", // ID côté "client de la solution"
        "external_ref": "PCXD", // REF côté "client de la solution"
        "label": { // Label center, liste des libellés (Default + locales)
          "default": "Mega BBQ BC",
          "be_FR": "Mega BBQ BC",
          "be_NL": "Mega BBQ BC"
        },
        "type": "product", // Type de l'élément
        "division": "30", // Division du produit (Famille)
        "category_kvs": "5", // Catégorie "cuisine" du produit
        "description": "", // Description du produit
        "barcode": null, // Code-Barre du produit
        "priceCenter": { // Price Center du produit
          "default": { // Prix de base (import)
            "price": 5.75, // Prix TTC
            "vatRate": 12 // Taux de tva
          },
          "takeaway": { // Liste des prix conditionés par destination
            "default": { // Prix par défaut de la destination
              "price": 0, // Prix TTC
              "vatRate": 6, // taux de tva
              "isExclusive": false, // Booléen de condition exclusive
              "isAbsolute": false, // Booléen de condition absolue
              "level": 1 // Niveau de prix
            },
            "prices": [] // Liste des prix conditions de la destination
          }
        }
      }
    },
    "map": { // Arborescence de la carte (Reprise des structures de chaques éléments + Imbrication)
      "1_103005370": {
        "id": "103005370",
        "label": {
          "default": "LUX POS"
        },
        "parent": "0",
        "description": null,
        "position": "1",
        "height": "1",
        "width": "1",
        "background": "",
        "icon": "",
        "color": "#999",
        "is_default": "0",
        "type": "category",
        "sub": {
            // Toute l'aborescence de la carte (Catégorie, produits, choix, composition)
        }
      }
    }
  }
}
```

----
> Gestion des produits fils

On appelle produit fils un produit lié à un autre par un lien de parenté. Ce lien sert à définir une notion d'appartenance, de composition, de choix, ...

Ex :
Le choix de l'entrée d'un menu est un produit fils du menu Entrée Plat

* Le sandwich BigMac est un produit fils du menu Big Mac
* Les ingrédients d'un bagel sont des produits fils de ce Big Mac

Il existe plusieurs types de produits fils :

* Produit choix
* Produit composition
* Produit ingrédient

Exemples
#### Menu

* **Menu Entrée Plat** Produit Menu
	* **Choix d'entrées** Produit Choix 1
		* **Entrée 1** Produit Composition 1a
		* **Entrée 2** Produit Composition 1b
		* **Entrée 3** Produit Composition 1c
	* **Choix de plats** Produit Choix 2
		* **Plat 1 Produit** Composition 2a
		* **Plat 2 Produit** Composition 2b
		* **Plat 3 Produit** Composition 2c

#### Produit composé

* **Frite Produit** composé
	* **Choix de sauce** Produit Choix 1
		* **Sauce 1 Produit** Composition 1a
		* **Sauce 2 Produit** Composition 1b
		* **Sauce 3 Produit** Composition 1c

La différence entre un produit Menu et un produit Composé réside dans la valorisation de ses éléments :

* les produits fils d'un produit Menu hérite de la valorisation du produit Menu
i.e. dans le cas d'un menu Entrée Plat, la valeur du menu est reventilée sur le produit Entrée et Plat choisis. La valorisation du produit menu est nulle.*
les produits fils d'un produit Composé n'hérite pas de la valorisation du produit Composé
* i.e. dans le cas d'une Frite avec des sauces, le produit frite garde sa valorisation et les produits sauces ne sont pas valorisés*
Produit ingrédients

Dans le cas où les ingrédients sont obligatoires et aucun choix n'est possible, les produits ingrédients ont directement le produit comme produit parent.

* **Bagel** Produit
	* **Pain** Produit ingrédient 1
	* **Cream cheese** Produit ingrédient 2
	* **Saumon Produit** ingrédient 3

Dans le cas où les ingrédients ne sont pas tous obligatoires et/ou qu'un choix est possible, les produits ingrédients ont un produit Choix comme parent. Le produit Choix a lui le produit en comme parent.

* **Bagel** Produit Menu
	* **Choix d'ingrédients** Produit Choix 1
		* **Pain Produit** ingrédient 1a
		* **Cream cheese** Produit ingrédient 1b
		* **Saumon Produit** ingrédient 1c

Le lien de parenté entre un produit parent et un produit fils peut porter un certain nombre d'information :

* le nombre minimum et maximum dans le cas d'un produit Choix
* le caractère "en supplément" pour un produit composition ou ingrédient
* le caractère "par défaut" pour un produit composition ou ingrédient

[*Retour en haut*](#sommaire)


---

# SIPS
/ONLY RELEVANT FOR SIPS-ATOS PAYMENT /

Les routes SIPS sont utilisées dans le cas d’un paiement via ATOS Worldline.

## `SPEC_TECH_SIPS_001_POST` - Demande code paiement

### POST /api/sips/request-payment-code/{orderId}

Description : Cette route permet d’initier le parcours de paiement sur Atos et ouvre la page de paiement depuis les serveur Atos pour permettre la demande d’autorisation de paiement.

#### Input : Order ID => correspond à l’identifiant de la commande qui est généré par la route /api/orders

#### Output :
Renvoie un JSON contenant l’URL d’envoie du formulaire (exemple ci-dessous) et une chaîne de caractère qui correspond à une donnée encodée (format non réversible).

Formulaire d’exemple :

```
<form method="post" action="https://rcet-payment.sips-atos.com:443/cgis-payment/prod/callpayment">
    <input type="hidden" name="DATA" value="2020353539603028502c2360552d3344532d2360522d2360502c3360502c2331302d4324575c224360542c3360502c2340522c2324502c232c502c3048502c2328502c2324552c2338582d3330512d4344582d5360502c2360515c224360522e3360502c2329463c4048502c232c502c2360532d4330505c224360502d3360502c2338512d5360542d23242a2c2360562c2360512d2328502c3338512c4328502c3338502d2330515c224360502e2360502c232c592d53402a2c2328582c2360502c4639525c224360502e3360502c2329463c4048502c3324502c2334503a2731543c272c5a2b525d493b472d54383659542b4735413d5c2259463c425943383729523936394f3d37284e38565d4d2b565d52392635522b362d4f3b4639493c46542a2c232c512c2360562c5641543d2721532e425c4f3a3659533d26254e3d5c2259553837304e3947284e385625523c4635463b5735522b462d4f3b325d413d265d532b5721413e3655453b47304f383735543b52555239372d503b565953393048502c332c502c2334503a2731543c272c5a2b525d493b472d54383659542b4735413d5c2259463c425943383729523936394f3d37284e38565d4d2b565d52392635522b5729453c3735453c57302a2c2324572c2360502d44392631443926314048502c3340502c2360562c2360502c2360505c224360522d4360502c33395c222d343457303328542d4334552e3330592c233d255c224360522d5360502d333c5c35352d2537542d333453585b3856384d3947294f3b4731413b5c2255533a3721532b462d533c53504f35352d2537542d333453585b33445d3f3444353334245d2e3454353f3424252731334c2a2c232c562c2360512e242d5c222b2539293454244c333425333524353230542532316048502c5340502c2360542c4338572c6048502c5344502c2360512d4048502d2360502c2324503544252c323431213524452f334048502d5338502c2360582c4360512c5360562c233c2a2c233c572c2360502c53244e2c6048502d5340502c2360533c2641505c22406060706f49be45d235f5">
    <div align="center">
        Vous utilisez le formulaire s&#233;curis&#233; standard SSL, choisissez une carte ci-dessous
        <img src="CLEF.gif" border="0"> :
        <br /><br />
    </div>
    <div align="center">
        <input type="image" name="CB" border="0" src="CB.gif">
        <img src="INTERVAL.gif">
        <input type="image" name="VISA" border="0" src="VISA.gif">
        <img src="INTERVAL.gif">
        <input type="image" name="MASTERCARD" border="0" src="MASTERCARD.gif">
        <img src="INTERVAL.gif">
    </div>
</form>
```

L’envoie de ce formulaire ouvrira une webview sur les serveurs d’ATOS.

## `SPEC_TECH_SIPS_002_GET` - Demande statut

### GET /api/sips/get-status

> non-utilisé

## `SPEC_TECH_SIPS_003_POST` - Nouvelle transaction

### POST /api/sips/new-transaction

Persiste la réponse d’ATOS suite à la demande d’autorisation de prélèvement afin de faire la capture par la suite

#### Input :
objet “réponse Atos” (obtenu obtenu encrypté via le callback d’Atos à la fin de la demande d’autorisation)

#### Output :
objet transaction

## `SPEC_TECH_SIPS_004_POST` - Envoyer paiement

### POST /api/sips/send-payment

Cette route permet la capture d’une transaction dont l’autorisation a été préalablement faite

#### Input :
merchant id
transaction id
transaction date
amount

#### Output :

Exemple :

```
curl -X POST -H "Content-Type: application/x-www-form-urlencoded" -d 'merchantId=068541698700001&transactionId=143912&transactionDate=20160831&amount=0750' "http://%7B%7Burl%7D%7D/api/sips/send-payment"
```

/ END OF PART ONLY RELEVANT FOR SIPS-ATOS PAYMENT /

[*Retour en haut*](#sommaire)


# ORDER
## `SPEC_TECH_ORDER_001` - Set Ready
### POST  /api/orders/{orderId}/setReady.{_format}

`orderId` as parameter

Triggers made on order management
* Change order statut from 2 to 4 (validated to ready)
* Triggers the following events :
* Trigger the event `ORDER_READY`
* Generate the purchase order as pdf file (send to customer)
* Create the invoice
* Send the payment capture to the relevant Payment Service Provider
* Recalculate delivery fees

This command is used by specific customer.
## `SPEC_TECH_ORDER_002` - Order validation (payment)
This methods allows for payment validation

### POST  /api/orders/{orderId}/validate.{_format}

This route is called when the bank validate the authorisation request and the customer is debited. This is done through Wynd Marketplace Back Office.

Change order status to validated : “valid”

Send a push notification to the Wynd terminal (Android Application to receive and process orders on-sites) using Pubnub.

* DB storage: `llx_commande`

template JSON :


## `SPEC_TECH_ORDER_003` - Create an order using a basket

### POST  /api/orders.{_format}

La création d'une commande avec ou sans produit menu se fait via la route POST /api/orders
#### Input
Comme toute route de l'API, il est nécessaire de passer le token d'authentification en header de la requête.
Il est nécessaire de passer le JSON de la commande dans le body de la requête.
Exemple

```json
{
  "entity": 3,	//id de l'entité
  "deviceID": null,	//id du device
  "deviceNumber": null,	//numéro du device
  "idUser": null,	//id de l'utilisateur
  "userName": null,	//nom de l'utilisateur
  "origin": "website",	//origin de l'order (website ou pos)
  "orderNumber": null,	//numero de l'order (NULL à la création)
  "orderDate": null,	//date de création de l'order (NULL à la création)
  "total": 14.504,	//montant TTC total de l'order
  "content": [	//liste des items de l'order
    {
      "externalId": null,	//external id de l'item
      "externalRef": null,	//external ref de l'item
      "featured": false,	//boolean de mise en avant de l'item
      "picture": false,	//url de l'image de l'item
      "type": "menu",	//type du product (menu, choice, product)
      "categoryKvs": "11",	//id de la categorie KVS
      "tvaTx": "10.000",	//taux de TVA de l'item
      "priceTtc": "7.50000000",	//montant TTC de l'item
      "priceHt": "6.81818000",	//montant HT de l'item
      "prices": { //liste de prix de l'item
        "1": {
          "price_ttc": 7.5,
          "price_ht": 6.81818,
          "price_per_unit": 0,
          "unit_ratio": false,
          "tva_tx": 10,
          "to_sell": true
        }
      },
      "product_origin": null,	//origine de l'item
      "extra_data_image": false,	//url image de l'item
      "extra_data_weight": 0,	//poids de l'item
      "extra_data_weight_unit": false,	// unité de poids de l'item
      "root_category_id": false,	// id de de la root category de l'item
      "root_category_label": false,	// label de la root category de l'item
      "category_limit": false, //nb maximum de produits de la category dans la limite
      "extra_data_packaging": false, //packaging de l'item
      "extra_categories": [// tableau des categories de l'item

      ],
      "extra_data": [ //tableau des extra_data

      ],
      "sub": [	//liste des produits enfants (ingrédients ou composants d'un menu)
        {
          "externalId": 4,
          "externalRef": "Hambourgeois bœuf bacon",
          "featured": false,
          "picture": false,
          "type": "Sandwich",
          "categoryKvs": "5",
          "tvaTx": "3.000",
          "priceTtc": "7.00400000",
          "priceHt": "6.80000000",
          "prices": {
            "1": {
              "price_ttc": 7.004,
              "price_ht": 6.8,
              "price_per_unit": 0,
              "unit_ratio": false,
              "tva_tx": 3,
              "to_sell": true
            }
          },
          "product_origin": null,
          "extra_data_image": false,
          "extra_data_weight": 0,
          "extra_data_weight_unit": false,
          "root_category_id": false,
          "root_category_label": false,
          "category_limit": false,
          "extra_data_packaging": false,
          "extra_categories": [

          ],
          "extra_data": [

          ],
          "id": 366,
          "slug": "",
          "ref": "HAMBOURGEOIS_BB",
          "label": "Hambourgeois bœuf bacon",
          "description": "Pain brioch&eacute; grain&eacute;, steak hach&eacute;, bacon grill&eacute;, mayonnaise all&eacute;g&eacute;e, ketchup, oignons rissol&eacute;s, roquette, tomate, cornichons.<br />\r\n<em>Accompagn&eacute; de pommes de terre r&ocirc;ties et de salade verte.</em>",
          "to_sell": 1,
          "barcode": null,
          "tags": [

          ],
          "is_payable": 0,
          "quantity": 1
        },
        {
          "externalId": null,
          "externalRef": null,
          "featured": false,
          "picture": false,
          "type": null,
          "categoryKvs": "0",
          "tvaTx": "5.500",
          "priceTtc": "2.50000000",
          "priceHt": "2.36967000",
          "prices": {
            "1": {
              "price_ttc": 2.5,
              "price_ht": 2.36967,
              "price_per_unit": 0,
              "unit_ratio": false,
              "tva_tx": 5.5,
              "to_sell": true
            }
          },
          "product_origin": null,
          "extra_data_image": false,
          "extra_data_weight": 0,
          "extra_data_weight_unit": false,
          "root_category_id": false,
          "root_category_label": false,
          "category_limit": false,
          "extra_data_packaging": false,
          "extra_categories": [

          ],
          "extra_data": [

          ],
          "id": 385,
          "slug": "",
          "ref": "BADOIT_CITRON_VERT_50",
          "label": "Badoit citron vert 50cl",
          "description": "",
          "to_sell": 1,
          "barcode": null,
          "tags": [

          ],
          "is_payable": 0,
          "quantity": 1
        }
      ],
      "id": 389,	//id de l'item
      "slug": "",
      "ref": "MENU_TEST", //reference de l'item
      "label": "Menu Test", //label de l'item
      "description": "", //description de l'item
      "to_sell": 1, //caractère vendable de l'item
      "barcode": null, //code barre de l'item
      "tags": [	//list des tags de l'item

      ],
      "quantity": 1	//quantite de l'item
    },
    {
      "externalId": null,
      "externalRef": null,
      "featured": false,
      "picture": false,
      "type": null,
      "categoryKvs": "0",
      "tvaTx": "3.000",
      "priceTtc": "7.00400000",
      "priceHt": "6.80000000",
      "prices": {
        "1": {
          "price_ttc": 7.004,
          "price_ht": 6.8,
          "price_per_unit": 0,
          "unit_ratio": false,
          "tva_tx": 3,
          "to_sell": true
        }
      },
      "product_origin": null,
      "extra_data_image": false,
      "extra_data_weight": 0,
      "extra_data_weight_unit": false,
      "root_category_id": false,
      "root_category_label": false,
      "category_limit": false,
      "extra_data_packaging": false,
      "extra_categories": [

      ],
      "extra_data": [

      ],
      "children": null,
      "id": 370,
      "slug": "",
      "ref": "QUICHE_LORRAINE",
      "label": "Quiche lorraine",
      "description": "Lardons, &oelig;uf, cr&egrave;me, lait. Accompagn&eacute;e de salade verte",
      "to_sell": 1,
      "barcode": null,
      "tags": [

      ],
      "quantity": 1
    }
  ],
  "payments": null,	//payments sur l'order
  "discounts": null,	//discounts sur l'order
  "interventions": null,	//interventions sur l'order
  "tickets": null,
  "timer": null,	//timer de l'order
  "deliveryTime": "2016-12-30 17:30:00",	//heure de livraison
  "delivery_lat_long": "(48.87469509999999, 2.323271200000022)", //longitude et latitude de l'adresse de livraison
  "address_delivery": "96 Boulevard Haussmann, 75008 Paris, France",	//adresse de livraison
  "destination": "delivery",	//destination (takeaway, delivery)
  "customer": { // client de l'order
    "id": 6,	//id du client
    "firstname": "Tii",	//prénom du client
    "lastname": "Toto",	//nom du client
    "email": "toto@mail.fr",	//email du client
    "login": "toto@mail.fr",	//login du client
    "phone": "0102030409",	//numero de téléphone
    "newsletter": false, //optin newsletter
    "token": "15ee2fd446edabadd9f37647b297bdd81117adc3",
    "stats": {
      "user_category": "Visiteur",
      "user_amount": 0,
      "user_newcustomer": "1",
      "user_last_order_date": ""
    },
    "address": "22 Rue de la Tour d\\'Auvergne, Paris, France",
    "additional_information": "B\u00e2tment C - 2\u00e8me \u00e9tage - porte droite droite",
    "digicode": "1702",
    "haveBilling": null
  },
  "comment": "commentaire du client" //Commentaire du client lié à l'order
}
```
#### Output

La route retourne le JSON de l'order créé.
Exemple

```json
{
  "data": {
    "status_message": "order.status_open_pending",
    "has_substitution": false,
    "orderItems": null,
    "id": 115,
    "reference": "1-0000000115",
    "entity": {
      "id": 3,
      "label": "PAUL Gare du Nord - RER",
      "description": "",
      "town": null,
      "zipcode": null,
      "address": null,
      "address_additional": null,
      "phone": null,
      "mail": null,
      "website": null,
      "extrafields": {}
    },
    "customer": {
      "id": 6,
      "entity": "1",
      "statut": "0",
      "name": "Tii Toto",
      "email": "toto@mail.fr",
      "addresses": []
    },
    "addresses": [
      {
        "id": 98,
        "type": "billing",
        "address_inline": "22 Rue de la Tour d\\'Auvergne, Paris, France",
        "comment": null,
        "digicode": null,
        "phone": null,
        "extra_phone": null,
        "email": null,
        "street_number": null,
        "street_name": null,
        "complement": null,
        "zip": null,
        "city": null,
        "country": null,
        "floor": null,
        "door": null
      },
      {
        "id": 97,
        "type": "delivery",
        "address_inline": "22 Rue de la Tour d\\'Auvergne, Paris, France",
        "comment": null,
        "digicode": "1702",
        "phone": "0102030409",
        "extra_phone": null,
        "email": "toto@mail.fr",
        "street_number": null,
        "street_name": null,
        "complement": "Bâtment C - 2ème étage - porte droite droite",
        "zip": null,
        "city": null,
        "country": null,
        "floor": null,
        "door": null
      }
    ],
    "items": [
      {
        "label": "Quiche lorraine",
        "product": {
          "extra_data_image": false,
          "root_category_id": false,
          "root_category_label": false,
          "category_limit": false,
          "extra_data_packaging": false,
          "extra_categories": [],
          "id": 370,
          "label": "Quiche lorraine",
          "description": "Lardons, &oelig;uf, cr&egrave;me, lait. Accompagn&eacute;e de salade verte",
          "barcode": null
        },
        "qty": 1,
        "price": 6.8,
        "total_ht": 6.8,
        "total_ttc": 7.004,
        "total_vat": 0.204,
        "status": 1
      }
    ],
    "basket": {
      "id": 49,
      "items": [
        {
          "parent_id": 389,
          "label": "Hambourgeois bœuf bacon",
          "qty": 1,
          "price": 5.53,
          "price_ht": 5.368932038835,
          "total_ht": 5.368932038835,
          "total_ttc": 5.53,
          "total_vat": 0.16106796116505,
          "product": {
            "id": 366,
            "label": "Hambourgeois bœuf bacon",
            "description": "Pain brioch&eacute; grain&eacute;, steak hach&eacute;, bacon grill&eacute;, mayonnaise all&eacute;g&eacute;e, ketchup, oignons rissol&eacute;s, roquette, tomate, cornichons.<br />\r\n<em>Accompagn&eacute; de pommes de terre r&ocirc;ties et de salade verte.</em>"
          }
        },
        {
          "parent_id": 389,
          "label": "Badoit citron vert 50cl",
          "qty": 1,
          "price": 1.97,
          "price_ht": 1.8672985781991,
          "total_ht": 1.8672985781991,
          "total_ttc": 1.97,
          "total_vat": 0.10270142180095,
          "product": {
            "id": 385,
            "label": "Badoit citron vert 50cl",
            "description": ""
          }
        },
        {
          "parent_id": null,
          "label": "Quiche lorraine",
          "qty": 1,
          "price": 7.004,
          "price_ht": 6.8,
          "total_ht": 6.8,
          "total_ttc": 7.004,
          "total_vat": 0.204,
          "product": {
            "id": 370,
            "label": "Quiche lorraine",
            "description": "Lardons, &oelig;uf, cr&egrave;me, lait. Accompagn&eacute;e de salade verte"
          }
        }
      ]
    },
    "created_at": "2017-02-13T12:48:49+0100",
    "updated_at": "2017-02-13T11:48:50+0100",
    "status": 0,
    "amount_ht": null,
    "tva": 0.46776938,
    "total_ht": 14.03623062,
    "total_ttc": 14.504,
    "delivery_address": "96 Boulevard Haussmann, 75008 Paris, France",
    "delivery": null,
    "extrafields": {
      "delivery_time": "2016-12-30T17:30:00+0100",
      "comment": "commentaire du client"
    },
    "reference_ext": "117021312485000"
  }
}
```

## `SPEC_TECH_ORDER_004` - Récupération du statut de la commande

GET /api/order/{orderId}/status.{_format}

## `SPEC_TECH_ORDER_005` - Retrieving Order QR code as an image (.gif format)

### GET  /api/orders/{orderId}/qr-code.gif

This route let you retrieve the QR code used for picking order on-site.

The QR code is made of :
A table with orders ID. The ID account for the order ID inside WyndOrder.
The customer data ( id , email, phone)

Practically, the Qr code is used to pick-up your order on-site (using Wynd POS or Wynd- Terminal). It bears the order ID and the customer ID. The same QR code can be used to pick up several orders at differents sites.

```json
{
  "orders": [
    {
    "id": "2370385490"
    },
    {
    "id": "2370385491"
    },
    {
    "id": "2370385492"
    }
  ],
  "customer" : {
    "id": "55455455544",
    "email" : "johndoe@yolo.com",
    "phone : "+33654785458"
  }
}
```

orders : table containing orders object
|__ id : Wynd order ID
customer : Customer information (object format)
|__ id : Customer ID into Wynd referentiel
|__ email : Customer email
|__ phone : Customer phone number (international format)






## `SPEC_TECH_ORDER_006` - Retrieving Order QR code as a JSON

### GET  /api/orders/{orderId}/qr-code.json

Retrieve QR code content into JSON

QR code details available in  `SPEC_TECH_ORDER_005` -  Retrieving Order QR code as an image (.gif format)


Technical details of QR code format:
redundancy : low,
format : gif,
size : 350x350 pixels,
color : black on white

## `SPEC_TECH_ORDER_007` - Changing order delivery time

### PUT  /api/update-order-deliverytime/{orderId}.{_format}

This route allows changing delivery time of an existing order. The route also freeing the previous slot and select another one.

#### Input :
orderId : Id order that needs to be modified
body : {"delivery_time": “DATETIME FORMAT”}

Example :
URL : PUT /api/update-order-deliverytime/1.json
body :
```json
{
    "delivery_time": "2017-01-04T15:00:00+00:00"
}
```

#### Output :
The object  Order is updated and serialized :

```json
{
  "data": {
	"status_message": "order.status_preparing",
	"has_substitution": false,
	"id": 1,
	"reference": "1-0000000001",
	"entity": {
  	"id": 1,
  	"label": "Entité maître",
  	"description": "Entité maître, ne peut pas être supprimée",
  	"town": null,
  	"zipcode": null,
  	"address": null,
  	"address_additional": null,
  	"phone": null,
  	"mail": null,
  	"website": null,
  	"extrafields": {}
	},
	"customer": {
  	"id": 1,
  	"entity": "1",
  	"statut": "0",
  	"name": "Client par défaut",
  	"email": null,
  	"addresses": []
	},
	"addresses": [],
	"items": [],
	"created_at": "2016-09-28T20:15:42+0200",
	"updated_at": "2017-01-06T15:27:01+0100",
	"status": 3,
	"amount_ht": 0,
	"tva": 0.5636,
	"total_ht": 18.7864,
	"total_ttc": 19.35,
	"delivery_address": null,
	"delivery": null,
	"extrafields": {
  	"delivery_time": "2017-01-04T15:00:00+0000"
	}
  }
}
```
[*Retour en haut*](#sommaire)


# BASKET

## `SPEC_TECH_BASKET_001` - Retrieve an empty basket

### GET  /api/basket.{_format}

This Route retrieve the JSON structure of an empty basket, than can then be fed.

```json
{
   "id": null,
   "entity": null,
   "deviceID": null,
   "deviceNumber": null,
   "idUser": null,
   "userName": null,
   "origin": null,
   "orderNumber": null,
   "orderDate": null,
   "total": null,
   "content": null,
   "payments": null,
   "discounts": null,
   "interventions": null,
   "tickets": null,
   "timer": null,
   "deliveryTime": null,
   "delivery_lat_long": null,
   "address_delivery": null,
   "destination": null,
   "customer": null,
   "total_tax_incl": null,
   "total_tax_excl": null,
   "total_tax": null,
   "original_json_request": null,
   "lines": null,
   "hasSubstitution": false
}
```




**attribut**|**DB > attribut**|**description**
:-----:|:-----:|:-----:
id|not stored|not used (coming soon)
entity|not stored|Entity ID (point de vente)
deviceID|not stored|POS device ID
deviceNumber|not stored|POS number (ex : 1, 2 …)
idUser|not stored|POS Operator ID
userName|not stored|not used with eShop
origin|not stored|Original basket creation channel (website / pos)
orderNumber|not stored|
orderDate|not stored|
total|not stored|Basket total price (price inclusive)
content|not stored|"Table containing added product (ID product and Quatity mandatory)
payments|not stored|
discounts|not stored|
interventions|not stored|
tickets|not stored|
timer| |
deliveryTime| |Delivery (or pickup) date and time (datetime)
delivery_lat_long| |
address_delivery| |
destination| |
customer| |
total_tax_incl| |



##### Ex : Full basket
```json
{
    "id": null,
    "entity": 4,
    "deviceID": null,
    "deviceNumber": null,
    "idUser": null,
    "userName": null,
    "origin": "website",
    "orderNumber": null,
    "orderDate": null,
    "total": 2.9699999999999998,
    "content": {
        "1301": {
            "externalId": null,
            "externalRef": null,
            "featured": null,
            "picture": null,
            "type": "product",
            "categoryKvs": null,
            "tvaTx": "5.500",
            "priceTtc": "1.75000000",
            "priceHt": "1.65876777",
            "prices": {
                "1": {
                    "price_ttc": 1.75,
                    "price_ht": 1.65876777,
                    "price_per_unit": 13.46,
                    "unit_ratio": "\u20ac \/ KG",
                    "tva_tx": 5.5,
                    "to_sell": true
                }
            },
            "product_origin": {
                "1": {
                    "code": "BE",
                    "description": "BELGIQUE",
                    "cle_bcp": "017",
                    "cle_picxyz": "BE",
                    "cle_mandar": "002",
                    "display_name": "BELGIQUE"
                }
            },
            "extra_data_image": "3168930002987",
            "extra_data_weight": 13.461538461538462,
            "extra_data_weight_unit": "KG",
            "root_category_id": "R07",
            "root_category_label": "Epicerie Sal\u00e9e",
            "category_limit": false,
            "extra_data_packaging": "le sachet de 130g",
            "extra_categories": ["Epicerie Sal\u00e9e", "Pour l'ap\u00e9ritif", "Chips"],
            "extra_data": {
                "id_category1": "R07",
                "label_category1": "Epicerie Sal\u00e9e",
                "id_category2": "R07F01",
                "label_category2": "Pour l'ap\u00e9ritif",
                "id_category3": "R07F01SF01",
                "label_category3": "Chips",
                "id_category4": "",
                "label_category4": "",
                "packaging": "le sachet de 130g",
                "brand_name": "Lay's",
                "ingredients": "Produit \u00e0 base de pommes de terre cuit au four go\u00fbt nature:<BR\/>Flocons de pommes de terre (68%), amidon, huile de tournesol, sucre, \u00e9mulsifiant (l\u00e9cithine de soja), dextrose, sel, extrait de curcuma.",
                "flag_produit_frais": false,
                "flag_organic_trade_item_code": false,
                "flag_quality": false,
                "flag_label_rouge": false,
                "free_from_ogm": false,
                "free_from_gluten": false,
                "picto_silhouette": false,
                "picto_point_exclamation": false,
                "picto_explosion": false,
                "picto_tete_mort": false,
                "picto_acide_main": false,
                "picto_flamme": false,
                "picto_flamme_rond": false,
                "picto_poison": false,
                "picto_bouteille": false,
                "caliber": "",
                "rich_text_traceability": "",
                "variete": "",
                "nutritional_value_proteins": "6g pour 100g",
                "nutritional_value_lipids": "10g pour 100g",
                "nutritional_value_saturated_fatty_acid": "1g pour 100g",
                "nutritional_value_glucids": "73g pour 100g",
                "of_which_sugar": "6,5g pour 100g",
                "nutritional_value_dietary_fiber": "5g pour 100g",
                "nutritional_value_sodium": "0,6g pour 100g",
                "nutritional_value_vitamins": "",
                "nutritional_value_kj": "1750kj pour 100g",
                "nutritional_value_cal": "415kCal pour 100g",
                "measurement_alcohol_by_volume": "",
                "block_rank8": "8",
                "block_title8": "",
                "block_content8": "",
                "block_rank9": "9",
                "block_title9": "",
                "block_content9": "",
                "block_rank10": "5",
                "block_title10": "",
                "block_content10": "A conserver \u00e0 l'abri de la chaleur et de l'humidit\u00e9. Conditionn\u00e9 sous atmosph\u00e8re protectrice.",
                "block_rank11": "7",
                "block_title11": "",
                "block_content11": "",
                "taxe_message": "",
                "measure_weight": "0.135",
                "measure_height": "255.0",
                "measure_depth": "55.0",
                "measure_width": "172.0",
                "nature": "Chips",
                "category": "",
                "country_origin": "BE",
                "measure_net_weight": "0.13",
                "measure_net_weight_unit": "KG",
                "picture_url": "3168930002987"
            },
            "children": null,
            "id": 1301,
            "ref": "3168930002987",
            "label": "Chips Les Cuites au Four nature Lay's",
            "description": null,
            "barcode": "3168930002987",
            "quantity": 1
        },
        "1306": {
            "externalId": null,
            "externalRef": null,
            "featured": null,
            "picture": null,
            "type": "product",
            "categoryKvs": null,
            "tvaTx": "5.500",
            "priceTtc": "1.22000000",
            "priceHt": "1.15639810",
            "prices": {
                "1": {
                    "price_ttc": 1.22,
                    "price_ht": 1.1563981,
                    "price_per_unit": 9.76,
                    "unit_ratio": "\u20ac \/ KG",
                    "tva_tx": 5.5,
                    "to_sell": true
                }
            },
            "product_origin": {
                "1": {
                    "code": "FR",
                    "description": "FRANCE",
                    "cle_bcp": "001",
                    "cle_picxyz": "FR",
                    "cle_mandar": "001",
                    "display_name": "FRANCE"
                }
            },
            "extra_data_image": "3497911101129",
            "extra_data_weight": 9.76,
            "extra_data_weight_unit": "KG",
            "root_category_id": "R07",
            "root_category_label": "Epicerie Sal\u00e9e",
            "category_limit": false,
            "extra_data_packaging": "le sachet de 125 g",
            "extra_categories": ["Epicerie Sal\u00e9e", "Pour l'ap\u00e9ritif", "Chips"],
            "extra_data": {
                "id_category1": "R07",
                "label_category1": "Epicerie Sal\u00e9e",
                "id_category2": "R07F01",
                "label_category2": "Pour l'ap\u00e9ritif",
                "id_category3": "R07F01SF01",
                "label_category3": "Chips",
                "id_category4": "",
                "label_category4": "",
                "packaging": "le sachet de 125 g",
                "brand_name": "Bret's",
                "ingredients": "Chips de pommes de terre saveur poulet brais\u00e9<BR\/>Pommes de terre (France) (61%), huile de tournesol (34%), base aromatisante poulet brais\u00e9 (ar\u00f4me (BLE), viande de poulet en poudre), sel.<BR\/>Fabriqu\u00e9 dans un atelier qui utilise : lait, c\u00e9leri, moutarde",
                "flag_produit_frais": false,
                "flag_organic_trade_item_code": false,
                "flag_quality": false,
                "flag_label_rouge": false,
                "free_from_ogm": false,
                "free_from_gluten": false,
                "picto_silhouette": false,
                "picto_point_exclamation": false,
                "picto_explosion": false,
                "picto_tete_mort": false,
                "picto_acide_main": false,
                "picto_flamme": false,
                "picto_flamme_rond": false,
                "picto_poison": false,
                "picto_bouteille": false,
                "caliber": "",
                "rich_text_traceability": "",
                "variete": "",
                "nutritional_value_proteins": "6,4g pour 100g",
                "nutritional_value_lipids": "34g pour 100g",
                "nutritional_value_saturated_fatty_acid": "3,1g pour 100g",
                "nutritional_value_glucids": "50g pour 100g",
                "of_which_sugar": "2g pour 100g",
                "nutritional_value_dietary_fiber": "",
                "nutritional_value_sodium": "1,6g pour 100g (sel)",
                "nutritional_value_vitamins": "",
                "nutritional_value_kj": "2257kj pour 100g",
                "nutritional_value_cal": "542kCal pour 100g",
                "measurement_alcohol_by_volume": "",
                "block_rank8": "8",
                "block_title8": "Ingr\u00e9dients",
                "block_content8": "Chips de pommes de terre saveur poulet brais\u00e9<BR\/>Pommes de terre (France) (61%), huile de tournesol (34%), base aromatisante poulet brais\u00e9 (ar\u00f4me (BLE), viande de poulet en poudre), sel.<BR\/>Fabriqu\u00e9 dans un atelier qui utilise : lait, c\u00e9leri, moutarde",
                "block_rank9": "9",
                "block_title9": "Analyse Nutritionnelle",
                "block_content9": "Valeurs nutritionnelles moyennes pour 100g<BR\/>Valeur \u00e9nerg\u00e9tique                           2257kJ<BR\/>                                             542kcal<BR\/>Mati\u00e8res grasses                             34g<BR\/> Mati\u00e8res grasses dont Acides Gras Satur\u00e9s   3,1g<BR\/>Glucides                                     50g<BR\/>Glucides dont sucre                          2g<BR\/>Prot\u00e9ines                                    6,4g<BR\/>Sel                                          1,6g<BR\/>",
                "block_rank10": "5",
                "block_title10": "Autres Infos conso",
                "block_content10": "A conserver \u00e0 l'abri de la chaleur et de l'humidit\u00e9.<BR\/>Altho<BR\/>Altho route de St Varadec 56920 St G\u00e9rand<BR\/>www.brets.fr",
                "block_rank11": "0",
                "block_title11": "Tra\u00e7abilit\u00e9",
                "block_content11": "",
                "taxe_message": "",
                "measure_weight": "0.134",
                "measure_height": "270.0",
                "measure_depth": "185.0",
                "measure_width": "50.0",
                "nature": "Chips",
                "category": "",
                "country_origin": "FR",
                "measure_net_weight": "0.125",
                "measure_net_weight_unit": "KG",
                "picture_url": "3497911101129"
            },
            "children": null,
            "id": 1306,
            "ref": "3497911101129",
            "label": "Chips saveur poulet brais\u00e9 Bret's",
            "description": null,
            "barcode": "3497911101129",
            "quantity": 1
        }
    },
    "payments": null,
    "discounts": null,
    "interventions": null,
    "tickets": null,
    "timer": null,
    "deliveryTime": "2016-12-22 17:30:00",
    "delivery_lat_long": "(48.87469509999999, 2.323271200000022)",
    "address_delivery": "96 Boulevard Haussmann, 75008 Paris, France",
    "destination": "delivery",
    "customer": {
        "id": 1609,
        "firstname": "Michael",
        "lastname": "Rivet",
        "email": "ezozug@ofighreruhgzer.com",
        "phone": "0101010101",
        "address": "96 Boulevard Haussmann, 75008 Paris, France",
        "digicode": "",
        "additional_information": "",
        "billing": {
            "firstname": "Michael",
            "lastname": "Rivet",
            "address": "96 Boulevard Haussmann, 75008 Paris, France"
        },
        "haveBilling": true
    },
    "total_tax_incl": 2.9699999999999998,
    "total_tax_excl": 2.9699999999999998,
    "total_tax": null,
    "hasSubstitution": null
}
```

Ex :

```json

{
"entity":"1",
"deviceID":"5",
"deviceNumber":"1",
"idUser":"2",
"userName":"Support WY",
"origin":"pos",
"id":1483630690745,
"orderNumber":"131",
"orderDate":null,
"total":9.5,
"content":[
{
"id":"1",
"label":"formuleA",
"price":0,
"tva_tx":10,
"quantity":1,
"category_kvs":"0",
"external_ref":"M000",
"division":"2",
"sub":[
{
"id":"7",
"label":"PlatB",
"price":"2.22",
"tva_tx":10,
"quantity":1,
"is_payable":1,
"category_kvs":"1",
"external_ref":null,
"division":"1",
"path":"1_51,1_52,6_1,1_9,2_7",
"comment":null,
"discount":{
"amount":0.11,
"label":"Remise 5%",
"code":"5_PERCENT",
"external_id":null,
"id":"3"
},
"price_takeaway":"2.22",
"price_ht":2.0181818181818,
"price_ht_takeaway":2.0181818181818
},
{
"id":"3",
"label":"CocaCola",
"price":"7.78",
"tva_tx":20,
"quantity":1,
"is_payable":1,
"category_kvs":"2",
"external_ref":null,
"division":"5",
"path":"1_51,1_52,6_1,1_5,1_3",
"comment":null,
"discount":{
"amount":0.39,
"label":"Remise 5%",
"code":"5_PERCENT",
"external_id":null,
"id":"3"
},
"price_takeaway":"7.78",
"price_ht":6.4833333333333,
"price_ht_takeaway":6.4833333333333
}
],
"comment":null,
"price_ht":0,
"price_takeaway":0,
"price_ht_takeaway":0
}
],
"payments":[
{
"id":"4",
"code":"TR",
"type":"popup",
"amount":"10.00",
"operator":null,
"data":[
]
}
],
"discounts":[
{
"code":"5_PERCENT",
"label":"Remise 5%",
"amount":"0.50"
}
],
"interventions":[
],
"timer":{
"hours":"00",
"minutes":"01",
"seconds":12
},
"deliveryTime":null,
"customer":null,
"tickets":[
],
"destination":"onsite",
"discountByTva":[
{
"label":"TVA 10%",
"amountTTC":0.11
},
{
"label":"TVA 20%",
"amountTTC":0.39
}
],
"tva":[
{
"label":"TVA 10%",
"amountHT":1.9181818181818,
"amountTVA":0.19181818181818,
"amountTTC":2.11
},
{
"label":"TVA 20%",
"amountHT":6.1583333333333,
"amountTVA":1.2316666666667,
"amountTTC":7.39
}
],
"total_ht":8.0765151515152,
"dateTicket":"2017-01-05 16:44:28",
"date":"2017-01-05 16:44:28",
"orderRef":"1-0000000553"
}
```


## `SPEC_TECH_BASKET_002` - Add a product to a basket

### PUT  /api/basket/update/{id}.{_format}
Check that the maximum product quantity per basket is not over the limit.

id : ID of added product

INVOICE
## `SPEC_TECH_FACTURE_001` - Create an order invoice
### GET  /api/facture/{orderId}.{_format}
The route return the generated invoice
orderId : ID of the order the invoice needs to be created for

[*Retour en haut*](#sommaire)



# WYND_TERMINAL
The Wynd Terminal (or WyndT) is an android Application used to managed the order retrieving system. The hardware embed a QR code reader as well as a printer.

## `SPEC_TECH_WYND_TERMINAL_001` - Connect a WyndT

### GET /api/wyndt/connect/{macAddress}.{_format} Get infos

## `SPEC_TECH_WYND_TERMINAL_002` - Retrieve an order

### POST /api/wyndt/order/{orderId}/handled.{_format} Return handled order


[*Retour en haut*](#sommaire)


# TAG
The application filters a product's offer in relation to a tag ex: breakfast, lunch, snacks, gluten_free, vegetarian. A Type can be related to many tags and a tag is related to only one Type (ex : desire, location).


### GET  /api/types
Get all types

#### Output :
```json
[
  {
	"id": 1,
	"label": "desire",
	"tags": [
  	{
    	"id": 1,
    	"label": "petit_dejeuner",
    	"description": "This is the description",
    	"picture_url": "https://www.pictures.com/example.jpg"
  	},
  	{
    	"id": 2,
    	"label": "sans_gluten",
    	"description": "This is the description",
    	"picture_url": "https://www.pictures.com/example.jpg"
  	},
  	{
    	"id": 3,
    	"label": "vegetarien",
    	"description": "This is the description",
    	"picture_url": "https://www.pictures.com/example.jpg"
  	}
	]
  },
  {
	"id": 2,
	"label": "location",
	"tags": [
  	{
    	"id": 4,
    	"label": "ligne_4",
    	"description": "This is the description",
    	"picture_url": "https://www.pictures.com/example.jpg"
  	},
  	{
    	"id": 5,
    	"label": "ligne_5",
    	"description": "This is the description",
    	"picture_url": "https://www.pictures.com/example.jpg"
  	},
  	{
    	"id": 6,
    	"label": "rer",
    	"description": "This is the description",
    	"picture_url": "https://www.pictures.com/example.jpg"
  	},
  	{
    	"id": 7,
    	"label": "eurostar",
    	"description": "This is the description",
    	"picture_url": "https://www.pictures.com/example.jpg"
  	}
	]
  }
]
```

### GET  /api/types/{type_id}
Get one Type

#### Input : /api/types/1

#### Output :

```json
{
  "id": 1,
  "label": "desire",
  "tags": [
	{
  	"id": 1,
  	"label": "petit_dejeuner",
  	"description": "This is the description",
  	"picture_url": "https://www.pictures.com/example.jpg"
	},
	{
  	"id": 2,
  	"label": "sans_gluten",
  	"description": "This is the description",
  	"picture_url": "https://www.pictures.com/example.jpg"
	},
	{
  	"id": 3,
  	"label": "vegetarien",
  	"description": "This is the description",
  	"picture_url": "https://www.pictures.com/example.jpg"
	}
  ]
}
```


### DELETE  /api/types/{type_id}
Delete one Type

Response code : `HTTP_NO_CONTENT (204)`


### PUT  /api/types/{type_id}
Update one Type

#### Input : /api/types/1
```json
{
    “label”: “test”
}
```

#### Output :
```json
{
   "id": 1,
   "label": "test",
   "tags": [
     {
       "id": 1,
       "label": "petit_dejeuner"
     },
     {
       "id": 2,
       "label": "sans_gluten"
     },
     {
       "id": 3,
       "label": "vegetarien"
     }
   ]
}
```

### POST  /api/types
Create a new Tag type

#### Input :
```json
{
    “label”: “newType”
}
```


#### Output :
```json
{
	"id": 3,
	"label": "newType",
	"tags": null
  }
```





### GET  /api/tags
Get all Tags

#### Output :
```json
[
  {
	"id": 1,
	"label": "petit_dejeuner",
	"description": "This is the description",
	"picture_url": "https://www.pictures.com/example.jpg",
	"type": {
  	"id": 1,
  	"label": "desire"
	},
	"entities": [],
	"products": [
  	{
    	"externalId": 1,
    	"externalRef": "Salade Paul",
    	"featured": false,
    	"picture": false,
    	"type": "Salade",
    	"categoryKvs": "3",
    	"tvaTx": "3.000",
    	"priceTtc": "7.00400000",
    	"priceHt": "6.80000000",
    	"prices": {
      	"1": {
        	"price_ttc": 7.004,
        	"price_ht": 6.8,
        	"price_per_unit": 0,
        	"unit_ratio": false,
        	"tva_tx": 3,
        	"to_sell": true
      	}
    	},
    	"product_origin": null,
    	"extra_data_image": false,
    	"extra_data_weight": 0,
    	"extra_data_weight_unit": false,
    	"root_category_id": false,
    	"root_category_label": false,
    	"category_limit": false,
    	"extra_data_packaging": false,
    	"extra_categories": [],
    	"id": 363,
    	"slug": "",
    	"ref": "SALADE_PAUL",
    	"label": "Salade Paul",
    	"description": "Filets de poulet, copeaux de parmesan, sauce Caesar, cro&ucirc;tons aill&eacute;s, salade, ciboulette.",
    	"to_sell": 1,
    	"barcode": null,
    	"tags": [
      	null
    	]
  	}
	]
  },
  {
	"id": 2,
	"label": "sans_gluten",
	"description": "This is the description",
	"picture_url": "https://www.pictures.com/example.jpg",
	"type": {
  	"id": 1,
  	"label": "desire"
	},
	"entities": [],
	"products": [
  	{
    	"externalId": 2,
    	"externalRef": "Salade mer",
    	"featured": false,
    	"picture": false,
    	"type": "Salade",
    	"categoryKvs": "3",
    	"tvaTx": "3.000",
    	"priceTtc": "7.00400000",
    	"priceHt": "6.80000000",
    	"prices": {
      	"1": {
        	"price_ttc": 7.004,
        	"price_ht": 6.8,
        	"price_per_unit": 0,
        	"unit_ratio": false,
        	"tva_tx": 3,
        	"to_sell": true
      	}
    	},
    	"product_origin": null,
    	"extra_data_image": false,
    	"extra_data_weight": 0,
    	"extra_data_weight_unit": false,
    	"root_category_id": false,
    	"root_category_label": false,
    	"category_limit": false,
    	"extra_data_packaging": false,
    	"extra_categories": [],
    	"id": 364,
    	"slug": "",
    	"ref": "SALADE_MER",
    	"label": "Salade de la mer",
    	"description": "Saumon fum&eacute;, crevettes roses, tartinade de Dieppois, avocat, tomate, salade, ciboulette.",
    	"to_sell": 1,
    	"barcode": null,
    	"tags": [
      	null
    	]
  	}
	]
  },
  {
	"id": 3,
	"label": "vegetarien",
	"description": "This is the description",
	"picture_url": "https://www.pictures.com/example.jpg",
	"type": {
  	"id": 1,
  	"label": "desire"
	},
	"entities": [],
	"products": [
  	{
    	"externalId": 3,
    	"externalRef": "Salade 3 fromages",
    	"featured": false,
    	"picture": false,
    	"type": "Salade",
    	"categoryKvs": "3",
    	"tvaTx": "3.000",
    	"priceTtc": "7.00400000",
    	"priceHt": "6.80000000",
    	"prices": {
      	"1": {
        	"price_ttc": 7.004,
        	"price_ht": 6.8,
        	"price_per_unit": 0,
        	"unit_ratio": false,
        	"tva_tx": 3,
        	"to_sell": true
      	}
    	},
    	"product_origin": null,
    	"extra_data_image": false,
    	"extra_data_weight": 0,
    	"extra_data_weight_unit": false,
    	"root_category_id": false,
    	"root_category_label": false,
    	"category_limit": false,
    	"extra_data_packaging": false,
    	"extra_categories": [],
    	"id": 365,
    	"slug": "",
    	"ref": "SALADE_3_FROMAGES",
    	"label": "Salade 3 fromages",
    	"description": "Salade, toast au fromage &agrave; raclette, toast au fromage de ch&egrave;vre, toast au camembert, raisins noirs, oignons rouges, ciboulette.",
    	"to_sell": 1,
    	"barcode": null,
    	"tags": [
      	null
    	]
  	}
	]
  },
  {
	"id": 4,
	"label": "ligne_4",
	"description": "This is the description",
	"picture_url": "https://www.pictures.com/example.jpg",
	"type": {
  	"id": 2,
  	"label": "location"
	},
	"entities": [
  	{
    	"id": 3,
    	"wynd_id": "",
    	"external_id": null,
    	"name": "",
    	"label": "PAUL Gare du Nord - RER",
    	"description": "",
    	"town": null,
    	"zipcode": null,
    	"address": null,
    	"address_additional": null,
    	"phone": null,
    	"mail": null,
    	"website": null,
    	"photo": null,
    	"logo": null,
    	"capital": null,
    	"code_rcs": null,
    	"code_siret": null,
    	"code_siren": null,
    	"code_ape": null,
    	"vat_number": null,
    	"legal_form": null,
    	"latitude": null,
    	"longitude": null,
    	"created_at": "2016-06-28T15:21:45+0200",
    	"updated_at": "2016-09-01T08:10:48+0200",
    	"is_visible": true,
    	"is_active": true,
    	"created_by": 1,
    	"tags": [
      	null,
      	{
        	"id": 5,
        	"label": "ligne_5",
        	"description": "This is the description",
        	"picture_url": "https://www.pictures.com/example.jpg",
        	"type": {
          	"id": 2,
          	"label": "location"
        	},
        	"entities": [
          	null
        	],
        	"products": []
      	}
    	]
  	}
	],
	"products": []
  },
  {
	"id": 5,
	"label": "ligne_5",
	"description": "This is the description",
	"picture_url": "https://www.pictures.com/example.jpg",
	"type": {
  	"id": 2,
  	"label": "location"
	},
	"entities": [
  	{
    	"id": 3,
    	"wynd_id": "",
    	"external_id": null,
    	"name": "",
    	"label": "PAUL Gare du Nord - RER",
    	"description": "",
    	"town": null,
    	"zipcode": null,
    	"address": null,
    	"address_additional": null,
    	"phone": null,
    	"mail": null,
    	"website": null,
    	"photo": null,
    	"logo": null,
    	"capital": null,
    	"code_rcs": null,
    	"code_siret": null,
    	"code_siren": null,
    	"code_ape": null,
    	"vat_number": null,
    	"legal_form": null,
    	"latitude": null,
    	"longitude": null,
    	"created_at": "2016-06-28T15:21:45+0200",
    	"updated_at": "2016-09-01T08:10:48+0200",
    	"is_visible": true,
    	"is_active": true,
    	"created_by": 1,
    	"tags": [
      	{
        	"id": 4,
        	"label": "ligne_4",
        	"description": "This is the description",
        	"picture_url": "https://www.pictures.com/example.jpg",
        	"type": {
          	"id": 2,
          	"label": "location"
        	},
        	"entities": [
          	null
        	],
        	"products": []
      	},
      	null
    	]
  	}
	],
	"products": []
  },
  {
	"id": 6,
	"label": "rer",
	"description": "This is the description",
	"picture_url": "https://www.pictures.com/example.jpg",
	"type": {
  	"id": 2,
  	"label": "location"
	},
	"entities": [],
	"products": []
  },
  {
	"id": 7,
	"label": "eurostar",
	"description": "This is the description",
	"picture_url": "https://www.pictures.com/example.jpg",
	"type": {
  	"id": 2,
  	"label": "location"
	},
	"entities": [],
	"products": []
  }
]
```





### GET  /api/tags/{tag_id}
Get one tag

#### Input : /api/tags/1

Ouput :
```json
{
  "id": 1,
  "label": "petit_dejeuner",
  "description": "This is the description",
  "picture_url": "https://www.pictures.com/example.jpg",
  "type": {
	"id": 1,
	"label": "desire"
  },
  "entities": [],
  "products": [
	{
  	"externalId": 1,
  	"externalRef": "Salade Paul",
  	"featured": false,
  	"picture": false,
  	"type": "Salade",
  	"categoryKvs": "3",
  	"tvaTx": "3.000",
  	"priceTtc": "7.00400000",
  	"priceHt": "6.80000000",
  	"prices": {
    	"1": {
      	"price_ttc": 7.004,
      	"price_ht": 6.8,
      	"price_per_unit": 0,
      	"unit_ratio": false,
      	"tva_tx": 3,
      	"to_sell": true
    	}
  	},
  	"product_origin": null,
  	"extra_data_image": false,
  	"extra_data_weight": 0,
  	"extra_data_weight_unit": false,
  	"root_category_id": false,
  	"root_category_label": false,
  	"category_limit": false,
  	"extra_data_packaging": false,
  	"extra_categories": [],
  	"id": 363,
  	"slug": "",
  	"ref": "SALADE_PAUL",
  	"label": "Salade Paul",
  	"description": "Filets de poulet, copeaux de parmesan, sauce Caesar, cro&ucirc;tons aill&eacute;s, salade, ciboulette.",
  	"to_sell": 1,
  	"barcode": null,
  	"tags": [
    	null
  	]
	}
  ]
}
```





### DELETE  /api/tags/{tag_id}
Delete one tag

Response code : HTTP_NO_CONTENT (204)

### PUT  /api/tags/{tag_id}
Update a tag

Example :/api/tags/1

```json
{
  "id": 1,
  "label": "petit_dejeuner",
  "description": "This is the description",
  "picture_url": "https://www.pictures.com/example.jpg",
  "type": {
	"id": 1,
	"label": "desire"
  },
  "entities": [],
  "products": [
	{
  	"externalId": 1,
  	"externalRef": "Salade Paul",
  	"featured": false,
  	"picture": false,
  	"type": "Salade",
  	"categoryKvs": "3",
  	"tvaTx": "3.000",
  	"priceTtc": "7.00400000",
  	"priceHt": "6.80000000",
  	"prices": {
    	"1": {
      	"price_ttc": 7.004,
      	"price_ht": 6.8,
      	"price_per_unit": 0,
      	"unit_ratio": false,
      	"tva_tx": 3,
      	"to_sell": true
    	}
  	},
  	"product_origin": null,
  	"extra_data_image": false,
  	"extra_data_weight": 0,
  	"extra_data_weight_unit": false,
  	"root_category_id": false,
  	"root_category_label": false,
  	"category_limit": false,
  	"extra_data_packaging": false,
  	"extra_categories": [],
  	"id": 363,
  	"slug": "",
  	"ref": "SALADE_PAUL",
  	"label": "Salade Paul",
  	"description": "Filets de poulet, copeaux de parmesan, sauce Caesar, cro&ucirc;tons aill&eacute;s, salade, ciboulette.",
  	"to_sell": 1,
  	"barcode": null,
  	"tags": [
    	null
  	]
	}
  ]
}
```



### POST  /api/tags
Create a tag

Create a tag with label ‘testB’ with entity 1 and product 363 and product 364
```json
{
  "label": "testB",
  "description": "My tag",
  "type": {
	"id": 1
  },
  "entities": [{
	"id": 3
  }],
  "products": []
}
```





### POST  /api/tags/{tag_id}
Post a picture to a tag

Post as form-data with “picture”, an image file under 2M.
The result is a Tag with the secure url of the uploaded image.

```json
{
  "id": 1,
  "label": "petit_dejeuner",
  "description": "This is the description",
  "picture_url": "https:// [...] /petit_dejeuner.jpg",
  "type": {
	"id": 1
  },
  "entities": [],
  "products": [
	{
  	"id": 363
	}
  ]
}
```




[*Retour en haut*](#sommaire)


# FACEBOOK CONNECT (Work In Progress)
Facebook Connect is a secure, fast and convenient way for people to log into an app.

Facebook Application (developers.facebook.com) :
The creation of a Facebook Application allows us to have the App ID and the App Secret. They are essential to the API to communicate with Facebook. We use the latest Facebook API version (v2.8) supported at least until October 2018.

We also need to create a Facebook product called “Facebook Login” to handle our authentication.

Facebook Login product (developers.facebook.com) :
In the settings part, “Client OAuth Login” and “Web OAuth Login” are activated and we need a valid OAuth redirect URI (In our case, https:// … /api/connect/facebook-check)


Permissions :
public_profile : Implied with every request and isn't required, although the best practice is to declare it. Provides access to a subset of items that are part of a person's public profile (id and name for our case)
email : Provides access to the person's primary email address

### GET  /api/facebook-generate-url
Generate the Facebook login Url with email permissions

#### Output :
```json
{
	"url": "https://www.facebook.com/v2.8/dialog/oauth?scopes%5B0%5D=public_profile&scopes%5B1%5D=email&state=328865e1eb064c632a080142344e9b1f&scope=public_profile%2Cemail&response_type=code&approval_prompt=auto&redirect_uri=http%3A%2F%2Fapi.docker%2Fapp_dev.php%2Fapi%2Fconnect%2Ffacebook-check&client_id=1849327745310986"
}
```






### GET  /api/connect/facebook-check
This is not a direct API route to call. This route handle the callback from facebook.com.

#### Output:
```json
{
	"is_authenticated": true,
	"customer": "test@test.com",
	"token": "ayJhbGciOiJSUzI1NiIsInR5cCI6IkpXUyJ9.eyJleHAiOjE0OTUzNzk0NTIsInVzZXJuYW1lIjoidmlsbGVnZXIuY0BnbWFpbC5jb20iLCJpYXQiOiIxNDg2NzM5NDUyIn0.qArpsLu6A9vyZkJwXHroIUCuO3JwYQhRDjbJXdc_NGGVjZam-2ludMZ1o2gjzi7pLkj3awmGI9jsNHFdjsxH7SH565rVPYLEzKfNzVEOyFgvNcLuHg2pkfYIlbXGQ5gTAiJLqyW_yWlfoKdKNCr9UVqxfJcsREu-jIyCn85CP1li17Vc6fgf3b6kbOKFgcPW9AYxRVKIq8Kmyr74PKLWCq1qLU4uwfrjSr6aT08gUBuJ87no46xmedy0cEb5Svm7KxQVkMriP74dUpfdXY5mr-oo1Y43G2EF0lsvylgT3reNIadErm1dX58Ply7B1i3dpSQNQ7QZaq5HYyfPJPq5uWeCDkDErQX8hsW1gYvrUawczAMToUAZBdqeFttAqbcTSqN7QKR7cyyEX6XHHldCe2yY9RtbICNRwjbhak8rXSah1IT-Fs8DAORInb4CZ1I1BNeftVA2DNdjyN1EMoP5ET6g6ggbFs_HdZiJuDlV70LbP9Uuv1g6cQBk09E9R2W1GpDc7TztsPY-KbK-0qIUgTamXKh1wY5T_IjZGR35HehYaWXUrW87wE0ukZTX1jcVgA4ehTTqIBg-BAGOuv4N5xJGSvgxcsnU8DnrofNYp2UdfqUgMi4uju7iQdnW4XsSSL5e1IKND6rZ3hDQnqTG3OKDvEk1upHFbddMIifppcI"
}
```



Facebook Connect Error management :

Customer decline global Facebook Access : "There was an error getting access from Facebook. Please try again."
Customer decline the email access : "Customer have not authorize Facebook to get email. Please unauthorize it, and retry."


[*Retour en haut*](#sommaire)


 # STATUS DEFINITION

**Status name EN**|**Status name FR**|**CODE**|**Description**
:-----:|:-----:|:-----:|:-----:
`OPEN`|OUVERT|0|Default order status. Defined when order number is created.
`VALIDATED`|Validé|2|Change to validated status when the entity accept the order at reception.
`IN PROGRESS`|En préparation|3|Change to status In Progress when the order is being managed (or sent to Kitchen) by the entity
`PROCESSED`|Finalisée|1|Change to status Processed when the order is done and recorded with all its details in the system
`DECLINED`|Refusée|-2|Change to status Declined when the entity decline the order when received
`CANCELED`|Annulée|-1|Change to status Canceled when the order is canceled after that the invoice been generated
`READY`|Prête|4|Change to status Ready when order preparation is done and the order is ready for delivery or takeaway or eatin.
`ABANDONED`|Abandonnée|-5|Change to status abandoned when the order is aborded before paiement
`CLOSED`|Clôturée|-4|Change to status closed when the order is automatically closed with Z report closing.
`TECHNICAL ERROR`|Erreur technique|-3|Change to status Technical Error when a technical error happened during order taking, processing or recording.
`DELIVERY IN PROGRESS`|En livraison|5|Change to status Delivery In Progress when the delivery operator has picked the order
`DELIVERED`|Délivrée|10|Change to status Delivered when the order is given to the customer. in this case, the order is deemed as closed.
`ERROR THIRD PARTY DELIVERY`|Erreur tiers livraison|-10|Change to status Error Third Party Delivery when the delivery operator return an error

[*Retour en haut*](#sommaire)


# EVENT GLOSSARY


**Name**|**Description**|**Route**
:-----:|:-----:|:-----:
`CUSTOMER_CREATED`|Create customer account|POST /customers
`CUSTOMER_AUTHENTICATED`|Customer Authentification|
`CUSTOMER_LOGGED_IN`|Customer succesfully authentificate|POST /customers/authenticate
`CUSTOMER_LOGGED_OUT`|Customer disconnected|
`CUSTOMER_PASSWORD_RECOVERING`|Retrieving password|
`CUSTOMER_PASSWORD_RECOVERED`|Password retrieved|
`CUSTOMER_EDITED`|Customer account modified|
`ORDER_CREATED`|Order created|
`ORDER_VALIDATED`|Order validated|
`ORDER_READY`|Order ready|
`ORDER_UPDATED`|Order updated|
`ORDER_CANCELLED`|Order cancelled|


[*Retour en haut*](#sommaire)
