# 📼 Container Technologies for ft_transcendence
This document provides an overview of various container technologies, evaluating their suitability for your ft_transcendence project,
with a focus on ease of learning, project scope, and compliance with school rules.

Understanding Container Technologies
Container technologies provide a lightweight, portable, and consistent way to package and run applications. They virtualize the operating system level,
allowing applications to run in isolated "containers" that share the host OS kernel but have their own filesystem, processes, and network interfaces.

For ft_transcendence, the goal is to package the web application (frontend, backend, database) into one or more containers that can be launched with a single command.

## 1. Docker
Explanation: Docker is the most widely recognized and used container platform. It consists of the Docker Engine (daemon), a CLI, and Docker Compose for multi-container applications.
It builds images from Dockerfiles and runs them as containers.

✔️ Pros for ft_transcendence:
- Team Familiarity: As most of the team is already familiar with Docker, the initial learning curve for basic container operations (docker build, docker run, docker-compose up)
will be minimal.
- Mature Ecosystem: Docker has a vast ecosystem, extensive documentation, and a large community, making it easy to find solutions and best practices.
- docker-compose: This tool is specifically designed for defining and running multi-service Docker applications, which is highly relevant for ft_transcendence (frontend, backend, database). It directly supports the "single command launch" requirement.
- Wide Adoption: Being the industry standard, using Docker prepares you for real-world development environments.

❌ Cons for ft_transcendence:
- Rootless Challenges: As detailed in the existing [choosing_rootles.md](choosing_rootles.md) document, running Docker in rootless mode introduces complexities with port binding, volume mounts, and file permissions. These require careful configuration and understanding.
- Daemon-based: Docker Engine runs as a background daemon, which some consider an overhead or a potential single point of failure (though generally stable).

Project Scope & Tools:
- Dockerfile: Used to define how the application images are built. This is a core part of the project.
- docker-compose.yml: Essential for orchestrating a multi-service application (frontend, backend, database) with a single docker-compose up command.
- Build Process: You'll use docker build to create images and docker run (or docker-compose up) to run them. The "rebuilding instead of live editing" challenge will apply.

## 2. Podman
Explanation: Podman is a daemonless container engine for developing, managing, and running OCI (Open Container Initiative) compliant containers on your Linux system.
It's often seen as a direct alternative to Docker, providing a very similar command-line interface.

✔️ Pros for ft_transcendence:

- Native Rootless Support: This is Podman's biggest advantage for your project. It's designed from the ground up to run containers as non-root users,
which can significantly simplify many of the challenges you face with Docker's rootless mode (e.g., user ID mapping, permissions).
- Docker-Compatible CLI: The command-line interface for Podman is largely identical to Docker (e.g., podman build, podman run, podman ps),
making the learning curve extremely low for a team familiar with Docker.
- Daemonless Architecture: Podman doesn't require a constantly running background daemon, which can be seen as simpler and more secure.
With Podman, when you run a container, it's typically a child process of your terminal session.
- podman-compose: A tool that mimics docker-compose functionality, allowing you to manage multi-container applications using a docker-compose.yml file.

❌ Cons for ft_transcendence:

- Maturity of podman-compose: While functional, podman-compose might be slightly less mature or have fewer advanced features compared to docker-compose.
- Less Widespread (Historically): While gaining significant traction, Podman is still less universally adopted than Docker, meaning fewer online resources or pre-built solutions specifically for Podman
(though Docker resources are often directly applicable).
 
Project Scope & Tools:

- Dockerfile (or Containerfile): Podman uses the same Dockerfile format.
- podman-compose: The equivalent to docker-compose for multi-service orchestration.
- Simplified Rootless Management: Its native rootless design could potentially make debugging permission and port issues easier compared to Docker's rootless mode.

## 3. Containerd
Explanation: Containerd is a core container runtime that manages the complete container lifecycle (image transfer and storage, container execution, and supervision).
It's a low-level component that powers many higher-level container platforms, including Docker itself (since Docker 1.11).

✔️ Pros for ft_transcendence:

- Lightweight and Efficient: As a core runtime, it's very efficient and has a small footprint.
- Foundational Understanding: Working with containerd directly provides a deeper understanding of how containers fundamentally operate.

❌ Cons for ft_transcendence:

