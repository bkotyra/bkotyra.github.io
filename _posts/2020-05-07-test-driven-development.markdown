---
layout: post
title:  "Wprowadzenie do Test-Driven Development"
author: Bartłomiej Kotyra
date:   2020-05-07 15:00:00 +0100
categories: tdd
---

Test-Driven Development stanowi specyficzną technikę wytwarzania oprogramowania, zaliczaną do metodyk zwinnych (agile). Jak wynika z samej nazwy, proces tworzenia oprogramowania jest w tym podejściu sterowany / kierowany testami.


# Kilka słów o historii

TDD wywodzi się z metodyki Programowania Ekstremalnego (XP) - zbioru 29 reguł dotyczących prowadzenia projektów programistycznych, opublikowanego pierwotnie w 1999 roku. Jedną z najważniejszych reguł XP było kodowanie testów jednostkowych **przed** rozpoczęciem faktycznej implementacji ("test first"). Ta idea stanowi podstawę Test-Driven Development.

Za wynalazcę techniki TDD uznawany jest Kent Beck. On sam mówi jednak raczej o jej "ponownym odkryciu", powołując się na podobne koncepcje z literatury jeszcze z czasów taśm perforowanych. Jego książka "Test Driven Development: By Example", wydana w 2002 roku, stanowi pierwsze ujęcie współczesnego podejścia do tego zagadnienia.

Obecnie TDD stanowi samodzielną technikę (kontekst Programowania Ekstremalnego nie jest "obowiązkowy").


# Na czym polega TDD?

W najprostszym ujęciu, TDD koncentruje się na implementacji testów jednostkowych przed rozpoczęciem pisania kodu produkcyjnego. Czyli: najpierw opisujemy testami w jaki sposób kod (którego jeszcze nie ma) powinien działać, a dopiero potem faktycznie implementujemy daną funkcjonalność.

O ile idea wydaje się dość prosta, o tyle sposoby jej praktycznego zastosowania i wynikające z nich konsekwencje wcale nie muszą być oczywiste.

Na początku należałoby podkreślić, że wszelkie reguły i dobre praktyki dotyczące testów jednostkowych (i programowania w ogólności) nadal obowiązują. Kod testowy jest tak samo istotny jak kod produkcyjny - aby testy stanowiły rzeczywistą pomoc, a nie przeszkodę w rozwijaniu projektu, ważne jest implementowanie i utrzymywanie ich z zachowaniem ogólnie przyjętych standardów.

Testy jednostkowe powinny być możliwie proste i krótkie (co w naturalny sposób redukuje szanse na popełnienie błędu w samym teście). Nie powinniśmy zajmować się testowaniem szczegółów implementacyjnych, ani "na siłę" dążyć do stuprocentowego pokrycia kodu (łącznie z setterami, getterami itd.) - zamiast tego znacznie lepiej jest skoncentrować się na testowaniu zachowań, jakich oczekujemy od naszego systemu.


# Cykl "red / green / refactor"

Pojedynczy cykl techniki TDD składa się z trzech faz, powszechnie określanych jako "czerwone, zielone, refaktoryzacja".

Przystępując do implementacji nowego elementu systemu, powinniśmy rozpocząć od przygotowania testów. Oczywiście świeżo napisane testy nie będą kończyły się sukcesem (etap "czerwone") - mogą się nawet nie kompilować. Jest to całkowicie naturalne, ponieważ z reguły nie mamy jeszcze nawet implementacji, która będzie podlegała tym testom.

Etap negatywnych wyników zaimplementowanych testów stanowi swoisty mechanizm kontroli. Świeżo napisany test **powinien** nie przechodzić - w przeciwnym wypadku świadczyłoby to o błędach w samym teście.

Dopiero posiadając odpowiednie testy przystępujemy do implementacji kodu produkcyjnego. Z reguły celem tego etapu jest doprowadzenie do stanu, w którym testy zaczynają przechodzić (etap "zielone") możliwie krótką i prostą drogą. Rozwiązanie, które powstaje na tym etapie, zwykle nie jest najbardziej eleganckim z możliwych, ale nie należy się tym zbytnio przejmować - technika TDD przewiduje taki stan rzeczy.

Ostatnim etapem cyklu jest refaktoryzacja. Posiadamy poprawną implementację i przechodzące testy - czas zająć się doprowadzeniem kodu do odpowiednich standardów. Porządkujemy i oczyszczamy kod, usuwamy powtórzenia, ekstrahujemy metody - w zależności od potrzeb. Na tym etapie posiadane przez nas testy mają istotną wartość - po każdej zmianie możemy sprawdzić, czy nasz kod nadal jest poprawny (testy powinny cały czas przechodzić).

Uwaga: refaktoryzacja stanowi **obowiązkowy** element TDD. Pomijanie tego etapu jest traktowane jako błąd.

Ważne jest podkreślenie, że opisany cykl pracy powinien być **możliwie krótki**. Absolutnie nie chodzi tutaj o programowanie wyłącznie testów przez kilka dni, żeby potem siadać do implementacji nie pamiętając już o co chodziło w pierwszych testach.


# Dlaczego najpierw testy?

Idea TDD może budzić pewne zdziwienie - właściwie dlaczego należy zaczynać od testów? Ok, testy są ważne, ale co za różnica czy napiszemy je na przed, czy po implementacji?

