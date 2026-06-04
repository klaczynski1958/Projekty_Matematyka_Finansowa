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


# 🧠 Detekcja Ryzyka Udaru i Optymalizacja Kosztów Asymetrycznych (NFZ)

### Projekt z zakresu Data Science, Statystyki Medycznej i Finansów Ochrony Zdrowia

Większość standardowych modeli uczenia maszynowego skupia się na maksymalizacji ogólnej dokładności (Accuracy). Ten projekt przyjmuje jednak zupełnie inną perspektywę – **perspektywę asymetrycznych kosztów biznesowo-medycznych**. 

Celem projektu jest stworzenie modelu predykcyjnego oceniającego ryzyko udaru mózgu, którego głównym zadaniem jest **minimalizacja strat budżetowych państwa (NFZ)**. W modelu założono, że koszt przeoczenia chorych pacjentów (Fałszywie Negatywni – 150 000 PLN z tytułu rehabilitacji i renty) jest drastycznie wyższy niż koszt prewencyjnego badania zdrowych pacjentów (Fałszywie Pozytywni – 2 000 PLN za rezonans magnetyczny).

**Plik:** `UDAR_PROJEKT.pdf`

---

## 🚀 Przebieg Projektu i Zastosowana Metodologia

Aby osiągnąć optymalny punkt pracy modelu, przeprowadzono kompleksowy proces analityczny, składający się z następujących etapów:

### 1. Inżynieria Cech i Eliminacja Współliniowości (VIF)
Stworzono nowe zmienne krzyżowe (tzw. fuzje, np. wiek podniesiony do kwadratu `age_sq`, czy interakcja wieku z poziomem glukozy `age_gluc`). Następnie, aby uniknąć zaburzeń stabilności matematycznej modelu (problem Singular Matrix), zastosowano wskaźnik **Variance Inflation Factor (VIF)**. Model automatycznie usunął skrajnie skorelowane zmienne (VIF > 10), pozostawiając jedynie te, które wnosiły unikalną wartość informacyjną.

### 2. Zaawansowane Modele i Cost-Complexity Pruning (CCP)
Do analizy wybrano algorytmy takie jak Regresja Logistyczna (z karą L2) oraz Drzewa Decyzyjne. W przypadku drzew zrezygnowano z domyślnego przycinania pod kątem "Accuracy". Zamiast tego zaimplementowano algorytm poszukujący optymalnego hiperparametru $\alpha$ pod kątem stabilności diagnostycznej – maksymalizując pole pod krzywą **ROC (metryka AUC)**.

### 3. Optymalizacja Progu Decyzyjnego (Thresholding)
Zamiast standardowego progu klasyfikacji (50%), zastosowano siatkę poszukiwań (*Grid Search*) do symulacji budżetowej każdego możliwego progu od 1% do 99%. Model samodzielnie zidentyfikował optymalny punkt odcięcia (np. próg na poziomie 8.9%), który generował najmniejszy całkowity koszt dla systemu opieki zdrowotnej.
* **Skutek:** Celowo poświęcono Swoistość na rzecz ekstremalnie wysokiej **Czułości (powyżej 97%)**. Model woli wysłać kilku zdrowych pacjentów na niepotrzebne badania, aby mieć pewność, że nie przeoczy żadnego pacjenta z grupy najwyższego ryzyka.

### 4. Weryfikacja Niezawodności (Metoda Bootstrap)
Aby dowieść stabilności modelu i odnieść się do Prawa Wielkich Liczb, zaimplementowano symulację losowania ze zwracaniem (**Bootstrap**). Na podstawie 1000 iteracji wygenerowano wirtualne próby pacjentów, wyznaczając 95-procentowe przedziały ufności (Confidence Intervals) dla kluczowych metryk (AUC oraz Czułości).

---

## 🛠️ Wykorzystane Technologie i Narzędzia
* **Język programowania:** Python (kody stworzone przy pomocy AI)
* **Czyszczenie i manipulacja danymi:** `pandas`, `numpy`
* **Uczenie maszynowe:** `scikit-learn` (LogisticRegression, DecisionTreeClassifier, standardyzacja danych, metryki oceny)
* **Wizualizacja:** `matplotlib`, `seaborn` (Krzywe ROC, Macierze Pomyłek)
* **Walidacja statystyczna:** `resample` (Bootstrap)
  

---

## ⚖️ Prawa autorskie / Copyright
**Copyright (c) 2026 Kacper Łączyński. Wszelkie prawa zastrzeżone.**

*Kod oraz wyniki analizy znajdujące się w tym repozytorium stanowią część portfolio projektowego i zostały udostępnione publicznie wyłącznie w celach poglądowych. Kopiowanie, modyfikowanie, dystrybucja lub wykorzystanie komercyjne bez wyraźnej zgody autora jest zabronione.*

