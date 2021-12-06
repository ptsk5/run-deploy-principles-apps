FROM registry.access.redhat.com/ubi8/python-38

ENV APP_ROOT=/usr/src/app 

WORKDIR $APP_ROOT

ADD requirements.txt .

RUN pip install --upgrade pip && \ 
    pip install --no-cache-dir -r requirements.txt 

ADD src .

EXPOSE 4000

CMD [ "python", "app.py" ]
