# Use a base Python image with Rust (needed for uv)
FROM python:3.10-slim

# Set working directory
WORKDIR /app

# System dependencies for building uv
RUN apt-get update && apt-get install -y curl build-essential git pkg-config libssl-dev rustc && \
    apt-get clean

# Install uv from prebuilt binary
RUN curl -Ls https://astral.sh/uv/install.sh | bash

# Add uv to PATH (in case it isn't linked)
ENV PATH="/root/.cargo/bin:$PATH"

# Copy app code
COPY . .

# Install Flask using uv (optional step for clean deps)
RUN uv pip install flask

# Expose the port the app runs on
EXPOSE 8002

# Run the app using uv
CMD ["uv", "run", "app.py"]
