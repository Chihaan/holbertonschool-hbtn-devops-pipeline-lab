# Staging Deployment

## Deployment trigger

The staging deployment is triggered automatically after a successful push to
the `main` branch.

The pipeline runs:

test -> build -> deploy

The deploy job only runs if the test and build jobs succeed.

## Deployment target

The application is deployed to a Render Web Service using the Docker image
published to GitHub Container Registry (GHCR).

Image:

ghcr.io/chihaan/hbtn-devops-pipeline-lab

The CI pipeline publishes both:

- `latest`
- a commit-specific tag using the Git commit SHA

## Database

The staging application uses a Render PostgreSQL database.

The Render Web Service has a `DATABASE_URL` environment variable configured
with the internal PostgreSQL connection string.

Database credentials must not be committed to the repository.

## Verification

Check application liveness:

```bash
curl https://holbertonschool-hbtn-devops-pipeline-lab.onrender.com/health
