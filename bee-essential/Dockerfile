FROM msaegusa/mecab-python3:latest

RUN apk update
RUN apk --no-cache add jpeg-dev zlib-dev freetype-dev lcms2-dev openjpeg-dev tiff-dev tk-dev tcl-dev

ENV PYTHONUNBUFFERED 1

RUN git clone https://github.com/saegusa/bee-essential.git /code
WORKDIR /code

RUN pip3 install -r requirements.txt

#Kosugi_Maru font
RUN wget -P . https://fonts.google.com/download?family=Kosugi%20Maru -O Kosugi_Maru.zip \
    && unzip ./Kosugi_Maru.zip -n

RUN chmod -R +x cgi-bin
RUN chmod +x start.sh

EXPOSE 8000