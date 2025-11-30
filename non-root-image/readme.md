# 🛠️ Step-by-Step: Dockerfile Example Using UID 1000


```Dockerfile
# Use a minimal base image
FROM alpine:3.19

# Add a non-root user with UID and GID 1000
RUN addgroup -g 1000 appgroup && \
    adduser -u 1000 -G appgroup -D appuser

# Create a working directory with proper permissions
RUN mkdir /app && chown -R 1000:1000 /app
WORKDIR /app

# Simple script to show current user info
COPY whoami.sh .

# Make script executable
RUN chmod +x whoami.sh

# Default command
CMD ["./whoami.sh"]
```
📄 whoami.sh
```bash
#!/bin/sh
echo "🧑 Running as user: $(whoami)"
echo "🆔 UID: $(id -u)"
echo "🆔 GID: $(id -g)"
```


⸻

🧪 Build the Image
```bash
docker build -t my-nonroot-app .
```


⸻

▶️ Run the Image with --user 1000:1000
`docker run --rm --user 1000:1000 my-nonroot-app`

⸻

❗ What Happens Without --user

If your Dockerfile uses USER appuser, then --user is not needed.

But if not set, Docker will run as root by default:

`docker run --rm my-nonroot-app`
