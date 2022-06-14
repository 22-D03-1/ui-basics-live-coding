# Einrichtung eines SCSS-Projekts

Mit SCSS können wir unsere Stylesheets besser strukturieren und effizienter schreiben. SCSS erweitert CSS um sehr nützliche Funktionen. Damit ein Browser die Styles interpretieren kann, müssen wir sie aber erst in normales CSS umwandeln. Dazu nutzen wir das node.js-Modul "sass".

1. Wir beginnen mit der Einrichtung des Projekts. Führen wir `npm init -y` im Projektverzeichnis aus, wird eine package.json erstellt.
2. Anschließend installieren wir sass mit dem Befehl `npm install sass` (oder in Kurzform: `npm i sass`). Die package.json wurde nun erweitert um den Bereich "dependencies".
3. **GANZ WICHTIG:** Bevor wir unser Projekt committen oder pushen, müssen wir noch die Datei .gitignore anlegen und darin eine Zeile `node_modules` eintragen. Damit verhindern wir, dass unsere Dependencies (das Modul "sass") mit im Repo landet. Diese lassen sich nämlich einfach mit dem Befehl `npm install` installieren und sollten von uns nicht in eigenen Repos gespeichert werden.
4. In der package.json gibt es einen Bereich "scripts". Hier fügen wir die folgende Zeile hinzu: `"build": "sass -w scss/style.scss css/style.css"`. So erstellen wir einen eigenen Befehl, den wir gleich aufrufen werden. Der zweite Teil beschreibt den Befehl, der dadurch ausgeführt wird. Das installierte Modul "sass" überwacht (-w) die erste angegebene Datei (scss/style.scss) und erzeugt unser fertiges CSS an der zweiten Stelle (css/style.css) bei jeder Änderung.
5. Die CSS-Datei css/style.css wird automatisch generiert. Die scss/style.scss müssen wir selbst anlegen.
6. In der SCSS-Datei können wir nun unsere Styles definieren. Hier können wir zuerst unsere bisherigen CSS-Styles einfügen.
7. In der HTML-Datei müssen wir noch auf die neu generierte CSS-Datei (css/style.css) verlinken.
8. Jetzt lassen sich unsere Styles auf einzelne SCSS-Dateien aufteilen. Eine sinnvolle Aufteilung wäre bspw. nach den Bereichen: Header, Footer, verschiedene Inhaltsbereiche etc.
9. Damit die Styles der einzelnen Dateien im CSS auftauchen, nutzen wir `@import` in scss/style.scss. So werden beim Durchlaufen unseres Befehls alle importierten Dateien zusammengefasst und in eine CSS-Datei geschrieben.
10. Sind wir soweit durch, starten wir unseren `build`-Befehl im Terminal mit `npm run build`. Der Befehl läuft so lange, bis wir das Terminal schließen oder die Ausführung mit STRG + C abbrechen.

Das Ergebnis ist eine einzige style.css, die der Browser laden muss. Trotzdem haben wir durch die einzelnen Dateien für die verschiedenen Bereiche eine ordentliche Struktur, in der man nicht lange suchen muss.

Damit wir später noch wissen, wo unsere Styles eigentlich herkommen, werden sogenannte Source Maps angelegt. Das ist in unserem Projekt die Datei css/style.css.map. Damit lässt sich in den Browser Dev Tools der Ursprung der Styles verfolgen, da diese ja aus den einzelnen Dateien stammen. Ohne diese Source Map würde der Browser lediglich die css/style.css als Quelle angeben.
