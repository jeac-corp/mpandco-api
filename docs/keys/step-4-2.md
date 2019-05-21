[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step42"></div>
## 5.2. Solicitud de token de acceso.

El proceso de autenticación se basa en el protocolo [OAuth2](https://oauth.net/2/) el cual funciona generando un único token de acceso principal, por medidas de seguridad es importante realizar la solicitud del token principal una sola vez donde usara el "username" y "password" de la cuenta, posteriormente debe usar el "token_refresh" para renovar cada token y evitar enviar datos sensibles en cada petición (por favor consultar el flujo de autenticación en oAuth2).

Para acceder a la API usted debe generar un código de acceso (access_token) que deberá enviar cada vez que usara la API.

Generación de un token de acceso:

`
POST https://test.mpandco.com/oauth/v2/token
`
<table border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td width="132">
<p><strong>Nombre</strong></p>
</td>
<td width="125">
<p><strong>Tipo</strong></p>
</td>
<td width="409">
<p><strong>Descripci&oacute;n</strong></p>
</td>
</tr>
<tr>
<td width="132">
<p>client_id</p>
</td>
<td width="125">
<p>String</p>
</td>
<td width="409">
<p><strong>Requerido.</strong> El id de mPandco que recibi&oacute; para su aplicación oAuth2 de mPandco.</p>
</td>
</tr>
<tr>
<td width="132">
<p>client_secret</p>
</td>
<td width="125">
<p>String</p>
</td>
<td width="409">
<p><strong>Requerido.</strong> La clave secreta que registr&oacute; para su aplicación oAuth2 de mPandco.</p>
</td>
</tr>
<tr>
<td width="132">
<p>grant_type</p>
</td>
<td width="125">
<p>String</p>
</td>
<td width="409">
<p><strong>Requerido.</strong> Tipo de token solicitado (urn:client_apps o refresh_token).</p>
</td>
</tr>
</tbody>
</table>

### Ejemplo:

    curl -X POST https://test.mpandco.com/oauth/v2/token \
    -F client_id=LLAVE_CLIENTE \
    -F client_secret=LLAVE_SECRETA \
    -F grant_type=urn:client_apps

### Respuesta:
Por defecto, la respuesta toma la siguiente forma:

    {
        "access_token": "Yzc4MDBlODlkMTRhMzY1OWI2MzhlZjQ3Mzk0N2JiYzdiN2U1ZmQ2NzBkY2Q5OWFmYWU0ODg2MTExZjQ5YmQ5Mg",
        "expires_in": 3600,
        "token_type": "bearer",
        "scope": "API",
        "refresh_token": "NTBkOWUwMjRlZDYxYTA4MWZhMjgzZTU0YjAyOTU0ZGZlM2NjOGMxZjYyZTBjZjUwMzU3MDRkMGVjMzdkZWM2MA"
    }
