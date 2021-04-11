---
layout: post
title:  "Relacje między klasami"
author: Bartłomiej Kotyra
date:   2021-04-11 21:00:00 +0100
categories: uml
---

Diagramy klas w UML pozwalają na wyrażanie relacji między poszczególnymi klasami. Zaznacza się je za pomocą odpowiednich strzałek.

Istotna jest umiejętność rozróżnienia tych symboli. Każda ze strzałek ma swoje własne, specyficzne znaczenie. Stosowanie ich w niewłaściwy sposób wprowadza sporo zamieszania i utrudnia (lub nawet uniemożliwia) właściwą interpretację diagramu.

---

# Dziedziczenie

Najbardziej oczywistą dla osób poznających UML jest relacja **dziedziczenia** (generalizacji). Do jej zaznaczenia wykorzystujemy **strzałkę z ciągłą linią i niezamalowanym, trójkątnym grotem**. Strzałka powinna być **skierowana w stronę klasy bazowej**. Dobrą praktyką jest umieszczanie klas pochodnych poniżej klasy bazowej.

<center><img src="/images/dziedziczenie.png"></center>

---

# Realizacja (interfejsu)

Drugi, dość podobny przypadek, dotyczy **realizacji interfejsu**. Strzałka również ma **trójkątny, niezamalowany grot**, ale **linia jest przerywana**. Grot znajduje się **po stronie interfejsu**.

<center><img src="/images/realizacja.png"></center>

---

# Kompozycja

Kolejny rodzaj relacji to **kompozycja**. Tutaj mówimy o sytuacji, w której jedna z klas stanowi nieodłączną część składową innej. Czas życia obiektów obu klas jest ściśle powiązany - obiekty są tworzone i usuwane w tym samym czasie (stworzenie całości wymaga stworzenia części składowej; usunięcie całości z pamięci pociąga za sobą usunięcie części składowej). Kompozycję oznacza się za pomocą **ciągłej linii z zamalowanym grotem w kształcie rombu**. Grot znajduje się po stronie klasy reprezentującej całość.

<center><img src="/images/kompozycja.png"></center>

---

# Agregacja

Podobną, ale nieco "luźniejszą" relacją jest **agregacja**. Również mówimy tutaj o formie relacji części do całości, jednak na znacznie luźniejszych zasadach. Obiekty obu klas mogą istnieć niezależnie od siebie. W praktyce zwykle wiąże się to z sytuacją, w której jedna z klas zawiera modyfikowalną kolekcję obiektów innej klasy. Agregację oznaczamy **ciągłą linią z pustym rombem** po stronie całości.

<center><img src="/images/agregacja.png"></center>

---

# Powiązanie

Następny rodzaj relacji to **powiązanie**. Na poziomie implementacji określa się tak głównie sytuacje, w których jedna z klas zawiera w swoich polach referencję/wskaźnik na obiekt innej klasy. Powiązania mogą być jedno- lub dwustronne. Oznacza się je **ciągłą linią z otwartym grotem** wskazującym na kierunek powiązania (lub po prostu linią w przypadku powiązania dwustronnego).

<center><img src="/images/powiazanie.png"></center>

---

# Zależność

**Zależność** między klasami dotyczy scenariusza, w którym jedna z klas w jakiś sposób używa obiektów innej klasy. Z reguły obiekty nie pamiętają o sobie (nie przechowują wzajemnych referencji, jak ma to miejsce w przypadku powiązania), a współpraca odbywa się jedynie na poziomie metod (np. metoda jednej z klas przyjmuje w argumencie referencję na obiekt innej klasy). Zależność oznacza się **przerywaną linią z otwartym grotem**. Grot powinien znajdować się po stronie klasy niezależnej (tej, której kod nie odwołuje się do drugiej klasy).

<center><img src="/images/zaleznosc.png"></center>

---
