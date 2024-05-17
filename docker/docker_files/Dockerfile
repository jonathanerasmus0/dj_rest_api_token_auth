FROM python:3.12.3

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

RUN set -eux; \
    apt-get update && \
    apt-get install -y --no-install-recommends \
        netcat-traditional \
        gettext \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir /code
COPY . /code/
WORKDIR /code

RUN set -eux; \
    /usr/local/bin/python -m pip install --upgrade pip && \
    python3 -m pip install -r /code/requirements.txt && \
    chmod +x /code/docker/entrypoints/entrypoint.sh




EXPOSE 8000
ENTRYPOINT ["/code/docker/entrypoints/entrypoint.sh"]


RUN chmod +x /code/docker/entrypoints/entrypoint.sh


