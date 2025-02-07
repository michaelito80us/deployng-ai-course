## Chapter 1: Project Initialization & Environment Setup

### Introduction

In this chapter, you’ll lay the groundwork for developing your AI-powered document assistant. You’ll create a reliable, repeatable environment for development by using tools like Docker and Minikube, which will help you manage your code and test it in conditions that mirror the production environment. This ensures your app will scale smoothly as you move into more complex tasks like deployment and performance optimization later in the course.

### Goals

- **Define the project scope**: Identify core features and the architecture needed for the AI-powered document assistant.
- **Set up the development environment**: Install Docker and Minikube to containerize the application, which ensures consistent development environments and helps with testing in production-like conditions.
- **Distinguish between development and production environments**: Learn how Docker and Kubernetes are used in both local and production contexts to ensure scalability, security, and performance.
- **Understand how CI/CD pipelines fit into the project**: Lay the groundwork for future automated deployment and monitoring.

### Concept Explanations

- **Project Scope**:
The goal of this project is to develop an AI-powered document assistant. This application allows users to upload documents, query them, and receive AI-generated answers. It combines frontend, backend, and AI integration to create a system that can interpret and respond to questions based on the document content. In this chapter, we'll set up the foundational environment to ensure that the application can be developed in a consistent and scalable way.

- **Development Environment Setup**:
A well-structured development environment is essential for building scalable and maintainable applications. By setting up Docker for containerization and Minikube for local Kubernetes orchestration, you can create a development environment that mirrors production conditions. This makes it easier to scale the app and troubleshoot potential issues as the project grows.

- **Docker**:
Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. Containers allow you to package your application along with its dependencies, so it can run consistently across any environment. For instance, whether you're developing locally or deploying to production, Docker ensures that your application behaves the same. This is particularly important when developing complex applications like the AI-powered document assistant, which will require consistent setups for the frontend, backend, and AI components.

- **Kubernetes**:
  Kubernetes is an open-source platform for automating the deployment, scaling, and management of containerized applications. In this chapter, you’ll set up a local Kubernetes environment using **Minikube**, which simulates a production Kubernetes cluster on your local machine. Kubernetes will be essential later in the course when we discuss cloud deployment, scaling, and managing multiple instances of containers. Minikube allows you to start testing your deployment strategy early, ensuring a smoother transition to the cloud.

- **Cluster of Hosts**:
A Kubernetes "cluster" is a set of physical or virtual machines that work together to run containerized applications. When you deploy your application in a cloud environment, it will run across multiple nodes (hosts) in a Kubernetes cluster. This setup provides redundancy, scalability, and load balancing. For now, Minikube helps you simulate this setup locally, so you can test how your containers will behave when scaled to production.

- **Development vs. Production Environments**:
  Development environments are typically used for coding, debugging, and testing, while production environments are where your app runs for real users. In this chapter, we set up a local development environment that uses Docker and Kubernetes to ensure your code will run smoothly when you eventually deploy it to a cloud service. This local setup helps you catch issues early, such as container misconfigurations or version inconsistencies, that might otherwise cause problems in production.

### Tasks

#### Task Checklist

1. Install Docker and Minikube.
2. Create a Git repository and set up project folders.
3. Link GitHub repository to local Git.
4. Set up Docker and Kubernetes locally.
5. Install and configure Husky and Lint-staged.

---

#### 1. Install Docker and Minikube (local Kubernetes setup)

- Install Docker to create containers and Minikube to set up a local Kubernetes cluster.  
  *Hint*: Ensure Docker’s system requirements are met on your machine. If using Minikube, verify that your system supports virtualization (check BIOS settings for Intel VT-x or AMD-V).

#### 2. Initialize a Git repository and create a basic project folder structure

- Create a Git repository and set up the following directory structure:
  - `/client` – For the frontend code.
  - `/server` – For the backend code.
  - `/docs` – For documentation.  
  *Hint*: To initialize Git, use `git init` and then `git add` to track your files. Consider creating a `.gitignore` file to avoid tracking unnecessary files (e.g., node_modules for frontend).

#### 3. Create a GitHub repository and connect it to your local repository

- Create a repository on GitHub and link it to your local repository. Push the initial commit to GitHub.  
  *Hint*: Use the `git remote add origin <your-repo-url>` command to connect your local repo to GitHub.

#### 4. Set up Docker and Kubernetes locally (or use a managed cluster)

- Set up Docker containers for local development and ensure your local Kubernetes cluster (Minikube) is running, or sign up for a managed Kubernetes service if preferred.  
  *Hint*: Run `kubectl get nodes` to check the status of your Kubernetes cluster after setting up Minikube.

#### 5. Set up Pre-commit Hooks with Husky and Lint-staged

- To ensure that code quality checks are run before each commit, you’ll set up pre-commit hooks using **Husky** and **Lint-staged**. These tools help automate linting and formatting tasks on the staged files before they're committed.  
  *Hint*: Make sure to add the appropriate linter configurations (e.g., ESLint for JavaScript/TypeScript or Prettier for formatting) to your project.

---

### Implementation Steps

#### Step 1: Install Docker

