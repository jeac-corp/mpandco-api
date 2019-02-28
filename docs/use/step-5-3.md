[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step53"></div>
## 5.3. Generar intención de pago (API de facturación).

Este método permite crear una intención de pago mediante un sistema de facturación para solicitar a un cliente.

**Importante**: En el parámetro **“paymentintent[intent]”** debe enviar el valor **“request”** y el parámetro **“paymentintent[recipient]”** es requerido, debe enviar el nombre del usuario destinatario que realizará el pago.

URL: `https://test.mpandco.com/api/payment-intent/.json`

Método HTTP: `POST`

Documentación completa de la API:
[Ir a la documentación](https://test.mpandco.com/docs#post--api-payment-intent-.json)

### Ejemplo de petición:

    curl -X POST \
      https://test.mpandco.com/api/payment-intent/.json \
      -H 'authorization: Bearer OAUTH-TOKEN' \
      -F 'paymentintent[intent]=request' \
      -F 'paymentintent[redirectUrls][returnUrl]=http://localhost:5000/payments/ExecutePayment.php?success=true&carId=200' \
      -F 'paymentintent[redirectUrls][cancelUrl]=http://localhost/payments/ExecutePayment.php?success=false&carId=200' \
      -F 'paymentintent[transactions][0][digitalAccountDestination]=demo01' \
      -F 'paymentintent[transactions][0][amount][total]=20' \
      -F 'paymentintent[transactions][0][amount][currency]=VES' \
      -F 'paymentintent[transactions][0][amount][details][shipping]=0' \
      -F 'paymentintent[transactions][0][amount][details][tax]=1.3' \
      -F 'paymentintent[transactions][0][amount][details][subTotal]=17.50' \
      -F 'paymentintent[transactions][0][description]=Compra por eBay' \
      -F 'paymentintent[transactions][0][invoiceNumber]=F00015' \
      -F 'paymentintent[transactions][0][items][0][name]=telefono' \
      -F 'paymentintent[transactions][0][items][0][quantity]=1' \
      -F 'paymentintent[transactions][0][items][0][sku]=P001' \
      -F 'paymentintent[transactions][0][items][0][price]=7.5' \
      -F 'paymentintent[transactions][0][items][0][currency]=VES' \
      -F 'paymentintent[recipient]=demo03'

### Respuesta:

200 - Correcto. Retorna JSON de tipo 'PaymentIntent'

Ejemplo de respuesta (200):

    {
    "id":"0f78eef2-ff02-11e8-a647-b62cbc289574",
    "payer":{
       "payer_info":{
             "id":"0cac1d76-ff01-11e8-a647-b62cbc289574",
             "_data":{
    "fullname":"584125550000"
            }
          }
       },
       "intent":"request",
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
             "id":"0f7a8104-ff02-11e8-a647-b62cbc289574",
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
             "pay_tokens":[
               {
                  "id":"0f7b8f72-ff02-11e8-a647-b62cbc289574",
                  "_data":{
                     "name":"J255500006-Pepitos House"
                   }
               }
             ]
          }
       ],
       "_links":{
         "self":{
            "href":"http://test.mpandco.com/api/payment-intent/show?id=0f78eef2-ff02-11e8-a647-b62cbc289574",
            "method":"GET"
          },
          "execute":{
            "href":"http://test.mpandco.com/api/payment-intent/execute/request?id=0f78eef2-ff02-11e8-a647-b62cbc289574",
            "method":"POST"
          }
       }
    }

### Al realizar una solicitud mediante el API de facturación, el cliente puede pagar de dos formas:

**a) Mediante su teléfono**: el cliente recibirá una notificación en su teléfono móvil donde se le indica que debe pagar la solicitud, una vez el cliente pague se llamará la dirección enviada en **"redirect_urls.return_url"** con el id de la intención de pago aprobada, usted debe obtener la intención con el enlace contenido en **"_links.self"** y verificar que el estatus sea **“executed”**.  

