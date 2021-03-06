# docker Prototyp

Dieses ist eine kleine Anwendungsbeispiel. Wir können die protokol für schaffen Docker Containers sehen.

## Installation

**Windows**: Sie müssen die Docker-Konsole eingeben. Dann legen Sie sich in das Projektverzeichnis ...


1. Schaffen der Container: (in Console) ```bash ./myDocker.sh```

    1.1. Build Container: Option 1- wählen die Ports.

    1.2. Start / Stop Containers: Option 2

    1.3. Siehe Starten Containers: Option 3

    1.4. Remove Containers: Option 4 (Remove und backup database)

    1.5. Schließen: Option 0

#### Optionen

- Erstellung der Dokumentation: (in Console) ```./doc.sh```
- Test CodeQualität: (in Console) ```phpcs ./src```


### Erstellt Docker-Umgebung.


Jetzt haben wir 3 container: **php** (unsere Anwendung), **db** (DataBase) und **phpmyadmin**.


## Zugang zu Dienstleistungen.

**Anwendung**

*Port, der in der Installation ausgewählt wurde

```
Windows:

http://192.168.99.100:8050*

Linux:
http://0.0.0.0:8050*
```
***

**Phpmyadmin**

*Port, der in der Installation ausgewählt wurde

```
Windows:

http://192.168.99.100:8100*

Linux:
http://0.0.0.0:8100*
```

**Password Phpmyadmin**

User = root

Password = admin

***

**db**
```
CLI
```

**Password CLI mysql**

User = root

Password = admin


## Datenbank.

Die Datenbank ist mit dem Namen im **data** gespeichert werden **init.sql**


Die Docker-Compose-Datei importiert die Datenbank.


Beispieldatei **init.sql**

**Wichtig: Die Datei muss mit --NAME_DATABASE beginnen**

**--Name** wird dann von "myDocker.sh" verwendet, um die "backup DataBase"

```
--midb3
CREATE DATABASE midb3;
USE midb3;

CREATE TABLE `names` (
  `id` int(11) NOT NULL,
  `name` varchar(50) COLLATE utf8_unicode_ci NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;

--
-- Volcado de datos para la tabla `names`
--

INSERT INTO `names` (`id`, `name`) VALUES
(1, 'Peter'),
(2, 'Thomas');

--
-- Índices para tablas volcadas
--

--
-- Indices de la tabla `names`
--
ALTER TABLE `names`
  ADD PRIMARY KEY (`id`);

..... etc. etc.

```

![3 containers](https://github.com/ElementSystems/docker-prototyp/blob/master/dev_install/info.jpg)

## Die werkzeug

Die werkzeug gebraucht in diesem Anwendung. Wir installieren druch  "Composer".

- **phpcpd** - Control über duplicate code.
- **phpunit** - Test unit.
- **phpdocumentor** -Documentation
- **phpcs** - Code Qualität

## Backup sql

**myDocker.sh** macht  eine backup Datenbank. In **./data/backup** . Der Name der Backup wird automatisch mit folgender Struktur erstellt:

Wenn es ausgeführt option:remove container[r] wird

```Y-m-d-hmsNameUser.sql```

Wenn es ausgeführt option:Creration (run) container[1] wird

```Y-m-d-hmsNameUser-update.sql```


## Datenbanksicherheit

Das System sichert nun die Datenbank, immer.

Wenn Sie einen Container löschen. Oder wenn wir einen Run laufen und die Anwärter überschreiben.

Um zu erkennen, dass ein Container eine Datenbank enthält, muss der Service als **db** benannt werden, im Docker-Compose.



![image Datenbanksicherheit](https://github.com/ElementSystems/docker-prototyp/blob/master/dev_install/info2.jpg)

# Verzeichnisstruktur

- **command** - Dateien suport Jenkins. 
- **data** - Basedate init for Dev.
    - **backup** - Backups von Dev, generate von myDocker.sh .
- **dev_install** - includes for myDocker.sh. 
- **doc** - Dokumentation von PHPDocumentator. 
- **reports** - Reports von Jenkins Test 
- **src** - Code.
- **tests** - Dateien PHPunit.
- **vendor** - Vendor.
