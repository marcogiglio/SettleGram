FROM python:3.8

RUN python -m pip install --upgrade pip
WORKDIR /code
COPY requirements.txt requirements.txt
RUN python -m pip install -r requirements.txt
RUN python -m spacy download en_core_web_sm
RUN python -m spacy download it_core_news_sm
COPY . /code
