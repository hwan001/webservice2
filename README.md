# Webservice2

## init commands

### frontend
- React.js
    ```bash
    npx create-react-app frontend
    ```

### backend
- node.js
    ```bash
    npm init -y
    npm install express
    ```


## Deployment
- docker-compose
    ```bash
    docker-compose up --build
    ```

## Diagram
```mermaid
%%{init: {"flowchart": {"htmlLabels": false, "curve": "linear"}} }%%
flowchart LR
subgraph "system"
    style system fill:#666,stroke:#666,stroke-width:1px
    subgraph webserveice2["Web Service 2 (docker-compose)"]
        style webserveice2 fill:#777,stroke:#777,stroke-width:1px
        
        nginx["`nginx:80`"]
        frontend["`frontend:3000`"]
        backend["`backend:5000`"] 
    end

    smtp["`smtp server`"]
    db["`db:27017`"]
    vpn["`wireguard:51821`"]
end
    
    user -->|http://url| nginx
    nginx -->|80:3000| frontend
    nginx --> |url:80/api| backend
    frontend --> |url:80/api| nginx
    backend <--> db
    backend <--> vpn
    backend --> smtp
    smtp --> gmail
```