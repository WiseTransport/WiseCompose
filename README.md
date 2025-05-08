## Docker Setup & Launch

### Prerequisites

* [Install Docker Engine](https://docs.docker.com/engine/install/)
* [Install Docker Compose](https://docs.docker.com/compose/install/)

### Configuration

1. Rename the environment file:

   * **Linux/macOS**:

     ```bash
     cp .env.example .env
     ```
   * **Windows (PowerShell)**:

     ```powershell
     Copy-Item .env.example .env
     ```

2. Edit `.env` to set required environment variables. Example values include:

   ```env
   BKK_KEY=your_bkk_key_here
   GOOGLE_KEY=your_google_maps_api_key
   DB_USERSMS_DRIVER=postgresql
   DB_USER=your_db_user
   DB_PASSWORD=your_db_password
   DB_NAME=your_db_name
   ```

   * Get your BKK key from [opendata.bkk.hu](https://opendata.bkk.hu). A test key for NOIT is:
     `ac84fd0b-c679-419b-935a-831744f6728c`
   * Set the appropriate database and API key values.

### Launch with Docker Compose

Run the following command from the project root:

```bash
docker compose up --build
```

This command will:

* Build and launch the `frontend`, `otp-provider`, `geocode-ms`, `users-ms`, and `users_db` services.
* Map the ports:

  * Frontend: `localhost:3000`
  * OTP Provider: `localhost:8080`
  * Geocode Microservice: `localhost:8001`
  * Users Microservice: `localhost:8000`

Make sure your Docker daemon is running. Services are connected via a shared `backend` network and `users_db` data is persisted in a Docker volume named `pgdata`.

