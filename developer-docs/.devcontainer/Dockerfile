FROM python:3.9-alpine
LABEL name=com.sap.developer-docs
LABEL vendor="psmware ltd"
LABEL com.sap.developer-docs.version="1.0"
LABEL com.sap.developer-docs.version.release-date="2020-10-10"
LABEL com.sap.developer-docs.version.version.is-production=""

RUN apk --no-cache upgrade && apk add --no-cache --virtual .build-deps \
    git \
    gnupg \
    less \
    zsh \
    zip \
    curl \
    vim \
    sudo \
    openssh-client
# Setting up user access
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN echo "===> Creating installing MkDocs..." \
    && python -m pip install --upgrade pip
COPY .devcontainer/*requirements.txt /root
RUN pip3 install -r /root/requirements.txt
RUN echo "===> Creating development user and group..." \
    && addgroup -g $USER_GID $USERNAME \
    && adduser -D -s /bin/zsh -G $USERNAME -u $USER_UID $USERNAME \
    # Add sudo support for non-root user
    && apk add sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && mkdir -p /app
USER ${USERNAME}
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" \
    && touch /home/$USERNAME/.z
COPY .devcontainer/.zshrc  /home/$USERNAME/
USER root
COPY ./.devcontainer/.ashrc /root/
RUN chown -fR $USERNAME:$USERNAME /home/$USERNAME \
    && chown -fR $USERNAME:$USERNAME /app \
    && rm -f /root/requirements.txt
WORKDIR /app