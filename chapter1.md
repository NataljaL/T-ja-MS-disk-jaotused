---
title       : Diskreetsed jaotused
description : Siin tutvume selliste diskreetsete jaotustega nagu binoom- (Bernoulli), Poissoni ja geomeetriline jaotused. Õpime väljastama nii tõenäosus- kui ka jaotusfunktsioonide väärtuseid, genereemina jaotustest ning kujundama vastavaid graafikuid. Alustame!

--- type:NormalExercise lang:r xp:100 skills:1 key:af3c1cf198
## Binoomjaotus
Binoomajaotus on hästi tuntud diskreetne jaotus. Selle jaotuse abil saame kirjeldada huvipakkuva sündmuse $A$ realiseerumiste arvu lõplikus katseseerias, kus kõik katsed on sõltumatud ning igal katsel antud sündmus võib kas realiseeruda või mitte. Eelduseks on ka see, et sündmus $A$ realiseerub igas katses võrdse tõenäosusega. Jaotusel on kaks parameetrit: katsete arv $n$ katseseerias ja sündmuse $A$ realiseerumise tõenäosus ühes katses $p = P(A)$.

Binoomajotusega on näiteks kirjade arv, kui visata münti 20 korda. Siin on kokku 20 katset ning igal katselt kiri võib tulla tõenäosusega 0.5, seega $X\sim Bin(20,\ 0.5)$, kus $X$='"kirjade koguarv'". Binoomajotusega on seotud `R`-is järgmised funktsioonid:

* `dbinom()`: binoomjaotuse tõenäosusfunktsiooni väärtuseed, ehk tõenäosused $P(X = x)$;
* `pbinom()`: kumulatiivsed tõenäosused ehk jaotusfunktsiooni väärtused, $P(X \leq x)$;
* `qbinom()`: kvantiilide väärtused binoomjaotuse korral;
* `rbinom()`: (pseudo)juhuslik(ud) väärtus(ed) binoomjaotusest.

Kasuta `help()` või `?`, et teada saada rohkem nende funktsioonide kasutuse kohta.

*** =instructions
* Oletame, et poes, kus müüakse t-särke, on eelneva statistika põhjal teada: klient ostab särgi tõenäosusega 0.3. Poes on hetkel 8 kliente, kes vaatavad ringi. Kliendid omavahel ei suhtle.
* Mis on tõenäosus, et kaks nendest ostavad t-särgi?
* Mis on tõenäosus, et seitse nendest ostavad t-särgi?
* Mis on tõenäosus, et *vähemalt* kaks nendest ostavad t-särgi? Pane tähele, et pead kasutama argumenti `lower.tail`. Sellel argumendil on kaks võimalikku väärtust: kui `TRUE` (vaikimisi), siis leitakse tõenäosust $P(X\leq x)$, kui `FALSE`, siis $P(X>x)$.
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Mis on tõenäosus, et kaks klienti ostab t-särgi ära? P(X = 2)
dbinom(2, size = 8, prob = 0.3)

# Mis on tõenäosus, et seitse klienti ostab t-särgi ära? P(X = 7)


# Mis on tõenäosus, et vähemalt kaks klienti ostab t-särgid ära? P(X => 2)


```

*** =solution
```{r}
# Mis on tõenäosus, et kaks klienti ostab t-särgi ära? P(X = 2)
dbinom(2, size = 8, prob = 0.3)

# Mis on tõenäosus, et seitse klienti ostab t-särgi ära? P(X = 7)
dbinom(7, size = 8, prob = 0.3)

# Mis on tõenäosus, et vähemalt kaks klienti ostab t-särgid ära? P(X => 2)
pbinom(1, size = 8, prob = 0.3, lower.tail = FALSE)

```

*** =sct
```{r}

# submission correctness tests

test_output_contains("dbinom(7, size = 8, prob  = 0.3)", incorrect_msg = "Kas leidsid tõenäosuse, et 7 klienti 8-st ostab t-särgi?")

test_output_contains("pbinom(1, size = 8, prob = 0.3, lower.tail=FALSE)", incorrect_msg = "Kas leidsid tõenäosuse, et VÄHEMALT kaks klienti ostab t-särgi? Kasutada tuleks funktsiooni `pbinom`")

# test if the students code produces an error
test_error()

