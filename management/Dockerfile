# Use AlmaLinux as the base image
FROM alpine:latest

RUN apk add --no-cache \
        ca-certificates \
        curl \
        openssl

# Install kubectl
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" \
    && chmod +x ./kubectl \
    && mv ./kubectl /usr/local/bin/kubectl

# Install talosctl
RUN curl -LO https://github.com/siderolabs/talos/releases/latest/download/talosctl-linux-amd64 \
    && chmod +x talosctl-linux-amd64 \
    && mv talosctl-linux-amd64 /usr/local/bin/talosctl

# Set environment variables
ENV KUBECONFIG=/opt/kubeconfig/kubeconfig
ENV TALOSCONFIG=/opt/talosconfig/talosconfig

# The CMD directive is optional, adjust it to your preferred default command
CMD ["tail", "-f", "/dev/null"]
