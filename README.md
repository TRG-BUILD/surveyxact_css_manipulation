
# SurveyXact tilpasning

Hvis navigations menuerne skal fjernes på et spørgsmål, så kan følgende kode bruges.


## CSS
CSS indsættes ved at redigere Layout i surveyxact, koden her vil fjern navigationsmenuen på side 1

.page1 .navigation.navigation-buttons {
display: none;
}

## JavaScript:

Skal navigationsmenuen frem igen kan javascript herunder bruges.

Denne stump kode fortæller surveyxact at nu er en iframe* klar til at gå videre.

_Gå til Rediger i QuickQuestPlus og vælg Indsæt/Redigere Tekst og skriv:_

```&lt;script&gt;
window.addEventListener("message", (event) => {
            try {
                // Tjek om message er fra iframe
                if (event.data.type === "doneCallback") {
                    document.getElementsByClassName("page1")[0].getElementsByClassName("navigation-buttons")[0].style.display = "flex"
                }
            } catch (e) {
                console.error(e.message);
            }
        });
&lt;/script&gt;
```
