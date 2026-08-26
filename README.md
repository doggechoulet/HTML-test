# Urban Escape – HTML-widgetar

Testyta för HTML-widgetar till kunden Urban Escape. Fristående HTML-filer utan
byggsteg – öppna dem direkt i webbläsaren.

## Innehåll

| Fil | Beskrivning |
| --- | --- |
| `index.html` | Huvudsidan. Använder bilderna i `assets/`. |
| `widget.html` | Den interaktiva RoomOS-widgeten med knappar. |
| `guide-film.html` | Den animerade guidefilmen. |
| `assets/` | Bilder (`.png`) och `sim-logo.svg` som `index.html` refererar till. |
| `experiment/` | Testfiler som inte används skarpt (`gamal.html`, `matt.html`). |

## Att tänka på

* `index.html` refererar bilderna med relativa sökvägar (`assets/...`) – filen
  måste ligga kvar i repots rot för att bilderna ska hittas.
* `widget.html` och `guide-film.html` har sina bilder inbäddade som base64 och
  är därför självbärande.
