[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step57"></div>
## 6.7. Obtener historial de los pagos.

Este método permite obtener un paginador con el historial de los pagos.

URL: `api/payment/.json`

Método HTTP: `GET`

Documentación completa de la API:
[Ir a la documentación](https://test.mpandco.com/docs#get--api-payment-.json)

### Ejemplo de petición:

    curl -X GET \
      'https://test.mpandco.com/api/payment/.json' \
      -H 'authorization: Bearer OAUTH-TOKEN'

### Respuesta:

200 - Correcto. Retorna JSON de tipo 'Paginator'
