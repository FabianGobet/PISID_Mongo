ARG INDX

FROM ubuntu
RUN apt-get install gnupg
RUN curl -fsSL https://pgp.mongodb.com/server-6.0.asc | gpg -o /usr/share/keyrings/mongodb-server-6.0.gpg --dearmor
RUN echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-6.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-6.0.list
RUN apt-get update
RUN apt-get install -y mongodb-org
RUN mkdir mongo && cd mongo

# ------------- CONFIG SERVER AND SHARD SETUP -------------------------
RUN mkdir -p cfg${INDX}/data cfg${INDX}/log a${INDX}/data b${INDX}/data c${INDX}/data a${INDX}/log b${INDX}/log c${INDX}/log
RUN touch cfg${INDX}/log/logs.log a${INDX}/log/logs.log b${INDX}/log/logs.log c${INDX}/log/logs.log

# APENAS GERAR KEYFILE NUMA MAQUINA E COPIAR PARA /mongo NAS OUTRAS
RUN openssl rand -base64 756 > keyfile

RUN cd.. && chmod 700 mongo

# -------------- MONGOS (ROUTER) SETUP ------------------------
#RUN mkdir mongo && cd mongo
#RUN mkdir -p s0/data s0/log
#RUN touch s0/log/logs.log
# COPIAR KEYFILE PARA /mongo
#RUN chmod 600 keyfile
