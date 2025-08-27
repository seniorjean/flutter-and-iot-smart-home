# Projet IoT Éducatif pour Enfants

<img src="https://raw.githubusercontent.com/seniorjean/flutter-and-iot-smart-home/refs/heads/main/assets/preview.png" width="200">

[![Watch the video](https://raw.githubusercontent.com/seniorjean/flutter-and-iot-smart-home/refs/heads/main/assets/video-preview.png)](https://raw.githubusercontent.com/seniorjean/flutter-and-iot-smart-home/refs/heads/main/assets/demo.mp4)


## Vue d'ensemble

Ce projet combine Arduino, ESP8266, une interface Scratch pour enfants et une application mobile Flutter pour créer un système IoT éducatif interactif.

## 🏗️ Architecture du Système

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Arduino UNO   │◄──►│    ESP8266      │◄──►│  Application    │
│   (Capteurs)    │    │ (Communication) │    │    Mobile       │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         ▲                                              ▲
         │                                              │
         ▼                                              ▼
┌─────────────────────────────────────────────────────────────────┐
│              Interface Scratch pour Enfants                     │
└─────────────────────────────────────────────────────────────────┘
```

## 📁 Structure du Projet

```
project/
├── ARDUINO-UNO-CODE/
│   └── ARDUINO-UNO-CODE.ino
├── ESP8266-CODE/
│   └── ESP8266-CODE.ino.ino
├── kids_block_file.sb3
├── mobile_app_flutter/
│   ├── lib/
│   ├── android/
│   ├── ios/
│   └── pubspec.yaml
└── README.md
```

## 🛠️ Prérequis

### Matériel Nécessaire
- **Arduino UNO**
- **Module ESP8266** (NodeMCU ou Wemos D1 Mini)
- **Câbles de connexion**
- **Capteurs** (selon votre projet)
- **Ordinateur** avec Windows/Mac/Linux
- **Smartphone Android/iOS**

### Logiciels Requis
- [Arduino IDE](https://www.arduino.cc/en/software) (version 2.0 ou supérieure)
- [Visual Studio Code](https://code.visualstudio.com/) ou [Android Studio](https://developer.android.com/studio)
- [Flutter SDK](https://flutter.dev/docs/get-started/install)
- [Scratch for Desktop](https://scratch.mit.edu/download) ou application compatible .sb3

## 🚀 Installation et Configuration

### 1. Configuration de l'Arduino IDE

1. **Télécharger et installer Arduino IDE**
   ```bash
   # Visitez https://www.arduino.cc/en/software
   ```

2. **Ajouter le support ESP8266**
   - Ouvrir Arduino IDE
   - Aller dans `Fichier` > `Préférences`
   - Dans "URLs de gestionnaire de cartes supplémentaires", ajouter :
   ```
   http://arduino.esp8266.com/stable/package_esp8266com_index.json
   ```
   - Aller dans `Outils` > `Type de carte` > `Gestionnaire de cartes`
   - Rechercher "ESP8266" et installer le package

### 2. Installation du Code Arduino

#### 📟 Arduino UNO
1. **Connecter l'Arduino UNO** à votre ordinateur via USB
2. **Ouvrir le fichier** `ARDUINO-UNO-CODE/ARDUINO-UNO-CODE.ino`
3. **Sélectionner la carte** :
   - `Outils` > `Type de carte` > `Arduino UNO`
4. **Sélectionner le port** :
   - `Outils` > `Port` > (sélectionner le port COM approprié)
5. **Téléverser le code** :
   ```
   Clic sur le bouton "Téléverser" (→) ou Ctrl+U
   ```

![Arduino Upload](https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Arduino-uno-perspective-transparent.png/1164px-Arduino-uno-perspective-transparent.png)

#### 📡 ESP8266
1. **Connecter l'ESP8266** à votre ordinateur via USB
2. **Ouvrir le fichier** `ESP8266-CODE/ESP8266-CODE.ino.ino`
3. **Configurer WiFi** (modifier dans le code) :
   ```cpp
   const char* ssid = "VOTRE_WIFI";
   const char* password = "VOTRE_MOT_DE_PASSE";
   ```
4. **Sélectionner la carte** :
   - `Outils` > `Type de carte` > `ESP8266` > `NodeMCU 1.0 (ESP-12E Module)`
5. **Sélectionner le port** correspondant
6. **Téléverser le code**

### 3. Configuration de l'Interface Scratch

1. **Installer Scratch Desktop**
   - Télécharger depuis : https://scratch.mit.edu/download
   - Installer l'application

2. **Ouvrir le projet**
   - Lancer Scratch Desktop
   - Cliquer sur `Fichier` > `Ouvrir à partir de l'ordinateur`
   - Sélectionner le fichier `kids_block_file.sb3`

![Kids Block Interface](https://raw.githubusercontent.com/seniorjean/flutter-and-iot-smart-home/refs/heads/main/assets/kidsblock.png)

### 4. Installation de l'Application Flutter

#### Prérequis Flutter
1. **Installer Flutter SDK**
   ```bash
   # Windows
   git clone https://github.com/flutter/flutter.git -b stable
   # Ajouter flutter/bin au PATH
   
   # macOS/Linux
   wget https://storage.googleapis.com/flutter_infra_release/releases/stable/macos/flutter_macos_arm64_3.x.x-stable.zip
   unzip flutter_macos_arm64_3.x.x-stable.zip
   export PATH="$PATH:`pwd`/flutter/bin"
   ```

2. **Vérifier l'installation**
   ```bash
   flutter doctor
   ```

#### Avec Visual Studio Code
1. **Ouvrir VS Code**
2. **Installer les extensions Flutter et Dart**
3. **Ouvrir le dossier du projet** `mobile_app_flutter`
4. **Installer les dépendances** :
   ```bash
   flutter pub get
   ```
5. **Lancer l'application** :
   ```bash
   flutter run
   ```

#### Avec Android Studio
1. **Ouvrir Android Studio**
2. **Installer les plugins Flutter et Dart**
3. **Importer le projet** : `File` > `Open` > sélectionner `mobile_app_flutter`
4. **Synchroniser** : Cliquer sur "Pub get" quand demandé
5. **Lancer** : Appuyer sur le bouton "Run" ▶️

## 🔧 Configuration Réseau

### Connexion WiFi ESP8266
Modifier les paramètres dans le code ESP8266 :
```cpp
// Configuration WiFi
const char* ssid = "VotreNomWiFi";
const char* password = "VotreMotDePasse";

// Configuration serveur (optionnel)
const char* server_ip = "192.168.1.100";
const int server_port = 8080;
```

### Configuration Application Mobile
Dans le fichier `mobile_app_flutter/lib/config.dart` :
```dart
class Config {
  static const String ESP8266_IP = "192.168.1.101";
  static const int PORT = 80;
  static const String API_BASE_URL = "http://192.168.1.101";
}
```

## 🎮 Utilisation

### 1. Démarrage du Système
1. **Alimenter l'Arduino UNO** (via USB ou alimentation externe)
2. **Alimenter l'ESP8266** (généralement via USB)
3. **Vérifier les connexions** - Les LEDs devraient s'allumer
4. **Attendre la connexion WiFi** de l'ESP8266

### 2. Interface Scratch
1. **Ouvrir** le fichier `kids_block_file.sb3`
2. **Glisser-déposer** les blocs pour créer des programmes
3. **Cliquer sur le drapeau vert** pour exécuter

### 3. Application Mobile
1. **Lancer l'application** Flutter
2. **Se connecter** au réseau local
3. **Contrôler les capteurs** et actuateurs via l'interface

## 📱 Fonctionnalités

- ✅ **Contrôle à distance** via application mobile
- ✅ **Programmation visuelle** avec Scratch
- ✅ **Lecture de capteurs** en temps réel
- ✅ **Interface intuitive** pour enfants
- ✅ **Communication WiFi** entre appareils

## 🔍 Dépannage

### Problèmes Courants

**Arduino ne se connecte pas :**
- Vérifier le câble USB
- Vérifier le port sélectionné dans l'IDE
- Redémarrer l'Arduino IDE

**ESP8266 ne se connecte pas au WiFi :**
- Vérifier le nom et mot de passe WiFi
- Vérifier que le WiFi est en 2.4GHz (pas 5GHz)
- Vérifier la portée du signal

**Application Flutter ne compile pas :**
```bash
flutter clean
flutter pub get
flutter run
```

**Scratch ne trouve pas le fichier :**
- Vérifier l'extension .sb3
- Essayer de redémarrer Scratch Desktop

## 📞 Support

Pour toute question ou problème :
1. Vérifier la section dépannage ci-dessus
2. Consulter les logs dans l'Arduino IDE (Moniteur série)
3. Vérifier les connexions physiques
4. Créer une issue sur GitHub si le problème persiste

## 🤝 Contribution

Les contributions sont les bienvenues ! N'hésitez pas à :
- 🐛 Signaler des bugs
- 💡 Proposer des nouvelles fonctionnalités
- 📖 Améliorer la documentation
- 🧪 Ajouter des tests

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier `LICENSE` pour plus de détails.

---

**Bon codage ! 🚀**
