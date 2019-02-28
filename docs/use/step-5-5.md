[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step55"></div>
## 5.5. Obtener intención de pago.

Este método permite obtener una intención de pago previamente generada.

URL: `api/payment-intent/show.json`

Método HTTP: `GET`

Documentación completa de la API:
[Ir a la documentación](https://test.mpandco.com/docs#get--api-payment-intent-show.json)

### Ejemplo de petición:

    curl -X GET \
      'https://test.mpandco.com/api/payment-intent/show.json?id=03b9f66c-fefb-11e8-a647-b62cbc289574' \
      -H 'authorization: Bearer OAUTH-TOKEN'

### Respuesta:

200 - Correcto. Retorna JSON de tipo 'PaymentIntent'

Ejemplo de respuesta (200):

    {
       "id":"03b9f66c-fefb-11e8-a647-b62cbc289574",
       "intent":"sale",
       "state":"created",
       "redirect_urls":{
         "return_url":"http://localhost/payments/ExecutePayment.php?success=true&carId=200",
         "cancel_url":"http://localhost/payments/ExecutePayment.php?success=false&carId=200",
         "history_responses":[

         ]
       },
       "total":{
       "currency":{
            "id":"VES"
          },
          "items":17.5,
          "shipping":0,
          "tax":1.3,
          "amount":18.8
       },
       "transactions":[
          {
             "id":"03bb1538-fefb-11e8-a647-b62cbc289574",
             "amount":{
                "currency":{
                   "id":"VES"
                },
                "total":20,
                "details":{
                   "shipping":0,
                   "tax":1.3,
                   "sub_total":17.5
               }
             },
             "items":[
                {
                   "name":"telefono",
                   "quantity":1,
                   "currency":{
                      "id":"VES"
                   },
                   "sku":"P001",
                   "price":7.5
                }
             ],
             "description":"Compra por eBay",
             "invoice_number":"F00015",
             "related_resources": {
                    “request”: {
                           “id”: “0368dbf8-2405-11e9-865d-5254008a2539”,
                           “ref”: “P1901293671246”
                     },
                    “sale”: {
                           “id”: “0368dbf8-2405-11e9-865d-5254008a2539”,
                           “ref”: “P1901293671246”
                     }

              },
             "pay_tokens":[

            ]
         }
       ],
       "_links":{
         "self":{
             "href":"http://test.mpandco.com/api/payment-intent/show?id=03b9f66c-fefb-11e8-a647-b62cbc289574",
             "method":"GET"
          },
          "execute":{
            "href":"http://test.mpandco.com/api/payment-intent/execute/sale?id=03b9f66c-fefb-11e8-a647-b62cbc289574",
            "method":"POST"
          },
          "approval_url":{
             "href":"http://test.mpandco.com/p/express-checkout/03b9f66c-fefb-11e8-a647-b62cbc289574/1",
             "method":"GET"
          }
       }
    }
