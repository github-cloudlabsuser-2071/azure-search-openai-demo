# `app.py` Documentation

## Overview

`app.py` is the asynchronous backend for this web application, built with the Quart framework. It integrates multiple Azure services, including:

- **Azure Cognitive Services** (Speech): For speech-to-text and text-to-speech capabilities.
- **Azure Blob Storage**: For storing and serving static and user-uploaded content.
- **Azure Data Lake Storage**: For secure, scalable file storage and user uploads.
- **Azure Search**: For advanced search capabilities over ingested content.
- **OpenAI**: For natural language processing and chat features.
- **OpenTelemetry**: For distributed tracing and observability.

## Dependencies

- Quart
- Azure Cognitive Services
- Azure Blob Storage
- Azure Data Lake Storage
- Azure Search
- OpenAI
- OpenTelemetry

## Main Routes

- `/` — Serves the main entry point (`index.html`).
- `/redirect` — Blank page for login redirect support.
- `/favicon.ico` — Serves the favicon.
- `/assets/<path:path>` — Serves static assets from `static/assets`.
- `/content/<path>` — Serves files from blob storage with access control.
- `/ask` (`POST`) — Processes user queries and returns responses.
- `/chat` (`POST`) — Handles chat messages and returns responses.
- `/chat/stream` (`POST`) — Streams chat responses as they are generated.
- `/auth_setup` (`GET`) — Sends MSAL.js authentication settings to the client.
- `/config` (`GET`) — Provides configuration settings to the client.
- `/speech` (`POST`) — Handles text-to-speech requests, returns audio data.
- `/upload` (`POST`) — Handles file uploads to Azure Data Lake Storage.
- `/delete_uploaded` (`POST`) — Allows users to delete their uploaded files.
- `/list_uploaded` (`GET`) — Lists files uploaded by the authenticated user.

## Key Classes & Functions

- **`JSONEncoder`**: Custom JSON encoder for dataclasses.
- **`setup_clients`**: Initializes Azure service clients and other app dependencies before serving requests.

## Usage

1. **Deployment**: Deploy as a Quart application. Ensure all required environment variables are set (Azure credentials, configuration, etc.).
2. **Authentication**: Uses MSAL.js for authentication and access control.
3. **Extensibility**: Add new routes or Azure integrations as needed for your scenario.

## Example: Running the Backend

```bash
export <REQUIRED_ENV_VARS>
python3 app.py
```

Or use the provided `start.sh` script for local development.

---

For more details on configuration, deployment, and customization, see the project-level `README.md` and documentation in the `docs/` directory.

