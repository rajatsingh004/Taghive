# Start from a Python 3.9 base image
FROM python:3.9-alpine

# Set the working directory to /app
WORKDIR /app

# Copy the requirements file to the container
COPY requirements.txt .

# Install the Python dependencies
RUN apk --no-cache add build-base libffi-dev openssl-dev && \
    pip install --no-cache-dir -r requirements.txt && \
    apk del build-base libffi-dev openssl-dev

# Copy the application code to the container
COPY . .

# Expose port 5000 for the Flask web application
EXPOSE 5000

# Set a non-root user to run the container for added security
RUN addgroup -S myuser && adduser -S myuser -G myuser
USER myuser

# Start the Flask web application
CMD ["python", "app_a.py"]

