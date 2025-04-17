# docker-practice

[![Deploy to GitHub Pages](https://github.com/retrocolours/docker-practice/actions/workflows/deploy.yml/badge.svg)](https://github.com/retrocolours/docker-practice/actions/workflows/deploy.yml)

## Project Description

A React application containerized with Docker for development, built with Vite, and deployed to GitHub Pages. This setup demonstrates a hot-reloading development workflow using Docker Compose and a CI/CD pipeline with GitHub Actions for automatic deployments.

## Live Demo

[View the live demo](https://retrocolours.github.io/docker-practice)

## Technology Stack

- React
- Vite
- Docker & Docker Compose
- GitHub Actions
- GitHub Pages

## Local Development

### Prerequisites

- Docker and Docker Compose installed
- Git

### Setup and Run

1. Clone the repository

   ```bash
   git clone https://github.com/retrocolours/docker-practice.git
   cd docker-practice
   ```

2. Start the Docker development environment

   ```bash
   docker-compose up
   ```

3. Open your browser and navigate to [http://localhost:5173](http://localhost:5173)

## Environment Variables

- `NODE_ENV` — Set to "development" (configured via `docker-compose.yml`).

## Deployment

This project is automatically deployed to GitHub Pages via GitHub Actions on pushes to the `main` branch.

### Manual Deployment

If you need to deploy manually:

1. Build the application

   ```bash
   npm run build
   ```

2. Deploy to GitHub Pages
   ```bash
   npm run deploy
   ```

_(Note: Ensure a `deploy` script is defined in your `package.json`, e.g., `"deploy": "gh-pages -d dist"`.)_

## GitHub Actions Workflow

The CI/CD pipeline includes the following steps:

1. Checkout code
2. Setup Node.js environment (v20) with caching
3. Install dependencies
4. Build the application
5. Upload the `dist` artifact and deploy to GitHub Pages

## Configuration Details

### GitHub Pages Configuration

- **Base path:** `/docker-practice/` (configured in `vite.config.js`)
- **Homepage URL:** `https://retrocolours.github.io/docker-practice`

### Docker Development Configuration

- **Dockerfile.dev:** Uses Node 20-alpine, installs dependencies, and runs `npm run dev -- --host` for external access.
- **Volumes:** Mounts project directory (`.`) and `node_modules` for hot reload and dependency caching.
- **Ports:** Maps container port `5173` to host port `5173`.
- **Environment:** `NODE_ENV=development` set in `docker-compose.yml`.

### This badge displays the status of the deployment workflow for the project.

![Deploy](https://github.com/retrocolours/docker-practice/actions/workflows/deploy.yml/badge.svg)
