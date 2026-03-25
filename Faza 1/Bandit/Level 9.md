Link: [Level 9](https://overthewire.org/wargames/bandit/bandit9.html)

Zadaniem jest znalezienie hasła w pliku `data.txt` i jest to unikalna linia

1. Zadanie sugeruje by szukać unikalnej linii, więc trzeba odsiać duplikaty
2. używam `sort -u` ale okazuje się, że zwraca on po jednym wystąpieniu z każdego więc zmieniam taktykę i teraz policzę wystąpienia poszczególnych wyrazów a potem wyfiltruję ten z jednym wystąpieniem
3. Zmiana koncepcji: najpierw sortujemy tak by `uniq` mogło policzyć wystąpienia a potem grep filtruje regexem konkretne wystąpienie
4. Odczytuję hasło i zapisuję