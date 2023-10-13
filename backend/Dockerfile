FROM python:3.8-slim

RUN pip install --upgrade pip

COPY ./requirements.txt .
RUN pip install -r requirements.txt

COPY . /app
WORKDIR /app

RUN python manage.py makemigrations
RUN python manage.py migrate --no-input
RUN python manage.py collectstatic --no-input

EXPOSE ${PORT}

CMD ["sh", "-c", "gunicorn backend.wsgi:application --bind ${PORT}"]
