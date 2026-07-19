FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

# 1. Instalar dependencias necesarias para manejar repositorios
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    gnupg \
    ca-certificates \
    sudo

# 2. Instalar el gestor de paquetes de devkitPro
RUN curl -LO https://github.com/devkitPro/pacman/releases/download/devkitpro-pacman-1.0.1/devkitpro-pacman.deb \
    && dpkg -i devkitpro-pacman.deb \
    && rm devkitpro-pacman.deb

# 3. CRÍTICO: Inicializar pacman y actualizar bases de datos
# Sin esto, dkp-pacman no sabe dónde buscar los paquetes de Wii U
RUN /opt/devkitpro/pacman/bin/pacman-key --init \
    && /opt/devkitpro/pacman/bin/pacman-key --populate devkitpro \
    && /opt/devkitpro/pacman/bin/pacman -Sy

# 4. Instalar las herramientas
RUN /opt/devkitpro/pacman/bin/pacman -S --noconfirm \
    wiiu-dev \
    wut

# 5. Exportar variables de entorno para que el compilador las encuentre siempre
ENV DEVKITPRO=/opt/devkitpro
ENV DEVKITPPC=/opt/devkitpro/devkitPPC
ENV PATH=$PATH:/opt/devkitpro/devkitPPC/bin
