```mermaid
sequenceDiagram
    participant User as Usuario
    participant Browser as Navegador
    participant Server as Servidor

    Note right of User: El usuario escribe una nueva nota y hace clic en "Guardar"

    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate Server
    Note right of Server: El servidor recibe y guarda la nueva nota
    Server-->>Browser: { "message": "nota guardada" }
    deactivate Server

    Note right of Browser: El navegador actualiza la lista de notas sin recargar la página
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ..., { "content": "Nueva nota", "date": "2024-6-10" }]
    deactivate Server

    Note right of Browser: El navegador renderiza la nueva lista de notas
