# cryptographie
## Cryptosystème 
### Base d'openssl
Pour chiffrer -> ```$ openssl enc -<cryptosystème> -in <plaintext_file> [-out <ciphertext_file>] -e```

Pour déchiffrer -> ```$ openssl enc -<cryptosystème> -in <plaintext_file> [-out <ciphertext_file>] -d```

Les options -d et -e veulent respectivement dire decrypt et encrypt 

Création de clé hexadecimal random ```openssl -rand hex 20``` 20 étant le nombre de bit que fera la clé ou l'iv

Chiffrement de données avec clé ```openssl enc -aes128-cbc -k <key> -iv <iv> -in <plaintext_file> -out <cyphertext_file>```

>L'iv ne se met uniquement lors d'un chiffrement par bloc tel que cbc

>En général la clé fait 16 bits et l'iv en fait 8

```ls -l ``` == voir les fichier et leurs tailles

suppression des octets du padding automatique avec openssl mais si on ne veut pas les supprimer ```-nopad```

Pour générer une Private key ```openssl genrsa -out <file> <taille>

>la taille s'exprime en bit

>```openssl rsa -in <file> -text -noout``` permet de voir les infos de la clé ```-text``` affiches les composante & les infos publique de la clé ```-noout``  supprime l'affichage de la clé chiffré
