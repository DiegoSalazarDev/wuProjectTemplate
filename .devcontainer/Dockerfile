FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

# 1. Instalar dependencias base y herramientas de firma
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    gnupg \
    ca-certificates \
    apt-transport-https

# 2. Agregar la llave GPG y el repositorio de devkitPro
RUN curl -sL https://keyserver.ubuntu.com/pks/lookup?op=get&search=0x21703666068222A8 | gpg --dearmor > /usr/share/keyrings/devkitpro.gpg \
    && echo "deb [signed-by=/usr/share/keyrings/devkitpro.gpg] https://apt.devkitpro.org stable main" > /etc/apt/sources.list.d/devkitpro.list

# 3. Instalar dkp-pacman y herramientas
RUN apt-get update && apt-get install -y \
    dkp-pacman \
    wiiu-dev \
    wut

# 4. Configurar variables de entorno
ENV DEVKITPRO=/opt/devkitpro
ENV DEVKITPPC=/opt/devkitpro/devkitPPC
ENV PATH=$PATH:/opt/devkitpro/devkitPPC/bin
