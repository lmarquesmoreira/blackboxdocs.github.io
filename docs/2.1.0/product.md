---
layout: page-classic-sidebar-left
title: Produto
previous: /docs/2.1.0/oauth
next: /docs/2.1.0/shopper
---
---
Última Atualização: `05/02/2017`{:.custom-highlight}  

Permite ao `VENDEDOR`{:.custom-highlight} cadastrar e gerenciar seus produtos e respectivos SKUs.  
  
## Atributos do objeto
-----------------------------------

Atributo | Descrição | 
------------ | -------------
Id | Identificador do produto  | `int`{:.custom-tag}  
CreatedOn | Data da criação  | `datetime`{:.custom-tag}  
UpdatedOn | Data da última atualização  | `datetime`{:.custom-tag}  
MerchantId | Identificador da loja  | `guid`{:.custom-tag}  
Name | Nome do produto  | `string`{:.custom-tag}  `256`{:.custom-tag} 
Description | Descrição do produto  | `string`{:.custom-tag}  `2048`{:.custom-tag} 
IsEnabled | Flag que indica se produto está habilitado  | `bool`{:.custom-tag}  
Manufacturer.Name | Fabricante  | `string`{:.custom-tag}  `64`{:.custom-tag}  `opcional`{:.custom-tag}  
Manufacturer.Warranty | Garantia do produto (em meses)  |  `int`{:.custom-tag}  `opcional`{:.custom-tag}  
Manufacturer.Model | Modelo do produto  | `string`{:.custom-tag}  `64`{:.custom-tag}  `opcional`{:.custom-tag}  
Skus | Lista de SKUs do produto  | `array`{:.custom-tag}  `opcional`{:.custom-tag}  

<a name="http_operations"></a>

## Operações HTTP
-----------------------------------

Verbo | Path | Descrição | 
------------ | ------------- | -------------
`POST`{:.http-post} | [/api/product/](#post_product) | Criação de produto  | 
`PUT`{:.http-put} | [/api/product/{productId}](#put_product) | Atualização de produto  | 
`GET`{:.http-get} | [/api/product/{productId}](#getbyid_product) | Obtenção de Produto por Id  | 
`GET`{:.http-get} | [/api/product/](#get_product) | Listagem de Produtos  | 
  

<a name="post_product"></a>

### `POST`{:.http-post} Criação de Produto 
-------------------------------------------

**REQUEST:**  

``` http
POST /api/product/ HTTP/1.1
Host: {blackbox endpoint}
Authorization: Bearer {access_token}
Content-Type: application/json
```

``` json
{
  "MerchantId": "99999999-9999-9999-9999-999999999999",
  "Name": "Nome do produto",
  "Description": "Descrição do produto",
  "Manufacturer": {
    "Name": "Fabricante do produto", 
    "Warranty": 12,
    "Model": "MODEL0001"
  }
}
```

**RESPONSE:**  

``` http
HTTP/1.1 201 Created
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Id": 9999,
  "Links": {
    "self": {
      "href": "/api/product/9999",
      "method": "GET"
    }
  }
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
<a name="put_product"></a>

### `PUT`{:.http-put} Atualização de Produto 
-------------------------------------------
  
**PARÂMETROS:**  

``` csharp
productId: int  // id do produto
```

**REQUEST:**  

``` http
PUT /api/product/{productId} HTTP/1.1
Host: {blackbox endpoint}
Authorization: Bearer {access_token}
Content-Type: application/json
```

``` json
{
  "MerchantId": "99999999-9999-9999-9999-999999999999",
  "Name": "Nome do produto",
  "Description": "Descrição do produto",
  "Manufacturer": {
    "Name": "Fabricante do produto", 
    "Warranty": 12,  
    "Model": "MODEL0001" 
  }
}
```

**RESPONSE:**  

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Id": 9999,
  "Links": {
    "self": {
      "href": "/api/product/9999",
      "method": "GET"
    }
  }
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
<a name="getbyid_product"></a>

### `GET`{:.http-get} Obtenção de Produto por Id
-------------------------------------------------

**PARÂMETROS:**  

``` csharp
productId: int  // id do produto
```

**REQUEST:**  

``` http
GET /api/product/{productId} HTTP/1.1
Host: {blackbox endpoint}
Authorization: Bearer {access_token}
Content-Type: application/json
```

**RESPONSE:**  

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Id": 9999,
  "CreatedOn": "2017-01-23T09:44:13.3466667",
  "UpdatedOn": "2017-01-23T09:44:13.3466667",
  "MerchantId": "99999999-9999-9999-9999-999999999999",
  "Name": "Nome do produto",
  "Description": "Descrição do produto",
  "Manufacturer": {
    "Name": "Fabricante do produto",
    "Warranty": 12,
    "Model": "MODEL0001"
  },
  "IsEnabled": true,
  "Skus": [
    {
      "Id": 9999999,
      "Sku": "PROD9999",
      "CreatedOn": "2017-01-23T09:44:15.16",
      "UpdatedOn": "2017-01-23T09:44:15.16",
      "Status": 0,
      "Name": "SKU PROD9999",
      "Description": "Descrição do item",
      "Inventory": {
        "UpdatedOn": "2017-01-23T09:44:14.66",
        "Quantity": 100,
        "Type": 0
      },
      "Dimensions": {
        "Weight": 1.0,
        "Height": 2.5,
        "Lenght": 2.5,
        "Width": 10
      },
      "ListPrice": {
        "CreatedOn": "2017-01-23T09:44:13.97",
        "Amount": 10000,
        "Currency": "BRL"
      },
      "SellPrice": {
        "CreatedOn": "2017-01-23T09:44:14.16",
        "Amount": 9000,
        "Currency": "BRL"
      }
    }
  ]
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
<a name="get_product"></a>
### `GET`{:.http-get} Listagem de Produtos
-------------------------------------------------

**REQUEST:**  

``` http
GET /api/product/ HTTP/1.1
Host: {blackbox endpoint}
Authorization: Bearer {access_token}
Content-Type: application/json
```

**RESPONSE:**  

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
```
``` json
[
  { ... },
  { ... },
  { ... }
]
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>