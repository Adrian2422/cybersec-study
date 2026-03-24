Link: [Level 5](https://overthewire.org/wargames/bandit/bandit5.html)

Zadaniem jest znalezienie hasła zlokalizowanego w jedynym "human-readable" pliku

1. Listuję strukturę `find`
2. Widzę katalog `inhere` z wieloma plikami. 
3. przechodzę `cd inhere`
4. Sprawdzanie plików po kolei byłoby czasochłonne, więc szukam odpowiedniego narzędzia
5. Po przeczytaniu manuala `find` postanawiam go użyć podając mu dodatkową akcję `find -maxdepth 1 -exec file {} +;` 
	1. `-maxdepth 1` by ograniczyć głębokość (w razie jakby katalog był rabbit-hole)
	2. `-exec file {} +` by wykonać na nich `file`
	3. `{}` to placeholder, gdzie `find` wstawia nazwy plików
	4. `+` to znak kończący, który powoduje, że zostaje zbudowana jedna długa linia poleceń ze wszystkich znalezionych plików zamiast wiele mniejszych co przekłada się na wyższą wydajność
6. Pojawia się lista plików oraz ich typ, widzę jeden plik który jest "human-readable" (ASCII text)
7. Otwieram go, odczytuję i zapisuję hasło