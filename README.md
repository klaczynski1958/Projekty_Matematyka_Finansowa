# 📈 Quantitative Finance & Risk Analysis Portfolio

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)
![SAS](https://img.shields.io/badge/SAS-0072C6?style=for-the-badge&logo=sas&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)

## 📌 O repozytorium
Witaj! To repozytorium to moje analityczne portfolio projektowe. Znajdziesz tutaj zrealizowane przeze mnie projekty z zakresu **analizy danych rynkowych, inżynierii finansowej, oceny ryzyka oraz data science w optymalizacji kosztów**. 

Moje główne obszary zainteresowań to modelowanie ryzyka rynkowego, analiza procesów stochastycznych oraz budowa predykcyjnych narzędzi biznesowych.

---

## 🚀 Zrealizowane projekty

| Nazwa Projektu | Krótki opis | Technologie | Status |
| :--- | :--- | :--- | :---: |
| **[1. Analiza Stóp Zwrotu i Ryzyko Systemowe (Sektor Bankowy)](#)**<br>`Zadanie1.ipynb` | Pobieranie danych giełdowych przez API (`yfinance`), kalkulacja logarytmicznych stóp zwrotu i detekcja "grubych ogonów". Budowa macierzy korelacji Pearsona dowodzącej homogenicznej struktury sektora. | Python | ✅ Gotowe |
| **[2. Szacowanie Value at Risk (VaR)](#)**<br>`Zadanie2.ipynb` | Wycena potencjalnych strat dwóch wariantów portfeli dla poziomów ufności 95% i 99%. Porównanie VaR metodą historyczną oraz parametryczną z krytyką wpływu hossy na przeszacowanie ryzyka. | Python | ✅ Gotowe |
| **[3. Wycena Opcji i "Greki" (Black-Scholes vs Monte Carlo)](#)**<br>`Zadanie3.ipynb` | Implementacja analitycznego modelu Blacka-Scholesa oraz numerycznej symulacji Monte Carlo (GBM na 50k ścieżek). Wyznaczenie i interpretacja Greków dla strategii Delta Hedging. | Python, numpy | ✅ Gotowe |
| **[4. Detekcja Ryzyka Udaru vs Koszty NFZ (Data Science)](#)**<br>`UDAR_PROJEKT.pdf` | Model ML optymalizujący asymetryczne koszty medyczne. Inżynieria cech (eliminacja VIF), Cost-Complexity Pruning i symulacja Bootstrap z maksymalizacją czułości (97%) na zadanym progu odcięcia. | Python, scikit-learn | ✅ Gotowe |

*(Powyższe linki w nazwach projektów w tabeli podepnij pod swoje odpowiednie pliki, wymieniając po prostu znaczek `#` na ścieżkę do pliku w Twoim repozytorium).*

---

## 🧠 Więcej o projekcie: Detekcja Ryzyka Udaru i Koszty NFZ

Większość standardowych modeli ML skupia się na ogólnej dokładności (Accuracy). Ten projekt przyjmuje perspektywę **asymetrycznych kosztów biznesowo-medycznych**. Model zakłada, że przeoczenie pacjenta (koszt rehabilitacji i renty - 150 000 PLN) jest drastycznie wyższe niż prewencyjne badanie (rezonans - 2 000 PLN). 

<details>
<summary><b>Kliknij, aby rozwinąć szczegóły zastosowanej metodologii</b></summary>

**1. Inżynieria Cech i Eliminacja Współliniowości (VIF)**
Stworzono zmienne krzyżowe (fuzje, np. `age_sq`, `age_gluc`). Zastosowano Variance Inflation Factor (VIF) usuwając zmienne o VIF > 10, by zapobiec problemowi Singular Matrix.

**2. Modele i Cost-Complexity Pruning (CCP)**
Zastosowano m.in. Drzewa Decyzyjne. Zrezygnowano z przycinania pod kątem "Accuracy" na rzecz algorytmu szukającego hiperparametru stabilności diagnostycznej (maksymalizacja AUC).

**3. Optymalizacja Progu Decyzyjnego**
Zamiast standardowego 50%, użyto *Grid Search* symulując budżet dla progów 1%-99%. Wyznaczono optymalny próg decyzyjny (np. 8.9%), poświęcając Swoistość na rzecz Czułości (powyżej 97%).

**4. Weryfikacja Niezawodności (Bootstrap)**
Dla weryfikacji w kontekście Prawa Wielkich Liczb wykonano symulację losowania ze zwracaniem na 1000 iteracji, wyznaczając 95% przedziały ufności dla metryk.
</details>

---

## ⚖️ Prawa autorskie / Copyright
**Copyright (c) 2026 Kacper Łączyński. Wszelkie prawa zastrzeżone.**

*Kod oraz wyniki analizy znajdujące się w tym repozytorium stanowią część portfolio projektowego i zostały udostępnione publicznie wyłącznie w celach poglądowych. Kopiowanie, modyfikowanie, dystrybucja lub wykorzystanie komercyjne bez wyraźnej zgody autora jest zabronione.*
