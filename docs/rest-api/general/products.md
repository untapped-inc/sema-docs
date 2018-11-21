disqus: sema-docs

Product services. Returns an array of products that can be purchased by customers.

## Endpoints
<span class="status-macro aui-lozenge conf-macro output-inline get-method">GET</span> sema/products

## Headers
| Header | Required | Example | Description
| ------ | -------- | ------- | -----------
| Authorization | YES | `Authorization: Bearer xxxx.yyyy.zzzz` | Contains token as received from login

## Path Parameters
None

## Query Parameters
| Parameter | Required | Format	| Description
| --------- | -------- | ------ | -----------
| updated-date | NO	| string ISO 8601 format | Returns all products whose updated date is LATER than updated-date.

## Sample request

```
curl --header "authorization: Bearer <token>" http://localhost:3001/sema/products
```


## Sample Response

```json
{
  "products": [
    {
      "productId": 17,
      "active": true,
      "base64encodedImage":"<Image Data>",
      "categoryId": 3,
      "description": "1.5 Liter water bottle",
      "maximumQuantity": null,
      "minimumQuantity": null,
      "priceAmount": 2600,
      "priceCurrency": "UGX",
      "sku": "sku1",
      "updatedDate": "2018-01-01T08:00:00.000Z",
      "unitPerProduct": 1.5,
      "unitMeasure": "liters",
      "cogsAmount": 1300
    },
    {
      "productId": 18,
      "active": true,
      "base64encodedImage":"<Image Data>",
      "categoryId": 3,
      "description": "5 Liter water bottle",
      "maximumQuantity": null,
      "minimumQuantity": null,
      "priceAmount": 4000,
      "priceCurrency": "UGX",
      "sku": "sku2",
      "updatedDate": "2018-01-01T08:00:00.000Z",
      "unitPerProduct": 5,
      "unitMeasure": "liters",
      "cogsAmount": 2000
    },
    {
      "productId": 19,
      "active": true,
      "base64encodedImage": "<Image Data>",
      "categoryId": 3,
      "description": "18.9 Liter water jug",
      "maximumQuantity": null,
      "minimumQuantity": null,
      "priceAmount": 20000,
      "priceCurrency": "UGX",
      "sku": "sku3",
      "updatedDate": "2018-08-07T03:18:14.000Z",
      "unitPerProduct": 18.9,
      "unitMeasure": "liters",
      "cogsAmount": 10000
    },
    {
      "productId": 20,
      "active": true,
      "base64encodedImage":"<Image Data>",
      "categoryId": 3,
      "description": "20 Liter water jug",
      "maximumQuantity": null,
      "minimumQuantity": null,
      "priceAmount": 25000,
      "priceCurrency": "UGX",
      "sku": "sku4",
      "updatedDate": "2018-01-01T08:00:00.000Z",
      "unitPerProduct": 20,
      "unitMeasure": "liters",
      "cogsAmount": 13000
    }
  ]
}
```