1. Download Docker from the [Docker official site](https://docs.docker.com/get-docker/).
2. Follow the installation instructions specific to your operating system:
   - Windows: Docker Desktop for Windows (enable WSL 2 if you're on Windows 10/11).
   - macOS: Docker Desktop for Mac.
   - Linux: Follow the commands for your distribution (e.g., `sudo apt-get install docker-ce` for Ubuntu).
3. Once installed, open a terminal/command prompt and verify the installation:

   ```bash
   docker --version
   ```

   This should return the Docker version if everything is set up correctly.

#### Step 2: Install Minikube (Local Kubernetes Setup)

1. Install Minikube by following the guide [here](https://minikube.sigs.k8s.io/docs/start/).
2. Once installed, start your local Kubernetes cluster:

   ```bash
   minikube start
   ```

3. Verify it's running by checking the nodes:

   ```bash
   kubectl get nodes
   ```

   You should see output similar to:

   ```bash
   NAME       STATUS   ROLES    AGE   VERSION
   minikube   Ready    master   5m    v1.21.2
   ```

#### Step 3: Initialize a Git Repository

1. Navigate to your project folder in the terminal:

   ```bash
   cd /path/to/your/project
   ```

2. Initialize the Git repository:

   ```bash
   git init
   ```

3. Add all your files to Git:

   ```bash
   git add .
   ```

4. Commit the initial set of files:

   ```bash
   git commit -m "Initial commit"
   ```

#### Step 4: Create a GitHub Repository

1. Go to GitHub and create a new repository (make it private or public based on your preference).
2. Once the repository is created, link it to your local repository:

   ```bash
   git remote add origin <https://github.com/yourusername/your-repository.git>
   ```

3. Push the initial commit to GitHub:

   ```bash
   git push -u origin master
   ```

#### Step 5: Set Up Docker and Kubernetes Locally

1. Test Docker: Verify that Docker is working by running:

   ```bash
   docker run hello-world
   ```

   This will download and run a test container, printing a success message if Docker is working correctly.

2. Verify Kubernetes (Minikube): To ensure your Kubernetes cluster is set up correctly, run:

   ```bash
   kubectl get nodes
   ```

   This command will show the status of your Minikube node. It should display something like:

   ```bash
   NAME       STATUS   ROLES    AGE   VERSION
   minikube   Ready    master   5m    v1.21.2
   ```

#### Step 6: Set up Pre-commit Hooks with Husky and Lint-staged

1. Install Husky and Lint-staged:
   In your project directory, install the necessary packages using npm or yarn:

   ```bash
   npm install --save-dev husky lint-staged
   ```

2. Set Up Husky to Enable Git Hooks
   1. Run the following command to initialize Husky in your project:

      ```bash
      npx husky-init
      ```

      This command will create a `.husky/` directory and set up a basic pre-commit hook.

   2. To make sure Husky is set up correctly, open `.husky/pre-commit` and ensure it includes the following:

      ```bash
      # .husky/pre-commit
      npx lint-staged
      ```

3. Configure Lint-staged
   Open `package.json` and add a lint-staged configuration that specifies which files should be linted before committing. For example, if you're using ESLint and Prettier, you might configure it like this:

   ```json
   "lint-staged": {
     "*.ts": "eslint --fix",
     "*.tsx": "eslint --fix",
     "*.js": "eslint --fix",
     "*.json": "prettier --write",
     "*.md": "prettier --write"
   }
   ```

   This ensures that:

   - `.ts`, `.tsx`, and `.js` files will be linted and fixed by ESLint.
   - `.json` and `.md` files will be formatted using Prettier.

4. Test the Pre-commit Hook
   Make some changes to a file that violates your linting rules (e.g., add a missing semicolon or incorrect formatting).
   Stage the file:

   ```bash
   git add path/to/your/file.ts
   ```

   Try committing the file:

   ```bash
   git commit -m "Test Husky and Lint-staged setup"
   ```

   Husky will trigger the pre-commit hook and run Lint-staged to check and fix any issues before allowing the commit to be finalized.

---

### Best Practices

- Ensure your Git workflow is clean and structured, with proper branching for different features or fixes.
- Use Docker for consistent development environments across machines.
- Customize Linter Rules: Tailor your ESLint or Prettier configuration files to match your team’s style guide or project needs.
- Performance: Be mindful that running linters and formatters on every commit can slow down large projects. Consider configuring Husky to only lint staged files or to run heavier tasks only on specific conditions.
- **Security**: Use trusted Docker images from the official repositories to minimize security risks. Additionally, manage sensitive data like API keys and environment variables using secure methods like `.env` files and Kubernetes secrets.
- **CI/CD Integration**: For added protection, you can also integrate these checks into your CI/CD pipeline to ensure that no invalid code gets merged into the main branch.

### Advanced Options & Error Handling

- **Docker Compose**: If your app grows to include multiple services (e.g., a backend API, a database, and a frontend), Docker Compose can simplify the process of running them together. It lets you define multiple containers and their relationships in a single YAML file.

- **Error Handling Tips**: If you run into errors during Docker or Kubernetes setup, common issues could be related to system requirements (e.g., virtualized hardware support for Minikube). Check the Docker and Minikube documentation for troubleshooting steps or seek help from online communities if you encounter persistent issues.

### Summary

By completing these tasks, you’ve not only set up the foundational tools and environment but also ensured that your AI-powered document assistant will have a robust and scalable infrastructure from the start. As you move through the course, this environment will enable you to test and deploy your app with confidence, knowing it will behave the same way locally as it does in production.

---
