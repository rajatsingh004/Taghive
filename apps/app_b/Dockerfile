# Build stage
FROM python:3.10.10-slim as builder

# Install dependencies
RUN apt-get update && apt-get install -y sqlite3

# Set the working directory
WORKDIR /app

# Copy the requirements file and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code
COPY app_b.py schema.sql ./

# Create the database schema and insert data
RUN sqlite3 database.db < schema.sql

# Deploy stage
FROM python:3.13.0a3-slim

# Set the working directory
WORKDIR /app

# Copy the application code and database from the build stage
COPY --from=builder /app .

# Set the UID and GID of the nobody user to 65534
RUN chown -R 65534:65534 /app && \
    chmod -R 777 /app

# Set the user to nobody
USER nobody

# Expose port 5001 for the Flask web application
EXPOSE 5001

# Start the Flask web application
CMD ["python", "app_b.py"]

