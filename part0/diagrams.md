# Exercise 0.4

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note

    Note right of browser: Data is sent as the body of the POST request

    activate server
    server-->>browser: HTML document
    deactivate server

    Note right of browser: The POST request gets a response from the server with code 302 (URL redirect)

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: (...) 99: {content: "as armas e os barões assinalados", date: "2024-04-21T12:47:18.376Z"} (...)
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```

# Exercise 0.5

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/new_note_spa

    activate server
    server-->>browser: HTML document
    deactivate server

    Note left of server: The SPA sends a single HTML document to the browser.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: (...) 99: {content: "as armas e os barões assinalados", date: "2024-04-21T13:25:47.278Z"} (...)
    deactivate server
```

# Exercise 0.6

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa

    Note right of browser: Data is sent with a POST request and the data type is JSON. The data is fetched by the event handler.

    activate server
    server-->>browser: JSON Application
    deactivate server

    Note left of server: All the JS code is run on the server and the HTML status code the browser gets back is 201 (Created)    
```