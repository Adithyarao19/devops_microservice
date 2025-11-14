# service_1/Dockerfile
FROM golang:1.24-alpine

# utilities for module fetch & healthcheck tools
RUN apk add --no-cache ca-certificates git wget

WORKDIR /app

# copy go.mod and go.sum first (if present) to leverage Docker cache
# If you don't have go.mod/go.sum yet, the build will still work but it's recommended to create them.
COPY go.mod go.sum ./

# download modules (cached)
RUN go mod download || true

# copy source
COPY . .

# build
RUN go build -o main .

# expose port (optional for clarity)
EXPOSE 8001

CMD ["./main"]
