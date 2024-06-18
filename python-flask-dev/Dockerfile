FROM python:3.10-bullseye as vanilla
WORKDIR /app
COPY requirements.txt requirements.txt
COPY requirements-dev.txt requirements-dev.txt
RUN pip install --upgrade pip && pip install -r requirements.txt
RUN pip install -r requirements-dev.txt
RUN pip install pip-tools

FROM vanilla as frontend
WORKDIR /app
COPY requirements-frontend.txt requirements-frontend.txt
RUN pip install --upgrade pip && pip install -r requirements-frontend.txt

FROM vanilla as db
WORKDIR /app
COPY requirements-db.txt requirements-db.txt
RUN pip install --upgrade pip && pip install -r requirements-db.txt
