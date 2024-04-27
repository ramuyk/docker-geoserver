# Introduction

This repository provides a `docker-compose.yml` ready-to-use Docker configuration to simplify the deployment of the official GeoServer Docker container. For comprehensive details about extra configurations, please refer to the [GeoServer official Docker installation guide](https://docs.geoserver.org/latest/en/user/installation/docker.html).

## Repository Contents 

This repository includes:

- **Docker Compose File**: A pre-configured `docker-compose.yml` file that sets up the GeoServer container. Key features enabled by this configuration include:
  - **Volume Mounting**: Persistent data storage to maintain GeoServer data across container restarts.
  - **Vector Tiles Extension**: Enhanced support for serving map data in vector tile formats.
  - **CORS Configuration**: Cross-Origin Resource Sharing (CORS) enabled to allow web clients hosted on different domains to interact with the GeoServer APIs.

## Getting Started

### Quick Setup

1. **Clone the Repository**:
   Clone this repository to your local machine using Git:
   ```bash
   git clone https://github.com/ramuyk/docker-geoserver.git
   cd docker-geoserver
   ```

2. **Start GeoServer**:
   Run the following command to start GeoServer using Docker Compose:
   ```bash
   docker-compose up -d
   ```

3. **Access GeoServer**:
   Open a web browser and navigate to `http://localhost:10001/geoserver` to access the GeoServer web interface. Default login credentials are:
   - **Username**: admin
   - **Password**: geoserver

   It is highly recommended to change these default credentials after your first login to ensure security.

### Configuration Details

#### Enabling CORS

CORS is configured to allow all domains (`*`). This setting can be adjusted in the `docker-compose.yml` file to meet specific security requirements by modifying the `CORS_ALLOWED_ORIGINS` environment variable.

#### Using the Vector Tiles Extension

The Vector Tiles extension is pre-enabled in this setup. This allows GeoServer to serve data in efficient vector tile formats compatible with various GIS applications.

#### Data Persistence

The `docker-compose.yml` file is configured to mount a persistent data volume at `/opt/geoserver_data`. This ensures that your GeoServer configurations and data are not lost when the container is restarted.

