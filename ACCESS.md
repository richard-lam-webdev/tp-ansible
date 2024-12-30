# Accéder au Projet Déployé

Ce README explique comment accéder au projet Bagisto après déploiement via Ansible.

## Étapes pour accéder à Bagisto
1. **Adresse URL :**
   - Ouvrez un navigateur web et entrez l'URL suivante :
     ```
     http://<IP_de_la_machine>
     ```
   - Remplacez `<IP_de_la_machine>` par l'adresse IP ou le nom de domaine de votre serveur.

2. **Port utilisé :**
   - Par défaut, le port utilisé est **80**.

3. **Vérification :**
   - Vous devriez voir l'interface de Bagisto si le déploiement s'est correctement effectué.

## Configuration par défaut
- **Base de données :** `bagisto`
- **Utilisateur :** `bagisto_user`
- **Mot de passe :** défini dans le rôle Ansible `database`.

## Dépannage
- Si le site n'est pas accessible :
  - Vérifiez que le service Nginx fonctionne.
  - Assurez-vous que les règles de pare-feu autorisent le trafic HTTP sur le port 80.
