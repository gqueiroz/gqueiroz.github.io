ARG BASE_IMAGE=qgis/qgis:release-3_22
FROM ${BASE_IMAGE}

LABEL img.author="Gilberto Ribeiro de Queiroz" \
      img.description="Este script possibilita a criação de \
uma imagem com o aplicativo QGIS que facilita o compartilhamento \
de volumes entre o host e os contêiners criados a partir dela."

ARG ROOT_USER=root
ARG QGIS_USER_NAME=qgis
ARG QGIS_USER_ID=1000
ARG QGIS_USER_GROUP=qgis
ARG QGIS_USER_GROUP_ID=1000

RUN pip3 install --upgrade pip && \
    pip3 install --upgrade setuptools && \
    pip3 install --upgrade wheel && \
    pip3 install pb_tool

RUN groupadd --gid ${QGIS_USER_GROUP_ID} ${QGIS_USER_GROUP} && \
    useradd --create-home \
            --shell /bin/bash \
            --uid ${QGIS_USER_ID} \
            --gid ${QGIS_USER_GROUP} ${QGIS_USER_NAME}

USER ${QGIS_USER_NAME}

WORKDIR /home/${QGIS_USER_NAME}

USER ${ROOT_USER}
