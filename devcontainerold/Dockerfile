FROM mcr.microsoft.com/devcontainers/base:debian

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    git \
    fzf \
    ripgrep \
    npm \
    lazygit \
    fd-find \
    neovim \
    vim \
    && curl -s https://fluxcd.io/install.sh | sudo bash \
    && flux completion bash | sudo tee /etc/bash_completion.d/flux >/dev/null \
    && wget https://github.com/derailed/k9s/releases/latest/download/k9s_linux_amd64.deb \
    && sudo apt install ./k9s_linux_amd64.deb \
    && rm k9s_linux_amd64.deb \
    && curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.37/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg \
    && sudo chmod 644 /etc/apt/keyrings/kubernetes-apt-keyring.gpg \
    && echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.37/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list \
    && sudo chmod 644 /etc/apt/sources.list.d/kubernetes.list \
    && sudo apt-get update \
    && sudo apt-get install -y kubectl
