# Introduction

This repository provides a `docker-compose.yml` ready-to-use Docker configuration to simplify the deployment of the official GeoServer Docker container. For comprehensive details about extra configurations, please refer to the [GeoServer official Docker installation guide](https://docs.geoserver.org/latest/en/user/installation/docker.html).

## Repository Contents 

This repository includes:

- **Docker Compose File**: A pre-configured `docker-compose.yml` file that sets up the GeoServer container with the following features:
  - **Volume Mounting**: Configures a persistent data volume at `/opt/geoserver_data` to maintain GeoServer data across container restarts, ensuring that your GeoServer configurations and data are not lost.
  - **Vector Tiles Extension**: Pre-enabled in this setup, allowing GeoServer to serve map data in efficient vector tile formats compatible with various GIS applications.
  - **CORS Configuration**: Cross-Origin Resource Sharing (CORS) is enabled to allow web clients hosted on different domains to interact with the GeoServer APIs. CORS is configured to allow all domains (`*`), which can be adjusted in the `docker-compose.yml` file by modifying the `CORS_ALLOWED_ORIGINS` environment variable to meet specific security requirements.

## Getting Started

### Important Preliminary Steps

Before starting the quick setup, please note the following adjustments:

1. **Important Note on Port Mapping**: The `docker-compose.yml` file contains a port mapping to `127.0.0.1`, limiting access to the localhost only. To make the service accessible from other machines or publicly, change the IP address in the port mapping. For instance, use `0.0.0.0` to bind to all network interfaces, updating the ports line to `- "0.0.0.0:8088:8088"` for broader network access.

2. **Resource Limits**: The Docker container is configured to use a maximum of 8 GB of RAM and 4 CPU cores, optimizing performance while preventing overutilization of host resources. These settings can be adjusted inside the `docker-compose.yml` file to suit your specific needs or to align with the capabilities of your system.

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
   docker compose up -d
   ```

3. **Access GeoServer**:
   Open a web browser and navigate to `http://localhost:10001/geoserver` to access the GeoServer web interface. Default login credentials are:
   - **Username**: admin
   - **Password**: geoserver

   It is highly recommended to change these default credentials  under `Users, Groups` after your first login to ensure security.

