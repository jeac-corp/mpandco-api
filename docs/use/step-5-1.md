[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step51"></div>
## 5.1. Generar intención de pago (Botón de pago).

Este método permite crear una intención de pago mediante un botón de pago y enviársela a un cliente.

**Importante**: En el parámetro **“paymentintent[intent]”** debe enviar el valor **“sale”**.

URL: `https://test.mpandco.com/api/payment-intent/.json`

Método HTTP: `POST`

Documentación completa de la API:
[Ir a la documentación](https://test.mpandco.com/docs#post--api-payment-intent-.json)

### Ejemplo de petición:

    curl -X POST \
      https://test.mpandco.com/api/payment-intent/.json \
      -H 'authorization: Bearer OAUTH-TOKEN' \
     -F 'paymentintent[intent]=sale' \
     -F 'paymentintent[redirectUrls][returnUrl]=http://localhost:5000/payments/ExecutePayment.php?success=true&carId=200' \
     -F 'paymentintent[redirectUrls][cancelUrl]=http://localhost:5000/payments/ExecutePayment.php?success=false&carId=200' \
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
      -F 'paymentintent[transactions][0][items][0][currency]=VES'

### Respuesta:

200 - Correcto. Retorna JSON de tipo 'PaymentIntent'

Ejemplo de respuesta (200):

    {
      "id":"03b9f66c-fefb-11e8-a647-b62cbc289574",
      "intent":"sale",
      "state":"created",
      "redirect_urls":{
      "return_url":"http:\/\/localhost\/payments\/ExecutePayment.php?success=true&carId=200",
      "cancel_url":"http:\/\/localhost\/payments\/ExecutePayment.php?success=false&carId=200",
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


### Links:
- **self**: Retorna la intención de pago generada.
- **execute**: Ejecuta la intención de pago, luego que un cliente autoriza el pago. (Al ejecutar el pago, se realiza el descuento al cliente y abono la cuenta recaudadora).
- **approval_url**: Dirección que el cliente debe abrir para autorizar el pago. Una vez el cliente autorice el pago se redireccionará a redirect_urls.return_url con los parámetros paymentIntent (intención de pago a ejecutar) y payerId (cliente que autorizó el pago) con el parámetro payer, que posteriormente usará para ejecutar el pago y si lo cancela se redireccionará a redirect_urls.cancel_url.

Al abrir **"approval_url"** el cliente deberá ingresar con sus credenciales y autorizar el pago:
![image018.png]({{site.baseurl}}/images/image018.png)

![image020.png]({{site.baseurl}}/images/image020.png)
