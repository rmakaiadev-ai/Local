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

### Déploiement sur Scalingo

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