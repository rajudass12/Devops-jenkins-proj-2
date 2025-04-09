FROM python:3.10  # Safer and compatible with distutils

# Install required system dependencies
RUN apt-get update && apt-get install -y python3-distutils

# Install Django
RUN pip install django==3.2

# Copy project files
COPY . .

# Run database migrations
RUN python manage.py migrate

# Expose the app on port 8000 (change if needed)
EXPOSE 8000

# Start the Django development server
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]


