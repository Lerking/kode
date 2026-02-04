# Hemmelige koder

## Resultatet

Vi skal i dag lave en applikation, hvor man kan indtaste en tekst, og få den gjort hemmelig. Ved at angive den samme tekst igen skal man kunne få den tekst man startede med.

Første gang vi kører programmet skal vi skrive det vi vil holde hemmeligt:

```
Skriv den tekst der skal gøres hemmelig: 
This is a secret
>> Tuvf vf n frperg
```

Herefter kan vi bede om at få dekodet den hemmelige tekst "Tuvf vf n frperg":

```
Skriv den tekst der skal gøres hemmelig: 
Tuvf vf n frperg
>> This is a secret
```

## Kode del 1: Indtastning af tekst
Det første vi har brug for, er den tekst vi skal behandle. Dette prøvede i sidste gang.
Start med at skrive denne kode:

```python
tekst = input("Skriv den tekst der skal gøres hemmelig: \n")
print(tekst)
```

Her kalder vi funktionen __input__. Funktionen skriver en tekst til skærmen og lader brugeren skrive noget til vores program.  
Det som brugeren skriver til vores program gemmes i variablen __tekst__.
 
> [!TIP]  
> Kan du finde ud af hvad "\n" gør i koden ovenfor?

Bagefter kalder vi __print__ som skriver noget til skærmen, uden at brugeren kan svare på det.
Vi printer bare det brugeren har skrevet, så vi kan se vi har fået det rigtigt.

## Kode del 2: Iteration
Ordet iteration betyder at tælle igennem noget. Det kunne være at tælle til 10 eller at tælle igennem alle bogstaverne i vores __tekst__.

Til at starte med prøver vi at skrive alle bogstaverne i det brugeren indtastede.
Tilføj denne kode til dit program:

```python
for tegn in tekst:
  print(tegn)
```

Her laver vi en ny variabel __tegn__. For hvert tegn der er i vores __tekst__ bliver koden nedenunder kørt. Her udskriver vi bare det enkelte tegn.

> [!WARNING]  
> Det er vigtigt at linjen med __print__ har noget mellemrum foran. Det er denne måde programmeringssproget ved hvad den skal gøre.

> [!TIP]  
> Kan du gennemskue forskellen på de to stykker kode nedenfor?

Kode 1:
```python
for tegn in tekst:
  print(tegn)
  print("Færdig")
```

Kode 2:
```python
for tegn in tekst:
  print(tegn)
print("Færdig")
```

## Kode del 3: Ændring af tegn
Nu skal vi til at gøre tegnene hemmelige. Vi gør det et tegn ad gangen.

Først skal vi beskrive hvordan vi oversætter tegnene. Vi starter med en simpel løsning, hvor oversættelsen kan ses i koden.  
Tilføj denne kode til dit program:

```python
kode = {
   'a':  '1',
   'b':  '2',
   'c':  '3',
   'd':  '4',
   'e':  '5',
   'f':  '6',
   'g':  '7'
}
```

Her laver vi en variabel __kode__ og sætter den til et _Dictionary_, Et _Dictionary_ er noget, hvor man kan slå noget op og få noget andet. 
 * Hvis vi slår 'a' op, får vi '1'.
 * Hvis vi slår 'b' op, får vi '2'.
 * Hvis vi slår 'g' op, får vi '3'.

Ret den kode der udskriver de enkelte tegn til dette:
```python
for tegn in tekst:
  tegn = kode[tegn]
  print(tegn)
```

Den nye linje er:
```python
  tegn = kode[tegn]
```

Denne linje siger at vi skal kigge i vore _Dictionary_ og oversætte det tegn vi har og gemme det tilbage i variablen tegn.

> [!TIP]  
> __Prøv at køre programmet og oversæt teksten:__  
> abe  
> __Fik du også__
> 125

> [!TIP]  
> __Prøv at køre programmet og oversæt teksten:__  
> ged  
> __Fik du også__
> 754

> [!WARNING]  
> __Hvad sker der hvis du kører programmet og oversætter teksten__  
> fejl  

