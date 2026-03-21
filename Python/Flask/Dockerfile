##### Dockerfile for Python/Flask applications #####
## Build stage: Compile the Python/Flask application using Node.js  
FROM python:3.10-slim-buster

WORKDIR /app

## Install dependencies
COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

## Copy the rest of the application code
COPY . .

CMD [ "python3", "-m" , "flask", "run" ]