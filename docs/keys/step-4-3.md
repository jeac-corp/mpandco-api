[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step42"></div>
## 4.3. Usar token de acceso para acceder a la API.

Luego de generar el token de acceso debe pasar el "access_token" encabezado de Autorización.

`Autorization: token OAUTH-TOKEN`

Por ejemplo, en curl puede establecer el encabezado de autorización de esta manera:

    curl -H "Authorization: Bearer OAUTH-TOKEN" -X GET https://test.mpandco.com/api/user/profile.json

Si el token es valido la API retornara código `200` en caso de que el token no sea valido retornara `403 Forbidden`.

Si desea mas información de los códigos http puede visitar en enlace [Códigos Http.](https://es.wikipedia.org/wiki/Anexo:C%C3%B3digos_de_estado_HTTP)
