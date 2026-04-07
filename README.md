# Transformer jako experimentální alternativa ke klasickým ML metodám

Tento projekt se zabývá využitím architektury **Transformer** pro predikci vývoje geometrické polohy železniční koleje. Práce zkoumá, zda lze moderní sekvenční modely využít jako alternativu ke klasickým přístupům strojového učení (např. Random Forest, Gradient Boosting) pro modelování degradačních procesů.

## 📌 Přehled projektu

Hlavním cílem bylo ověřit schopnost Transformeru zachycovat závislosti v dlouhých časových řadách při predikci trendu geometrie koleje. Projekt se zaměřuje na predikci budoucího vývoje na základě historických měření a historie technologických zásahů.

* **Vstupní data**: Historická měření veličin G1, G2, D1 a D2.
* **Cílová veličina**: Parametr G3 (složky posun a zdvih).
* **Metodika**: Příprava dat pomocí klouzavého okna (*window_size*) a diskretizace numerických hodnot do intervalů (*num_bins*).

## 🏗️ Architektura modelu

Model využívá encoderově orientovanou variantu Transformeru přizpůsobenou pro numerická data.
* **Self-attention**: Umožňuje zohledňovat vztahy mezi jednotlivými prvky sekvence v širším kontextu.
* **Embedding**: Převod vstupní sekvence do vnitřní reprezentace modelu.
* **Multi-head attention**: Mechanismy vícehlavé pozornosti pro zachycení nelineárních závislostí.
* **Regularizace**: Použití dropoutu pro omezení přeučení na omezeném objemu dat.

## 🧪 Experimentální výsledky

V rámci práce bylo realizováno 10 experimentů rozdělených do dvou etap: hledání základní konfigurace (kolej č. 1) a aplikace na odlišný datový soubor (kolej č. 3).

### Klíčová zjištění
* **Délka okna**: Zkrácení vstupního okna ze 120 na 60 kroků přispělo v některých případech ke stabilnějšímu chování modelu.
* **Kapacita modelu**: Navyšování kapacity (větší embedding nebo počet hlav) nemusí být při daném objemu dat přínosné.
* **Přenositelnost**: Optimální nastavení je vysoce citlivé na charakter konkrétního datasetu; přenos konfigurace mezi kolejemi není přímočarý.

### Nejúspěšnější konfigurace (MAE [mm])
| Pokus | Dataset | MAE Posun | MAE Zdvih | Charakteristika |
| :--- | :--- | :---: | :---: | :--- |
| **3** | Kolej č. 1 | 4,086 | 5,987 | 128 binů, window 120 |
| **6** | Kolej č. 1 | 4,257 | 5,441 | Úprava hloubky a počtu hlav |
| **10** | Kolej č. 3 | 5,284 | 12,786 | Kompaktní model, delší trénink |

## 🛠️ Konfigurační parametry

* `window_size`: Délka vstupní sekvence (historický kontext).
* `embed_size`: Velikost vnitřní reprezentace dat.
* `n_heads` / `n_layers`: Počet hlav pozornosti a hloubka architektury.
* `default_num_bins`: Počet intervalů pro diskretizaci vstupů.

## 📖 Literatura

1. Liao, S.-H. et al. (2022). Prediction models for railway track geometry degradation using machine learning methods: A review.
2. Nie, Y. et al. (2023). A time series is worth 64 words: Long-term forecasting with transformers.
3. Srivastava, N. et al. (2014). Dropout: A simple way to prevent neural networks from overfitting.
4. Vaswani, A. et al. (2017). Attention is all you need.
5. Wang, Z. et al. (2023). Prediction of railroad track geometry change using a hybrid CNN-LSTM spatial-temporal model.
6. Wu, H. et al. (2021). Autoformer: Decomposition transformers with auto-correlation for long-term series forecasting.
7. Zhou, H. et al. (2021). Informer: Beyond efficient transformer for long sequence time-series forecasting.

---
**Autor**: David Lískovský
**Instituce**: Ostravská univerzita, Přírodovědecká fakulta
**Datum**: 07.04.2026
