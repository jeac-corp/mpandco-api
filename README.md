![API.png]({{site.baseurl}}/images/API.png)

<div id="step2"></div>
**mPandco** es una plataforma electrónica que provee un servicio de pago instantáneo a bajo costo, tanto para personas naturales como jurídicas. Se puede realizar la adquisición de productos y/o servicios, mediante el uso de una cuenta electrónica recargable proporcionada a través de una aplicación para teléfonos celulares.

Si deseas recibir pagos por internet, a través de tu dispositivo móvil, página web o sistema de facturación, puedes apoyarte con **mPandco** para lograr tus objetivos.

Este manual de integración tiene como finalidad facilitar a los departamentos de tecnologías de los comercios y a desarrolladores independientes a integrar sus soluciones web con la plataforma de pagos mPandco.<br/>

[Acceder a la documentación online.](https://jeac-corp.github.io/mpandco-api/)<br/>
<br/>
## Contenido
1. <a href="#step1">Histórico de cambios</a><br/>
2. <a href="#step2">Introducción</a><br/>
3. [Condiciones de uso.]({{site.baseurl}}/docs/terms.html)<br/>
4. Requisitos.<br/>
4.1. [Sandbox para desarrolladores.]({{site.baseurl}}/docs/step-6.html)<br/>
4.2. [Requisitos para producción.]({{site.baseurl}}/docs/step-6.html#step42)<br/>
5. Creación de llaves.<br/>
5.1. [Registro de aplicaciones oAuth2.]({{site.baseurl}}/docs/keys/step-4-1.html)<br/>
5.2. [Solicitud de token de acceso.]({{site.baseurl}}/docs/keys/step-4-2.html)<br/>
5.3. [Usar token de acceso para acceder a la API.]({{site.baseurl}}/docs/keys/step-4-3.html)<br/>

6. Uso del API mPandco<br/>
6.1. [Generar intención de pago (Botón de pago).]({{site.baseurl}}/docs/use/step-5-1.html#step51)<br/>
6.1.1 [Generar intención de pago y distribuir fondos (Botón de pago).]({{site.baseurl}}/docs/use/step-5-1.html#step511)<br/>
6.2. [Ejecutar intención de pago (Botón de pago).]({{site.baseurl}}/docs/use/step-5-1.html#step52)<br/>
6.3. [Generar intención de pago (API de facturación).]({{site.baseurl}}/docs/use/step-5-3.html#step53)<br/>
6.4. [Ejecutar intención de pago (API de facturación).]({{site.baseurl}}/docs/use/step-5-3.html#step54)<br/>
6.5. [Obtener intención de pago.]({{site.baseurl}}/docs/use/step-5-5.html)<br/>
6.6. [Obtener historial de las intenciónes de pagos.]({{site.baseurl}}/docs/use/step-5-6.html)<br/>
6.7. [Obtener historial de los pagos.]({{site.baseurl}}/docs/use/step-5-7.html)<br/>
6.8. [Modelos de respuesta.]({{site.baseurl}}/docs/use/step-5-8.html)<br/>
6.9. [Anular una intención de pago ejecutada.]({{site.baseurl}}/docs/use/step-5-9.html)<br/>
6.10. [Agregar registro de pagos masivos (Dispersión).]({{site.baseurl}}/docs/use/step-5-10.html)<br/>
6.11. [(Pago) Obtener un pago previamente realizado.]({{site.baseurl}}/docs/use/payment.html)<br/>
7. [Recomendaciones.]({{site.baseurl}}/docs/recommendations.html)<br/>
8. SDK para desarrolladores<br/>
8.1. [PHP >= 5.6](https://github.com/jeac-corp/mpandco-php-sdk)

<div id="step1"></div>
## 1. Histórico de cambios
<table>
  <thead>
    <tr>
      <th>&nbsp;&nbsp;Fecha&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
      <th>Versión</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>13-12-2018</td>
    <td>1.0</td>
    <td>Versión de API y Documentación</td>
  </tr>
  <tr>
    <td>07-01-2019</td>
    <td>1.1</td>
    <td>Nuevo parámetro del Request del PaymentIntent</td>
  </tr>
  <tr>
    <td>29-01-2019</td>
    <td>1.2</td>
    <td>
    - Se agrego API de movimientos de pagos "/api/payment/.json".<br/>
    - Se agrego "relatedResources" a la intencion de pago para facilitar las conciliaciones.<br/>
    - Nueva API para listar el historial de las intenciones de pago "GET /api/payment-intent/.json".
    </td>
  </tr>
  <tr>
    <td>21-03-2019</td>
    <td>1.3</td>
    <td>
    - Se agrego API de anulación de intención de pago "/api/payment-intent/cancel.json".<br/>
    - Intención de pago: Ahora no se generan solicitudes sino se completa el proceso.<br/>
    - Intención de pago: se mejoro proceso de distribución.
    </td>
  </tr>
  <tr>
    <td>28-04-2019</td>
    <td>1.4</td>
    <td>
    - Se agrego uso obligatorio de grant_type "urn:client_apps".<br/>
    - Se agrego enlace a SDK de PHP.
    </td>
  </tr>
  <tr>
    <td>10-11-2019</td>
    <td>1.5</td>
    <td>
    - Se actualiza estructura de la intención de pago<br/>
    - Se llama los enlaces asignados en la intencion de pago de tipo "request".
    </td>
  </tr>
  <tr>
    <td>19-02-2020</td>
    <td>1.6</td>
    <td>
    - Se agrega API de dispersión por pagos masivos.<br/>
    </td>
  </tr>
  <tr>
    <td>27-04-2020</td>
    <td>1.7</td>
    <td>
    - Se eliminan parametros requeridos "phone" y "email" de API de dispersión por pagos masivos.<br/>
    </td>
  </tr>

  <tr>
    <td>19-05-2021</td>
    <td>1.7.1</td>
    <td>
    - Se agrega API para consulta de pago.<br/>
    </td>
  </tr>

  </tbody>
</table>

<hr/>

### Soporte o Contacto

¿Tienes dudas, sugerencias o problemas con la integración? por favor comunícate con nosotros mediante atencionalcliente@mpandco.com y te ayudaremos.
