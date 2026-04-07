# Transformer jako experimentální alternativa ke klasickým ML metodám

[cite_start]Tento projekt se zabývá využitím architektury **Transformer** pro predikci vývoje geometrické polohy železniční koleje[cite: 3]. [cite_start]Práce zkoumá, zda lze moderní sekvenční modely využít jako alternativu ke klasickým přístupům strojového učení (např. Random Forest, Gradient Boosting) pro modelování degradačních procesů[cite: 16, 17].

## 📌 Přehled projektu

[cite_start]Hlavním cílem bylo ověřit schopnost Transformeru zachycovat závislosti v dlouhých časových řadách při predikci trendu geometrie koleje[cite: 18, 28]. [cite_start]Projekt se zaměřuje na predikci budoucího vývoje na základě historických měření a historie technologických zásahů[cite: 19, 31].

* [cite_start]**Vstupní data**: Historická měření veličin G1, G2, D1 a D2[cite: 44, 93].
* [cite_start]**Cílová veličina**: Parametr G3 (složky posun a zdvih)[cite: 45, 104].
* [cite_start]**Metodika**: Příprava dat pomocí klouzavého okna (*window_size*) a diskretizace numerických hodnot do intervalů (*num_bins*)[cite: 56, 64].

## 🏗️ Architektura modelu

[cite_start]Model využívá encoderově orientovanou variantu Transformeru přizpůsobenou pro numerická data[cite: 78].
* [cite_start]**Self-attention**: Umožňuje zohledňovat vztahy mezi jednotlivými prvky sekvence v širším kontextu[cite: 81].
* [cite_start]**Embedding**: Převod vstupní sekvence do vnitřní reprezentace modelu[cite: 90, 94].
* [cite_start]**Multi-head attention**: Mechanismy vícehlavé pozornosti pro zachycení nelineárních závislostí[cite: 96, 97].
* [cite_start]**Regularizace**: Použití dropoutu pro omezení přeučení na omezeném objemu dat[cite: 99, 122].

## 🧪 Experimentální výsledky

[cite_start]V rámci práce bylo realizováno 10 experimentů rozdělených do dvou etap: hledání základní konfigurace (kolej č. 1) a aplikace na odlišný datový soubor (kolej č. 3)[cite: 140, 154, 155].

### Klíčová zjištění
* [cite_start]**Délka okna**: Zkrácení vstupního okna ze 120 na 60 kroků přispělo v některých případech ke stabilnějšímu chování modelu[cite: 168, 169].
* [cite_start]**Kapacita modelu**: Navyšování kapacity (větší embedding nebo počet hlav) nemusí být při daném objemu dat přínosné[cite: 175].
* [cite_start]**Přenositelnost**: Optimální nastavení je vysoce citlivé na charakter konkrétního datasetu; přenos konfigurace mezi kolejemi není přímočarý[cite: 212, 249].

### Nejúspěšnější konfigurace (MAE [mm])
| Pokus | Dataset | MAE Posun | MAE Zdvih | Charakteristika |
| :--- | :--- | :---: | :---: | :--- |
| **3** | Kolej č. 1 | 4,086 | 5,987 | [cite_start]128 binů, window 120 [cite: 151, 164] |
| **6** | Kolej č. 1 | 4,257 | 5,441 | [cite_start]Úprava hloubky a počtu hlav [cite: 151, 173] |
| **10** | Kolej č. 3 | 5,284 | 12,786 | [cite_start]Kompaktní model, delší trénink [cite: 151, 209] |

## 🛠️ Konfigurační parametry

* [cite_start]`window_size`: Délka vstupní sekvence (historický kontext)[cite: 118].
* [cite_start]`embed_size`: Velikost vnitřní reprezentace dat[cite: 119].
* [cite_start]`n_heads` / `n_layers`: Počet hlav pozornosti a hloubka architektury[cite: 120, 121].
* [cite_start]`default_num_bins`: Počet intervalů pro diskretizaci vstupů[cite: 123].

## 📖 Literatura

1. Liao, S.-H. et al. (2022). [cite_start]Prediction models for railway track geometry degradation...[cite: 281].
2. Nie, Y. et al. (2023). [cite_start]A time series is worth 64 words...[cite: 284].
3. Srivastava, N. et al. (2014). [cite_start]Dropout: A simple way to prevent overfitting...[cite: 286].
4. Vaswani, A. et al. (2017). [cite_start]Attention is all you need[cite: 288].
5. Wang, Z. et al. (2023). [cite_start]Prediction of railroad track geometry change using hybrid CNN-LSTM...[cite: 290].
6. Wu, H. et al. (2021). [cite_start]Autoformer: Decomposition transformers for long-term forecasting[cite: 292].
7. Zhou, H. et al. (2021). [cite_start]Informer: Beyond efficient transformer for long sequence forecasting[cite: 294].

---
[cite_start]**Autor**: David Lískovský [cite: 6]
[cite_start]**Instituce**: Ostravská univerzita, Přírodovědecká fakulta [cite: 1]
[cite_start]**Datum**: 07.04.2026 [cite: 10]
