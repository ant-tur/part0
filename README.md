# Part 0

## Task 0.4

sequenceDiagram
    participant user
    participant browser
    participant server

    Note over user, browser: User types a note into the text field

    user->>browser: Clicks "Save" button

    Note right of browser: Browser prevents default form submission behavior
    Note right of browser: Browser creates a JavaScript object with note content and date

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: 302 Redirect to /notes
    deactivate server

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

    Note right of browser: Browser executes JavaScript to fetch JSON data

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated notes as JSON
    deactivate server

    Note right of browser: Browser re-renders the notes, including the new one


## Task 0.5

sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: JavaScript is executed<br/>It fetches notes from the backend

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON with notes
    deactivate server

    Note right of browser: Browser renders the notes dynamically without page reload


## Task 0.6

sequenceDiagram
    participant user
    participant browser
    participant server

    user->>browser: Clicks "Save" after entering a note

    Note right of browser: JS captures form event<br/>Creates new note object (content + date)

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: 201 Created (or empty response)
    deactivate server

    Note right of browser: JS updates the note list in memory<br/>And re-renders the list dynamically
