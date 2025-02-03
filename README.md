# MySQL-Docker-Image

Dieses Repository enthält ein einfaches Docker-Image für MySQL. Es ermöglicht eine schnelle und einfache Einrichtung einer MySQL-Datenbank in einem Container.

## Voraussetzungen
- Docker muss auf dem System installiert sein.

## Installation & Nutzung
### 1. Docker-Container mit MySQL starten
```sh
docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=mydb -p 3306:3306 -d mysql:latest
```

### 2. Verbindung zur MySQL-Datenbank herstellen
```sh
docker exec -it mysql-container mysql -u root -p
```
Gebe das Passwort `rootpass` ein, um dich anzumelden.

### 3. Container stoppen und löschen
```sh
docker stop mysql-container
```
```sh
docker rm mysql-container
```

## Persistente Daten speichern (Optional)
Um sicherzustellen, dass Daten nicht verloren gehen, kann ein Volume genutzt werden:
```sh
docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=mydb -p 3306:3306 -v mysql_data:/var/lib/mysql -d mysql:latest
```

## Weitere Anpassungen
Falls du eine benutzerdefinierte Konfigurationsdatei nutzen möchtest, kannst du eine eigene `my.cnf` Datei einbinden:
```sh
docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=mydb -p 3306:3306 -v $(pwd)/my.cnf:/etc/mysql/my.cnf -d mysql:latest
```

## Lizenz
Dieses Projekt steht unter der MIT-Lizenz.

