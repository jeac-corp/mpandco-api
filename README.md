![API.png]({{site.baseurl}}/images/API.png)
## Tabla de contenido

1. Histórico de cambios
2. Introducción
3. Requisitos<br/>
4. Creación de llaves.<br/>
4.1. Registro de aplicaciones  oAuth2.<br/>
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

## Histórico de cambios
Fecha  | Versión  |  Descripción
--|---|--
13-12-2018  | 1.0  |  Creación de documentación
07-01-2019  | 1.1  |  Nuevo parámetro del Request del PaymentIntent
29-01-2019  | 1.2  |  Se agrego API de movimientos de pagos "/api/payment/.json". Se agrego "relatedResources" a la intencion de pago para facilitar las conciliaciones. Nueva API para listar el historial de las intenciones de pago "GET /api/payment-intent/.json".


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
