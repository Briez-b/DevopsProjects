# Build stage
FROM python:3-slim AS builder
WORKDIR /app
COPY . .

# RUN stage
FROM gcr.io/distroless/python3
COPY --from=builder /app /app
WORKDIR /app
CMD ["hello.py"]