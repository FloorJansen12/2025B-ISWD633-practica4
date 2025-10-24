- Antes de esta práctica, no sabía que se podía limitar los recursos que pueden utilizar los contenedores, ni que se podían crear imágenes personalizadas. Después aprendí a instalar Apache mediante un DockerFile, usar límites de memoria y CPU, aplicar healthchecks y políticas de reinicio. También entendí cómo identificar imágenes huérfanas y el uso del caché en las construcciones. Se presentó un problema al momento de instalar Centos 7, ya que en algunos repositorios no está disponible, y en los que sí, no son seguros de instalar, por eso en cambio se instaló rockylinux:8 mediante el siguiente comando:

```
FROM rockylinux:8

RUN dnf -y update && \
    dnf -y install httpd && \
    dnf clean all

COPY ./web /var/www/html

EXPOSE 80

CMD ["httpd", "-D", "FOREGROUND"]
```
