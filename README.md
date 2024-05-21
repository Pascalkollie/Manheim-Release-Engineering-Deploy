# Simple Serverless Website on GCP

## Project Overview
This project demonstrates the simplest method to create a serverless website using Google Cloud Platform (GCP) Cloud Storage. The focus is on simplicity and speed, leveraging GCP services and tools to quickly set up and host a static website. This repository contains the necessary files and configurations to deploy a static website with minimal infrastructure, ideal for a hiring project scenario.

## Website Structure
The website consists of basic HTML files:
- `index.html`: The main page of the website.
- `404.html`: Custom error page to handle not found errors.

## Technology Stack
- **Google Cloud Platform (GCP) Cloud Storage**: Serves the static website.
- **GCP Cloud Build**: Automates the deployment process from GitHub to Cloud Storage.
- **GCP CLI**: Manages resources and performs initial setup tasks.
- **Terraform**: Optional for infrastructure as code; here we use GCP CLI for simplicity.

## Quick Setup Guide
1. **Prerequisites**:
   - Ensure you have a GCP account and `gcloud` CLI installed and configured.
   - Verify your domain (e.g., `example.com`) with GCP to create the bucket.

2. **Creating the Bucket**:
   - Using GCP CLI, run:
     ```bash
     gcloud storage buckets create [BUCKET_NAME] --project=[PROJECT_ID] --uniform-bucket-level-access
     ```

3. **Deploying the Website**:
   - Configure the `cloudbuild.yaml` file to handle the deployment from GitHub to GCP Cloud Storage.
   - This file includes steps to copy the static files (`index.html` and `404.html`) to the designated bucket.

## CI/CD Pipeline
- Cloud Build triggers are set up to react to commits to different branches (dev/qa/prod).
- Merging to a specific branch automatically deploys to the corresponding environment.
- To tear down an environment, a flag can be passed to the Cloud Build command to clean up resources.

## Deployment Steps
- Commit your changes to the respective branch (dev/qa/prod).
- The CI/CD pipeline configured in Cloud Build will pick up the changes and execute the operations defined in `cloudbuild.yaml`.
- The operations include copying files to Cloud Storage and updating or tearing down environments based on the branch and commands.

## Limitations and Enhancements
- **SSL Configuration**: This setup does not include SSL; to enable SSL, configure a Google Load Balancer (GLB) to issue certificates and manage traffic.
- **Advanced Routing**: Not included in this simple setup. For production, consider setting up more advanced DNS and routing configurations using GLB.

## Conclusion
This project provides a straightforward, quick-launch framework for hosting static websites on GCP, emphasizing ease of deployment and maintenance. It's designed to fulfill the requirements of a hiring project without overcomplication, demonstrating effective use of cloud resources and DevOps practices.
