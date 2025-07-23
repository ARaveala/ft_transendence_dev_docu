## 🚫 Why Rootless Is a Challenge

#### 🔒 1. Port Limitations
You can’t bind to privileged ports like 80 (HTTP) or 443 (HTTPS) without root.
- Solutions:
    - Use higher ports (e.g. 8080, 8443) and reverse proxy if needed
    - Document that users must visit https://localhost:8443 instead of the default
#### 📁 2. No Bind-Mounting Volumes
You can’t use volume mounts (-v ./src:/app/src) unless the container’s UID matches the host’s — which it usually doesn’t.
- Solutions:
    - Use `COPY` in your Dockerfile to move files into the container
    - Use named Docker volumes for persistent internal storage (e.g. /app/data)
    - Avoid relying on live host-container syncing
#### 🔧 3. File Permissions Inside Container
If the container runs as a non-root user (UID ≠ 0), you might hit:
- Permission errors when accessing files or running certain scripts
- Issues writing to mounted volumes or log directories
- Solution:
    - Set correct ownership and permissions during Dockerfile build (chown, chmod)
    - Use non-root-friendly paths like /tmp or /app/data over system level locations like /etc
    - Consider running only the essential parts that require elevated access during local dev
#### 🧱 4. Some Tools Expect Root
Some services (like PostgreSQL, certain cert managers, or debug tools) expect root access.
- Solutions:
    - Use rootless-compatible base images (e.g. node:alpine, postgres:14)
    - Check Dockerfile layers carefully — avoid USER root unless necessary
#### ⚠️ 5. Networking Quirks
Cross-container communication can get tricky, especially if you rely on localhost.
- Solution:
    - Use Docker Compose with service names (e.g. db:5432) for internal networking
    - Avoid assumptions that all containers share the same network stack automatically
    - Test service discovery and container DNS properly
#### 📜 6. Certificate Setup for HTTPS
Managing TLS certificates is harder without root, especially when tools write to /etc/ssl or use privileged ports.
- Solution:
    - Generate certs ahead of time on a dev machine with root
    - Add them to the container during build (COPY ./certs)
    - Serve HTTPS from NGINX inside the container on 8443
    - Ensure the frontend uses WSS for secure WebSockets
#### 🧪 7. Rebuilding Instead of Live Editing
Without volume mounts, you may need to rebuild your container every time you update code.
- Solution:
    - Automate rebuild with Makefile or bash script
    - Structure Dockerfile layers for faster rebuilds (e.g. COPY ./src as a final step)
    - Develop locally with live editing, then sync changes to /goinfre before rebuilding

#### 8. Pre-Build Everything With Root → Run in Rootless
Use full privileges on your own machine to build and test, then deploy to rootless environments.

Workflow:
- docker build + local cert generation + image testing
- Push final images to a public registry (e.g. Docker Hub)
- On school machine: docker pull + docker run
⚠️ Ensure your built image doesn’t require root actions at runtime (like privileged ports)
#### 🔄 9. Git-Driven Iteration
Git can replace the need for bind-mounting files between host and container.

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
