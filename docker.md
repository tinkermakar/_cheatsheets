# Docker Cheatsheet

1. Docker Swarm can have multiple master nodes as well
    ```bash
    docker swarm join-token manager
    ```

1. When we don't use JSON notation for CMD and ENTRYPOINT arguments, the executables referenced won't receive signals from the OS correctly. This is particularly relevant when talking about how to signal to a running container that it is being shut down (i.e., a SIGTERM). (credit: https://depot.dev/blog/dockerfile-linting-issues)

1. Docker builder stores an insane amount of cache. Run `docker builder prune` from time to time.

1. `ADD` directive is `COPY` on steroids -- it can copy from the web and even pre-extract compressed archive files

1. Mount a secret during the build:
    ```
    RUN --mount=type=secret,id=mysecret cat /run/secrets/mysecret
    ```

1. BuildKit cache mounts persist package-manager/build-tool caches across builds without baking them into the image layer.
    ```dockerfile
    RUN --mount=type=cache,target=/root/.npm npm ci
    ```

1. Exclude a directory like `node_modules` from a bind mount by adding a separate anonymous volume for it.
    ```yaml
    services:
      app:
        volumes:
          - .:/app
          - /app/node_modules
    ```
