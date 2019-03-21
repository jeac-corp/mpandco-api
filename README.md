![API.png]({{site.baseurl}}/images/API.png)

<div id="step2"></div>
**mPandco** es una plataforma electrónica que provee un servicio de pago instantáneo a bajo costo, tanto para personas naturales como jurídicas. Se puede realizar la adquisición de productos y/o servicios, mediante el uso de una cuenta electrónica recargable proporcionada a través de una aplicación para teléfonos celulares.

Si deseas recibir pagos por internet, a través de tu dispositivo móvil, página web o sistema de facturación, puedes apoyarte con **mPandco** para lograr tus objetivos.

Este manual de integración tiene como finalidad facilitar a los departamentos de tecnologías de los comercios y a desarrolladores independientes a integrar sus soluciones web con la plataforma de pagos mPandco.

[Acceder a la documentación online.](https://jeac-corp.github.io/mpandco-api/)

## Contenido
1. <a href="#step1">Histórico de cambios</a>
2. <a href="#step2">Introducción</a>
3. <a href="#step3">Requisitos</a><br/>
4. Creación de llaves.<br/>
4.1. [Registro de aplicaciones oAuth2.]({{site.baseurl}}/docs/keys/step-4-1.html)<br/>
4.2. [Solicitud de token de acceso.]({{site.baseurl}}/docs/keys/step-4-2.html)<br/>
4.3. [Usar token de acceso para acceder a la API.]({{site.baseurl}}/docs/keys/step-4-3.html)<br/>

5. Uso del API mPandco<br/>
5.1. [Generar intención de pago (Botón de pago).]({{site.baseurl}}/docs/use/step-5-1.html#step51)<br/>
5.1.1 [Generar intención de pago y distribuir fondos (Botón de pago).]({{site.baseurl}}/docs/use/step-5-1.html#step511)<br/>
5.2. [Ejecutar intención de pago (Botón de pago).]({{site.baseurl}}/docs/use/step-5-1.html#step52)<br/>
5.3. [Generar intención de pago (API de facturación).]({{site.baseurl}}/docs/use/step-5-3.html#step53)<br/>
5.4. [Ejecutar intención de pago (API de facturación).]({{site.baseurl}}/docs/use/step-5-3.html#step54)<br/>
5.5. [Obtener intención de pago.]({{site.baseurl}}/docs/use/step-5-5.html)<br/>
5.6. [Obtener historial de las intenciónes de pagos.]({{site.baseurl}}/docs/use/step-5-6.html)<br/>
5.7. [Obtener historial de los pagos.]({{site.baseurl}}/docs/use/step-5-7.html)<br/>
5.8. [Modelos de respuesta.]({{site.baseurl}}/docs/use/step-5-8.html)<br/>
5.9. [Anular una intención de pago ejecutada.]({{site.baseurl}}/docs/use/step-5-9.html)<br/>
6. [Sandbox para desarrolladores.]({{site.baseurl}}/docs/step-6.html)
7. [Recomendaciones.]({{site.baseurl}}/docs/recommendations.html)
8. [Condiciones de uso.]({{site.baseurl}}/docs/terms.html)

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
    - Intención de pago: Ahora no se generan solicitudes sino se completa el proceso..<br/>
    - Intención de pago: se mejoro proceso de distribución.
    </td>
  </tr>
  </tbody>
</table>

<div id="step3"></div>
## 3. Requisitos
El comercio debe cumplir con los siguientes requisitos para poder recibir pagos a través de mPandco:

- Código de afiliación para el registro del comercio. Este código se obtiendo a través del cuerpo de ventas de mPandco.
- Dominio propio.
- Código fuente propio o acceso al mismo.
- Alojamiento en servidor propio o terceros.

La integración con **mPandco** se realiza mediante su **API** basado en métodos **RESTful** bajo **HTTPS**.

<hr/>

### Soporte o Contacto

¿Tienes dudas, sugerencias o problemas con la integración? por favor comunícate con nosotros mediante atencionalcliente@mpandco.com y te ayudaremos.
