FROM debian:bookworm-slim

RUN apt-get update &&  apt-get install -y \
    curl \
    ca-certificates \
    --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*


ARG OLLAMA_VERSION=0.5.7
ARG OLLAMA_URL=https://github.com/ollama/ollama/releases/download/v${OLLAMA_VERSION}/ollama-linux-arm64.tgz

RUN curl -L ${OLLAMA_URL} -o /tmp/ollama.tgz && \
    cd /tmp && \
    echo "Contents of /tmp:" && \
    ls -la && \
    echo "Contents of tarball:" && \
    tar tvf ollama.tgz && \
    echo "Extacting..." && \
    tar xzf ollama.tgz && \
    echo "Contents after extraction:" && \
    ls -la && \
    find . -name "ollama" -type f -exec mv {} /usr/local/bin/ \; && \
    chmod +x /usr/local/bin/ollama && \
    rm /tmp/ollama.tgz

RUN mkdir -p /root/.ollama

RUN ollama --version
EXPOSE 11434

CMD ["/usr/local/bin/ollama", "serve"]