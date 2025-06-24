FROM python:3.10-slim

WORKDIR /app

# Install Rust + build dependencies for uv
RUN apt-get update && apt-get install -y curl build-essential git pkg-config libssl-dev rustc && \
    apt-get clean

# Install uv from official script
RUN curl -Ls https://astral.sh/uv/install.sh | bash

# Ensure the uv binary path is available
ENV PATH="/root/.local/bin:$PATH"

# Copy your app code
COPY . .

# Install Flask using uv
RUN uv pip install flask

EXPOSE 8002

# Run the app using uv
CMD ["uv", "run", "app.py"]
