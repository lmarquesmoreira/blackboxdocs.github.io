---
layout: page-classic-sidebar-left
title: Pedido
previous: /docs/2.1.0/cart
next: 
---
---

Pedidos são criados a partir do checkout de um carrinho de compras. Um pedido é composto por ao menos um item de pedido.  

  
<a name="attributes"></a>
  
## Atributos  
-----------------------------------

**Id**{:.custom-attrib}  `number`{:.custom-tag}  
Identificador do pedido (gerado automáticamente)  

**CreatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data da criação  

**Status.Code**{:.custom-attrib}  `number`{:.custom-tag}  
Estado atual do pedido. Os valores possíveis são:  

``` javascript
 0 // criado  
 1 // pagamento pendente  
 2 // pagamento confirmado  
 10 // enviado  
 20 // cancelado  
 30 // entregue  
```
  
**Customer.UserId**{:.custom-attrib}  `36`{:.custom-tag}  `string`{:.custom-tag}  
Identificador do usuário proprietário do carrinho  

``` javascript
 "99999999-9999-9999-9999-999999999999"
```

**Customer.Name**{:.custom-attrib}  `256`{:.custom-tag}  `string`{:.custom-tag}  
Nome completo do comprador  

**Customer.Email**{:.custom-attrib}  `256`{:.custom-tag}  `string`{:.custom-tag}  
Endereço de e-mail do comprador  

**Customer.IpAddress**{:.custom-attrib}  `32`{:.custom-tag}  `string`{:.custom-tag}  
Endereço IPv4 do comprador  

**Shipping.Type**{:.custom-attrib}  `32`{:.custom-tag}  `string`{:.custom-tag}  
Método de envio (frete)   

**Shipping.Price**{:.custom-attrib}  `opcional`{:.custom-tag}  `object`{:.custom-tag}  
Custo do método de envio  

**Shipping.Address**{:.custom-attrib}  `opcional`{:.custom-tag}  `object`{:.custom-tag}  
Endereço de entrega do pedido  

**Payment.Type**{:.custom-attrib}  `number`{:.custom-tag}  
Código do meio de pagamento utilizado. Os valores possíveis são:  

``` javascript
 0 // cartão de crédito  
 1 // cartão de débito  
```
  
**Payment.Object**{:.custom-attrib}  `object`{:.custom-tag}  
Dados do meio de pagamento utilizado  
  

**Device.Id**{:.custom-attrib}  `opcional`{:.custom-tag}  `36`{:.custom-tag}  `string`{:.custom-tag}  
Identificador do dispositivo acionador. Só é utilizado quando o pedido for gerado a partir de um dispositivo IoT  
  

**OrderItems**{:.custom-attrib}  `array`{:.custom-tag}  
Coleção de itens que compõem o pedido  

  
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
  
<a name="put_inventory"></a>

#### `PUT`{:.http-put} Atualização de estoque do SKU 
-------------------------------------------
  
**PARÂMETROS:**  

``` csharp
productId: int  // id do produto
skuId: int  // id do sku
```

**REQUEST:**  

``` http
PUT /api/product/{productId}/sku/{skuId}/inventory HTTP/1.1
Content-Type: application/json
```

``` json
{
  "Status": 0,
  "Quantity": 100,
  "Type": 0
}
```

**RESPONSE:**  

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Id": 999999,
  "Links": {
    "self": {
      "href": "/api/product/9999/sku/999999",
      "method": "GET"
    }
  }
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
    
<a name="get_inventory"></a>

#### `GET`{:.http-get} Obtenção de estoque do SKU 
-------------------------------------------
  
**PARÂMETROS:**  

``` csharp
productId: int  // id do produto
skuId: int  // id do sku
```

**REQUEST:**  

``` http
GET /api/product/{productId}/sku/{skuId}/inventory HTTP/1.1
Content-Type: application/json
```
  

**RESPONSE:**  

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Status": 0,
  "Quantity": 100,
  "Type": 0
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
    
<a name="put_price"></a>

#### `PUT`{:.http-put} Atualização do preço de venda do SKU 
-------------------------------------------
  
**PARÂMETROS:**  

``` csharp
productId: int  // id do produto
skuId: int  // id do sku
```

**REQUEST:**  

``` http
PUT /api/product/{productId}/sku/{skuId}/price HTTP/1.1
Content-Type: application/json
```

``` json
{
  "Amount": 10000,
  "Currency": "BRL"  
}
```

**RESPONSE:**  

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Id": 999999,
  "Links": {
    "self": {
      "href": "/api/product/9999/sku/999999",
      "method": "GET"
    }
  }
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
    
<a name="get_price"></a>

#### `GET`{:.http-get} Obtenção do preço de venda do SKU 
-------------------------------------------
  
**PARÂMETROS:**  

``` csharp
productId: int  // id do produto
skuId: int  // id do sku
```

**REQUEST:**  

``` http
GET /api/product/{productId}/sku/{skuId}/price HTTP/1.1
Content-Type: application/json
```
  

**RESPONSE:**  

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Amount": 10000,
  "Currency": "BRL"  
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  