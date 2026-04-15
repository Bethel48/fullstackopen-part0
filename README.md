# Full Stack Open - Part 0

## 0.4 New Note Diagram 
This diagram shows what happens when a user creates a new note.

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types a note and clicks Save

    browser->>server: POST /new_note
    activate server
    Note right of server: Server saves the new note
    server-->>browser: Redirect to /notes
    deactivate server

    browser->>server: GET /notes
    activate server
    server-->>browser: HTML page
    deactivate server

    browser->>server: GET /main.css
    server-->>browser: CSS file

    browser->>server: GET /main.js
    server-->>browser: JavaScript file

    Note right of browser: Browser fetches updated notes

    browser->>server: GET /data.json
    server-->>browser: Updated notes JSON

    Note right of browser: New note is rendered on the page
```
## 0.5 Single Page App Diagram

This diagram shows how the single-page application loads notes without reloading the page.

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET /spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET /main.css
    server-->>browser: CSS file

    browser->>server: GET /spa.js
    server-->>browser: JavaScript file

    Note right of browser: Browser executes SPA JavaScript

    browser->>server: GET /data.json
    activate server
    server-->>browser: Notes JSON data
    deactivate server

    Note right of browser: Notes are rendered dynamically without page reload
```
## 0.6 New Note in Single Page App

This diagram shows how a new note is created in the SPA without reloading the page.

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes a note and clicks Save

    Note right of browser: JavaScript prevents default form submission

    browser->>server: POST /new_note_spa (JSON data)
    activate server
    Note right of server: Server stores the new note
    server-->>browser: 201 Created (response)
    deactivate server

    Note right of browser: Browser updates UI immediately

    Note right of browser: New note is added to the list without reload
```
