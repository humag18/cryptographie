# Cryptographie
## Cryptosystème 
### Chiffrement symétrique
Pour chiffrer -> ```$ openssl enc -<cryptosystème> -in <plaintext_file> [-out <ciphertext_file>] -e```

Pour déchiffrer -> ```$ openssl enc -<cryptosystème> -in <plaintext_file> [-out <ciphertext_file>] -d```

Les options -d et -e veulent respectivement dire decrypt et encrypt 

Création de clé hexadecimal random ```openssl -rand hex 20``` 20 étant le nombre de bit que fera la clé ou l'iv

#### Fonctionnement du vecteur initial 
Chiffrement de données avec clé ```openssl enc -aes128-cbc -k <key> -iv <iv> -in <plaintext_file> -out <cyphertext_file>```

>L'iv ne se met uniquement lors d'un chiffrement par bloc tel que cbc

>En général la clé fait 16 bits et l'iv en fait 8

```ls -l ``` == voir les fichier et leurs tailles

suppression des octets du padding automatique avec openssl mais si on ne veut pas les supprimer ```-nopad```
### Chiffrement asymétrique
Pour générer une Private key ```openssl genrsa -out <file> <taille>

>```openssl rsa -in <file> -text -noout``` permet de voir les infos de la clé ```-text``` affiches les composante & les infos publique de la clé ```-noout``  supprime l'affichage de la clé chiffré

Génération de la clé publique associé à la clé privée ```openssl rsa -in <fichier clé priv> -pubout -out <fichier clé publique>```
   
>Pour visualier les infos relative à la clé ```openssl rsa -in <fichier clé public> -pubin -text -noout```

Le chiffrement des données avec le RSA se fait avec la commande ```openssl rsautl -encrypt -in <fichier_entree> -pubin -inkey <clé> -out
<fichier_sortie>```
   
### Hachage de données
Pour hacher un fichier ```openssl dgst -<algorithme de hachage> <file.txt>``` ceci génère directement l'empreinte du fichier
   
pour stocker l'empreinte dans un fichier utiliser la commande ```openssl dgst <algo> -out <file.txt.alog> <file.txt>``` 
   > file.txt.algo = fichier de reception de l'empreinte
   
Les différents algos de hachage
   - MD5 -> pas très sécu
   - SHA-1 -> peu sur
   - SHA-224
   - SHA-256
   - SHA-384
   - SHA-512
   - SHA3-224/256/384/512
   
### Signature de fichier
   Pour signer un fichier avec une clé RSA ```openssl rsautl -sign -in <fichier_empreinte> -inkey <cle> -out <signature>```
   > ```openssl rsautl -verify -in <signature> -pubin -inkey <cle> -out <f_empreinte>``` cette commande permet de vérifier si la signature est bonne
   
## PGP
   Installer thunderbird et pgpdump ```sudo apt install thunderbird pgpdump```
   
   Connection à une adresse mail ou création avec mailfence
   
   Générer la clé PGP dans les paeamètres de thunderbird dans les paramètres de compte aller dans ```End-To-End Encryption``` 
   
