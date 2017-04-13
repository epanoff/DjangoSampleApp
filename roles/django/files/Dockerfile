FROM debian:stable
MAINTAINER epanoff
RUN apt-get update && \
    apt-get install -y python-dev python-setuptools python python-pip git libpq-dev
RUN mkdir /opt/django/ && \
    cd /opt/django && \
    ls -lah && \
    git clone https://github.com/kirpit/django-sample-app.git projectname && cd projectname && \
    pip install -r requirements.txt && \
    pip install uwsgi && \
    find ./ -type f -exec sed -i 's/{{ project_name }}/projectname/' {} \;

COPY  settings.py  /opt/django/projectname/projectname
WORKDIR /opt/django/projectname

CMD ["uwsgi" ,"--http", ":8000", "--wsgi-file", "projectname/wsgi.py"]
