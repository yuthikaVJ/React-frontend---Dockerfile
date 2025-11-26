# React + Vite Frontend - Docker Setup

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) (or [oxc](https://oxc.rs) when used in [rolldown-vite](https://vite.dev/guide/rolldown)) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.

## Docker Setup

### Prerequisites
- Docker Desktop installed on your Windows machine
- Docker daemon running

### Building the Docker Image

1. **Navigate to the project directory:**
   ```cmd
   cd <file path>
   ```

2. **Build the Docker image:**
   ```cmd
   docker build -t <Image name> .
   ```

   Or with a specific tag:
   ```cmd
   docker build -t <Image name>:<tag> .
   ```

### Running the Container

1. **Run the container in development mode:**
   ```cmd
   docker run --name <container name > -p <PORT>:5173 <image name or ID>
   ```

2. **Run the container in detached mode (background):**
   ```cmd
   docker run --name <container name > -d -p <PORT>:5173  <image name or ID>
   ```

3. **Run with volume mounting for development (live reload):**
   ```cmd
   ocker run --name <container name > -d -p <port>:5173 -v /app/node_modules -v ${PWD}:/app -e CHOKIDAR_USEPOLLING=true <IMABE NAME OR ID>
   ```

### Docker Commands Reference

- **List running containers:**
  ```cmd
  docker ps
  ```

- **Stop a running container:**
  ```cmd
  docker stop react-app
  ```

- **Remove a container:**
  ```cmd
  docker rm react-app
  ```

- **View container logs:**
  ```cmd
  docker logs react-app
  ```

- **Execute commands inside the container:**
  ```cmd
  docker exec -it react-app /bin/sh
  ```

### Accessing the Application

Once the container is running, open your browser and navigate to:
- **Development server:** http://localhost:<PORT>


For production deployment, the Dockerfile should build the optimized production bundle and serve it with a web server like Nginx.