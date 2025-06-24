# Use the official Go base image
FROM golang:1.20-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy Go source files into the container
COPY . .

# Build the Go application
RUN go build -o main .

# Expose port 8001 (same as in main.go)
EXPOSE 8001

# Run the compiled Go binary
CMD ["./main"]
