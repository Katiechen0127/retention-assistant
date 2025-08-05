# Use an official Python base image
FROM python:3.9-slim

# Install system dependencies (gcc, tesseract, build tools, etc.)
RUN apt-get update && apt-get install -y \
    gcc \
    tesseract-ocr \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender-dev \
    build-essential \
    && apt-get clean

# Set working directory
WORKDIR /app

# Copy everything into the image
COPY . .

# Install Python packages
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# Download spaCy model
RUN python -m spacy download en_core_web_sm

# Expose Streamlit port
EXPOSE 8501

# Run your Streamlit app
CMD ["streamlit", "run", "record_retention_app.py", "--server.port=8501", "--server.enableCORS=false"]
