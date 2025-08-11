# Docker GHCR Test

A simple test repository for building and publishing Docker images to GitHub Container Registry (GHCR).

## Overview

This repository demonstrates the basic workflow for automatically building and publishing Docker images to GitHub's Container Registry using GitHub Actions. The container runs a simple bash script that outputs a greeting message.

## Repository Structure

```
.
├── .github/
│   └── workflows/
│       └── publish-image.yaml    # GitHub Actions workflow
├── Dockerfile                    # Container definition
├── entrypoint.sh                 # Application script
└── README.md                     # This file
```

## Docker Image

The image is based on Alpine Linux and includes:
- Bash shell
- A simple entrypoint script that prints "Hello world! Today will be a beautiful day!"

### Running the Image

Pull and run the latest image from GHCR:

```bash
docker run ghcr.io/othneildrew/docker-ghcr-test:latest
```

## CI/CD Pipeline

The repository uses GitHub Actions to automatically build and publish the Docker image when code is pushed to the `main` branch.

### Workflow Steps

1. **Checkout code** - Retrieves the repository contents
2. **Build and push** - Builds the Docker image and pushes it to GHCR

### Requirements

The workflow requires a GitHub Personal Access Token (PAT) stored as a repository secret named `GH_PAT` with appropriate permissions to write to GitHub Container Registry.

### Setting up GHCR Publishing

To use this workflow in your own repository:

1. Create a Personal Access Token with `write:packages` permission
2. Add the token as a repository secret named `GH_PAT`
3. Update the image name in the workflow file to match your username/repository

## Image Registry

The built images are published to:
- **Registry**: `ghcr.io`
- **Image**: `ghcr.io/othneildrew/docker-ghcr-test:latest`

## Local Development

To build and test locally:

```bash
# Build the image
docker build -t docker-ghcr-test .

# Run the container
docker run docker-ghcr-test
```

## License

This is a test repository for demonstration purposes.
