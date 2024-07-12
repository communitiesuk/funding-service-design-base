
# --------------------------------------------------
# Basic python flask image that the other FSD images can build upon
# --------------------------------------------------

FROM python:3.10-bullseye as flask
WORKDIR /app
COPY requirements.txt requirements.txt
COPY requirements-dev.txt requirements-dev.txt
RUN pip install --upgrade pip && pip install -r requirements.txt
RUN pip install -r requirements-dev.txt
RUN pip install pip-tools

# --------------------------------------------------
# Base image to build frontend applications on - includes flask and other frontend frameworks such as govuk-frontend-jinja
# --------------------------------------------------

FROM flask as frontend
WORKDIR /app
COPY requirements-frontend.txt requirements-frontend.txt
RUN pip install --upgrade pip && pip install -r requirements-frontend.txt



# --------------------------------------------------
# Base image to build db images on - includes sqwl alchemy and connexion
# --------------------------------------------------

FROM flask as db
WORKDIR /app
COPY requirements-db.txt requirements-db.txt
RUN pip install --upgrade pip && pip install -r requirements-db.txt
RUN apt-get install -y lsb-release && apt-get clean all
