[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step58"></div>
## 6.8. Modelos de respuesta.

A continuación se muestra ejemplo de los modelos de respuesta de la API en formato JSON, el objeto de tipo **"Paginator"** se utiliza para las listas.

### Tipo: Paginator

    {
          "links": {
                    "first": {
                       "href": "Primera pagina"
                    },
                   "self": {
                        "href": "Pagina actual"
                    },      │        
                   "next": {
                        "href": "Pagina siguiente"
                    },
                    "last": {
                        "href": "Ultima pagina"
                    }
          },
          "meta": {
                    "currentPage": 1,
                    "maxPerPage": 10,
                    "totalPages": 1,
                    "totalResults": 2
          },
          "data": [ “Lista de datos del paginador” ],
    }

### Códigos de respuesta de la llamada al API

<table border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td width="289">
<p>C&oacute;digo</p>
</td>
<td width="263">
<p>Descripci&oacute;n</p>
</td>
</tr>
<tr>
<td width="289">
<p>200</p>
</td>
<td width="263">
<p>Correcto. Retorna JSON de tipo 'PaymentIntent'</p>
</td>
</tr>
<tr>
<td width="289">
<p>400</p>
</td>
<td width="263">
<p>Solicitud incorrecta (revisar datos del formulario)</p>
</td>
</tr>

<tr>
<td width="289">
<p>401</p>
</td>
<td width="263">
<p>Token vencido o expirado</p>
</td>
</tr>

<tr>
<td width="289">
<p>403</p>
</td>
<td width="263">
<p>Sin acceso al recurso solicitado</p>
</td>
</tr>

<tr>
<td width="289">
<p>404</p>
</td>
<td width="263">
<p>No se encontro el recurso solicitado</p>
</td>
</tr>

<tr>
<td width="289">
<p>405</p>
</td>
<td width="263">
<p>Método Http no permitido (por ejemplo solo acepta POST ó GET)</p>
</td>
</tr>

<tr>
<td width="289">
<p>503</p>
</td>
<td width="263">
<p>No tiene permiso para acceder al recurso solicitado</p>
</td>
</tr>
</tbody>
</table>

**Nota**: Si recibe un código de respuesta diferente a los antes descritos deben ser tomados como errores de protocolo HTTPS.

### Código de respuesta 400

    {
       "code": 400,
       "message": "Validation Failed",
       "errors": {
           "errors": [
               "Saldo insuficiente para realizar este env\u00edo de dinero."
           ],
           "children": {
               "digitalAccountSource": [],
               "bank": [],
               "recipient": [],
               "saveContact": [],
               "identificationType": [],
               "identificationNumber": [],
               "amount": [],
               "message": []
           }
       }
    }

Otro ejemplo de una respuesta 400:

    {
       "code":400,
       "message":"Validation Failed",
       "errors":{
          "children":{
             "intent":{

             },
             "redirectUrls":{
                "children":{
                   "returnUrl":{
                      "errors":[
                         "La URI de retorno es obligatoria."
                      ]
                   },
                   "cancelUrl":{
                      "errors":[
                         "La URI de cancelaci\u00f3n el obligatoria."
                      ]
                   }
                }
             },
             "transactions":{
                "children":[
                   {
                      "children":{
                         "digitalAccountDestination":{

                         },
                         "amount":{
                            "children":{
                               "total":{

                               },
                               "currency":{

                               },
                               "details":{
                                  "children":{
                                     "shipping":{

                                     },
                                     "tax":{

                                     },
                                     "subTotal":{

                                     }
                                  }
                               }
                            }
                         },
                         "description":{

                         },
                         "invoiceNumber":{

                         },
                         "items":{
                            "children":[
                               {
                                  "children":{
                                     "name":{

                                     },
                                     "quantity":{

                                     },
                                     "sku":{

                                     },
                                     "price":{

                                     },
                                     "currency":{

                                     }
                                  }
                               },
                               {
                                  "children":{
                                     "name":{

                                     },
                                     "quantity":{

                                     },
                                     "sku":{

                                     },
                                     "price":{

                                     },
                                     "currency":{

                                     }
                                  }
                               }
                            ]
                         },
                         "distributions":{

                         }
                      }
                   }
                ]
             },
             "recipient":{

             }
          }
       }
    }
