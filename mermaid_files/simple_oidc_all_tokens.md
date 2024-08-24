```mermaid
sequenceDiagram
    participant User as User
    participant Client as Client
    participant AuthServer as Authorization Server
    participant ResourceServer as Resource Server

    User->>Client: Access Client Application
    Client->>AuthServer: Request ID Token, Access Token & Refresh Token (Authentication Request)
    AuthServer-->>Client: ID Token, Access Token & Refresh Token

    Client->>Client: Validate ID Token (User Authentication)
    Client->>ResourceServer: Request Resource with Access Token
    ResourceServer-->>Client: Provide Resource

    Note over Client,ResourceServer: Access Token expires

    Client->>AuthServer: Use Refresh Token to get New Access Token
```