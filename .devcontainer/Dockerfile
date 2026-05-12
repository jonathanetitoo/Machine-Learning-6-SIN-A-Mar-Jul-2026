FROM mcr.microsoft.com/devcontainers/python:1-3.11-bookworm

# Instalar uv (gestor rápido de paquetes)
RUN pip install --no-cache-dir uv

WORKDIR /workspace

# Copiar archivos de dependencias primero (mejor caching de Docker)
COPY pyproject.toml uv.lock ./

# Crear venv y sincronizar con --python (CRÍTICO en Docker)
RUN uv venv .venv --python 3.11 \
 && uv pip install --python .venv/bin/python -r pyproject.toml

# Activar el venv para sesiones interactivas
ENV PATH="/workspace/.venv/bin:$PATH"
ENV VIRTUAL_ENV="/workspace/.venv"

# Registrar kernel de Jupyter
RUN .venv/bin/python -m ipykernel install --user --name ml-p2 \
    --display-name "Python (ML P2)"