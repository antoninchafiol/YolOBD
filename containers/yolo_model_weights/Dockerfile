# Use an official lightweight Python image
FROM python:3.9-slim

# Install system dependencies
RUN apt-get update && apt-get upgrade && apt-get install -y git

# Install Python dependencies
RUN pip install --upgrade pip && \
    pip install opencv-python-headless torch torchvision tensorflow pandas

# Clone the YOLOv5 repo (or other repo depending on the model you're using)
RUN git clone https://github.com/ultralytics/yolov5.git && \
    cd yolov5 && pip install -r requirements.txt

# Set the working directory
WORKDIR /yolov5

# Copy any necessary files into the container (e.g., scripts or configs)
COPY . /yolov5

# Default command
CMD ["python", "export.py", "--weights", "yolov5s.pt", "--include", "saved_model"]