## Kode del 4: Tegn vi ikke kender
Det kan ske at brugeren skriver et tegn til os som vi ikke kender. Måske vi bare skulle lade være med at oversætte dem.

Ret den kode der udskriver de enkelte tegn til dette:
```python
for tegn in tekst:
  if tegn in kode:
    tegn = kode[tegn]
  print(tegn)
```

Den nye linje er:
```python
  if tegn in kode:
```

Her siger vi at koden der står under if kun skal køres, hvis __tegn__ findes i __kode__.

Læg mærke til at den næste linje har fået flere mellemrum foran sig. Det betyder at den kun skal køres, hvis linje med "if" er rigtig. Linken med "print" har lige så mange mellemrum som "if". Den er lige så vigtig og kører altid, uanset om det der står med "if" er rigtigt eller ej.

> [!TIP]  
> __Prøv at køre programmet og oversæt teksten:__  
> fejl  

Nu virker det, men nogle af bogstaverne bliver ikke hemmelige. 

> [!TIP]  
> Kan du selv rette programmet til så alle bogstaverne bliver hemmelige?

## Kode del 5: Kun en linje
Lige nu skriver vores program svaret nedad. Det er lidt besværligt, hvis det er en lang besked.

I stedet kan vi samle bogstaverne sammen til en enkelt tekst, i stedet for at skrive dem ud hver for sig.

> [!TIP]  
> Prøv om du kan placere de tre kode-dele korrekt.

---

Før vi itererer igennem bogstaverne skal vi lave en variabel med resultatet:
```python
resultat = ""
```
Her laver vi variablen __resultat__ og sætter den til en tom tekst.

---

Når vi kender det bogstav der skal stå, skal vi ikke udskrive det med __print__ men tilføje det til resultatet:
```python
  resultat = resultat + tegn
```
Her sætter vi resultatet til det vi allerede har og sætter det nye tegn bag på.

---

Når vi har bygget hele resultatet skal vi skrive det til skærmen:

```python
print(resultat)
```

## Kode del 6: Afkodning af hemmelig beskeder
Hvis du kører programmet og koder beskeden:

> Min hest har spist en sko  

Får du en hemmelig besked ud.

Hvis du kører programmet igen, og sætter den hemmelige besked ind, får du så den originale besked ud?

For at det virker begge veje, er det vigtigt at de samme tegn kan oversættes begge veje. Så hvis "a" bliver til "n", skal "n" også blive til "a". Prøv eventuelt med denne kode:

```python
kode = {
   'a':  'n',
   'b':  'o',
   'c':  'p',
   'd':  'q',
#....... <- Fortsæt rækkefølgen selv
   'l':  'y',
   'm':  'z',
   'n':  'a',
   'o':  'b',
   'p':  'c',
#....... <- Fortsæt rækkefølgen selv
   'w':  'j',
   'x':  'k',
   'y':  'l',
   'z':  'm'
}
```

> [!TIP]  
> Det er lettest at få til at passe, hvis der er et lige antal bogstaver.  
> Jeg brugte følgende bogstaver:  
> a b c d e f g h i j k l m n o p q r s t u v w x y z

## Kode del 7: Flere tegn
Nu kan vi kode og afkode beskeder. Men der er nogle ting der ikke virker.
 * Hvad nu hvis der er tal med i koden?
 * Hvad nu hvis der er STORE BOGSTAVER med i koden?

> [!TIP]  
> Har du en løsning til at få tal eller STORE BOGSTAVER til at virke?

## Svær ekstra opgave 1 - Morsekode
Med en lille tilrettelse kan vores program rettes til at lave morsekode.

Læs mere om morsealfabetet her: https://da.wikipedia.org/wiki/Morsealfabet

> [!TIP]  
> Kan du få dit program til at skrive morsekode for teksten "jeg kan morse".

## Svær ekstraopgave 2 - Morsekode baglæns (MEGET svær)
Kan du få dit program til at overætte morsekode tilbage til bogstaver?

Prøv eventuelt med denne morsekode:
> --./---/-../-//-.-/.-../.-/.-././-
