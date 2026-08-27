# Urban Escape – HTML-widgetar

Testyta för HTML-widgetar till kunden Urban Escape. Fristående HTML-filer utan
byggsteg – öppna dem direkt i webbläsaren eller lägg dem på valfri webbserver.

## Innehåll

| Fil / mapp | Beskrivning |
| --- | --- |
| `index.html` | Huvudsidan. **Helt fristående** – alla bilder ligger inbäddade som base64. Har en filmknapp som länkar till `guide-film.html`. |
| `widget.html` | Den interaktiva RoomOS-widgeten med knappar. Självbärande. |
| `widget-en.html` | Engelsk version av `widget.html`. Självbärande. |
| `guide-film.html` | Den animerade guidefilmen. Självbärande. |
| `originalbilder/` | Källbilder. **Laddas inte av någon sida.** Se nedan. |
| `experiment/` | Testfiler som inte används skarpt. |

Ingen av sidorna laddar externa filer, script eller typsnitt. De fungerar
offline och kan flyttas var som helst utan att sökvägar går sönder.

## originalbilder/

Bilderna här är byte-identiska med dem som ligger inbäddade i `index.html`.
De sparas som original i full kvalitet för framtida redigering och nya
exporter – inte för att sidan behöver dem.

Undantag: `motes-meny-webex.png` är inte inbäddad någonstans. Den ser ut att
vara Webex-motsvarigheten till `motes-meny-teams.png` och ligger kvar inför en
framtida version av sidan.

## Arbetsflöde

Ny version av en sida tas fram i exportverktyget, laddas ner och skriver över
filen i roten:

```sh
cp ~/Downloads/index.html index.html
git add index.html && git commit -m "..."
```

Eftersom sidorna är fristående behöver inga bildsökvägar justeras efteråt.
Verifiera gärna att exporten är komplett innan commit:

```sh
grep -c 'data:image' index.html                          # antal inbäddade bilder
grep -o 'src="[^"]*"' index.html | grep -v '^src="data:' # ska vara tomt
```

Notera att varje ny export av `index.html` lägger ungefär 3,5 MB i git-historiken.

## experiment/

`gamal.html` och `matt.html` är gamla testfiler som inte används. `gamal.html`
är trasig: den refererar bildsökvägar under `assets/` som aldrig funnits i
repot, samt ett `./support.js` som saknas. Den ligger kvar som referens – felsök
den inte i onödan.