- Steep Learning Curve (Too Low-Level): Containerd is designed for integration into platforms, not for direct end-user interaction for building and running complex applications.
Its CLI (ctr) is very verbose and lacks the user-friendliness of Docker or Podman.
- Not for Application Development: It doesn't offer built-in tools for building images (like Dockerfile parsing) or orchestrating multi-service applications
(like docker-compose). You would need to integrate other tools (like Buildah for building, and custom scripts for orchestration),
which goes against the "intuitive or very similar to Docker" requirement.
- Violates Prohibited Tools Rule (Indirectly): While not explicitly prohibited, using containerd directly would necessitate building many "features or modules"
(like image building, networking, volume management) from scratch or integrating numerous small tools, which could inadvertently lead to creating "complete solutions" for features,
depending on interpretation (Any direct instruction regarding the use (can, must, can’t) of
a third-party library or tool must be followed.). It's generally not the intended primary interface for an application project.

Project Scope & Tools:

Not Recommended as Primary Tool: Given the project's scope of building a web application and the team's familiarity with Docker, directly using containerd would add unnecessary complexity and a very steep learning curve. It's more relevant for those building container platforms or custom runtimes, not end-user applications.

## 4. Free Cloud-Hosted Docker Platforms (e.g., Replit, Gitpod, Render)
Explanation: These are online development environments or hosting platforms that provide pre-configured Linux environments where you can run Docker containers directly in the cloud. They abstract away much of the underlying infrastructure setup.

✔️ Pros for ft_transcendence:
- Bypass Local Machine Constraints: No need to worry about local Docker setup, rootless mode, /goinfre, or VM overhead.
- Accessibility/Collaboration: Easy to share development environments and collaborate.
- "Single Command Launch" Potential: Often integrate with docker-compose or similar orchestration, making launch simple.
- Instant Setup: Get a working environment quickly.

❌ Cons for ft_transcendence:

- School Rules Conflict (Potential): This is the biggest concern. These platforms might be considered "immediate and complete solutions for an entire feature or module" (i.e., the hosting/deployment feature), which is prohibited. This needs a strong caveat. It is crucial to clarify with your instructors if using such platforms for core project functionality is allowed for submission.
- Resource Limitations: Free tiers often have strict limits on CPU, RAM, and storage, which might not be sufficient for a multi-service application like ft_transcendence under load.
- Platform Restrictions: Some services may restrict container types, port exposure, or persistent volumes, requiring research into each platform's capabilities.
- Debugging Complexity: Debugging network issues or low-level container behavior can be harder than on a local machine or VM.

Evaluation Environment Mismatch: The evaluation will happen on 42 school machines, not these cloud platforms. Relying solely on them might lead to unexpected issues during grading.

Project Scope & Tools:

- You'd still use Dockerfile and docker-compose.yml.
- The primary tool is the platform's web interface or CLI.

Crucial Note: These platforms are primarily for development convenience and early testing. They should not be relied upon for the final submission due to potential rule violations and environment mismatches.

## Other Noteworthy Technologies (Briefly):
- runc: This is an even lower-level command-line tool for spawning and running containers according to the OCI runtime specification. It's a component within containerd and Docker. Definitely too low-level for direct project use.
- LXC/LXD: These are Linux container technologies that offer more VM-like isolation than Docker, but are less focused on application packaging and portability across different Linux distributions. They have a different paradigm and a steeper learning curve than Docker, making them less suitable for this project.
- Buildah / Skopeo: These are tools primarily associated with Podman. Buildah helps build OCI-compliant images (like docker build), and Skopeo helps copy/inspect images between registries. They are tools that complement container engines, rather than being container runtimes themselves. Using them might align with the "small library or tool that solves a simple, unique task" rule if integrated for specific build steps, but they wouldn't replace Docker/Podman as the main containerization platform.

### Recommendation for ft_transcendence
Given the team's familiarity with Docker and the project's constraints:

Docker (with careful attention to rootless mode solutions): This remains the most straightforward path due to team familiarity and the robust docker-compose ecosystem.
The challenges of rootless mode should be well documented in [choosing_rootles.md](choosing_rootles.md) and are manageable with the provided solutions.

Podman: This is a strong contender, especially if we find Docker's rootless mode configurations particularly cumbersome.
Its native rootless support and Docker-compatible CLI could offer a smoother experience once the initial setup is understood.
It's worth exploring if Docker's rootless quirks prove too problematic.

Avoid Containerd, runc, LXC/LXD as primary tools for this project. They are too low-level or too different from the Docker paradigm,
introducing unnecessary complexity and a significant learning curve that doesn't align with the project's goals of building a web application.
