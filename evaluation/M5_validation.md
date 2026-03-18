# M5 — Validation Protocol
*Önkoşul: M4 (risk mimarisi) tamamlanmış.*
*Bu modülü tamamlamak sistemin çalıştığı anlamına gelmez. [→META F4]*

---

## Validation Tierleri

| Tier | İçerik | Kullanım |
|---|---|---|
| **Retail-Minimum** | Backtest + regime + paper | Min boyutta canlı test için yeterli |
| **Advanced** | Tümü + walk-forward + sensitivity | Pozisyon büyütmeden önce zorunlu |

---

## R5.1 — Backtest (maliyet dahil — zorunlu)

**Minimum sample:**

| Timeframe | Min trade |
|---|---|
| Scalp | 200+ |
| Intraday | 150+ |
| Swing | 50+ |

**Maliyet dahil çalıştır (zorunlu — olmadan sonuç geçersiz):**
```
Exchange fee  : [taker her iki taraf]
Slippage      : [trade başına % tahmini]
Spread        : [ortalama bid-ask]
Funding       : [perp ise günlük ortalama]
```

> Maliyet sonrası sistem karlı değilse → **STOP. Viable değil.**

---

## R5.2 — Regime Coverage (zorunlu, optional değil)

| Rejim | Tarih aralığı | Kapsandı mı? |
|---|---|---|
| Boğa | [tarih] | [ ] |
| Ayı | [tarih] | [ ] |
| Yatay | [tarih] | [ ] |

> Üç rejim kapsanmıyorsa → validasyon **TAMAMLANMAMIŞ** — trade sayısı ne olursa olsun.

---

## R5.3 — Paper Trade (min 30 trade)

Her trade için kaydet:

| Alan | Format |
|---|---|
| Giriş sebebi | Hangi koşul tam tetikledi? |
| Kural uyumu | EVET / HAYIR (HAYIR ise sapma sebebi) |
| Çıkış sebebi | stop / hedef / zaman / manuel |
| Duygusal durum | Sakin / Stresli / FOMO / İntikam |

Kural-break trade'ler ayrı loglanır. Sistem performansı yalnızca uyumlu trade'lerden hesaplanır.

> Paper'da kural override ediyorsan → kuralları yeniden yaz, override'ı haklı çıkarma.

---

## R5.4 — Advanced: Walk-Forward

```
Eğitim dönemi : verinin ilk %65'i
Test dönemi   : kalan %35 — tasarımda hiç dokunulmadı

Parametre stability: her parametreyi ±%10 değiştir
Eşik: beklentide >%30 değişim → overfit sinyali

IS profit factor  : [değer]
OOS profit factor : [değer]
Delta kabul: < 0.3
```

---

## Validation Çıktısı

```
SAMPLE SIZE    : [sayı]
EXPECTANCY     : [risk başına ortalama kazanç]
PROFIT FACTOR  : [gross profit / gross loss]
MAX DRAWDOWN   : [%]
WIN RATE       : [%]
REGIME         : [Boğa✓/Ayı✓/Yatay✓ — hangisi eksik?]
OVERFITTING    : [var / yok]

VALIDATION STATUS:
  Unvalidated
  Retail-Minimum Validated
  Advanced-Validated
```

---

## Referans

`[→M4]` Position sizing validation sonuçlarını etkiler
`[→M6]` TradingView implementation sonraki adım
`[→META F4]` Tamamlama ≠ çalışıyor
