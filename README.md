# Subida de archivos jQuery

## Contenido

- [Descripción](#description)
- [Demo](#demo)
- [Funciones](#funciones)
- [Seguridad](#security)
- [Configuración](#configuración)
- [Requisitos](#requisitos)
- [Requisitos obligatorios](#requisitos-obligatorios)
- [Requisitos opcionales](#requisitos-opcionales)
- [Requisitos multidominio](#requisitos-multidominio)
- [Navegadores](#navegadores)
- [Navegadores de escritorio](#navegadores-de-escritorio)
- [Navegadores móviles](#navegadores-móviles)
- [Información ampliada sobre compatibilidad con navegadores](#información-amplia-sobre-compatibilidad-con-navegadores)
- [Pruebas](#pruebas)
- [Soporte](#soporte)
- [Licencia](#licencia)

## Descripción

> Widget de subida de archivos con selección múltiple de archivos, compatibilidad con arrastrar y soltar, barras de progreso, validación y previsualización de imágenes, audio y vídeo para jQuery.
> Admite subidas de archivos multidominio, fragmentadas y reanudables, y redimensionamiento de imágenes del lado del cliente.
> Funciona con cualquier plataforma del lado del servidor (PHP, Python, Ruby on Rails, Java, Node.js, Go, etc.) que admita la subida de archivos de formularios HTML estándar.

## Demo

[Demo de subida de archivos](https://blueimp.github.io/jQuery-File-Upload/)

## Características

- **Subida de varios archivos:**
Permite seleccionar varios archivos a la vez y subirlos simultáneamente.
- **Compatibilidad con arrastrar y soltar:**
Permite subir archivos arrastrándolos desde el escritorio o el gestor de archivos y soltándolos en la ventana del navegador.

- **Barra de progreso de subida:**
Muestra una barra de progreso que indica el progreso de subida de archivos individuales y de todas las subidas combinadas.
- **Subidas cancelables:**
Las subidas de archivos individuales se pueden cancelar para detener el progreso.
- **Subidas reanudables:**
Las subidas canceladas se pueden reanudar con navegadores compatibles con la API Blob.
- **Subidas fragmentadas:**
Los archivos grandes se pueden subir en fragmentos más pequeños con navegadores compatibles con la API Blob.
- **Redimensionamiento de imágenes del lado del cliente:**
Las imágenes se pueden redimensionar automáticamente en el lado del cliente con navegadores compatibles con las API JS requeridas.
- **Vista previa de imágenes, audio y vídeo:**
Se puede mostrar una vista previa de los archivos de imagen, audio y vídeo antes de subirlos con navegadores compatibles con las API requeridas.
- **No se requieren plugins de navegador (p. ej., Adobe Flash):**
La implementación se basa en estándares abiertos como HTML5 y JavaScript y no requiere plugins adicionales. - **Respaldo elegante para navegadores antiguos:**
Sube archivos mediante XMLHttpRequests si es compatible y utiliza iframes como respaldo para navegadores antiguos.
- **Respaldo para formulario de carga de archivos HTML:**
Permite mejoras progresivas mediante el uso de un formulario HTML estándar como elemento de widget.
- **Subidas de archivos entre sitios:**
Admite la subida de archivos a un dominio diferente mediante XMLHttpRequests entre sitios o redirecciones de iframe.
- **Múltiples instancias de plugin:**
Permite usar múltiples instancias de plugin en la misma página web.
- **Personalizable y extensible:**
Proporciona una API para configurar opciones individuales y definir métodos de devolución de llamada para diversos eventos de carga.
- **Subidas de archivos multiparte y con flujo de contenido de archivo:**
Los archivos se pueden subir como un flujo estándar "multipart/form-data" o con flujo de contenido de archivo (subida de archivos HTTP PUT). **Compatible con cualquier plataforma de aplicaciones del lado del servidor:**
Funciona con cualquier plataforma del lado del servidor (PHP, Python, Ruby on Rails, Java, Node.js, Go, etc.) que admita la carga de archivos de formularios HTML estándar.

## Seguridad

⚠️ Lea el documento [VULNERABILIDADES](VULNERABILITIES.md) para obtener una lista de las vulnerabilidades corregidas.

Lea también el documento [SEGURIDAD](SECURITY.md) para obtener instrucciones sobre cómo configurar de forma segura su servidor web para la carga de archivos.

## Configuración

jQuery File Upload se puede instalar mediante [NPM](https://www.npmjs.com/):

```sh
npm install blueimp-file-upload
```

Esto permite incluir [jquery.fileupload.js](js/jquery.fileupload.js) y sus extensiones mediante `node_modules`, por ejemplo:

```html
<script src="node_modules/blueimp-file-upload/js/jquery.fileupload.js"></script>
```

El widget se puede inicializar en un formulario de carga de archivos de la siguiente manera:

```js
$('#fileupload').fileupload(); ```

Para más información, consulta las siguientes guías:

- [Página principal de la documentación](https://github.com/blueimp/jQuery-File-Upload/wiki)
- [Lista de todas las opciones disponibles](https://github.com/blueimp/jQuery-File-Upload/wiki/Options)
- [La API del plugin](https://github.com/blueimp/jQuery-File-Upload/wiki/API)
- [Cómo configurar el plugin en tu sitio web](https://github.com/blueimp/jQuery-File-Upload/wiki/Setup)
- [Cómo usar solo el plugin básico](https://github.com/blueimp/jQuery-File-Upload/wiki/Basic-plugin)

## Requisitos

### Requisitos obligatorios

- [jQuery](https://jquery.com/) v1.7+
- [Widget jQuery UI](https://jquery.com/) v1.7+ factory](https://api.jqueryui.com/jQuery.widget/) v1.9+
(incluido): Requerido para el plugin básico de subida de archivos, pero muy ligero, sin otras dependencias de la suite jQuery UI.
- [Plugin de transporte de iframes de jQuery](https://github.com/blueimp/jQuery-File-Upload/blob/master/js/jquery.iframe-transport.js)
(incluido): Requerido para [navegadores sin compatibilidad con la subida de archivos XHR](https://github.com/blueimp/jQuery-File-Upload/wiki/Browser-support).

### Requisitos opcionales

- [Motor de plantillas JavaScript](https://github.com/blueimp/JavaScript-Templates)
v3+: Se utiliza para renderizar los archivos seleccionados y subidos. - [Biblioteca de carga de imágenes en JavaScript](https://github.com/blueimp/JavaScript-Load-Image)
v2+: Requerida para la vista previa de imágenes y la función de redimensionamiento.
- [Polyfill de Canvas a Blob en JavaScript](https://github.com/blueimp/JavaScript-Canvas-to-Blob)
v3+: Requerida para la función de redimensionamiento.
- [Galería blueimp](https://github.com/blueimp/Gallery) v2+: Se utiliza para mostrar las imágenes subidas en una caja de luz.
- [Bootstrap](https://getbootstrap.com/) v3+: Se utiliza para el diseño de la demostración.
- [Glyphicons](https://glyphicons.com/) Conjunto de iconos utilizado por Bootstrap.

Requisitos entre dominios

Las cargas de archivos entre dominios mediante el plugin de transporte de iframes requieren una redirección al servidor de origen para obtener los resultados de la carga. La implementación de ejemplo utiliza [result.html] como una página de redirección estática para el servidor de origen.

El repositorio también incluye el plugin jQuery XDomainRequest Transport (https://github.com/blueimp/jQuery-File-Upload/blob/master/js/cors/jquery.xdr-transport.js), que permite solicitudes AJAX multidominio limitadas en Microsoft Internet Explorer 8 y 9 (IE 10 admite solicitudes XHR multidominio).
El objeto XDomainRequest solo permite solicitudes GET y POST, y no admite la subida de archivos. Se utiliza en la demostración (https://blueimp.github.io/jQuery-File-Upload/) para eliminar archivos subidos del servicio de subida de archivos multidominio.

## Navegadores

### Navegadores de escritorio

El plugin de subida de archivos se prueba periódicamente con las últimas versiones de los navegadores y es compatible con las siguientes versiones mínimas:

- Google Chrome
- Apple Safari 4.0+
- Mozilla Firefox 3.0+
- Opera 11.0+
- Microsoft Internet Explorer 6.0+

### Navegadores móviles

El plugin de subida de archivos se ha probado y es compatible con los siguientes navegadores móviles:

- Apple Safari en iOS 6.0+
- Google Chrome en iOS 6.0+
- Google Chrome en Android 4.0+
- Navegador predeterminado en Android 2.3+
- Opera Mobile 12.0+

### Información sobre compatibilidad ampliada con navegadores

Para obtener una descripción detallada de las funciones compatibles con cada versión del navegador y los errores conocidos del sistema operativo/navegador, consulte la [Información sobre compatibilidad ampliada con navegadores](https://github.com/blueimp/jQuery-File-Upload/wiki/Browser-support).

## Pruebas

El proyecto incluye tres conjuntos de pruebas:

1. Análisis de código con [ESLint](https://eslint.org/).
2. Pruebas unitarias con [Mocha](https://mochajs.org/).
3. Pruebas integrales con [blueimp/wdio](https://github.com/blueimp/wdio).

Para ejecutar las pruebas, siga estos pasos:

1. Inicie [Docker](https://docs.docker.com/).
2. Instale las dependencias de desarrollo:
```sh
npm install
```
3. Ejecute las pruebas:
```sh
npm test
```

## Soporte

Este proyecto se mantiene activamente, pero no existe un canal de soporte oficial. Si tienes una pregunta que otro desarrollador podría resolver, publícala en [Stack Overflow](https://stackoverflow.com/questions/tagged/blueimp+jquery+file-upload)
y etiqueta tu pregunta con `blueimp jquery file upload`.

## Licencia

Publicado bajo la [licencia MIT](https://opensource.org/licenses/MIT).
 