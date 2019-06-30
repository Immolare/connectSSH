# connectSSH
Liste de commandes à effectuer pour se connecter en SSH sans mdp à un serveur distant via une vm


$ ssh-keygen

Note : donner nom + password. Password non nécessaire si la connexion sert à déployer un projet

Sur Homestead :

$ ssh-copy-id -i ~/.ssh/id_rsa.pub exemple@ssh.server.net
$ ssh-add

Note : sur OVH, ne pas préciser de PORT sinon ça plante.

A ce stade la clé publique est copiée sur le serveur de déploiement

## Créer un fichier de config dans ~/.ssh/

Afin de pouvoir se connecter directement via "ssh + monnom" :

$ sudo vim ~/.ssh/config

Dedans, y insérer :

Host monnom
        Hostname ssh.server.net
        User user
        Port 22
        IdentityFile ~/.ssh/id_rsa
        
Résultat : la commande ssh monnom se connecte au server sans password prompt.
