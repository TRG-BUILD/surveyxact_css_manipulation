
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

```html
<script>
window.addEventListener("message", (event) => {
            try {
                // Tjek om message er fra iframe
                if (event.data.type === "doneCallback") {
                    document.getElementsByClassName("page1")[0].getElementsByClassName("navigation-buttons")[0].style.display = "flex";
                    // Nedestående kan automatisk sende brugeren videre, hvis det er ukommenteret.
                    //document.getElementsByClassName("next-button");
                    //console.log(‘map finished’);
                    //collection[‘next’].click()
                }
            } catch (e) {
                console.error(e.message);
            }
        });
</script>
```


### Vis element basert på om en checkbox er sat.
```html
<script>
 
checkbox = document.getElementById('ch_1748233319-1748233321'); // Brug her id for checkboxen der skal overvåges!
 
checkbox.addEventListener('change', function() {
  if (this.checked) {
    console.log("Checkbox is checked..");
   iframe = document.getElementsByTagName('iframe');
   iframe[0].style.display = 'none';
  } else {
    console.log("Checkbox is not checked..");
iframe[0].style.display = 'block';
  }
});
 
</script>
```

### Indsæt iframe med externkey

Skal indsættes som Expression 

```html
"<iframe style='width:100%;height:800px;' src='https://urlforiframe.tld/something/?userid=" + [respondent/externkey] + "'></iframe>"
```