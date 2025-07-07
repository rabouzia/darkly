1 or 1=1 UNION SELECT commentaire, countersign FROM users

fix:
Il faut utiliser des requêtes préparées (prepared statements), qui séparent les données des instructions SQL.
Cela empêche l’interprétation du contenu comme du code SQL, même si l’utilisateur entre des caractères spéciaux comme ' ou OR 1=1.