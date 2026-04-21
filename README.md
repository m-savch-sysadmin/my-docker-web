## Step 1: Environment Provisioning
Initialize the workspace to ensure an organized project structure.

```
mkdir -p ~/my-docker-web && cd ~/my-docker-web
```

## Step 2:Configure Dockerfile
Defining the environment using a Dockerfile.

Dockerfile
```
nano Dockerfile
```
```
FROM httpd:2.4-alpine
COPY ./index.html /usr/local/apache2/htdocs/
COPY ./style.css /usr/local/apache2/htdocs/
```

## Step 3: Build & Run (Manual)
Building the source image from the Dockerfile.

```
# Build
docker build -t my-first-site .

# Run
docker run -d --name my-running-site -p 8082:80 my-first-site
```

## Step 4: Orchestration (Docker Compose)
Automated management using a YAML configuration.
```
nano docker-compose.yml
```
```
version: '3.8'
services:
  web-site:
    build: .
    container_name: my-running-site
    ports:
      - "8082:80"
    restart: always
```
<img width="959" height="194" alt="Screenshot 2026-04-21 172141" src="https://github.com/user-attachments/assets/6efbc981-54fa-4b81-821d-2eab6f9f9bb0" />

```
docker-compose up -d --build   # Start/Rebuild

docker-compose ps              # Check status

docker-compose down            # Stop/Remove
```
<img width="921" height="168" alt="Screenshot 2026-04-21 172306" src="https://github.com/user-attachments/assets/305aaa0e-1b74-4c33-9162-16e2305267fd" />



### Step 5: Git & Cloud Sync
Pushing the local infrastructure to the remote repository.
```
git add .
git commit -m "Full production setup"
git push origin main
```
