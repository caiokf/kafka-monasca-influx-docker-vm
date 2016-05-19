FROM python:2.7.11

COPY . /src/monasca_persister

RUN mkdir -p /var/log/monasca/persister
RUN touch /var/log/monasca/persister/persister.log

RUN pip install monasca-persister

CMD ["python", "/usr/local/lib/python2.7/site-packages/monasca_persister/persister.py", "--config-file", "/src/monasca_persister/persister.conf"]
