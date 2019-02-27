[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step40"></div>
## 4. Creación de llaves

La implementación OAuth de mPandco admite el tipo de concesión de código de autorización estándar.

<div id="step41"></div>
### 4.1. Registro de aplicaciones oAuth2

Al registrarse en mPandco  como cliente empresarial, tendrá acceso directo e inmediato al API de mPandco. Esto le permitirá desarrollar las funcionalidades de pago en línea en su sitio web desde el momento en que crea su cuenta.

Para interactuar con el API de mPandco debe seguir los siguientes pasos:

4.1.1 Ir a la url [https://test.mpandco.com](https://test.mpandco.com).

4.1.2. Ingresar con el usuario y clave de la cuenta empresarial.

![image003.png]({{site.baseurl}}/images/image003.png)

4.1.3. Ir al menú Configuraciones y seleccione la opción **“Aplicaciones oAuth”**.

![image005.png]({{site.baseurl}}/images/image005.png)

4.1.4. Dar click en **“Registrar aplicación”**.
![image007.png]({{site.baseurl}}/images/image007.png)

4.1.5 Registrar los datos de la aplicación: Esta opcional le permitirá el acceso de su sistema para poder generar los enlaces de integración de la API de mPandco.

![image008.png]({{site.baseurl}}/images/image008.png)

* **Nombre de la aplicación**: Ingresar nombre de la aplicación o sistema web.
* **Descripción de la aplicación**: Resumen breve de su aplicación.
* **Url de página de inicio**: Dominio principal de su aplicación desde el cual realizará la integración. Ej. htttp://www.mystore.com
* **Cuenta electrónica destinataria de los fondos**: Cuenta mPandco donde se acreaditaran todos los pagos recibidos.
* **Logo de la aplicación**: Adjuntar logo de su aplicación, debe ser imágen nítida en formato png.

4.1.6 Dar click en el botón **“Aceptar”**, la información será guardada y mostrara el resumen de los datos de acceso, tal como se muestra en las siguientes imágenes:

**Detalles de la aplicación registrada**:

![image010.png]({{site.baseurl}}/images/image010.png)

**Llaves de acceso**:

![image012.png]({{site.baseurl}}/images/image012.png)

**Nota**: _Bajo el ambiente de pruebas de mPandco la opción “Cliente listo para usar” estará habilitada, una vez realizada todas las pruebas y cumplido todos los requisitos deberá solicitar la activación para el uso de la API a través del correo atencionalcliente@mpandco.com_.

**Permisos**:

![image014.png]({{site.baseurl}}/images/image014.png)

**Nota**: _Por defecto el acceso al API de facturación estará deshabilitado, si desea integrar esta opción debe realizar la solicitud al correo atencionalcliente@mpandco.com_.

**Cuenta receptora**:

![image016.png]({{site.baseurl}}/images/image016.png)

Si desea la opción de distribución automática del dinero recibido entre varias cuentas **mPandco** , el comercio o empresa deberá realizar la solicitud al correo atencionalcliente@mpandco.com, autorizando está opción.

**IMPORTANTE: Una vez completada las pruebas de la API y cumplido con los requisitos, deben solicitar la habilitación de conexión en ambiente productivo a través del correo atencionalcliente@mpandco.com.**
