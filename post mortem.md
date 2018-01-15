
# DAWID CICHOŃ 156408 MAZE

## Informacje o wymiarach
Mapa 2500px 2500px
Gracz 50px 50px
Komórka 100px 100px


## 1. Mapa
Mapa może generować się nieprawidłowo w miejscach, które są na jej skraju. Dzieje się tak ponieważ algorytm jest dobry w labiryntach teoretycznie nieskończonych. 

Zapętlenie się labiryntu mogłoby rozwiązać problem. Problem ten czasami może uniemożliwić przejście gry.

## 2. Sterowanie.
Ze względu na zaokrąglenia sterowanie nie jest do końca przyjemne. Występują również graficzne błędy, a w skrajnych przypadkach można zablokować postać w ścianie. 

Próbowałem zaokrąglać pozycje w niektórych miejscach w górę ale niestety to wywołało inne błędy, które całkowicie uniemożliwiły mi poruszanie postaciom. Wróciłem do bazowe wersji sterowania i dodałem 10 pikseli w niektórych miejscach. Wygląda to lepiej, ale ostatecznie dalej jest nieidealne.

![Postać zablokowana w ścianie](img/md1.png?raw=true "Postać zablokowana w ścianie")

## 2a.
Informacje o tym, który klawisz jest wciśnięty pobieram przy użyciu onKeyDown(), które zagnieżdżone jest w tagu body. Był to spory błąd, ponieważ funckja dostaje sprzeczne informacje. Wywołuje to efekt Skakania po ekranie. Dobrym rozwiązaniem byłoby stworzenie funkcji, która pobiera informacje o tym czy klawisz został wciśnięty i sprawdza moment, w którym klawisz został puszczony. Błąd ten uniemożliwia też wciśnięcie dwóch klawiszy na raz, oraz przerywa poruszanie po wciśnięciu dowolnego klawisza.

## 3. Generowanie labiryntu. 
Do generowania labiryntu użyłem automatu komórkowego. Zaczynając od środka labiryntu losowo usuwa ściany działowe między nieaktywnymi jeszcze 

komórkami. Jeżeli proces się zakończy, a algorytm znajdzie komórki nie połaczone w żaden sposób z innymi komórkami to zaczyna losowo usuwać ściany. Na sam koniec algorytm generuje pustą przestrzeń, na której spawnuje się postać gracza.

## 4. Grafika
Grafiki pobrałem z internetu. Nie tworzyłem swoich ponieważ nie miało to znaczenia w projekcie.

## 5. Elementy blokowe
Całą grę stworzyłem na elementach blokowych, co było błędem (z perspektywy optymalizacji). Lepszym rozwiązaniem byłoby napisanie gry przy użyciu canvas. Ponadto elementy, których na ekranie nie widać dalej poruszają się po za krawędziom ekranu. Sprawia to, że gra jest niezoptymalizowana.

## 6. IE
Internet explorer nie daje sobie rady z grą. Dzieje się tak ponieważ nie dopisałem odpowiednich prefixów w CSS.

## 7. Zapisywanie
Zapisywanie gry odbywa się przy użyciu local.storage. Uważam, że jest to całkiem dobre rozwiązanie, ale ma swoje wady. Największą wadą jest fakt, że wynik znajduje się tylko na jednym komputerze i nie przesyła się na serwer. Rekordy uzyskane w grze są unikalne dla każdego komputera. Dobrym rozwiązaniem byłoby skorzystanie z bazy danych MySQL.
