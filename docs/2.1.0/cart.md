---
layout: page-classic-sidebar-left
title: Carrinho de Compras
previous: /docs/2.1.0/sku
next: /docs/2.1.0/order
---
---

Representa um carrinho de compras, e pode ser criado tanto pelo perfil `COMPRADOR`{:.custom-highlight}  como pelo perfil `VENDEDOR`{:.custom-highlight}. O carrinho de compras é composto por uma coleção não vazia de itens de carrinho.  

Um item de carrinho agrega as informações do SKU, sua a quantidade, preço e o método de envio. 

  
<a name="attributes"></a>
  
## Atributos  
-----------------------------------

**Id**{:.custom-attrib}  `number`{:.custom-tag}  
Identificador do carrinho (gerado automáticamente)  

**CreatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data de criação  

**UpdatedOn**{:.custom-attrib}  `datetime`{:.custom-tag}  
Data da última atualização  

**UserId**{:.custom-attrib}  `36`{:.custom-tag}  `string`{:.custom-tag}  
Identificador do usuário proprietário do carrinho  

``` javascript
 "99999999-9999-9999-9999-999999999999"
```

**Type**{:.custom-attrib}  `number`{:.custom-tag}  
Tipo de carrinho. Os valores possíveis são:  

``` javascript
 0 // privado  
 1 // social  
 2 // oferta do vendedor  
```
  

**MerchantId**{:.custom-attrib}  `opcional`{:.custom-tag}  `36`{:.custom-tag}  `string`{:.custom-tag}  
Identificador da loja. Só é utilizado quando o tipo de carrinho for uma oferta do vendedor (`Type = 2`)     

``` javascript
 "99999999-9999-9999-9999-999999999999"
```

**Label**{:.custom-attrib}  `128`{:.custom-tag}  `string`{:.custom-tag}  
Nome do carrinho  
  

**CouponCode**{:.custom-attrib}  `opcional`{:.custom-tag}  `36`{:.custom-tag}  `string`{:.custom-tag}  
Código de cupom de desconto     
  
**Permalink**{:.custom-attrib}  `string`{:.custom-tag}  
Link de exibição do carrinho  
  

**CartItems**{:.custom-attrib}  `array`{:.custom-tag}  
Lista de [Itens de Carrinho]({{ site.baseurl }}{% link docs/2.1.0/cartitem.md %})   

  
<a style="float: right;" href="#attributes"><i class="fa fa-angle-double-up fa-fw"></i></a>

<a name="http_operations"></a>

## Operações HTTP
-----------------------------------

`POST`{:.http-post} [/api/cart](#post_cart){:.custom-attrib}  
Criação de carrinho  

`PUT`{:.http-put} [/api/cart/{cartId}](#put_cart){:.custom-attrib}  
Atualização do carrinho {cartId}  

`GET`{:.http-get} [/api/cart/{cartId}](#getbyid_cart){:.custom-attrib}  
Obtenção do carrinho {cartId} por Id

`GET`{:.http-get} [/api/cart](#get_cart){:.custom-attrib}  
Listagem dos carrinhos  
  

<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>

<a name="post_cart"></a>

#### `POST`{:.http-post} Criação de carrinho  
-----------------------------------------


**REQUEST:**  

``` http
POST /api/cart/ HTTP/1.1
Content-Type: application/json
```

``` json
{
  "Type": 0,
  "Label": "Meu Carrinho de Compras"
}
```

**RESPONSE:**  

``` http
HTTP/1.1 201 Created
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Id": 999,
  "Links": {
    "self": {
      "href": "/api/cart/999",
      "method": "GET"
    }
  }
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
<a name="put_cart"></a>

#### `PUT`{:.http-put} Atualização do carrinho 
-------------------------------------------
  
**PARÂMETROS:**  

``` csharp
cartId: int  // id do carrinho 
```

**REQUEST:**  

``` http
PUT /api/cart/{cartId} HTTP/1.1
Content-Type: application/json
```

``` json
{
  "Type": 1,
  "Label": "Meu novo Carrinho de Compras",
  "CouponCode": "PROMOCODE" 
}
```

**RESPONSE:**  

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Id": 999,
  "Links": {
    "self": {
      "href": "/api/cart/999",
      "method": "GET"
    }
  }
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
<a name="getbyid_cart"></a>

#### `GET`{:.http-get} Obtenção do carrinho por Id
-------------------------------------------------

**PARÂMETROS:**  

``` csharp
cartId: int  // id do carrinho  
```

**REQUEST:**  

``` http
GET /api/cart/{cartId}/ HTTP/1.1
Content-Type: application/json
```

**RESPONSE:**  

``` http
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
```
``` json
{
  "Id": 999,
  "CreatedOn": "2017-02-11T14:10:39.1083643",
  "UpdatedOn": "2017-02-11T14:10:39.442996",
  "UserId": "7a6acd59-a7b1-4a7f-bc2d-0a3f6014cc4a",
  "Type": 2,
  "MerchantId": "612a64c0-22e7-4fb9-aa2b-eb31670f207f",
  "Label": "Exemplo de carrinho Oferta",
  "CouponCode": "PROMO001",
  "Permalink": "https://brasp.ag/cart/999",
  "CartItems": [
    {
      "Id": 100,
      "IsActive": true,
      "ProductId": 9999,
      "Caption": "Uma breve descrição do produto",
      "MerchantId": "99999999-9999-9999-9999-999999999999",
      "MerchantName": "BlackBox Virtual Store",
      "Quantity": 10,
      "Price": {
        "Amount": 1000,
        "Currency": "BRL"
      },
      "Sku": {
        "Id": 332,
        "Sku": "SKU332",
        "Status": 0,
        "Description": "Descrição do SKU de Produto",
        "Shipping": {
          "Type": 1,
          "Price": {
            "Amount": 500,
            "Currency": "BRL"
          }
        }
      }
    }
  ]
}
```
  
<a style="float: right;" href="#http_operations"><i class="fa fa-angle-double-up fa-fw"></i></a>
  
<a name="get_cart"></a>

#### `GET`{:.http-get} Listagem dos carrinhos
---------------------------------------------------
  

**REQUEST:**  

``` http
GET /api/cart/ HTTP/1.1
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
  