# Final message the student will see upon completing the exercise
success_msg("Oivaline! Suundu järgmise harjutuse juurde!")

```

--- type:NormalExercise lang:r xp:100 skills:1 key:1491be4b66
## Geomeetriline jaotus
Juhuslik suurus *X* on geomeetrilise jaotusega, kui katseseerias, kus kõik katsed on sõltumatud loetakse katsete arvu kuni sündmuse *A* esmakordse toimumiseni (kaasa arvatud). Igal katsel saab huvipakkuv sündmus *A* realiseeruda tõenäosusega $p=P(A)$. See tõenäosus ongi ainsaks jaotuse parameetriks.

Sageli defineeritakse geomeetrilist jaotust ka alternatiivselt: *X* on katsete arv **enne** esimest toimumist. Just sellist definitsiooni kasutab ka `R`. Analoogiliselt binoomjaotusega on ka geomeetrilisel jaotusel olemas 4 põhifunktsiooni: `dgeom()`, `pgeom()`, `qgeom()`, `rgeom()`. 

Kasuta `help()` või `?` et teada saada rohkem nende funktsioonide kasutuse kohta.


*** =instructions
* Oletame, et eelneva statistika põhjal on teada ühe väravavahi kohta, et ta püüab palli kinni tõenäosusega 0.82.
* Leia tõenäosus, et ta püüab alles kolmanda palli, mis lendab tema värava suunas. Arvestades `R`-i definitsiooni, tuleks leida $P(X = 2)$. 
* Mis on tõenäosus, et ta püüab kinni vaid viienda palli?
* Mis on tõenäosus, et *vähemalt* kaks palli laseb ta väravasse lüüa, enne kui suudab kinni püüda oma esimese palli?


*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Olgu X - ebaõnnestunud katsete arv kuni 1. õnnestunud katseni (pole kaasa arvatud).

# Mis on tõenäosus, et väravavaht suudab kinni püüda vaid kolmandat palli? P(X = 2)
dgeom(2, prob = 0.82)

# Mis on tõenäosus, et väravavaht suudab kinni püüda vaid viiendat palli? P(X = 4)


# Mis on tõenäosus, et vähemalt kahte palli ta laseb mööda enne kui suudab 
# kinni püüda esimest oma palli? P(X >= 2) = P(X > 1)
pgeom(__, prob = ____, lower.tail = ______)

```

*** =solution
```{r}
# Olgu X - ebaõnnestunud katsete arv kuni 1. õnnestunud katseni (pole kaasa arvatud).

# Mis on tõenäosus, et väravavaht suudab kinni püüda vaid kolmandat palli? P(X = 2)
dgeom(2, prob = 0.82)

# Mis on tõenäosus, et väravavaht suudab kinni püüda vaid viiendat palli? P(X = 4)
dgeom(4, prob = 0.82)

# Mis on tõenäosus, et vähemalt kahte palli ta laseb mööda enne kui suudab 
# kinni püüda esimest oma palli? P(X >= 2) = P(X > 1)
pgeom(1,  prob = 0.82, lower.tail = FALSE)

```

*** =sct
```{r}

# submission correctness tests

test_output_contains("dgeom(4, prob = 0.82)", incorrect_msg = "Kas leidsid tõenäosuse, et väravavaht suudab kinni püüda vaid viiendat palli? P(X = 4)")

test_output_contains("pgeom(1,  prob = 0.82, lower.tail = FALSE)", incorrect_msg = "Kas leidsid tõenäosuse, et vähemalt kahte palli ta laseb mööda enne kui suudab 
kinni püüda esimest oma palli? Kasuta funktsiooni `pgeom()` ja argumenti `lower.tail = FALSE`")

# test if the students code produces an error
test_error()

# Final message the student will see upon completing the exercise
success_msg("Hiilgav! Said hästi ülesandega hakkama!")

```


--- type:NormalExercise lang:r xp:100 skills:1 key:9e28345bca
## Poissoni jaotus
Poissoni jaotus sobib hästi  harvade sündmuste arvu kirjeldamiseks, mis võivad juhtuda küllaltki väikese tõenäosusega mingi aja jooksul. Poissoni jaotusel on üks parameeter, $X \sim Po(\lambda)$ ja see on jaotuse keskväärtus. 

