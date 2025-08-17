FROM docker.io/library/python:latest

WORKDIR /usr/src/server
ADD requirements.txt .
RUN pip install --trusted-host pypi.python.org -r requirements.txt
RUN apt-get update
RUN apt-get install -y tzdata

EXPOSE 8888
CMD ["python", "manage.py", "runserver", "0.0.0.0:8888"]
