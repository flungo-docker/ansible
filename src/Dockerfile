# Build from a configurable base image
ARG BASE_IMAGE=base/archlinux
FROM ${BASE_IMAGE}

# Configurable build arguments to support multiple distros
ARG PACKAGE_MANAGER=pacman
ARG PACKAGES=ansible

# Install ansible using the appropriate package manager
RUN case "${PACKAGE_MANAGER}" in \
    'pacman') \
      pacman -Syyu --noconfirm ${PACKAGES} && \
      rm -rf /var/cache/pacman/pkg/* /var/lib/pacman/sync/* \
    ;; \
    'apt-get') \
      apt-get update && \
      apt-get install -y ${PACKAGES} && \
      rm -rf /var/lib/apt/lists/* \
    ;; \
    *) \
      echo "Unknown PACKAGE_MANAGER"; \
      exit 1 \
    ;; \
  esac

# Add a basic hosts file
COPY hosts /etc/ansible/hosts
