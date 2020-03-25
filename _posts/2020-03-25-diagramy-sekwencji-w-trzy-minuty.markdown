---
layout: post
title:  "Diagramy sekwencji w trzy minuty"
author: Bartłomiej Kotyra
date:   2020-03-25 17:00:00 +0100
categories: uml
---
Jednym z bardziej istotnych narzędzi należących do UML są diagramy sekwencji.

Diagramy sekwencji należą do grupy **diagramów interakcji**. Jak można wywnioskować z tej nazwy, ich przeznaczeniem jest modelowanie **interakcji pomiędzy elementami systemu**.

Diagramy sekwencji obrazują w jaki sposób poszczególne części systemu **komunikują się ze sobą**. W kontekście programowania obiektowego, mówiąc o komunikacji zazwyczaj mamy na myśli **wywoływanie metod** jednego obiektu przez drugi. Należy jednak od razu zaznaczyć, że nie jest to jedyny sposób wykorzystania tych diagramów (choć prawdopodobnie najczęściej spotykany).

**Uczestnicy interakcji** są przedstawiani na diagramie za pomocą **prostokątów**. W najprostszej formie każdy z prostokątów zawiera opis w postaci **nazwa obiektu : nazwa klasy**. Nazwa obiektu może zostać pominięta (zazwyczaj mamy wtedy na myśli dowolny obiekt tej klasy).

<center><img src="/images/diagram_sekwencji_1.png"></center>

Każdy z uczestników posiada tzw. **linię życia**. Jest to pionowa, przerywana linia obrazująca czas istnienia danego obiektu. Należy mieć na uwadze, że ma diagramach sekwencji czas płynie "do dołu".

Czasami linia życia jest zakończona znakiem X, symbolizującym koniec istnienia danego obiektu. Jest to jednak opcjonalne - wszystko zależy od tego, co chcemy przedstawić na diagramie i co w danym kontekście jest istotne.

Esencją diagramów sekwencji jest komunikacja między obiektami. Komunikaty mają postać **strzałek między liniami życia**.

<center><img src="/images/diagram_sekwencji_2.png"></center>

W kontekście programowania obiektowego najważniejszym rodzajem komunikatu jest **wywołanie metody**. Na diagramie ma to postać strzałki z wypełnionym grotem, biegnącej od linii życia obiektu wywołującego metodę, do linii życia obiektu, na którym metoda jest wywoływana. Z reguły tuż nad strzałką umieszcza się nazwę wywoływanej metody (opcjonalnie z przekazywanymi argumentami, jeżeli są istotne).

Wąskie, pionowe prostokąty umieszczane na liniach życia obrazują czas wykonywania metody.

Czasami istotne jest zaznaczenie wyniku zwracanego przez wywołaną metodę. Zwrócenie wartości oznacza się przerywaną strzałką z otwartym grotem. Jej kierunek jest przeciwny do kierunku strzałki wywołania metody. Jednak same strzałki nie mówią nam zbyt wiele, dlatego zwykle umieszcza się przy nich opisy wyjaśniające, co jest wynikiem zwracanym przez daną metodę.

<center><img src="/images/diagram_sekwencji_3.png"></center>

Diagramy powinny być **krótkie i przejrzyste**. Każdy diagram powinien obrazować sposób działania pojedynczej rzeczy w danym systemie. Zdecydowanie lepiej przygotować wiele krótszych, czytelnych diagramów, niż próbować przedstawić działanie całego systemu na jednym.

Diagramy sekwencji świetnie uzupełniają inne narzędzia, których zadaniem jest obrazowanie statycznej struktury systemu (np. diagramy klas, przedstawiające strukturę klas i powiązania między nimi). Pewne aspekty działania systemu, takie jak kolejność wywołań metod z danej klasy, raczej trudno przedstawić na statycznych diagramach. Sam diagram klas mógłby okazać się niewystarczający, aby jednoznacznie wyrazić naszą wizję systemu. Diagramy sekwencji rozwiązują ten problem.

Należy pamiętać, że diagramy UML mają przede wszystkim **pomagać w komunikowaniu idei**. Modelując działanie systemu warto przemyśleć co podnosi ich wartość i poprawia czytelność, a co stanowi zbędne informacje, które można pominąć.
