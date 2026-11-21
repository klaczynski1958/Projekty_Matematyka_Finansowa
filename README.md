<div align="center">

# 📈 Quantitative Finance & Risk Analysis Portfolio

**Analiza danych rynkowych • Inżynieria finansowa • Ocena ryzyka • Data Science**

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white" alt="R" />
  <img src="https://img.shields.io/badge/SAS-0072C6?style=for-the-badge&logo=sas&logoColor=white" alt="SAS" />
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="SQL" />
  <img src="https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white" alt="Excel" />
</p>

<p>
  <a href="#-o-repozytorium">O repozytorium</a> •
  <a href="#-zrealizowane-projekty">Projekty</a> •
  <a href="#-case-study-detekcja-ryzyka-udaru-i-koszty-nfz">Case Study (ML)</a> •
  <a href="#-prawa-autorskie">Copyright</a>
</p>

</div>

---

## 📌 O repozytorium

Witaj! To repozytorium to moje analityczne portfolio projektowe. Znajdziesz tutaj zrealizowane przeze mnie projekty z zakresu **analizy danych rynkowych, inżynierii finansowej, oceny ryzyka oraz data science w optymalizacji kosztów**.

> Moje główne obszary zainteresowań to modelowanie ryzyka rynkowego, analiza procesów stochastycznych oraz budowa predykcyjnych narzędzi biznesowych.

---

## 🚀 Zrealizowane projekty

<!-- Zamień href="#" na właściwe ścieżki do plików w repozytorium, np. href="./Zadanie1.ipynb" -->
<table width="100%">
  <tr>
    <td width="50%" valign="top">
      <h3>📊 1. Analiza Stóp Zwrotu i Ryzyko Systemowe</h3>
      <p><b>Sektor Bankowy</b> • <a href="#"><code>Zadanie1.ipynb</code></a></p>
      <p>Pobieranie danych giełdowych przez API (<code>yfinance</code>), kalkulacja logarytmicznych stóp zwrotu i detekcja „grubych ogonów”. Budowa macierzy korelacji Pearsona dowodzącej homogenicznej struktury sektora.</p>
      <p><kbd>Python</kbd> <kbd>yfinance</kbd> &nbsp; | &nbsp; ✅ Gotowe</p>
    </td>
    <td width="50%" valign="top">
      <h3>📉 2. Szacowanie Value at Risk (VaR)</h3>
      <p><b>Ryzyko Portfelowe</b> • <a href="#"><code>Zadanie2.ipynb</code></a></p>
      <p>Wycena potencjalnych strat dwóch wariantów portfeli dla poziomów ufności 95% i 99%. Porównanie VaR metodą historyczną oraz parametryczną z krytyką wpływu hossy na przeszacowanie ryzyka.</p>
      <p><kbd>Python</kbd> <kbd>Statystyka</kbd> &nbsp; | &nbsp; ✅ Gotowe</p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>⚡ 3. Wycena Opcji i „Greki”</h3>
      <p><b>Black-Scholes vs Monte Carlo</b> • <a href="#"><code>Zadanie3.ipynb</code></a></p>
      <p>Implementacja analitycznego modelu Blacka-Scholesa oraz numerycznej symulacji Monte Carlo (GBM na 50k ścieżek). Wyznaczenie i interpretacja Greków dla strategii Delta Hedging.</p>
      <p><kbd>Python</kbd> <kbd>NumPy</kbd> &nbsp; | &nbsp; ✅ Gotowe</p>
    </td>
    <td width="50%" valign="top">
      <h3>🧠 4. Detekcja Ryzyka Udaru vs Koszty NFZ</h3>
      <p><b>Data Science & ML</b> • <a href="#"><code>UDAR_PROJEKT.pdf</code></a></p>
      <p>Model ML optymalizujący asymetryczne koszty medyczne. Inżynieria cech (eliminacja VIF), Cost-Complexity Pruning i symulacja Bootstrap z maksymalizacją czułości (97%) na zadanym progu odcięcia.</p>
      <p><kbd>Python</kbd> <kbd>scikit-learn</kbd> &nbsp; | &nbsp; ✅ Gotowe</p>
    </td>
  </tr>
</table>

---

## 🧠 Case Study: Detekcja Ryzyka Udaru i Koszty NFZ

Większość standardowych modeli ML skupia się na ogólnej dokładności (*Accuracy*). Ten projekt przyjmuje perspektywę **asymetrycznych kosztów biznesowo-medycznych**, w której koszt błędu drugiego rodzaju (przeoczenia pacjenta) wielokrotnie przewyższa koszt prewencji.

<div align="center">
  <table>
    <tr>
      <td align="center" width="33%">
        <h3>150 000 PLN</h3>
        <sub>Koszt przeoczenia pacjenta<br>(rehabilitacja i renta)</sub>
      </td>
      <td align="center" width="33%">
        <h3>2 000 PLN</h3>
        <sub>Koszt badania prewencyjnego<br>(rezonans magnetyczny)</sub>
      </td>
      <td align="center" width="33%">
        <h3>&gt; 97%</h3>
        <sub>Osiągnięta czułość modelu<br>(przy optymalnym progu)</sub>
      </td>
    </tr>
  </table>
</div>

<br>

<details>
  <summary><b>🔍 Kliknij, aby rozwinąć szczegóły zastosowanej metodologii</b></summary>
  <br>
  <ul>
    <li><b>1. Inżynieria Cech i Eliminacja Współliniowości (VIF):</b> Stworzono zmienne krzyżowe (np. <code>age_sq</code>, <code>age_gluc</code>). Zastosowano Variance Inflation Factor (VIF), usuwając zmienne o VIF &gt; 10, aby zapobiec problemowi <i>Singular Matrix</i>.</li>
    <li><b>2. Modele i Cost-Complexity Pruning (CCP):</b> Zastosowano m.in. Drzewa Decyzyjne. Zrezygnowano z przycinania pod kątem „Accuracy” na rzecz algorytmu szukającego hiperparametru stabilności diagnostycznej (maksymalizacja AUC).</li>
    <li><b>3. Optymalizacja Progu Decyzyjnego:</b> Zamiast standardowego 50%, użyto <i>Grid Search</i> symulując budżet dla progów 1%–99%. Wyznaczono optymalny próg decyzyjny (np. 8.9%), poświęcając Swoistość na rzecz Czułości (powyżej 97%).</li>
    <li><b>4. Weryfikacja Niezawodności (Bootstrap):</b> Dla weryfikacji w kontekście Prawa Wielkich Liczb wykonano symulację losowania ze zwracaniem na 1000 iteracji, wyznaczając 95% przedziały ufności dla metryk.</li>
  </ul>
</details>

---

## ⚖️ Prawa autorskie

<div align="center">
  <b>Copyright © 2026 Kacper Łączyński. Wszelkie prawa zastrzeżone.</b>
  <br><br>
  <sub>
    Kod oraz wyniki analizy znajdujące się w tym repozytorium stanowią część portfolio projektowego i zostały udostępnione publicznie wyłącznie w celach poglądowych.<br>
    Kopiowanie, modyfikowanie, dystrybucja lub wykorzystanie komercyjne bez wyraźnej zgody autora jest zabronione.
  </sub>
</div>
