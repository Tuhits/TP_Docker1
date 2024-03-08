# TP_Docker1 

CHEVALIER TUHITI B3

Installer "Docker Desktop" 
:
- docker run -v C:\Users\Tuhits\Documents\Devops\TP_Docker1\html:/usr/local/apache2/htdocs -p 8080:80 -d httpd
- docker run -p 8080:80 -d httpd
- docker cp C:\Users\Tuhits\Documents\Devops\TP_Docker1\html
- laughing_lewin:/usr/local/apache2/htdocs/

- docker build -t dockerbuild . docker run -d -p 8080:80 dockerbuild

  Mount Volume :

  Avantages :
  - Persistance des données : Les données sont stockées en dehors du conteneur, ce qui les rend persistantes même si le conteneur est supprimé.

  - Flexibilité : Vous pouvez monter des volumes depuis n'importe quel emplacement sur le système hôte, y compris des volumes partagés réseau.

  - Performances : Le montage d'un volume est généralement plus rapide que la copie de gros volumes de données.

  - Facilité de mise à jour : Les modifications apportées aux fichiers sur le système hôte sont immédiatement visibles dans le conteneur sans nécessiter de nouvelles opérations de construction d'image.

  Inconvénients :

  - Complexité : La gestion des volumes peut être plus complexe, surtout dans les environnements distribués. Dépendance au système hôte : Les volumes montés dépendent du système hôte, ce qui peut rendre le déploiement sur différents environnements plus compliqué.

  - Sécurité : Les volumes montés peuvent introduire des risques de sécurité si des autorisations inappropriées sont définies.


  Copy :

Avantages : 
- Portabilité : Les données sont directement incluses dans l'image Docker, ce qui rend l'image auto-suffisante et portable.
- Isolation : Les fichiers sont encapsulés dans l'image, ce qui réduit les dépendances du système hôte.
- Simplicité : Copier des fichiers est simple à mettre en œuvre et à comprendre, surtout pour les petites applications ou les démonstrations.
- Sécurité : Les données incluses dans l'image peuvent être plus sécurisées car elles sont encapsulées dans le conteneur.

Inconvénients :
- Manque de persistance : Les données sont incluses dans l'image et sont donc éphémères. Toute modification ou suppression des données nécessite la reconstruction de l'image.
- Taille de l'image : L'inclusion de grandes quantités de données peut augmenter considérablement la taille de l'image Docker, ce qui peut entraîner des temps de déploiement plus longs et une utilisation plus importante du stockage.
- Difficulté de mise à jour : Tout changement dans les données nécessite la reconstruction complète de l'image, ce qui peut être fastidieux et prendre du temps.

Dockerfile : 
- FROM httpd:latest COPY ./html/index.html /usr/local/apache2/htdocs/ EXPOSE 80

- docker run --name contener_phpmyadmin --link contener_mysql -p 8080:80 -d -e PMA_HOST=contener_mysql phpmyadmin/phpmyadmin

Docker est utilisé pour gérer des conteneurs individuels, tandis que Docker Compose est utilisé pour gérer des applications composées de plusieurs conteneurs interconnectés. Ils sont souvent utilisés ensemble pour simplifier le processus de développement, de déploiement et de gestion des applications conteneurisées.
La commande qui permet de lancer tous les conteneurs du fichier yaml est docker-compose up La commande qui permet de stopper tous les conteneurs du fichier yaml est docker-compose stop

fichier docker_compose :

version: '3.8'
services: db: image: mysql:latest restart: always environment: MYSQL_ROOT_PASSWORD: root MYSQL_DATABASE: mysql MYSQL_USER: root MYSQL_PASSWORD: root ports: - "3306:3306"
phpmyadmin: image: phpmyadmin/phpmyadmin:latest restart: always environment: PMA_HOST: db PMA_PORT: 3306 ports: - "8080:80" depends_on: - db
