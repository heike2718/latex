# latex

Sammlung von Dingen, die ich in meinem online-Aufgabenarchiv [Mathe für jung und alt](https://mathe-jung-alt/mja/) und [Minikänguru und der virtuellen Mathe-AG](https://mathe-jung-alt.de) verwende.

## Fonts für die Klassen 1 und 2

Eine Zeitlang habe ich einen Font Avantgarde verwendet:

```
\usepackage{avantgar}
```

der einem Font für Leseanfänger am nächsten kam. Allerdings stellte ich fest, dass Erst- und Zweitkläßler bei diesem Font das große I und das kleine l nicht gut außeinanderhalten konnten.

Auf der Suche nach geeigneten Fonts für Klasse 1 und 2, die ich in LaTeX einbinden konnte, stieß ich auf die Fibel-Fonts von Peter Wiegand und eine Schriftart von Wolfram Esser. Beide haben die geeignete Lizenz für die Nutzung in LaTeX.

[Quellen hier](https://mathe-jung-alt.de/fonts.html)


## Umwandlung in LaTeX-Fonts

erfolgte entsprechend dieser [Anleitung](http://www.radamir.com/tex/ttf-tex.htm).

## Docker

Basis-Image ist [heike2718/docker-java-latex](https://github.com/heike2718/mathe-jung-alt/tree/develop/backend/docker).

[Dockerfile heike2718/docker-java-latex](https://github.com/heike2718/mathe-jung-alt/blob/develop/backend/docker/docker-java-latex/Dockerfile)

Basierend auf diesem Image wird ein weiteres Image gebaut, das ein paar Imagetools zum Umwandeln von dvi in png enthält sowie die umgewandelten Fonts im  user-LaTeX-Verzeichnisbaum, damit alles schön von der TeXLife-Full-Installation im Container getrennt bleibt.

Hier die Befehle zum kopieren und Einbinden der Fonts:

(Dockerfile)
```
# copy fonts fondsmap etc to /usr/local/share/texmf/
COPY ./usr/local/share/texmf/ /usr/local/share/texmf/

...

RUN texhash

...

```

