# Rapport de déploiement - [VOTRE NOM]
## Liens
- **Application en ligne :** [[URL_SCALINGO](https://local-cloudrm.osc-fr1.scalingo.io/)]
- **Dépôt de code :** [[URL_GITHUB]https://github.com/rmakaiadev-ai/Local.githttps://github.com/rmakaiadev-ai/Local.git]
## Prérequis techniques
- PHP (version compatible avec Symfony)
- Composer
- Symfony CLI
- Git
- Twig
- Un compte GitHub
- Un compte Scalingo
## Fichier de configuration CI

# Le nom de ton assistant
name: Verification du Projet Local

# Quand doit-il travailler ?
on: [push] # Dès que tu envoies du code sur Github

# Qu'est-ce qu'il doit faire ?
jobs:
  verification-basique:
    runs-on: ubuntu-latest # Il utilise un ordinateur sous Linux

    steps:
    - name: Recuperer le code
      uses: actions/checkout@v4 # Il fait un "copy-paste" du code

    - name: Installer PHP
      uses: shivammathur/setup-php@v2
      with:
        php-version: '8.5' # Il installe la même version que toi

    - name: Verifier l'installation
      run: composer install --no-scripts # Il vérifie que tout fonctionne

## Procédure de déploiement pas à pas

### Étape 1 : Création du contrôleur

Créer le contrôleur :

```bash
php bin/console make:controller HomeController
```

---

### Étape 2 : Configuration de la route principale

Modifier :

```text
src/Controller/HomeController.php
```

Ajouter :

```php
#[Route('/', name: 'home')]
```

Le contrôleur retourne :

```php
return $this->render('home/index.html.twig');
```

---

### Étape 3 : Création de la page Twig

Modifier :

```text
templates/home/index.html.twig
```

Contenu ajouté :

- Titre : "Bienvenue sur mon projet Cloud"
- Nom
- Prénom
- Date et heure dynamique

Code utilisé :

```twig
{{ "now"|date("d/m/Y H:i:s") }}
```

---

### Étape 4 : Vérification locale

Accéder à :

```text
http://127.0.0.1:8000
```

Vérifier :

- Affichage du titre
- Affichage du nom et prénom
- Affichage dynamique de la date et de l'heure
- Fonctionnement correct de la route `/`

---

### Étape 5 : Envoi vers GitHub

Ajouter les fichiers :

```bash
git add .
git commit -m "Premier déploiement Symfony"
git push origin main
```

---

### Étape 6 : Déploiement sur Scalingo

1. Se connecter à Scalingo
2. Créer une nouvelle application
3. Connecter le dépôt GitHub
4. Déployer automatiquement la branche `main`
5. Attendre la fin du déploiement
6. Tester l'application en ligne

Résultat attendu :

✓ Page d'accueil accessible

✓ Titre affiché correctement

✓ Nom et prénom visibles

✓ Date et heure mises à jour dynamiquement
(⚠️ Rien concernant la base de données)