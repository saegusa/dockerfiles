FROM msaegusa/mecab:latest


RUN apk update
RUN apk --no-cache add python3-dev swig
RUN apk --no-cache add jpeg-dev zlib-dev freetype-dev lcms2-dev openjpeg-dev tiff-dev tk-dev tcl-dev

RUN pip3 install --upgrade pip
RUN pip3 install mecab-python3 matplotlib wordcloud
