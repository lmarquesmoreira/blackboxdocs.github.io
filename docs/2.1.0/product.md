---
layout: page-classic-sidebar-left
title: Produto
previous: /docs/2.1.0/oauth
next: /docs/2.1.0/sku
---
---

Permite ao `VENDEDOR`{:.custom-highlight} cadastrar e gerenciar seus produtos. Cada produto possui uma coleção de [SKUs]({{ site.baseurl }}{% link docs/2.1.0/sku.md %}).  

  
<a name="attributes"></a>
  
## Atributos  
-----------------------------------

**Id**{:.custom-attrib}  `number`{:.custom-tag}  
Identificador do produto (gerado automaticamente)  

**CreatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data da criação  

**UpdatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data da última atualização  

**MerchantId**{:.custom-attrib}  `36`{:.custom-tag}  `string`{:.custom-tag}  
Identificador da loja   

``` javascript
 "99999999-9999-9999-9999-999999999999"
```

**Name**{:.custom-attrib}  `256`{:.custom-tag}  `string`{:.custom-tag}  
Nome do produto

**Caption**{:.custom-attrib}  `128`{:.custom-tag}  `string`{:.custom-tag}  
Uma breve frase com a descrição do produto para exibição  

**Description**{:.custom-attrib}  `1024`{:.custom-tag}  `string`{:.custom-tag}  
Descrição do produto  

**Permalink**{:.custom-attrib}  `string`{:.custom-tag}  
Link de exibição do produto  

```
https://brasp.ag/product/9999
```

**IsEnabled**{:.custom-attrib}  `boolean`{:.custom-tag}  
Flag que indica se produto está habilitado para publicação no marketplace  

**DefaultSku**{:.custom-attrib}  `opcional`{:.custom-tag}  `32`{:.custom-tag}  `string`{:.custom-tag}  
SKU padrão para exibição na *user interface*  

**Metadata**{:.custom-attrib}  `opcional`{:.custom-tag}  `object`{:.custom-tag}  
Conjunto de pares chave-valor para armazenar informações adicionais sobre o produto  

``` json
{
    "id-local": "101020",
    "categoria": "utilidades"
}
```

**Manufacturer.Name**{:.custom-attrib}  `opcional`{:.custom-tag}  `64`{:.custom-tag}  `string`{:.custom-tag}  
Fabricante do produto

**Manufacturer.Model**{:.custom-attrib}  `opcional`{:.custom-tag}  `64`{:.custom-tag}  `string`{:.custom-tag}  
Modelo do produto  

**Manufacturer.Warranty**{:.custom-attrib}  `opcional`{:.custom-tag}  `number`{:.custom-tag}  
Garantia do produto (em meses)  

**Skus**{:.custom-attrib}  `opcional`{:.custom-tag}  `array`{:.custom-tag}  
Lista de [SKUs]({{ site.baseurl }}{% link docs/2.1.0/sku.md %}) do produto  
  
<a style="float: right;" href="#attributes"><i class="fa fa-angle-double-up fa-fw"></i></a>

<a name="http_operations"></a>

## Operações HTTP
-----------------------------------

`POST`{:.http-post} [/api/product/](#post_product){:.custom-attrib}  
Criação de produto  

`PUT`{:.http-put} [/api/product/{productId}](#put_product){:.custom-attrib}  
Atualização de produto  

`GET`{:.http-get} [/api/product/{productId}](#getbyid_product){:.custom-attrib}  
Obtenção de Produto por Id  

`GET`{:.http-get} [/api/product/](#get_product){:.custom-attrib}  
Listagem de Produtos  

<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>

<a name="post_product"></a>

#### `POST`{:.http-post} Criação de Produto 
-------------------------------------------

**REQUEST:**  

``` http
POST /api/product/ HTTP/1.1
Content-Type: application/json
```

``` json
{
  "MerchantId": "99999999-9999-9999-9999-999999999999",
  "Name": "Nome do produto",
  "Caption": "Uma breve descrição do produto",
  "Description": "Descrição mais detalhada do produto",
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
Content-Type: application/json
```

``` json
{
  "Name": "Nome do produto",
  "Description": "Descrição do produto",
  "Caption": "Uma breve descrição do produto",
  "DefaultSku": "PROD9999",
  "Metadata": {
    "id-local": "101020",
    "categoria": "utilidades"
  },
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
  "Caption": "Uma breve descrição do produto",
  "Description": "Descrição mais detalhada do produto",
  "Manufacturer": {
    "Name": "Fabricante do produto",
    "Warranty": 12,
    "Model": "MODEL0001"
  },
  "Metadata": {
    "id-local": "101020",
    "categoria": "utilidades"
  },
  "IsEnabled": true,
  "DefaultSku": "PROD9999",
  "Skus": [
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
  

