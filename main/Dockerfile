# The Dockerfile acts as a blueprint that tells Docker how to build the image,
# including setting up the base environment, installing dependencies, and
# defining the command to start your application.

# Use an official Python runtime as the base image
FROM python:3.13.2-slim

# Prevent Python from writing pyc files and buffer output
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set the working directory in the container to /app
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt /app/

# Install the Python dependencies
RUN pip install -r requirements.txt

# Copy the Django project code into the container
COPY . /app

# Collect static files for the Django application
RUN python manage.py collectstatic --noinput

# Expose port 8000 for the Django development server
EXPOSE 8000

# Run the Django development server
CMD ["gunicorn", "company_website.wsgi:application", "--bind", "0.0.0.0:8000"]