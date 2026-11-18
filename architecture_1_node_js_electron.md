# JavaScript Technologies (Electron & Node.js)

This alternative is built entirely around the JavaScript ecosystem and is particularly well-suited for developing cross-platform desktop applications that run on Windows, macOS, and Linux.

## Architecture Diagram

```mermaid
graph TD
    Browser["Browser / Electron UI<br>(React.js, English, Arabic)"]
    
    subgraph App ["ADK Reports App (Electron)"]
        WebApp["Local Backend<br>(Express.js / Node.js)"]
        LocalDB["Local Snapshot<br>(PouchDB / JSON)"]
        PDF["PDF Export<br>(Puppeteer / Chrome Headless)"]
        Queries["Report Queries<br>(GraphQL / ORM)"]
        Settings["Settings<br>(AES Encrypted JSON)"]
        Connection["Database Connection<br>(pg-promise / TLS)"]
        
        Browser <--> WebApp
        WebApp <--> LocalDB
        WebApp <--> PDF
        WebApp --> Queries
        Queries --> Connection
        Settings --> Connection
    end
    
    VPN["VPN / WireGuard<br>(Secure Tunnel)"]
    RemoteDB["PostgreSQL Server<br>(Read-Only)"]
    
    Connection --> VPN
    VPN --> RemoteDB
```

## Technologies Overview

1. **User Interface & Desktop Application (Electron & React.js):** Instead of relying on an external browser and a separate `.exe` file, the React frontend and local backend are bundled together into a single Electron desktop application.

2. **Local Backend (Express.js):** An alternative to FastAPI, responsible for handling application requests and processing them locally.

3. **Secure Connectivity & Remote Database (WireGuard & PostgreSQL):** Instead of using an SSH tunnel and SQL Server, this approach uses a secure virtual private network tunnel (WireGuard) to connect to a powerful, open-source PostgreSQL database.