### Exercise solution (0.4 to 0.6) for part 0, Fundamentals of Web apps

1. **Exercise: 0.4**

   Create a sequence diagram depicting the situation where the user creates a new note on the page https://studies.cs.helsinki.fi/exampleapp/notes by writing something into the text field and clicking the submit button.

   **Solution:**

```mermaid
sequenceDiagram
  participant browser
  participant server

    Note right of browser: User enters text in the input field and clicks on submit button

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note left of server: Server executes callback function adding new note to JSON & sends a URL redirect
    server-->>browser: URL redirect instruction for https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
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

2. **Exercise 0.5**

   Create a diagram depicting the situation where the user goes to the single-page app version of the notes app at https://studies.cs.helsinki.fi/exampleapp/spa.

   **Solution:**

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

  Note right of browser: The browser executes the callback function that renders the notes list
```

3. **Exercise 0.6**

   Create a diagram depicting the situation where the user creates a new note using the single-page version of the app.

   **Solution:**

```mermaid
sequenceDiagram
  participant browser
  participant server

  Note right of browser: 1. User enters text in the input field and clicks on submit button

  Note right of browser: 2. Browser executes the javascript code to re-render the updated notes list
  Note right of browser: 3. Browser sends a request with the submitterd data in JSON to the server

  browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
  activate server
  server-->>browser: Server responds with 200 status code saying note created
  deactivate server

```
