# M2 — Idea Triage
*Yeni bir fikir değerlendirilirken yükle.*
*Önkoşul: M0 (profil) + M1 (universe) tamamlanmış olmalı.*

---

## Ön Filtreler (bunları önce kontrol et)

| Filtre | Koşul | Sonuç |
|---|---|---|
| Profil filtresi | M0 = FOMO/News Chaser **ve** kaynak haber/sosyal medya | **REJECT** — triage'a girmez |
| Universe filtresi | Varlık M1 universe dışında | **REJECT** — universe ihlali |

---

## R2.1 — Analiz Soruları

| Alan | Soru |
|---|---|
| Core Hypothesis | Hangi edge iddia ediliyor? Neden devam etsin? |
| Timeframe | scalp / intraday / swing / position |
| Required Data | OHLCV / indicator / external |
| TV Compatibility | Full / Partial / Weak / None |
| Repaint Risk | Low / Medium / High — mekanizma nedir? |
| Execution Realism | M0 profilindeki trader için gerçekçi mi? |

---

## R2.2 — Çıktı Formatı

```
CORE IDEA      : [1 paragraf — hipotez, anlatı yok]
TIMEFRAME      : [scalp/intraday/swing/position]
DATA           : [tam liste]
TV COMPAT      : [level + sebep]
REPAINT        : [level + mekanizma]
EXEC RISKS     : [likidite | slippage | funding | regime]
WEAKNESSES     : [1] [2] [3]   ← tam 3, ne az ne fazla
CONFIDENCE     : [HIGH/MED/LOW + neden yanlış olabilir]
```

---

## R2.3 — Sınıflandırma

| Sınıf | Anlam | Sonraki adım |
|---|---|---|
| **Reject** | Yapısal olarak tradable değil | Reject Protocol → DUR |
| **Research Only — Structural** | Veri/yapı sorunu | Reject Protocol → DUR |
| **Research Only — Premature** | Erken aşama | Reject Protocol → DUR |
| **Manual Setup Only** | Otomasyon yok | M3'e geç, sınırlı |
| **TradingView-Compatible** | Devam edilebilir | M3'e geç |

---

## R2.4 — Reject Protokolü

Reject sessiz durmaz:
1. En önemli red sebebi
2. Yeniden değerlendirme için ne değişmeli
3. Kullanıcının keşfedebileceği bir alternatif yön

> **Kullanıcı Direnç Notu:** Fikir yeniden çerçevelenirse triage'ı yeni çerçevelemeyle yeniden çalıştır. Orijinal sorunun çözüldüğünü varsayma.

---

## Referans

`[→M0]` Profil filtresi | `[→M1]` Universe filtresi
`[→M3]` Triage geçtiyse devam
