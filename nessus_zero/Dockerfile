FROM ubuntu:latest

# Instalar dependencias
RUN apt-get update && apt-get upgrade -yy && \
    apt-get install -y curl sudo systemctl && \
    rm -rf /var/lib/apt/lists/*

# Descargar e instalar Nessus
RUN curl --request GET \ 
        --url 'https://www.tenable.com/downloads/api/v2/pages/nessus/files/Nessus-10.8.4-ubuntu1604_amd64.deb' \ 
        --output 'Nessus-10.8.4-ubuntu1604_amd64.deb' && \
    dpkg -i Nessus-10.8.4-ubuntu1604_amd64.deb && \
    rm Nessus-10.8.4-ubuntu1604_amd64.deb

# Exponer el puerto 8834
EXPOSE 8834 80 443

# Iniciar Nessus al ejecutar el contenedor
CMD ["/bin/bash", "-c", "systemctl start nessusd.service && tail -f /dev/null"]
