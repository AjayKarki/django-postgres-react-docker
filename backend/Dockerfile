# Use an official Python runtime as a parent image
FROM python:3.7-alpine

# Adding backend directory to make absolute filepaths consistent across services
WORKDIR /backend
RUN apk add --update --no-cache postgresql-client jpeg-dev
RUN apk add --update --no-cache --virtual .tmp-build-deps \
        gcc libc-dev linux-headers postgresql-dev musl-dev zlib zlib-dev

# Install Python dependencies
COPY requirements.txt /backend
RUN pip3 install --upgrade pip -r requirements.txt

# Add the rest of the code
COPY . /backend

# Make port 8000 available for the app
EXPOSE 8000

# Be sure to use 0.0.0.0 for the host within the Docker container,
# otherwise the browser won't be able to find it
CMD python3 manage.py runserver 0.0.0.0:8000