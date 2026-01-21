FROM python:3.10

WORKDIR /code
COPY requirements.txt ./
RUN pip install --upgrade pip \
    && pip install --no-cache-dir -r requirements.txt

COPY cats ./cats/
COPY kittygram_backend ./kittygram_backend/
COPY uwsgi/uwsgi.ini ./
COPY manage.py ./
RUN python manage.py collectstatic --noinput

ENV PYTHONUNBUFFERED=1
EXPOSE 8000

ENTRYPOINT ["uwsgi", "--strict", "--ini", "uwsgi.ini"]
