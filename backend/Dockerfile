FROM python:3.8-slim
WORKDIR /app

RUN pip install --upgrade pip

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . /app

EXPOSE ${PORT}

CMD ["sh", "-c", "python manage.py makemigrations user_api && python manage.py migrate --no-input && python manage.py collectstatic --no-input && gunicorn backend.wsgi:application --bind 0.0.0.0:${PORT}"]