Analoogiliselt binoom- ja geomeetrilise jaotustega on ka Poissoni jaotusel olemas 4 põhifunktsiooni: `dpois()`, `ppois()`, `qpois()`, `rpois()`. 

**Näide.** On teada, et linnas *T* juhtub keskmiselt 3 liiklusõnnetust ööpäevas. Tähistagu *X* liiklusõnnetuste arvu ööpäevas selles linnas. Et linnas elab üle 10000 elanikku, on liiklusõnnetuse tõenäosus küllalt väike ja on alust arvata, et juhusliku suuruse *X* kirjeldamiseks sobib Poissoni jaotus, $X\sim Po(3)$.

Tee läbi järgmised ülesanded.

*** =instructions
1. Tõenäosus, et ööpäeva jooksul juhtub linnas *T* täpselt 1 liiklusõnnetus, on juba leitud (muutuja `yl1`). Uuri!
2. Leia tõenäosus, et ööpäeva jooksul ei juhtu ühtegi õnnetust, $P(X = 0)$, omista vastus muutujale `yl2`.
3. Leia tõenäosus, et ööpäeva jooskul juhtub mitte rohkem kui 2 liiklusõnnetust, $P(X\leq 2)$, omista muutujale `yl3`.
4. Leia tõenäosus, et ööpäeva jooksul juhtub vähemalt 5 liiklusõnnetust, $P(X\geq 5)$, omista muutujale `yl4`.

*** =hint
Viimast ülesannet saab lahendada kahel viisil:
1. vastandsündmuse tõenäosuse kaudu: $P(X\geq 5) = 1 - P(X\leq 5)$, kus viimase tõenäosuse leidmiseks kasutada funktsiooni `ppois()`;
2. funktsiooni `ppois()` ja argumendi `lower.tail = FALSE` abil. Arvesta, et selle abil saab leida $P(X > x)$.

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Olgu X liiklusõnnetuste arv ööpäevas linnas T.

# Tõenäosus, et ööpäeva jooksul juhtub linnas täpselt 1 liiklusõnnetus:
yl1 <- dpois(1, lambda = 3)

# Tõenäosus, et ööpäeva jooksul ei juhtu ühtegi õnnetust, P(X = 0):
yl2 <- 

# Tõenäosus, et ööpäeva jooskul juhtub mitte rohkem kui 2 liiklusõnnetust, P(X <= 2): 
yl3 <-

# Tõenäosus, et ööpäeva jooksul juhtub vähemalt 5 liiklusõnnetust, P(X >= 5) = P(X > 4):
yl4 <- 

```

*** =solution
```{r}
# Olgu X liiklusõnnetuste arv ööpäevas linnas T.

# Tõenäosus, et ööpäeva jooksul juhtub linnas täpselt 1 liiklusõnnetus:
yl1 <- dpois(1, lambda = 3)

# Tõenäosus, et ööpäeva jooksul ei juhtu ühtegi õnnetust, P(X = 0):
yl2 <- dpois(0, lambda = 3)

# Tõenäosus, et ööpäeva jooskul juhtub mitte rohkem kui 2 liiklusõnnetust, P(X <= 2): 
yl3 <- ppois(2, lambda = 3)

# Tõenäosus, et ööpäeva jooksul juhtub vähemalt 5 liiklusõnnetust, P(X >= 5) = P(X > 4):
yl4 <- ppois(4, lambda = 3, lower.tail = FALSE)

```

*** =sct
```{r}

# submission correctness tests

test_object("yl2", undefined_msg = NULL, incorrect_msg = "Kas kasutasid funktsiooni `dpois()`, et leida $P(X = 0)$?")
test_object("yl3", undefined_msg = NULL, incorrect_msg = "Kas kasutasid funktsiooni `ppois()`, et leida $P(X <= 2)$?")
test_object("yl4", undefined_msg = NULL, incorrect_msg = "Kas kasutasid funktsiooni `ppois()`, et leida $P(X > 4)$ ja argumenti `lower.tail = FALSE`?")

# test if the students code produces an error
test_error()

# Final message the student will see upon completing the exercise
success_msg("Võrratu! Kolm diskreetset jaotust on nüüd selged!")

