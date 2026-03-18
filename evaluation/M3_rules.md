# M3 — Mechanical Rule Extraction
*Önkoşul: M2 sınıflandırması TradingView-Compatible veya Manual Setup Only.*

---

## Mekaniklik Standardı (P2)

> İki bağımsız trader, aynı grafik + aynı kural setine sahipken,
> iletişim kurmadan aynı çubukta aynı sinyale ulaşabiliyorsa → MEKANİK.

Bu standart karşılanamıyorsa sistem mekanik değil — kurallar ne kadar hassas yazılırsa yazılsın.

---

## R3.1 — Rule Grammar (7 alan zorunlu)

| Alan | Açıklama |
|---|---|
| Variable | Ne ölçülüyor |
| Data Source | OHLCV / indicator / external |
| Formula | Tam hesaplama |
| Threshold | Tam sayı veya dinamik referans |
| Operator | `>` `<` `=` `crosses above` `crosses below` |
| Timeframe | Hangi TF |
| Confirmation | `bar close` / `real-time` / `next bar` |

---

## R3.2 — Setup Compression Limiti

```
1 primary setup
1 variation    (opsiyonel — iyi gerekçe gerekir)
1 veto set
```

Her eklenen kural → "neden gerekli?" sorusuna cevap vermeli.
Filtre eklemek sistemi güçlendirmez — overfitting riskini artırır.

---

## R3.3 — Sistem Yapısı

**SETUP LOGIC** (pozisyon öncesi)
```
Condition 1 — Market State : [Variable|Source|Formula|Threshold|Op|TF|Confirm]
Condition 2 — Trend        : [same format]
Condition 3 — Location     : [same format]
```

**TRIGGER LOGIC**
```
Entry Event  : [tam koşul]
Bar Confirm  : [kapanış — her zaman tercih et]
Direction    : [long / short / her ikisi]
Single Entry : [aynı anda tek pozisyon? E/H]
```

**INVALIDATION LOGIC**
```
INV1 : [yapı kırılması — hangi pivot? kaç barlık?]
INV2 : [indicator failure — hangi değer?]
INV3 : [zaman — X bar içinde tetik yoksa]
```

**EXIT LOGIC**
```
Stop Loss   : [ATR/yapı/sabit% — hangisi ve neden?]
Take Profit : [R-katı/yapı/indicator]
Partial     : [varsa — hedefin %kaçında?]
Trailing    : [varsa — tam mekanizma]
Time Exit   : [X bar içinde hareket yoksa]
```

---

## R3.4 — Kör Kural Testi

> Her koşul: tek cümleyle anlatılabilir, sormadan aynı sonucu üretir mi?
> HAYIR → o koşul yeniden yazılmalı veya kaldırılmalı.

**`MECHANICAL INTEGRITY: PASS / FAIL`**
FAIL ise: hangi koşullar başarısız, neden?

---

## R3.5 — Hidden Discretion Score (HDS)

| Puan | Koşul |
|---|---|
| +1 | "güçlü retest", "temiz kırılım" gibi yorum gerektiren ifade |
| +1 | Hangi barlık pivot alındığı tanımsız |
| +1 | "Bağlam uygun" tipi genel koşul |
| +1 | Sinyal skip etme alanı var ("iyi görünüyorsa al") |
| +1 | İki koşul aynı bilgiyi farklı formatta tekrarlıyor |

| HDS | Sonuç | Aksiyon |
|---|---|---|
| 0–1 | Mechanical | Devam et |
| 2–3 | Semi-Mechanical | Uyarıyla devam — hangi koşullar puan aldı? |
| 4–5 | Manual Setup Only | [→M5]'e geçme — önce yeniden yaz |

**`HDS: [0-5]`** — her puan için gerekçe listele

---

## Referans

`[→M2]` Triage önkoşulu | `[→M4]` Risk tanımı sonraki adım
`[→META]` Güven etiketi için
