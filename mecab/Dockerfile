FROM alpine:latest

RUN apk update
RUN apk --no-cache add git gcc curl bash file sudo openssh build-base openssl

RUN mkdir crf
RUN cd crf
RUN curl -L -o CRF++-0.58.tar.gz 'https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7QVR6VXJ5dWExSTQ'
RUN tar -zxf CRF++-0.58.tar.gz
WORKDIR CRF++-0.58
RUN ./configure
RUN make
RUN make install

RUN mkdir /local
WORKDIR /local
RUN curl -L -o mecab-0.996.tar.gz 'https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7cENtOXlicTFaRUE'
RUN tar -zxf mecab-0.996.tar.gz
WORKDIR mecab-0.996
RUN  ./configure --enable-utf8-only --with-charset=utf8
RUN make
RUN make check
RUN make install

ENV IPADIC_VERSION 2.7.0-20070801
ENV ipadic_url https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7MWVlSDBCSXZMTXM

# Install IPA dic
WORKDIR /local
RUN  curl -SL -o mecab-ipadic-${IPADIC_VERSION}.tar.gz ${ipadic_url} \
&& tar zxf mecab-ipadic-${IPADIC_VERSION}.tar.gz \
&& cd mecab-ipadic-${IPADIC_VERSION} \
&& ./configure --with-charset=utf8 \
&& make \
&& make install

# Install Neologd
WORKDIR /local
RUN git clone --depth 1 https://github.com/neologd/mecab-ipadic-neologd.git \
&& mecab-ipadic-neologd/bin/install-mecab-ipadic-neologd -n -y