**b) Mediante el teclado numérico de su caja**: Cada transacción retornará una lista con de tokens para pagar (**pay_tokens**), usted deberá mostrar una lista de los tokens para permitir seleccionar el origen de los fondos del cliente con un campo numérico de **4 dígitos**, donde el cliente ingresará su pin de operaciones para autorizar el pago, al tener ambos datos deberá ejecutar el pago llamando el enlace **"_links.execute"**, tal como se indica en el paso [5.4.]({{site.baseurl}}/docs/use/step-5-3.html#step54)

<div id="step54"></div>
## 5.4. Ejecutar intención de pago (API de facturación).

Ejecuta una intención de pago de tipo "request" autorizada por un cliente y abona el dinero al comercio.

URL: `https://test.mpandco.com/api/payment-intent/request.json`

Método HTTP: `POST`

Documentación completa de la API:
[Ir a la documentación](https://test.mpandco.com/docs#post--api-payment-intent-execute-request.json)

### Ejemplo de petición:

    curl -X POST \
      'https://test.mpandco.com/api/payment-intent/execute/request.json?id=03b9f66c-fefb-11e8-a647-b62cbc289574' \
      -H 'authorization: Bearer OAUTH-TOKEN' \
      -F 'payment_execution[transactions][0][id]=2569f66c-fefb-11e8-a647-b62cbc289985' \
      -F 'payment_execution[transactions][0][payToken]=9859f66c-fefb-11e8-a647-b62cbc289241' \
      -F 'payment_execution[pin]=1111'

### Respuesta:

200 - Correcto. Retorna JSON de tipo 'PaymentIntent'

Ejemplo de respuesta (200):

    {
       "id":"ee12e986-ff04-11e8-a647-b62cbc289574",
       "payer":{
       "payer_info":{
             "id":"e7627ba6-ff04-11e8-a647-b62cbc289574",
             "_data":{
                "fullname":"584125550001"
             }
          }
       },
       "intent":"request",
       "state":"executed",
       "redirect_urls":{  "return_url":"http://test.mpandco.com/bc38875a09308af/callback-API?success=true&car=231",
    "cancel_url":"http://test.mpandco.com/bc38875a09308af/callback-API?success=false&car=231",
          "history_responses":[
             {
                  "uri":"http://test.mpandco.com/bc38875a09308af/callback-API?success=true&car=231&paymentIntent=ee12e986-ff04-11e8-a647-b62cbc289574&payerId=e7627ba6-ff04-11e8-a647-b62cbc289574",
                "method":"GET",
                "status_code":200,
                "body":"Pago procesado correctamente!"
             }
          ]
       },
       "total":{
       "currency":{
             "id":"VES"
          },
          "items":17.5,
          "shipping":1.2,
          "tax":1.3,
          "amount":20
       },
       "transactions":[
         {
           "id":"ee14637e-ff04-11e8-a647-b62cbc289574",
             "amount":{
               "currency":{
                   "id":"VES"
               },
                "total":4000,
                "details":{
                   "shipping":1.2,
                   "tax":1.3,
                   "sub_total":17.5
               }
             },
             "items":[
             {
                   "name":"televisor 65'",
                   "quantity":1,
                   "currency":{
                      "id":"VES"
                   },
                   "sku":"P002",
                   "price":2
               }
             ],
             "description":"Compra por eBay",
             "invoice_number":"F00015",
             "related_resources": {
                    “request”: {
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
             "href":"http://test.mpandco.com/api/payment-intent/show?id=ee12e986-ff04-11e8-a647-b62cbc289574",
             "method":"GET"
          },
          "execute":{
             "href":"http://test.mpandco.com/api/payment-intent/execute/request?id=ee12e986-ff04-11e8-a647-b62cbc289574",
             "method":"POST"
          }
       }
    }

**Importante**: Debe verificar que el estatus de la intención de pago en la respuesta es **“executed”**, el campo **“related_resources.request”** contiene el pago generado por la transacción.
