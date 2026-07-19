FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

# 1. Instalar dependencias necesarias para la configuración de repositorios
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    gnupg \
    ca-certificates \
    apt-transport-https \
    && rm -rf /var/lib/apt/lists/*

# 2. Agregar la llave GPG oficial y el repositorio apt de devkitPro
RUN curl -sL https://keyserver.ubuntu.com/pks/lookup?op=get&search=0x21703666068222A8 | gpg --dearmor > /usr/share/keyrings/devkitpro.gpg \
    && echo "deb [signed-by=/usr/share/keyrings/devkitpro.gpg] https://apt.devkitpro.org stable main" > /etc/apt/sources.list.d/devkitpro.list

# 3. Instalar dkp-pacman, wiiu-dev y wut
# Usamos apt update justo antes para que tome el nuevo repositorio
RUN apt-get update && apt-get install -y \
    dkp-pacman \
    wiiu-dev \
    wut \
    && rm -rf /var/lib/apt/lists/*

# 4. Configurar variables de entorno globales
# Esto permite que cualquier terminal que abras tenga el compilador listo
ENV DEVKITPRO=/opt/devkitpro
ENV DEVKITPPC=/opt/devkitpro/devkitPPC
ENV PATH=$PATH:/opt/devkitpro/devkitPPC/bin
