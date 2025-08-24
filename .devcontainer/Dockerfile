FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04
# Install the curl, vim and, tmux packages
RUN apt-get update && apt-get install -y curl vim tmux alacritty

COPY --from=jdxcode/mise /usr/local/bin/mise /usr/local/bin/

# Rename the 'vscode' user to 'david'
RUN usermod -l david vscode && \
    usermod -m -d /home/david david && \
    groupmod -n david vscode

# make sure mise is activated in both zsh and bash. Might be overridden by a user's dotfiles.
RUN echo 'eval "$(mise activate bash)"' >> /home/vscode/.bashrc && \
    echo 'eval "$(mise activate zsh)"' >> /home/vscode/.zshrc

