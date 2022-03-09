## Prérequis

Pour permettre l'installation de ITSM-NG. Il est nécessaire d'avoir un serveur Linux ou Windows ayant les services suivant d'installé et configuré : 
* Apache, Nginx, ISS, etc.
* MariaDB >= 10.X ou MySQL >= 5.7
* Php 7.2 ou supérieur

Note sur PHP : la version 7.4 reste recommandée dans le mesure où PHP 7.2 et 7.3 sont compatible avec le produit mais ne sont plus supportées par PHP. (voir : https://www.php.net/supported-versions.php)

Voici la liste des extensions PHP *requises* au fonctionnement de ITSM-NG :
* php-ctype
* php-curl
* php-gd
* php-iconv
* php-intl
* php-json
* php-mbstring
* php-mysqli
* php-simplexml
* php-zlib

Les extensions PHP suivantes sont optionnelles : 
* php-exif 
* php-imap
* php-ldap
* php-sodium
* php-zip et php-bz2
* php-apcu
* php-opcache
* php-xmlrpc

## Installation 

Téléchargez la version de votre choix : https://github.com/itsmng/itsm-ng/releases
Nous recommandons néamoins d'utiliser la dernière version disponible.

Note : Des versions de dev et nightly seront disponible sous peu pour ceux souhaitant tester les dernières fonctionnalités de ITSM-NG.




## Post installation

