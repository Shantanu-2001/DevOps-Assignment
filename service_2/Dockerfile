# Use a slim Python 3.10 base image
FROM python:3.10-slim

# Set working directory inside container
WORKDIR /app

# Install Rust and required build tools to support uv installation
RUN apt-get update && apt-get install -y curl build-essential git pkg-config libssl-dev rustc && \
    apt-get clean

# Install uv using official installation script and add to PATH
RUN curl -Ls https://astral.sh/uv/install.sh | bash
ENV PATH="/root/.local/bin:$PATH"

# Copy project files into the container
COPY . .

# Create virtual environment using uv and install flask
RUN uv venv && uv pip install flask

# Expose the port that the Flask app will run on
EXPOSE 8002

# Start the application using uv
CMD ["uv", "run", "app.py"]
