[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step56"></div>
## 5.6. Obtener historial de las intenciónes de pagos.

Este método permite obtener un paginador con el historial de las intenciones de pago generadas.

URL: `api/payment-intent/.json`

Método HTTP: `GET`

Documentación completa de la API:
[Ir a la documentación](https://test.mpandco.com/docs#get--api-payment-intent-.json)

### Ejemplo de petición:

    curl -X GET \
      'https://test.mpandco.com/api/payment-intent/.json' \
      -H 'authorization: Bearer OAUTH-TOKEN'

### Respuesta:

200 - Correcto. Retorna JSON de tipo 'Paginator'
