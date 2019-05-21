[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step6"></div>
## 4.1 Sandbox para desarrolladores.

Para interactuar con el **API de mPandco** bajo ambiente de prueba se cuenta con un ambiente separado de productivo, es importante que el cliente realice todas las pruebas necesarias antes de promover a productivo, para tener acceso al **Sandbox** debe seguir los siguientes pasos:

1. Ingresar al ambientes de prueba de mPandco a través de la url [test.mpandco.com](https://test.mpandco.com)
2. Registrar una cuenta de tipo empresarial.

![image022.png]({{site.baseurl}}/images/image022.png)

![image024.png]({{site.baseurl}}/images/image024.png)

Para este registro el sistema solicitará un código de afiliación el cual lo podrán obtener a través del siguiente enlace:

  [Obtener codigos de registro](https://test.mpandco.com/bc38875a09308a2/codes.json?access_token=f21d867c420680a2e4b90e761a9e751f)

Esto le responderá con dos códigos, uno **"regular"** y otro **"comercial"**, debe usarse el código de tipo **“regular”**, pueden generar cuantos códigos necesiten abriendo el enlace, a continuación un ejemplo de la respuesta:

Ejemplo de respuesta (200):

    {"regular":"k2yxdn1E","commercial":"JNSsYcFD"}

3. Ir al menú Configuraciones y seleccione la opción **“Aplicaciones oAuth”**. Seguir los pasos descritos en la sección [Registro de aplicaciones oAuth2.]({{site.baseurl}}/docs/keys/step-4-1.html)

4. Realizar pruebas con el API para **botón de pago** y **sistemas de facturación**, tal como se describe en la sección Uso del API mPandco.

Toda consulta desde el **Sandbox** debe apuntar a la url https://test.mpandco.com, una vez realizada las pruebas debe cambiar la ruta a https://app.mpandco.com y colocar las llaves del ambiente productivo.

- Enlace de **Sandbox**: https://test.mpandco.com
- Enlace de **Productivo**: https://app.mpandco.com

**IMPORTANTE**: Por defecto en el _Sandbox_ la opciones de integraciones de la API para botones de pago y sistemas de facturación estarán habilitadas con el fin de que pueda realizar todas las pruebas concernientes a la integración en su aplicación, sin embargo para activar las llaves en productivo debe contactarse con atencionalcliente@mpandco.com y allí le indicaran los requisitos de la activación.


<div id="step42"></div>

## 4.2 Requisitos para producción
El comercio debe cumplir con los siguientes requisitos para poder recibir pagos a través de mPandco:

- Código de afiliación para el registro del comercio. Este código se obtiendo a través del cuerpo de ventas de mPandco. 
- Dominio propio.
- Código fuente propio o acceso al mismo.
- Alojamiento en servidor propio o terceros.

La integración con **mPandco** se realiza mediante su **API** basado en métodos **RESTful** bajo **HTTPS**.