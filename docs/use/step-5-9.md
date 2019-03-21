[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step59"></div>
## 5.9. Anular una intención de pago ejecutada.

Este método permite anular una intención de pagó que fue ejecutada siempre y cuando fue ejecutada en un plazo menor a 24 horas, luego de este tiempo **no podrá ser anulada**.

**Importante**: La URL de anulación la puede obtener en **“_links.cancel.href”** del objeto que le retorna la API al generar la intención de pago.

URL: `/api/payment-intent/cancel.json`

Método HTTP: `POST`

Documentación completa de la API:
[Ir a la documentación](https://test.mpandco.com/docs#post--api-payment-intent-cancel.json)

### Datos mínimos a enviar:

    {
        "cancel_payment_intent": {
            "paymentIntent": "0cac1d76-ff01-11e8-a647-b62cbc289574"
        }
    }

### Ejemplo de petición:

    curl -X POST \
      https://test.mpandco.com/api/payment-intent/cancel.json \
      -H 'authorization: Bearer OAUTH-TOKEN' \
      -F 'cancel_payment_intent[paymentIntent]=0cac1d76-ff01-11e8-a647-b62cbc289574' \

### Respuesta:

200 - Correcto. Retorna JSON de tipo 'PaymentIntent'

Ejemplo de respuesta (200):

    {  
       "id":"f87d3bac-4c24-11e9-afc4-a4efc1f793fa",
       "payer":{  
          "payer_info":{  
             "id":"edda8d30-4c24-11e9-afc4-a4efc1f793fa",
             "_data":{  
                "fullname":"584125550001"
             }
          }
       },
       "intent":"request",
       "state":"annulled",
       "redirect_urls":{  
          "return_url":"http:\/\/app.mpandco.local\/app_dev.php\/bc38875a09308af\/callback-api?success=true&car=231",
          "cancel_url":"http:\/\/app.mpandco.local\/app_dev.php\/bc38875a09308af\/callback-api?success=false&car=231",
          "history_responses":[  
             {  
                "uri":"http:\/\/app.mpandco.local\/app_dev.php\/bc38875a09308af\/callback-api?success=true&car=231&paymentIntent=f87d3bac-4c24-11e9-afc4-a4efc1f793fa&payerId=edda8d30-4c24-11e9-afc4-a4efc1f793fa",
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
             "id":"f87f5df6-4c24-11e9-afc4-a4efc1f793fa",
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
             "related_resources":{  
                "request":{  
                   "id":"f9ef0d94-4c24-11e9-afc4-a4efc1f793fa",
                   "ref":"P1903211039678",
                   "_data":{  
                      "summary_1":"Recibido: 4.000,00 Bs.S",
                      "summary_2":"Monto solicitado 3.974,48 Bs.S",
                      "summary_3":"Cuenta del solicitante",
                      "summary_4":"Cuenta remitente",
                      "summary_5":"Solicitud de pago enviada",
                      "summary_status_color":"#D32F2F",
                      "username":null,
                      "user_from":"Camilo sexto",
                      "amount":0,
                      "status":"Reversado",
                      "type_payment_label":"Solicitud enviada a ",
                      "summary_amount":{  
                         "summary_1":"3974.48",
                         "summary_2":"4000.00"
                      },
                      "created_at":"hace menos de un minuto"
                   }
                }
             },
             "pay_tokens":[  

             ],
             "distributions":[  

             ]
          }
       ],
       "_links":{  
          "self":{  
             "href":"http:\/\/app.mpandco.local\/api\/payment-intent\/show.json?id=f87d3bac-4c24-11e9-afc4-a4efc1f793fa",
             "method":"GET"
          }
       }
    }


**Importante**: Debe verificar que el estatus de la intención de pago en la respuesta es **“annulled”**.
