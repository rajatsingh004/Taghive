# Start from a Python 3.9 base image
FROM python:3.9-slim-buster

# Set the working directory to /app
WORKDIR /app

# Install necessary packages
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    libssl-dev gcc libffi-dev git && \
    rm -rf /var/lib/apt/lists/*

# Install sqlite3
RUN apt-get update && apt-get install -y sqlite3 && \
    rm -rf /var/lib/apt/lists/*

# Copy the application code and requirements.txt to the container
COPY app_b.py schema.sql requirements.txt ./

# Install the required Python packages
RUN pip install --no-cache-dir -r requirements.txt && \
    rm -rf /root/.cache/pip/*

# Create the database schema and insert data
RUN sqlite3 database.db < schema.sql && \
    chmod 660 database.db

# Expose port 5001 for the Flask web application
EXPOSE 5001

# Start the Flask web application
CMD ["python", "app_b.py"]

