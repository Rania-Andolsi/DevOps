# Utiliser l'image MySQL officielle
FROM mysql:latest

# Informations d'identification de la base de données
ENV MYSQL_ROOT_PASSWORD=root_password
ENV MYSQL_DATABASE=my_database
ENV MYSQL_USER=db_user
ENV MYSQL_PASSWORD=db_password

# Copier les fichiers d'initialisation dans le conteneur
COPY init.sql /docker-entrypoint-initdb.d/

# Exposer le port MySQL
EXPOSE 3307

