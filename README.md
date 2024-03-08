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

  Avantages : Persistance des données : Les données sont stockées en dehors du conteneur, ce qui les rend persistantes même si le conteneur est supprimé.

  Flexibilité : Vous pouvez monter des volumes depuis n'importe quel emplacement sur le système hôte, y compris des volumes partagés réseau.

  Performances : Le montage d'un volume est généralement plus rapide que la copie de gros volumes de données.

  Facilité de mise à jour : Les modifications apportées aux fichiers sur le système hôte sont immédiatement visibles dans le conteneur sans nécessiter de nouvelles opérations de construction d'image.

  Inconvénients :

  Complexité : La gestion des volumes peut être plus complexe, surtout dans les environnements distribués. Dépendance au système hôte : Les volumes montés dépendent du système hôte, ce qui peut rendre le déploiement sur différents environnements plus compliqué.

  Sécurité : Les volumes montés peuvent introduire des risques de sécurité si des autorisations inappropriées sont définies.
