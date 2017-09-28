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



---
## <<<New Exercise>>>

```yaml
type: NormalExercise
key: 0f4ad4d427
lang: r
xp: 100
skills: 1
```


`@instructions`
dcds $A$ .

aefwsf $n$.

sdadwrerg $P=k$

`@hint`

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}

```

`@solution`
```{r}

```

`@sct`
```{r}

```
