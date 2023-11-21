# Task: Setting up a Pipeline in Google Cloud Platform for a PHP-Laravel framework. 

1. GCP pipline to autodeploy PHP-Laravel application in GCP erverless computing service.
2. Setup autoscalling feature for the orchestration of Docker containers.

# Travellist - Laravel GCP Project - Docker Compose commands.
```
docker compose build -t app
docker compose up -d
docker compose exec app ls -l
docker compose exec app rm -rf vendor composer.lock
docker compose exec app composer install
docker compose exec app php artisan key:generate
```

# Laravel GCP Project - cloudbuild.yaml file structure.

logsBucket: 'gs://react-electron_logs'

steps:
  # Step 1: Install Node.js and Yarn
  - name: 'node:14'
    entrypoint: 'bash'
    args:
      - '-c'
      - 'npm install'

  # Step 2: Install dependencies
  - name: 'gcr.io/cloud-builders/npm'
    entrypoint: 'bash'
    args:
      - '-c'
      - 'npm install concurrently --save-dev'

  # Step 3: Starting the application
  - name: 'gcr.io/cloud-builders/npm'
    entrypoint: 'npm'
    args:
      - 'run'
      - 'build'

  # Step 4 : Storing the artifact in docker image formate  
