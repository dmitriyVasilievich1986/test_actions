FROM python:3.14-slim

ARG VERSION=dev
LABEL org.opencontainers.image.version=$VERSION

COPY --from=ghcr.io/astral-sh/uv:0.9 /uv /usr/local/bin/uv

WORKDIR /app

COPY pyproject.toml uv.lock .python-version ./
RUN uv sync --frozen --no-dev

COPY . .

CMD ["uv", "run", "--no-sync", "python", "main.py"]