```

--- type:NormalExercise lang:r xp:100 skills:1 key:71dbad57bd
## Andmete visualiseerimine

Oskad juba leida tõenäosusi $P(X=k)$ binoom-, geomeetrilise ja Poissoni jaotuse korral.  Sageli on mugav esitada jaotust ka graafiku abil (näiteks saab graafiku abil leida suurima tõenäosusega väärtust, kas jaotus on üks tipp või mitu, kas jaotus on sümmeetriline jne).

Põhiline funktsioon jooniste tegemiseks on `plot()`, millel on väga palju argmente. Neid saad uurida käsuga `help(plot)` või `?plot`. Siin läheb vaja järgmisi argumente:

* `x` ja `y` -- koordinaatide vektorid,
* `main = ` -- graafiku pealkiri jutumärkide vahel,
* `xlab = ` ja `ylab = ` -- vastavalt *x* ja *y* telgede nimed jutumärkide vahel,
* `type = h` -- (sõnast *histogram*) vertikaalsete joonte tegemiseks,
* `col = "red"` -- võimalik on muuta joonte värvi.

*** =instructions
1. Tõenäosus, et ööpäeva jooksul juhtub linnas *T* täpselt 1 liiklusõnnetus, on juba leitud (muutuja `yl1`). Uuri!
2. Leia tõenäosus, et ööpäeva jooksul ei juhtu ühtegi õnnetust, $P(X = 0)$, omista vastus muutujale `yl2`.
3. Leia tõenäosus, et ööpäeva jooskul juhtub mitte rohkem kui 2 liiklusõnnetust, $P(X\leq 2)$, omista muutujale `yl3`.
4. Leia tõenäosus, et ööpäeva jooksul juhtub vähemalt 5 liiklusõnnetust, $P(X\geq 5)$, omista muutujale `yl4`.

*** =hint
Viimast ülesannet saab lahendada kahel viisil:
1. vastandsündmuse tõenäosuse kaudu: $P(X\geq 5) = 1 - P(X\leq 5)$, kus viimase tõenäosuse leidmiseks kasutada funktsiooni `ppois()`;
2. funktsiooni `ppois()` ja argumendi `lower.tail = FALSE` abil. Arvesta, et selle abil saab leida $P(X > x)$.

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Olgu X liiklusõnnetuste arv ööpäevas linnas T.

# Tõenäosus, et ööpäeva jooksul juhtub linnas täpselt 1 liiklusõnnetus:
yl1 <- dpois(1, lambda = 3)

# Tõenäosus, et ööpäeva jooksul ei juhtu ühtegi õnnetust, P(X = 0):
yl2 <- 

# Tõenäosus, et ööpäeva jooskul juhtub mitte rohkem kui 2 liiklusõnnetust, P(X <= 2): 
yl3 <-

# Tõenäosus, et ööpäeva jooksul juhtub vähemalt 5 liiklusõnnetust, P(X >= 5) = P(X > 4):
yl4 <- 

```

*** =solution
```{r}
# Olgu X liiklusõnnetuste arv ööpäevas linnas T.

# Tõenäosus, et ööpäeva jooksul juhtub linnas täpselt 1 liiklusõnnetus:
yl1 <- dpois(1, lambda = 3)

# Tõenäosus, et ööpäeva jooksul ei juhtu ühtegi õnnetust, P(X = 0):
yl2 <- dpois(0, lambda = 3)

# Tõenäosus, et ööpäeva jooskul juhtub mitte rohkem kui 2 liiklusõnnetust, P(X <= 2): 
yl3 <- ppois(2, lambda = 3)

# Tõenäosus, et ööpäeva jooksul juhtub vähemalt 5 liiklusõnnetust, P(X >= 5) = P(X > 4):
yl4 <- ppois(4, lambda = 3, lower.tail = FALSE)

```

*** =sct
```{r}

# submission correctness tests

test_object("yl2", undefined_msg = NULL, incorrect_msg = "Kas kasutasid funktsiooni `dpois()`, et leida $P(X = 0)$?")
test_object("yl3", undefined_msg = NULL, incorrect_msg = "Kas kasutasid funktsiooni `ppois()`, et leida $P(X <= 2)$?")
test_object("yl4", undefined_msg = NULL, incorrect_msg = "Kas kasutasid funktsiooni `ppois()`, et leida $P(X > 4)$ ja argumenti `lower.tail = FALSE`?")

# test if the students code produces an error
test_error()

# Final message the student will see upon completing the exercise
success_msg("Võrratu! Kolm diskreetset jaotust on nüüd selged!")

```
