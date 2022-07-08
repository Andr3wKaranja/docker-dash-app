FROM python:3.8.9-slim-buster

LABEL maintainer="Andrew Karanja andruu.karanja@gmail.com"

# Set working directory within the container.
WORKDIR /usr/src/app

# Copy and install packages
COPY requirements.txt /
RUN pip install --upgrade pip 
RUN pip install -r /requirements.txt

# Copy app folder to app folder in container
COPY /app /usr/src/app/

# Change to non-root user
RUN useradd -m appUser
# Switch to the newly created user.
USER appUser

# RUN cd
# Run Plotly Dash app using a Gunicorn WSGI Server locally on port 8050
CMD gunicorn --bind 0.0.0.0:8050 app:server