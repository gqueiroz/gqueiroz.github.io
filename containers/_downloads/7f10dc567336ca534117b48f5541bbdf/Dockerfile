ARG BASE_IMAGE=python:3.11-slim-bullseye
FROM ${BASE_IMAGE}

WORKDIR /app

COPY ./requirements.txt requirements.txt

RUN pip install -r requirements.txt --no-cache && \
    pip install gunicorn --no-cache

COPY ./app.py .

EXPOSE 5000

CMD ["gunicorn", "-w4" , "--bind=0.0.0.0:5000", "app:app"]
