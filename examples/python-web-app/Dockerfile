#STAGE 1
FROM python:3.11-slim AS builder

WORKDIR /app

COPY /devops /app

COPY requirements.txt .

RUN pip install --prefix=/install -r requirements.txt

SHELL ["/bin/bash", "-c"]

RUN python3 -m venv venv1 && \
source venv1/bin/activate && \
pip install --no-cache-dir -r requirements.txt


#STAGE2 BUILD 

FROM gcr.io/distroless/python3

COPY --from=builder /app /app 


EXPOSE 8000

SHELL ["/bin/bash", "-c"]


CMD source venv1/bin/activate && python3 manage.py runserver 0.0.0.0:8000




