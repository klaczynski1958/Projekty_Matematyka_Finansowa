# Quantitative Finance & Risk Analysis Portfolio

Witaj w moim repozytorium! Znajdują się tutaj projekty z zakresu analizy danych rynkowych, inżynierii finansowej oraz kwantyfikacji ryzyka, zrealizowane w języku Python. Główne obszary moich zainteresowań to modelowanie ryzyka rynkowego, analiza procesów stochastycznych oraz budowa narzędzi dla rynków finansowych.

Poniżej znajdują się krótkie opisy zrealizowanych przeze mnie analiz:

## 📊 Projekt 1: Analiza stóp zwrotu i macierz korelacji (Sektor Bankowy)
**Plik:** `Zadanie1.ipynb`

Projekt skupia się na przygotowaniu i weryfikacji surowych danych rynkowych pod kątem modelowania ryzyka. Przeanalizowałem zachowanie 5 największych spółek z polskiego sektora bankowego na przestrzeni 2 lat.
* **Zakres prac:** Pobieranie danych przez API (`yfinance`), walidacja braków danych (świadoma rezygnacja z metody `ffill` w celu uniknięcia fałszowania zmienności), kalkulacja logarytmicznych stóp zwrotu oraz detekcja wartości odstających (tzw. "grubych ogonów").
* **Wnioski biznesowe:** Zbudowałem i zinterpretowałem macierz korelacji Pearsona (oraz Heatmapę). Udowodniłem wysoce homogeniczną strukturę sektora (korelacje rzędu 0.76 - 0.87), co stanowi istotną informację o ryzyku systemowym uniemożliwiającym pełną dywersyfikację portfela.

## 📉 Projekt 2: Szacowanie Value at Risk (VaR)
**Plik:** `Zadanie2.ipynb`

Celem projektu była wycena potencjalnych strat dwóch wariantów portfeli inwestycyjnych (równoważonego oraz alokowanego losowo) przy użyciu miary Value at Risk (VaR) dla poziomów ufności 95% i 99%.
* **Zakres prac:** Poprawna agregacja zwrotów (wyliczenie prostych stóp zwrotu dla aktywów, zastosowanie średniej ważonej dla portfela i finalna konwersja na stopy logarytmiczne). Implementacja VaR dwoma podejściami.
* **Wnioski biznesowe:** Porównałem wyniki **metody historycznej** z **metodą parametryczną**. Przeprowadziłem merytoryczną krytykę metody parametrycznej, wykazując, że w warunkach rynkowej hossy wymusza ona na danych symetryczny rozkład normalny, co prowadzi do sztucznego przeniesienia historycznej zmienności (wywołanej wzrostami) na lewy ogon rozkładu i przeszacowania ryzyka strat.

## 📈 Projekt 3: Wycena opcji (Black-Scholes vs Monte Carlo) i "Greki"
**Plik:** `Zadanie3.ipynb`

Zaawansowany projekt z zakresu wyceny instrumentów pochodnych (Opcje Europejskie) na akcje PKO BP, łączący podejście analityczne ze stochastycznym.
* **Zakres prac:** Implementacja teoretycznego modelu **Blacka-Scholesa** jako benchmarku rynkowego. Zbudowanie od podstaw numerycznej symulacji **Monte Carlo** wykorzystującej zredukowany Geometryczny Ruch Browna (GBM) dla 10 000 oraz 50 000 ścieżek cenowych. Wektoryzacja obliczeń z użyciem `numpy` dla maksymalizacji wydajności.
* **Wnioski biznesowe:** Przeanalizowałem zbieżność wyników MC z modelem analitycznym w kontekście Prawa Wielkich Liczb. Wyznaczyłem parametry wrażliwości ryzyka (tzw. **Greki**: Delta, Gamma, Vega, Theta), interpretując ich wartości bezpośrednio pod kątem zarządzania portfelem zabezpieczającym (Delta Hedging) oraz ekspozycji na zmienność.
