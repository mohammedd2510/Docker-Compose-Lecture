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
USER appuser
# Default command
CMD ["./whoami.sh"]