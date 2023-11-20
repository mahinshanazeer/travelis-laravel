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



enable all the necessary APIs
create a service account and add necessary previlages (by default there will be a service account)
create a cloud-build service

enable:
Identity and Access Management (IAM) API
Manages identity and access control for Google Cloud Platform resources, including the creation of service accounts, which you can use to authenticate to Google and make API calls.


Roles:
Cloud Build Approver
Cloud Build Connection Admin
Cloud Run Admin
Logs Bucket Writer
Logs Writer

Permission to bucket added:
Compute Engine default service account	
Storage Legacy Bucket Owner
