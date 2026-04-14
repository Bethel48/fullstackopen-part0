## 0.4: New Note Diagram

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
    server-->>browser: HTML page

    browser->>server: GET /data.json
    server-->>browser: Updated notes JSON

    Note right of browser: New note is rendered
```
