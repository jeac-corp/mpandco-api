![API.png]({{site.baseurl}}/images/API.png)
## Tabla de contenido

1. <a href="#step1">Histórico de cambios</a>
2. <a href="#step2">Introducción</a>
3. <a href="#step3">Requisitos</a><br/>
4. [Creación de llaves.]({{site.baseurl}}/docs/creating-keys.md)<br/>
4.1. Registro de aplicaciones oAuth2.<br/>
4.2. Solicitud de token de acceso.<br/>
4.3. Usar token de acceso para acceder a la API.<br/>

5. Uso del API mPandco<br/>
5.1. Generar intención de pago (Botón de pago).<br/>
5.2. Ejecutar intención de pago (Botón de pago).<br/>
5.4. Generar intención de pago (API de facturación).<br/>
5.5. Ejecutar intención de pago (Sistemas de facturación).<br/>
5.6. Obtener intención de pago.<br/>
5.7. Obtener historial de las intenciónes de pagos.<br/>
5.8. Obtener historial de los pagos.<br/>
5.9. Modelos de respuesta<br/>
6. Sandbox para desarrolladores
7. Recomendaciones
8. Condiciones de uso

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
  </tbody>
</table>

<div id="step2"></div>
## 2. Introducción
mPandco es una plataforma electrónica que provee un servicio de pago instantáneo a bajo costo, tanto para personas naturales como jurídicas. Se puede realizar la adquisión de productos y/o servicios, mediante el uso de una cuenta electrónica recargable proporcionada a través de una aplicación para teléfonos celulares.


Si deseas recibir pagos por internet, a través de tu dispositivo móvil, página web o sistema de facturación, puedes apoyarte con mPandco para lograr tus objetivos.

Este manual de integración tiene como finalidad facilitar a los departamentos de tecnologías de los comercios y a desarrolladores independientes a integrar sus soluciones web con la plataforma de pagos mPandco.

<div id="step3"></div>
## 3. Requisitos
El comercio debe cumplir con los siguientes requisitos para poder recibir pagos a través de mPandco:

- Código de afiliación para el registro del comercio. Este código se obtiendo a través del cuerpo de ventas de mPandco.
- Dominio propio.
- Código fuente propio o acceso al mismo.
- Alojamiento en servidor propio o terceros.

La integración con mPandco se realiza mediante su API basado en métodos RESTful bajo HTTPS.


[I'm an inline-style link](https://www.google.com)




You can use the [editor on GitHub](https://github.com/jeac-corp/mpandco-api/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/jeac-corp/mpandco-api/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
