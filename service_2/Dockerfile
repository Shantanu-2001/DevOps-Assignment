FROM python:3.10-slim

WORKDIR /app

# Install Rust and other build tools
RUN apt-get update && apt-get install -y curl build-essential git pkg-config libssl-dev rustc && \
    apt-get clean

# Install uv
RUN curl -Ls https://astral.sh/uv/install.sh | bash
ENV PATH="/root/.local/bin:$PATH"

# Copy your app code
COPY . .

# Create a .venv environment before installing packages
RUN uv venv && uv pip install flask

EXPOSE 8002

CMD ["uv", "run", "app.py"]