Rzeczywiście różnica może wydawać się subtelna, ale w praktyce okazuje się wyjątkowo odczuwalna.

Pierwsza sprawa - rozpoczęcie od testów zmusza nas do przemyślenia implementowanej funkcjonalności **z perspektywy kodu, który będzie jej używał**. Pisząc testy patrzymy na nowy element systemu od strony kodu klienckiego. Jakie metody są nam potrzebne? Co powinny przyjmować, co powinny zwracać? Jak powinna wyglądać reakcja na nietypowe sytuacje? Zanim siądziemy do implementacji mamy już podjęte istotne decyzje, wpływające na jakość interfejsu nowego elementu. Pozwala to uniknąć częstej sytuacji, w której prostota korzystania z powstającej implementacji jest zaniedbywana. Siadamy do pisania kodu z jasną wizją tego, jak nasz nowy element będzie używany i tym samym czego oczekujemy od niego "z zewnątrz".

Kolejna ważna rzecz - TDD wymusza na nas pisanie kodu, który jest testowalny. Unikamy sytuacji, w której zaimplementowany element może i działa poprawnie, ale nie da się tego w stu procentach sprawdzić (a przynajmniej nie da się tego zrobić łatwo). Być może w trakcie pisania testów dojdziemy do wniosku, że bardzo przydałaby nam się pewna "pomocnicza" metoda, która znacznie ułatwi nam testowanie, a o której w ogóle nie pomyślelibyśmy zaczynając od implementacji. Albo inaczej zorganizujemy zależności między klasami, co pozwoli skorzystać z możliwości oferowanych przez mockowanie.

No i na koniec - zaczynanie od implementacji testów gwarantuje, że testy faktycznie powstaną. Jak często zdarzało się w praktyce, że testy miały zostać dodane na końcu cyklu, ale "nie było na to czasu"? No właśnie.


# Trzy prawa TDD

Robert Martin ("Uncle Bob"), w oparciu o swoją praktykę, sformułował trzy prawa Test-Driven Development. W wolnym tłumaczeniu:

1. Nie możesz pisać kodu produkcyjnego w innym celu niż doprowadzenie do przechodzenia testu.
2. Nie możesz pisać więcej kodu testującego niż jest potrzebne, żeby test nie przechodził; błąd kompilacji liczy się jako nieprzechodzący test.
3. Nie możesz pisać więcej kodu produkcyjnego niż jest wymagane, aby przejść jeden nieprzechodzący test.

Tym samym programista musi zacząć od kodu testującego. Druga reguła ogranicza sytuację, w której testy są pisane "dużymi porcjami" - w zasadzie kiedy tylko dochodzimy do sytuacji, w której test nie przechodzi, należy przerwać i zająć się kodem produkcyjnym. Jednak, zgodnie z trzecią regułą, kodu produkcyjnego należy napisać jedynie tyle, żeby test zaczął przechodzić.


# Konsekwencje

Praktyka pokazuje, że stosowanie TDD prowadzi do większej produktywności zespołu i krótszego czasu realizacji projektów. Co ciekawe, programiści konsekwentnie stosujący TDD twierdzą, że w zasadzie nie potrzebują korzystać z debuggerów.

W oczywisty sposób TDD prowadzi do szybszego wykrywania błędów popełnionych w kodzie. Wszyscy zdajemy sobie sprawę, że z późnym wykrywaniem błędów wiążą się wyższe koszty. W przypadku TDD czas od popełnienia do wykrycia błędu jest minimalny - błąd zostaje znaleziony przez programistę, który go popełnił, w zasadzie natychmiast (już na etapie implementowania danej funkcjonalności). Unikamy tym samym sytuacji, w której w sprawę zostaje dodatkowo zaangażowany tester odkrywający nasz błąd, albo, co gorsza, klient.

Testy pisane w zgodzie z metodyką TDD stanowią jednocześnie formę designu i dokumentacji naszego kodu. W celu zrozumienia danej funkcjonalności wystarczy sięgnąć do testów, stanowiących w gruncie rzeczy zestaw prostych przykładów jak z danego elementu można korzystać. W praktyce taka forma dokumentowania kodu okazuje się znacznie bardziej precyzyjna, niż typowa dokumentacja techniczna. Testy zawsze są aktualne - w przeciwnym wypadku by nie przechodziły. O tradycyjnej dokumentacji często nie można tego powiedzieć (nie oszukujmy się, nikt nie lubi pisać ani aktualizować dokumentacji...).

Generalnie TDD prowadzi do lepiej przemyślanego, lepiej zorganizowanego kodu. Technika może być stosowana zarówno przez pojedynczych programistów, jak i całe zespoły - jej wdrożenie nie wymaga szczególnie dużo czasu, a konsekwencje stają się odczuwalne bardzo szybko.

Klasycznym zarzutem wobec TDD jest wydłużenie czasu potrzebnego na implementację (o czas wymagany na napisanie testów). To samo dotyczy kwestii utrzymania - przy zmianach w kodzie produkcyjnym konieczna jest aktualizacja kodu testującego. Pisanie kodu bez testów jest rzeczywiście "szybsze", natomiast wiąże się z oczywistymi problemami, zwykle prowadzącymi ostatecznie do wydłużenia czasu projektu.
