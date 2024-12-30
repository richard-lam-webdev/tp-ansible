# Ansible-Bagisto

Ce projet contient des playbooks Ansible pour déployer l'infrastructure nécessaire à l'exécution de Bagisto.

---

## Lancer les playbooks Ansible

### Pré-requis
- **Ansible** installé sur votre machine locale.
- Accès SSH à une machine Ubuntu/Debian cible.

### Étapes
1. **Modifier l'inventaire** :
   - Ouvrez le fichier `inventory/production` et ajoutez l'adresse IP de votre machine cible.
     Exemple :
     ```
     [all]
     192.168.56.10 ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa
     ```

2. **Lancer le playbook principal** :
   - Exécutez la commande suivante :
     ```bash
     ansible-playbook -i inventory/production site.yml
     ```

3. **Vérifier le déploiement** :
   - Une fois terminé, vous pourrez accéder à Bagisto sur :
     ```
     http://<IP_de_la_machine>
     ```

---

## Alternative : Tester avec Docker

Ce projet inclut également un fichier `docker-compose.yml` permettant de tester les playbooks Ansible dans un environnement conteneurisé.

### Services Docker
1. **`node_manager` :**
   - Conteneur permettant d'exécuter Ansible pour appliquer les configurations.
2. **`target` :**
   - Conteneur simulant une machine cible où les playbooks Ansible sont appliqués.

### Étapes pour utiliser Docker
1. **Démarrer les conteneurs :**
   - Depuis la racine du projet, exécutez :
     ```bash
     docker-compose up --build
     ```

2. **Exécuter les playbooks :**
   - Une fois les conteneurs démarrés, connectez-vous au conteneur `node_manager` :
     ```bash
     docker exec -it <nom_du_conteneur_node_manager> /bin/sh
     ```
   - Lancez les playbooks Ansible depuis `node_manager` :
     ```bash
     ansible-playbook -i inventory/production site.yml
     ```

3. **Vérifier l'accès :**
   - Une fois le playbook exécuté, accédez à Bagisto sur :
     ```
     http://localhost:8080
     ```

## Structure des fichiers
- **`inventory/` :** Fichier d'inventaire pour spécifier les machines cibles.
- **`roles/` :** Rôles Ansible pour configurer le serveur web, la base de données et l'application.
- **`site.yml` :** Playbook principal pour orchestrer les déploiements.
- **`docker-compose.yml` :** Fichier pour démarrer les conteneurs de test.
- **`docker/` :** Dossier contenant les fichiers nécessaires pour construire les conteneurs.


