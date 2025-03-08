FROM python:3.9-slim-buster

RUN pip install --upgrade --default-timeout=100 pip -i https://www.piwheels.org/simple

ARG srcDir=src
WORKDIR /app
COPY $srcDir/requirements.txt .
RUN pip install --default-timeout=100 --no-cache-dir -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple

COPY $srcDir/run.py .
COPY $srcDir/app ./app

EXPOSE 5000

CMD ["gunicorn", "-b", "0.0.0.0:5000", "run:app"]
