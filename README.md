# Projet Radar de Présence ESPHome

## 📡 Présentation

Bienvenue sur le projet Radar de Présence basé sur ESPHome. 
Ce projet permet de transformer un capteur radar LD2420 et un ESP32 en un détecteur de présence intelligent et précis pour votre système domotique Home Assistant.

## ✨ Caractéristiques

- 🔍 Détection de présence précise (même sans mouvement)
- 📏 Mesure de distance en temps réel
- 🔧 Calibration automatique et manuelle
- 🛠️ Configuration complète via l'interface Home Assistant
- 📶 Connexion sans fil avec fallback en mode point d'accès
- 🔄 Mise à jour OTA (Over The Air)

## 🛠️ Matériel nécessaire

- ESP32 (modèle ESP32dev ou compatible)
- Capteur radar LD2420
- Alimentation 5V
- Quelques câbles de connexion

## 🔧 Installation

1. Clonez ce dépôt
2. Configurez votre fichier `secrets.yaml` avec vos identifiants WiFi
3. Flashez votre ESP32 avec ESPHome
4. Intégrez l'appareil dans Home Assistant

Consultez le [guide d'installation détaillé](./INSTALLATION.md) pour plus d'informations.

## 📝 Configuration

Le fichier de configuration ESPHome (`radar-presence.yaml`) inclut :

- Configuration WiFi et API sécurisée
- Paramètres UART pour la communication avec le capteur
- Capteurs et contrôles pour une configuration complète
- Système de calibration intelligent


## 🤝 Contribuer

Les contributions sont les bienvenues ! N'hésitez pas à ouvrir une issue ou à proposer une pull request.

## 📄 Licence

NONE.
