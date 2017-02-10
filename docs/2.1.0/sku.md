---
layout: page-classic-sidebar-left
title: SKU
previous: /docs/2.1.0/product
next: 
---
---

SKUs, ou *Stock Keeping Units*, representam uma variação específica do [produto]({{ site.baseurl }}{% link docs/2.1.0/product.md %}), como tamanho, cor ou sabor. Cada produto deve possuir ao menos um SKU antes de ser publicado.   

  
<a name="attributes"></a>
  
## Atributos  
-----------------------------------

**Id**{:.custom-attrib}  `number`{:.custom-tag}  
Identificador do SKU (gerado automáticamente)  

**Sku**{:.custom-attrib}  `32`{:.custom-tag}  `string`{:.custom-tag}  
Valor do SKU  

**UpdatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data da última atualização  

**Description**{:.custom-attrib}  `opcional`{:.custom-tag}  `512`{:.custom-tag}  `string`{:.custom-tag}  
Descrição do SKU

**Images**{:.custom-attrib}  `opcional`{:.custom-tag}  `array`{:.custom-tag}  
Array com até 8 URLs de imagens para o SKU  

``` json
[
  "http://www.myimages.com/image1.png",
  "http://www.myimages.com/image2.png",
  "http://www.myimages.com/image3.png"
]
```

**Attributes**{:.custom-attrib}  `opcional`{:.custom-tag}  `object`{:.custom-tag}  
Conjunto de pares chave-valor para armazenar até 5 atributos ao SKU. Exemplo:  

``` json
{
  "cor": "vermelho", 
  "tamanho": "médio" 
}
```
  
**Inventory.Status**{:.custom-attrib}  `number`{:.custom-tag}  
Estado do SKU no estoque. Os valores possíveis são:  

``` javascript
 0 // em estoque  
 1 // fora de estoque  
 2 // aceito sob demanda  
 3 // descontinuado  
```
  

**Inventory.UpdatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data da última atualização do SKU no inventório

**Inventory.Quantity**{:.custom-attrib}  `number`{:.custom-tag}  
Quantidade de itens disponíveis no inventório  

**Inventory.Type**{:.custom-attrib}  `number`{:.custom-tag}  
Tipo de estoque. Os valores possíveis são:  

``` javascript
 0 // finito  
 1 // infinito  
```
  

**Dimensions.Weight**{:.custom-attrib}  `opcional`{:.custom-tag}  `number`{:.custom-tag}  
Peso do item (em gramas)  

**Dimensions.Height**{:.custom-attrib}  `opcional`{:.custom-tag}  `number`{:.custom-tag}  
Altura do item (em centímetros)  

**Dimensions.Lenght**{:.custom-attrib}  `opcional`{:.custom-tag}  `number`{:.custom-tag}  
Comprimento do item (em centímetros)  

**Dimensions.Width**{:.custom-attrib}  `opcional`{:.custom-tag}  `number`{:.custom-tag}  
Largura do item  (em centímetros)  

**Price.Amount**{:.custom-attrib}  `number`{:.custom-tag}  
Valor em centavos do preço de venda. Exemplo: 150 (1,50)  

**Price.Currency**{:.custom-attrib}  `string`{:.custom-tag}  
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

`PUT`{:.http-put} [/api/product/{productId}/sku/{skuId}/inventory](#put_inventory){:.custom-attrib}  
Atualização de estoque para o SKU {skuId} do produto {productId}  

`GET`{:.http-get} [/api/product/{productId}/sku/{skuId}/inventory](#get_inventory){:.custom-attrib}  
Obtenção de estoque do SKU {skuId}  

`PUT`{:.http-put} [/api/product/{productId}/sku/{skuId}/price](#put_price){:.custom-attrib}  
Atualização do preço de venda do SKU {skuId}  

`GET`{:.http-get} [/api/product/{productId}/sku/{skuId}/price](#get_price){:.custom-attrib}  
Obtenção do preço de venda do SKU {skuId}  

<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>

<a name="post_sku"></a>

#### `POST`{:.http-post} Criação de SKU  
-----------------------------------------

**PARÂMETROS:**  

``` csharp
productId: int  // id do produto
```

**REQUEST:**  

``` http
POST /api/product/{productId}/sku HTTP/1.1
Content-Type: application/json
```

``` json
{
  "Sku": "PROD9999",
  "Description": "Descrição do SKU de Produto",
  "Inventory": {
    "Status": 0,
    "Quantity": 10,
    "Type": 0
  },
  "Dimensions": {
    "Weight": 1.0,
    "Height": 2.5,
    "Lenght": 2.5,
    "Width": 10
  },
  "Images": [
    "http://www.myimages.com/image1.png",
    "http://www.myimages.com/image2.png",
    "http://www.myimages.com/image3.png"
  ],
  "Attributes": {
    "cor": "vermelho",
    "tamanho": "médio" 
  },
  "Price": {
    "Currency": "BRL",
    "Amount" : 9000
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
      "href": "/api/product/{productId}/sku/9999",
      "method": "GET"
    }
  }
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
<a name="put_sku"></a>

#### `PUT`{:.http-put} Atualização de SKU 
-------------------------------------------
  
**PARÂMETROS:**  

``` csharp
productId: int  // id do produto
skuId: int  // id do sku
```

**REQUEST:**  

``` http
PUT /api/product/{productId}/sku/{skuId} HTTP/1.1
Content-Type: application/json
```

``` json
{
  "Description": "Nova descrição do SKU de Produto",
  "Dimensions": {
    "Weight": 1.0,
    "Height": 2.5,
    "Lenght": null,
    "Width": 10
  },
  "Attributes": {
    "cor": "verde", 
    "tamanho": "grande" 
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
      "href": "/api/product/{productId}/sku/9999",
      "method": "GET"
    }
  }
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
<a name="getbyid_sku"></a>

#### `GET`{:.http-get} Obtenção de SKU por Id
-------------------------------------------------

**PARÂMETROS:**  

``` csharp
productId: int  // id do produto  
skuId: int  // id do sku  
```

**REQUEST:**  

``` http
GET /api/product/{productId}/sku/{skuId} HTTP/1.1
Content-Type: application/json
```

**RESPONSE:**  

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Id": 9999999,
  "Sku": "PROD9999",
  "UpdatedOn": "2017-01-23T09:44:15.16",
  "Description": "Descrição do item",
  "Inventory": {
    "UpdatedOn": "2017-01-23T09:44:14.66",
    "Status": 0,
    "Quantity": 100,
    "Type": 0
  },
  "Dimensions": {
    "Weight": 1.0,
    "Height": 2.5,
    "Lenght": 2.5,
    "Width": 10
  },
  "Images": [
    "http://www.myimages.com/image1.png",
    "http://www.myimages.com/image2.png",
    "http://www.myimages.com/image3.png"
  ],
  "Attributes": {
    "cor": "vermelho", 
    "tamanho": "médio" 
  },
  "Price": {
    "Amount": 9000,
    "Currency": "BRL"
  }
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
<a name="get_sku"></a>

#### `GET`{:.http-get} Listagem de SKUs do Produto
---------------------------------------------------
  
**PARÂMETROS:**  

``` csharp
productId: int  // id do produto  
```

**REQUEST:**  

``` http
GET /api/product/{productId}/sku HTTP/1.1
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
  