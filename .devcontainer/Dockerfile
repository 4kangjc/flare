FROM gcc:11

WORKDIR /workspace/flare

RUN apt-get update && apt-get install -y \
    vim-common \
    python \
    && rm -rf /var/lib/apt/lists/*

RUN ARCH=$(uname -m) && \
    if [ "$ARCH" = "aarch64" ]; then \
        BAZEL_URL="https://github.com/bazelbuild/bazel/releases/download/6.3.2/bazel-6.3.2-linux-arm64"; \
    elif [ "$ARCH" = "x86_64" ]; then \
        BAZEL_URL="https://github.com/bazelbuild/bazel/releases/download/6.3.2/bazel-6.3.2-linux-x86_64"; \
    else \
        echo "Unsupported architecture"; \
        exit 1; \
    fi && \
    wget "$BAZEL_URL" -O /bin/bazel && \
    chmod +x /bin/bazel
