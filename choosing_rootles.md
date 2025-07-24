## 🚫 Why Rootless Is a Challenge

#### 🔒 1. Port Limitations
You can’t bind to privileged ports like 80 (HTTP) or 443 (HTTPS) without root.
- Solutions:
    - Use higher ports (e.g. 8080, 8443) for your services inside the container
    - If needed, you might use a reverse proxy (like NGINX) inside the container to handle routing, but it too must bind to a non-privileged port.
    - Document that users must visit https://localhost:8443 (or your chosen higher port) instead of the default ports
#### 📁 2. No Bind-Mounting Volumes
You can’t use volume mounts (-v ./src:/app/src) unless the container’s UID matches the host’s — which it usually doesn’t.
- Solutions:
    - `COPY` in Dockerfile: The most straightforward approach is to COPY your application files directly into the container during the build process. This means changes to your code require a container rebuild.
    - Named Docker Volumes: For persistent data (like database files or user uploads), use named Docker volumes (e.g., /app/data). These are managed by Docker and don't rely on direct host filesystem mapping, making them compatible with rootless mode.
    - Consider "Root as Unique UID" (Advanced/Alternative): The project rules mention "craft your own image with root as unique UID" as a possible strategy. If your container runtime uses the root UID (0), bind mounts can work. However, this often defeats the security benefits of a rootless host environment and might have its own security implications. It's generally discouraged in rootless setups unless absolutely necessary and fully understood.
    - Workflow Adaptation: Avoid relying on live host-container syncing. You won’t see instant code updates from your host inside the container.
#### 🔧 3. File Permissions Inside Container
If the container runs as a non-root user (UID ≠ 0), you might hit:
- Permission errors when accessing files or running certain scripts
- Issues writing to mounted volumes or log directories
- Solution:
    - Set correct ownership and permissions during Dockerfile build (`chown`, `chmod`)
    - Use non-root-friendly paths like `/app/data` over system level locations like `/etc`
    - Consider running only the essential parts that require elevated access during local dev
#### 🧱 4. Some Tools Expect Root
Some services (like PostgreSQL, certain cert managers, or debug tools) expect root access.
- Solutions:
    - Use rootless-compatible base images (e.g. node:alpine, postgres:14), these images are often optimized for smaller size and better security practices
    - Check Dockerfile layers carefully — avoid USER root unless necessary, switch back to a non-root user for the final runtime.
#### ⚠️ 5. Networking Quirks
Cross container communication can get tricky, especially if you rely on localhost.
- Solution:
    - Use Docker Compose with service names (e.g. db:5432) for internal networking
    - Avoid assumptions that all containers share the same network stack automatically
    - Test service discovery and container DNS properly
#### 📜 6. Certificate Setup for HTTPS
Managing TLS certificates is harder without root, especially when tools write to /etc/ssl or use privileged ports.
- Solution:
    -  Generate self-signed certs inside the container using openssl and store them in safe paths like `/app/certs`
    - Serve HTTPS from web server (e.g., NGINX, Express.js) inside the container or on non priviledged ports like  8443
    - Ensure your frontend uses WSS (WebSocket Secure) for secure WebSocket communication if your application relies on it.
#### 🧪 7. Rebuilding Instead of Live Editing
Without bind-mount volumes, you will likely need to rebuild your Docker container image every time you update your code. This is a significant change from typical local development workflows.
- Solution:
    - Automate rebuild with Makefile or bash script
    - Structure Dockerfile layers for faster rebuilds (e.g. COPY ./src as a final step), place frequently changing files (like your application code) in later layers, and less frequently changing dependencies (like npm packages or system libraries) in earlier layers.
    - Develop locally with live editing, then sync changes to /goinfre before rebuilding

#### 8. Pre-Build Everything With Root → Run in Rootless
Use full privileges on your own machine to build and test, then deploy to rootless environments.

Workflow:
- docker build + local cert generation (however this may not be needed if using self signed certs in docker)+ image testing
- Push final images to a public registry (e.g. Docker Hub)
- On school machine: docker pull + docker run
⚠️ Ensure your built image doesn’t require root actions at runtime (like privileged ports)
#### 🔄 9. Git-Driven Iteration
Git can serve as a robust mechanism to replace the need for bind-mounting files between your host and container, especially when working across different environments (like your local machine and the school cluster).

Workflow:
- Code on your personal machine with full access
- Commit and push via Git
- On school machine: git pull + rebuild container
⚠️ Still requires image rebuilds after changes

🧠 So Why consider Rootless mode?
- Compliant with campus environment restrictions
- Sandboxed = lower risk of system-wide mistakes
- Future-proofed for cloud-native environments (e.g. Kubernetes)
- Preferred for evaluation — it's what they'll test



## 🖥️ Using a Virtual Machine (VM)
A virtual machine gives you full root access and an isolated environment to run Docker without restrictions — ideal for development and portability.
```bash
./launch_vm_then_start_container.sh
```

This command should:
- Boot your VM (e.g. VirtualBox, QEMU)
- Launch your container stack inside the VM (e.g. docker-compose up)
- Run the full app automatically, without manual login or typing

✅ As long as your stack starts autonomously, this satisfies the “single command to launch autonomous container” rule.

✔️ Pros
- You control the OS — full root
- Easy volume mounts, port binding, certificate management
- Can run regular Docker without restrictions

❌ Cons
- High disk space usage — not ideal on slow or storage-limited school machines
- VM startup might be slow or flaky on some hardware
- You must ensure the VM itself auto-launches everything to stay compliant with the “single command” rule

## 🐳 Docker-in-Docker (DinD)
Docker-in-Docker is when a container runs a Docker daemon inside itself — so it can spawn other containers. This is useful in CI pipelines (like GitLab CI) but it’s not ideal in most projects like ft_transcendence.

🔍 Why It’s Often Discouraged:
- 💥 Security risks — DinD breaks container isolation and gives high privileges to nested processes.
- 🔧 Complexity — networking, volumes, and port mapping can get convoluted fast.
- ❌ Rootless mode conflict — DinD assumes some root-like permissions internally.
- ⚠️ TLS/HTTPS headaches — serving HTTPS (or WSS for WebSockets) from inside a DinD setup is much harder to configure.

🚫 DinD is often used in CI/CD pipelines but is not appropriate for ft_transcendence. Avoid this method — it's unnecessary and creates more problems than it solves.


## 🧪 Lightweight Virtual Alternatives

These tools simulate VM-like behavior with much less resource usage:

| Tool                     | Description                                           | Good For                        |
|--------------------------|-------------------------------------------------------|----------------------------------|
| **Colima / Rancher Desktop** | Docker-compatible VM layer for macOS/Linux             | Fast local dev with rootlike access |
| **Distrobox**            | Runs Linux inside your user namespace (no full VM)    | Lightweight isolated testing     |
| **WSL2 + Docker**        | Linux subsystem integrated into Windows               | Efficient container dev on Windows |

✔️ Pros
- Smaller footprint than full VMs
- Often support rootlike access inside sandbox
- Quick setup for local testing and debugging.

❌ Cons
- May not behave consistently on school machines
- Still rely on Docker inside the environment — rootless quirks may persist
- Not guaranteed to match school’s evaluation environment
