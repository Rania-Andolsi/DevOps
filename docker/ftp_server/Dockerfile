# Utilisez l'image pure-ftpd officielle
FROM stilliard/pure-ftpd:latest

# Définissez les variables d'environnement pour l'utilisateur FTP
ENV FTP_USER=myuser
ENV FTP_PASS=mypassword
ENV FTP_HOME=/home/ftpusers/myuser

# Créez les répertoires nécessaires
RUN mkdir -p /etc/pure-ftpd/passwd /etc/pure-ftpd/conf

# Créez le répertoire home de l'utilisateur FTP
RUN mkdir -p $FTP_HOME

# Créez un script pour générer le fichier passwd
RUN echo "#!/bin/bash" > /usr/bin/create_user.sh && \
    echo "pure-pw mkdb /etc/pure-ftpd/pureftpd.pdb -f /etc/pure-ftpd/passwd/pureftpd.passwd" >> /usr/bin/create_user.sh && \
    echo "echo \"$FTP_PASS\" > /tmp/passwdfile" >> /usr/bin/create_user.sh && \
    echo "pure-pw useradd $FTP_USER -f /etc/pure-ftpd/passwd/pureftpd.passwd -m -u ftpuser -d $FTP_HOME -p /tmp/passwdfile" >> /usr/bin/create_user.sh && \
    echo "rm /tmp/passwdfile" >> /usr/bin/create_user.sh && \
    chmod +x /usr/bin/create_user.sh

# Exécutez le script pour créer le fichier passwd et ajouter l'utilisateur FTP
RUN /usr/bin/create_user.sh

# Exposez le port FTP
EXPOSE 21

# Lancez le serveur FTP
CMD ["/usr/sbin/pure-ftpd", "-c", "50", "-C", "10", "-l", "puredb:/etc/pure-ftpd/pureftpd.pdb", "-E", "-j", "-R", "-P", "-p", "30000:30009", "-H", "-4", "-Y", "2", "-B"]

