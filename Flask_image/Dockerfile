# Start from a Python base image
FROM python:3.9-slim

# Set working directory inside the container
WORKDIR /app

# Install system dependencies if needed (for example, to avoid build errors)
RUN apt-get update && apt-get install -y gcc

# Copy the requirements.txt to the container first and install the dependencies
COPY requirements.txt . 

# Install dependencies, ensure that we are installing correct versions of Flask and Werkzeug
RUN pip install --no-cache-dir -r requirements.txt && \
    pip install --no-cache-dir Flask==2.0.1 werkzeug==2.0.1  # Define versions explicitly if needed

# Copy the Flask app into the container (all files from the current directory)
COPY . /app

# Expose the port the app will run on
EXPOSE 5000

# Set environment variables (optional, if required)
ENV FLASK_APP=app.py
ENV FLASK_ENV=production

# Command to run the Flask application and allow external connections
CMD ["flask", "run", "--host=0.0.0.0", "--port=5000"]
