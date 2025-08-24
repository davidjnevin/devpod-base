FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

ARG USERNAME=david
ARG USER_UID=1001
ARG USER_GID=$USER_UID

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    #
    # [Optional] Add sudo support. Omit if you don't need to install software after connecting.
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# ********************************************************
# * Anything else you want to do like clean up goes here *
# ********************************************************

# [Optional] Set the default user. Omit if you want to keep the default as root.

USER $USERNAME

# Install the curl, vim and, tmux packages
RUN apt-get update && apt-get install -y curl vim tmux alacritty

COPY --from=jdxcode/mise /usr/local/bin/mise /usr/local/bin/

# # Rename the 'vscode' user to 'david'
# RUN usermod -l david vscode && \
#     usermod -m -d /home/david david && \
#     groupmod -n david vscode

# make sure mise is activated in both zsh and bash. Might be overridden by a user's dotfiles.
RUN echo 'eval "$(mise activate bash)"' >> /home/vscode/.bashrc && \
    echo 'eval "$(mise activate zsh)"' >> /home/vscode/.zshrc

