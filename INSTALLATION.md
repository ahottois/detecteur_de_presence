# Guide d'installation du Radar de Présence

Ce guide vous explique en détail comment installer et configurer votre Radar de Présence basé sur ESPHome avec un capteur LD2420.

## Table des matières
- [Matériel nécessaire](#matériel-nécessaire)
- [Branchement des composants](#branchement-des-composants)
- [Installation d'ESPHome](#installation-desphome)
- [Configuration du fichier YAML](#configuration-du-fichier-yaml)
- [Premier déploiement](#premier-déploiement)
- [Intégration à Home Assistant](#intégration-à-home-assistant)
- [Calibration du capteur](#calibration-du-capteur)
- [Dépannage](#dépannage)

## Matériel nécessaire

- ESP32 (modèle ESP32dev ou compatible)
- Capteur radar LD2420
- Alimentation 5V (adaptateur ou câble USB)
- Câbles Dupont (femelle-femelle, mâle-femelle)
- Ordinateur avec accès à Home Assistant
- (Optionnel) Boîtier pour l'installation finale

## Branchement des composants

Connectez votre capteur LD2420 à l'ESP32 selon le schéma suivant :

| LD2420  | ESP32     |
|---------|-----------|
| VCC     | 5V        |
| GND     | GND       |
| RX      | GPIO17 (TX)|
| TX      | GPIO33 (RX)|

> ⚠️ **Note importante** : Assurez-vous que l'ESP32 est déconnecté de toute alimentation lors du branchement des composants.

## Installation d'ESPHome

1. Si vous n'avez pas encore ESPHome, installez-le dans Home Assistant:
   - Accédez à **Paramètres** > **Modules complémentaires**
   - Cliquez sur **Boutique des modules complémentaires**
   - Recherchez "ESPHome" et installez-le

2. Une fois installé, accédez à ESPHome depuis le tableau de bord de Home Assistant

## Configuration du fichier YAML

1. Créez un nouveau dispositif ESPHome en cliquant sur le bouton **+ Nouveau dispositif**
2. Nommez-le "radar-presence" (ou un nom de votre choix)
3. Sélectionnez "ESP32" comme type de carte
4. Créez un fichier `secrets.yaml` dans le dossier ESPHome avec vos informations WiFi:
   ```yaml
   wifi_ssid: "VotreReseauWiFi"
   wifi_password: "VotreMotDePasse"
   ```
5. Remplacez le contenu du fichier YAML généré par le code complet du projet (disponible dans le dépôt GitHub)

## Premier déploiement

1. Connectez votre ESP32 à votre ordinateur via USB
2. Dans l'interface ESPHome, cliquez sur les trois points (...) à côté de votre appareil
3. Sélectionnez **Téléverser**
4. Suivez les instructions pour installer le firmware sur votre ESP32
   - Pour la première installation, vous devrez peut-être maintenir le bouton BOOT enfoncé lors de la connexion
   - Si vous rencontrez des problèmes, essayez d'utiliser le mode "Téléverser via USB" ou "Compiler localement"

## Intégration à Home Assistant

1. Une fois le firmware installé, votre ESP32 devrait se connecter à votre réseau WiFi
2. Home Assistant devrait le détecter automatiquement
   - Si ce n'est pas le cas, accédez à **Paramètres** > **Appareils et services** > **Ajouter une intégration**
   - Recherchez "ESPHome" et suivez les instructions
3. Entrez l'adresse IP de votre ESP32 (visible dans l'interface ESPHome)
4. Votre Radar de Présence devrait maintenant apparaître dans Home Assistant

## Calibration du capteur

### Calibration automatique

1. Assurez-vous que la pièce est vide (sans présence humaine)
2. Accédez à l'entité "Démarrer Calibration" dans Home Assistant et cliquez dessus
3. Déplacez-vous à la distance que vous souhaitez calibrer (par exemple, à l'entrée de la pièce)
4. Restez immobile quelques secondes
5. Le statut de calibration devrait se mettre à jour automatiquement

### Calibration manuelle

1. Si vous connaissez la distance exacte que vous souhaitez utiliser:
2. Utilisez l'entité "Valeur Calibration" pour définir directement cette distance
3. La calibration sera mise à jour immédiatement

## Configuration avancée

Après l'installation de base, vous pouvez ajuster les paramètres suivants selon vos besoins:

- **Délai de Présence**: Durée pendant laquelle le capteur continue à signaler une présence après la dernière détection
- **Distance Minimale/Maximale**: Définit la plage de détection du capteur
- **Seuils de Mouvement et d'Immobilité**: Ajuste la sensibilité de détection

## Mise à jour du firmware

Pour les mises à jour futures, vous pourrez utiliser la fonction OTA (Over The Air):

1. Modifiez le fichier YAML selon vos besoins
2. Dans l'interface ESPHome, cliquez sur les trois points (...) puis sur **Téléverser**
3. Sélectionnez "Téléverser via OTA"

## Dépannage

### Le capteur ne se connecte pas au WiFi
- Vérifiez vos informations WiFi dans le fichier `secrets.yaml`
- L'ESP32 créera un point d'accès nommé "Radar-Fallback" avec le mot de passe "radar12345"

### Le capteur ne détecte pas correctement
- Assurez-vous que le capteur est correctement orienté vers la zone à surveiller
- Essayez d'ajuster les seuils de sensibilité
- Recalibrez le capteur

### Problèmes de communication avec le capteur
- Vérifiez les connexions UART (TX/RX)
- Assurez-vous que les broches définies dans le YAML correspondent à votre câblage

Si vous rencontrez d'autres problèmes, n'hésitez pas à ouvrir une issue sur GitHub.
