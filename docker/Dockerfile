# syntax=docker/dockerfile:1

FROM python:3.9-slim


RUN apt-get update && \
  apt-get install -y --no-install-recommends \
  libpq-dev nodejs npm gettext
RUN npm install -g gulp-cli
RUN pip install pipenv

COPY / /app/babybuddy
WORKDIR /app/babybuddy
RUN pipenv install --three --dev

WORKDIR /app
RUN cp babybuddy/package*.json ./ && npm install
ENV PATH=/app/node_modules/.bin:$PATH

ENV DJANGO_SETTINGS_MODULE babybuddy.settings.development

#RUN \
  #gulp migrate && \
  #gulp createcachetable

#RUN gulp

#VOLUME /config


# ports and volumes
EXPOSE 8000
