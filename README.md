# GitLab CI/CD Static Website

A containerized static website deployment solution using Docker, GitLab CI/CD, and Nginx.  This project demonstrates modern DevOps practices by automating the build and deployment of a static website through a multi-stage Docker build process.

## 🚀 About

This project showcases a **Docker-optimized** approach to deploying static websites with continuous integration and continuous deployment (CI/CD) capabilities. It leverages GitLab CI/CD pipelines to automatically build and deploy a containerized Nginx web server serving static content.

### Key Features

- **🐳 Multi-stage Docker Build**:  Optimized Docker image size using multi-stage builds
- **📦 Containerized Deployment**: Fully containerized application for consistent environments
- **🔄 GitLab CI/CD Integration**:  Automated build and deployment pipeline
- **⚡ Nginx Web Server**: High-performance static content serving
- **🔧 Dynamic Port Configuration**: Flexible port binding through environment variables
- **🎯 Alpine Linux Base**:  Minimal footprint using Alpine-based images

## 🏗️ Architecture

The project uses a **two-stage Docker build**:

1. **Stage 1 (Build Stage)**: 
   - Base:  `ubuntu:18.04`
   - Clones the static website repository
   - Prepares files for deployment

2. **Stage 2 (Runtime Stage)**:
   - Base: `nginx:stable-alpine3.17-slim`
   - Copies static files from build stage
   - Configures Nginx with custom configuration
   - Exposes port 80 for web traffic

## 🛠️ Technologies

- **Docker**:  Containerization platform
- **Nginx**: High-performance web server
- **GitLab CI/CD**: Automation and deployment pipeline
- **Git**: Version control
- **Alpine Linux**: Lightweight container OS

## 📋 Prerequisites

- Docker installed on your system
- GitLab account (for CI/CD pipeline)
- Basic understanding of Docker and containerization

## 🚀 Quick Start

### Building the Docker Image

```bash
docker build -t static-website . 
```

### Running the Container

```bash
docker run -d -p 8080:80 --name my-static-website static-website
```

### Running with Custom Port

```bash
docker run -d -p 8080:80 -e PORT=80 --name my-static-website static-website
```

Access your website at `http://localhost:8080`

## 🐳 Docker Configuration

### Dockerfile Highlights

- **Multi-stage build** reduces final image size
- **DEBIAN_FRONTEND=noninteractive** prevents installation prompts
- **Dynamic port configuration** through environment variable substitution
- **Custom Nginx configuration** for optimized static content delivery

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `PORT` | Nginx listening port | 80 |

## 📁 Project Structure

```
gitlab-CICD-staticwebsite/
├── Dockerfile              # Multi-stage Docker build configuration
├── nginx.conf             # Custom Nginx server configuration
└── README.md             # Project documentation
```

## 🔧 Customization

### Modifying the Static Website Source

Edit the Dockerfile to point to your own repository:

```dockerfile
RUN git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git /opt/files/
```

### Updating Nginx Configuration

Modify `nginx.conf` to customize server behavior, caching, compression, etc.

## 🚢 Deployment

This project is designed to work with GitLab CI/CD.  The pipeline automatically:

1. Builds the Docker image
2. Runs tests (if configured)
3. Pushes to container registry
4. Deploys to target environment

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. 

## 📝 License

This project is open source and available under the MIT License. 

## 👤 Maintainer

**TCHASSEM ANSELME** (@AnselmeG300)

## 🌟 Acknowledgments

- Static website example from [static-website-example](https://github.com/AnselmeG300/static-website-example)
- Nginx for powerful web serving capabilities
- Docker for containerization technology
- GitLab for CI/CD infrastructure

---

**Built with Docker** 🐳 | **Powered by Nginx** ⚡ | **Automated with GitLab CI/CD** 🔄
```
