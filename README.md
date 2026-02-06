<h1>0.4: Nuevo diagrama de nota</h1>

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: new note
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: updated notes view
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```

<h1>0.5: Diagrama de aplicación de una sola página</h1>

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

```

<h1>0.6: Nueva nota en diagrama de aplicación de una sola página</h1>

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: JSON with new note
    deactivate server

    Note right of browser: The browser updates the UI without reloading the page

```

<p>En una SPA, JavaScript modifica el DOM directamente usando los datos recibidos del servidor, sin recargar la página.</p><br>

<p>1.- El usuario escribe una nota y pulsa el botón de guardar.

2.- JavaScript captura el evento y evita que la página se recargue.

3.- JavaScript envía la nota al servidor usando una petición POST.

4.- El servidor guarda la nota y responde con los datos en formato JSON.

5.- JavaScript recibe la respuesta del servidor.

6.- JavaScript actualiza el HTML existente modificando el DOM.

7.- El navegador muestra la nueva nota sin recargar la página. </p><br>

<p>La página no se recarga porque JavaScript modifica el DOM con los datos recibidos del servidor en lugar de solicitar un nuevo documento HTML.</p>
