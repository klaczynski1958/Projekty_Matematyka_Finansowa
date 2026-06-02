# Optymalizacja Portfela Inwestycyjnego 📈

### Projekt z zakresu Zarządzania Ryzykiem i Matematyki Finansowej

Ten projekt to analityczne podejście do rynków finansowych. Głównym celem jest wyznaczenie optymalnych wag aktywów w portfelu inwestycyjnym, aby zmaksymalizować oczekiwaną stopę zwrotu przy zadanym poziomie ryzyka (lub zminimalizować ryzyko dla oczekiwanej stopy zwrotu).

---

## 🎯 Cel Biznesowy i Naukowy
W zarządzaniu ryzykiem rynkowym kluczowa jest odpowiednia dywersyfikacja. Projekt ten implementuje założenia **Nowoczesnej Teorii Portfelowej (Modern Portfolio Theory - MPT) Harry'ego Markowitza**. 

Model analizuje historyczne notowania giełdowe wybranych aktywów w celu:
* Obliczenia historycznych stóp zwrotu oraz ryzyka (odchylenia standardowego / zmienności).
* Wyznaczenia macierzy kowariancji, aby zbadać korelację między aktywami.
* Znalezienia **Granicy Efektywnej (Efficient Frontier)**.
* Wyznaczenia portfela o najwyższym wskaźniku Sharpe'a (Maksymalizacja premii za ryzyko).

---

## 🛠️ Wykorzystane Technologie
* **Język:** Python
* **Analiza Danych i Obliczenia:** `pandas`, `NumPy`
* **Wizualizacja Danych:** `matplotlib`, `seaborn` (do wizualizacji Granicy Efektywnej i macierzy korelacji)
* **Pobieranie Danych:** [np. `yfinance` - wpisz jeśli pobierałeś dane z Yahoo Finance, jeśli miałeś z pliku CSV, napisz po prostu "Dane historyczne z pliku CSV"]

---

## 📊 Metodologia Analityczna
1. **Pre-processing danych:** Oczyszczenie historycznych szeregów czasowych i wyrównanie braków w danych.
2. **Kalkulacja zwrotów i ryzyka:** Przekształcenie cen zamknięcia na dzienne/miesięczne logarytmiczne stopy zwrotu.
3. **Symulacja Monte Carlo:** Wygenerowanie [np. 10 000] losowych portfeli w celu zobrazowania możliwych kombinacji ryzyka i zwrotu.
4. **Optymalizacja matematyczna:** Wyznaczenie konkretnych wag procentowych dla każdego aktywa w portfelu optymalnym.

---

## ⚖️ Prawa autorskie / Copyright
**Copyright (c) 2026 [Twoje Imię i Nazwisko]. Wszelkie prawa zastrzeżone.**

*Kod oraz wyniki analizy znajdujące się w tym repozytorium stanowią część portfolio projektowego i zostały udostępnione publicznie wyłącznie w celach poglądowych. Kopiowanie, modyfikowanie, dystrybucja lub wykorzystanie komercyjne bez wyraźnej zgody autora jest zabronione.*
