# docker build -t <yourname>/rasa-jupyter-lab .
#
# docker run -i --rm \
#    -v </host/path/to/notebooks>:/notebooks \
#    -p <host_port>:8888 \
#    --name rasa-jupyter-lab \
#    <yourname>/rasa-jupyter-lab
#
# copy the url displayed in the docker log in your browser to begin

FROM python:3.6-slim

MAINTAINER Victor Rachieru

WORKDIR /notebooks

RUN apt-get update -qq \
	&& apt-get install -y build-essential \
	&& pip install rasa_core==0.9.0a7 rasa_nlu[spacy]==0.12.0 jupyterlab \
    && python -m spacy download en_core_web_md \
    && python -m spacy link --force en_core_web_md en

EXPOSE 8888

CMD [ "jupyter", "lab", "--allow-root","--ip=0.0.0.0", "--no-browser" ]
