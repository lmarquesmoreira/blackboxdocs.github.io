---
layout: page-classic-sidebar-left
title: SKU
previous: /docs/2.1.0/product
next: 
---
---

SKUs são gerenciados pelo `VENDEDOR`{:.custom-highlight} e representam uma variação específica de produto, como tamanho, cor ou sabor. 

 
<a name="attributes"></a>
  
## Atributos do objeto
-----------------------------------

**Id**{:.custom-attrib}  `int`{:.custom-tag}  
Identificador do SKU  

**Sku**{:.custom-attrib}  `32`{:.custom-tag}  `string`{:.custom-tag}  
Valor do SKU

**CreatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data da criação do objeto

**UpdatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data da última atualização do objeto

**Status**{:.custom-attrib}  `int`{:.custom-tag}  
Status do SKU no estoque. Valores possíveis: (0) em estoque, (1) sem estoque, (2) sob demanda, (3) descontinuado

**Name**{:.custom-attrib}  `256`{:.custom-tag}  `string`{:.custom-tag}  
Nome do SKU

**Description**{:.custom-attrib}  `2048`{:.custom-tag}  `string`{:.custom-tag}  
Descrição do SKU

**ImageUrl**{:.custom-attrib}  `opcional`{:.custom-tag}  `256`{:.custom-tag}  `string`{:.custom-tag}  
URL para a imagem do SKU

**Inventory.UpdatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data da última atualização do SKU no inventório

**Inventory.Quantity**{:.custom-attrib}  `int`{:.custom-tag}  
Quantidade de itens disponíveis no inventório  

**Inventory.Type**{:.custom-attrib}  `int`{:.custom-tag}  
Tipo de estoque. Valores possíveis: (0) Finito, (1) Infinito  

**Dimensions.Weight**{:.custom-attrib}  `opcional`{:.custom-tag}  `float`{:.custom-tag}  
Peso do item (em gramas)  

**Dimensions.Height**{:.custom-attrib}  `opcional`{:.custom-tag}  `float`{:.custom-tag}  
Altura do item (em centímetros)  

**Dimensions.Lenght**{:.custom-attrib}  `opcional`{:.custom-tag}  `float`{:.custom-tag}  
Comprimento do item (em centímetros)  

**Dimensions.Width**{:.custom-attrib}  `opcional`{:.custom-tag}  `float`{:.custom-tag}  
Largura do item  (em centímetros)  

**ListPrice.CreatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data de criação do preço de tabela  

**ListPrice.Amount**{:.custom-attrib}  `int`{:.custom-tag}  
Valor em centavos do preço de tabela. Exemplo: 150 (1,50)  

**ListPrice.Currency**{:.custom-attrib}  `string`{:.custom-tag}  
Código ISO 4217 da moeda utilizada no preço de tabela. Exemplos: BRL, USD, EUR  

**SellPrice.CreatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data de criação do preço de venda  

**SellPrice.Amount**{:.custom-attrib}  `int`{:.custom-tag}  
Valor em centavos do preço de venda. Exemplo: 150 (1,50)  

**SellPrice.Currency**{:.custom-attrib}  `string`{:.custom-tag}  
Código ISO 4217 da moeda utilizada no preço de venda. Exemplos: BRL, USD, EUR  

  
<a style="float: right;" href="#attributes"><i class="fa fa-angle-double-up fa-fw"></i></a>

<a name="http_operations"></a>

## Operações HTTP
-----------------------------------

`POST`{:.http-post} [/api/product/{productId}/sku](#post_sku){:.custom-attrib}  
Criação de SKU para o produto {productId}  

`PUT`{:.http-put} [/api/product/{productId}/sku/{skuId}](#put_sku){:.custom-attrib}  
Atualização de SKU {skuId} para o produto {productId}  

`GET`{:.http-get} [/api/product/{productId}/sku/{skuId}](#getbyid_sku){:.custom-attrib}  
Obtenção de SKU do produto {productId} por Id

`GET`{:.http-get} [/api/product/{productId}/sku](#get_sku){:.custom-attrib}  
Listagem dos SKUs do produto {productId}  

`GET`{:.http-get} [/api/product/](#get_product){:.custom-attrib}  
Listagem de Produtos  

<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>

<a name="post_product"></a>

#### `POST`{:.http-post} Criação de Produto 
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

#### `PUT`{:.http-put} Atualização de Produto 
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

#### `GET`{:.http-get} Obtenção de Produto por Id
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

#### `GET`{:.http-get} Listagem de Produtos
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
  