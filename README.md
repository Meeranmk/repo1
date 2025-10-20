Project Setup with  Podman

Quickstart guide for building and running the frontend and backend applications using Podman.

Prerequisites
Podman installed (podman version to verify)

Yarn installed

1. Check Podman Installation
bash
podman version
2. Update Reverse Proxy
In your frontend code or Dockerfile, ensure the API base URL or reverse proxy endpoint is set to:

text
http://localhost:7007/
Update the relevant environment variable, config file, or code as needed.

3. Install Dependencies and Build
bash
yarn install
yarn build:all
yarn build:backend
4. Build Docker Images Using Podman
bash
# Build the backend image
podman build -f packages/backend/Dockerfile -t backend:latest .

# Build the frontend image
podman build -f packages/app/Dockerfile -t frontend:latest .
5. Run Containers
bash
# Run the backend container
podman run -d --name backend -p 7007:7007 localhost/backend:latest

# Run the frontend container
podman run -d --name frontend -p 3000:8080 localhost/frontend:latest
6. Verify Both Containers
bash
podman ps
Both backend and frontend should now be running.

7. Access the Apps
Frontend: http://localhost:3000

Backend: http://localhost:7007
