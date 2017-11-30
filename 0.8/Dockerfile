FROM python:3
LABEL maintainer="e.a.blinov@gmail.com"

RUN pip install pymorphy2[fast]==0.8

# Получение сборщика словарей подходящей версии, сборка словаря и обновление соответствующего пакета
WORKDIR /tmp/pymorphy2-dicts-build
RUN pip install opencorpora-tools==0.5 nltk>3.0.0 && \
    git clone https://github.com/kmike/pymorphy2-dicts.git repo && \
    cd repo && \
    git reset --hard aad69229b9c19d07f7b5c55d8d77fdbd44424c02 && \
    mkdir -p pymorphy2_dicts/data && \
    python update.py && \
    pip install ./
# Очистка мусора сборки
WORKDIR /
RUN rm -Rf /tmp/pymorphy2-dicts-build
