# M7 — Daily Operating Workflow
*Her seans öncesi, her trade sonrası, her hafta yükle.*
*Bu modül rapor değil, kontrol listesi. Her kutu sayısal kriter içerir.*

---

## PRE-SESSION (~10-15 dk, seans açılmadan önce)

### A — Market Context Gate

| Kontrol | Eşik | Sonuç |
|---|---|---|
| BTC 24h değişim | >%5 | Swing setup yok — sadece en yüksek confluence |
| Majör haber/event bugün | FOMC/CPI/halving/büyük listing | **Seans yok** |
| Genel funding | >%0.1/8h | Perp long setup yok |
| Watchlist'te büyük spread | >%0.2 | O coin için bugün trade yok |
| Kendi duygusal durumu | Stresli/FOMO/İntikam | **Bugün seans yok** |

**A Skoru:**
- 0-1 işaretli → Normal seans
- 2 işaretli → Risk %50 azalt, sadece en güçlü setup
- 3+ işaretli → Seans yok

### B — Setup Hazırlığı

- [ ] Bugün hangi setup aranıyor? → `[tek setup ismi]`
- [ ] Alert kuruldu mu? → Kurulmadıysa seans yok
- [ ] Max alarm sayısı bugün: `[sayı — önerilen: 3-5]`
- [ ] Tüm varlıklar universe içi mi? [→M1]

> **Pre-session tamamlanmadan seans açılmaz.**

---

## DURING SESSION

### Günlük Trade Limitleri (M0 profilinden gelir)

| Profil | Max trade/gün |
|---|---|
| Chaotic Overtrader | **2** |
| FOMO/News Chaser | **2** |
| Indicator Dependent | **3** |
| Semi-Systematic | **4** |
| Low-Freq Rule Follower | **5** |

> Limit dolunca seans biter. "Ama çok iyi görünüyor" bu kuralı değiştirmez.

### Alert → Karar Süreci

```
Alarm çaldı
  → Karar süresi: [2-5 dk] — aşılırsa setup geçilir, chase edilmez
  → Kontrol et:
     [ ] Setup koşulları hâlâ geçerli mi?
     [ ] Spread < eşik mi? [→M1]
     [ ] Position size hesaplandı mı? [→M4] — hesaplanmadan giriş yok
     [ ] Günlük trade limiti dolmadı mı?
  → Tümü evet → Trade al
  → Herhangi biri hayır → Pas geç, logla
```

### Pas Geçme Koşulları (herhangi biri → trade almama)

- Karar süresi geçti
- Setup koşullarından biri artık sağlanmıyor
- Spread eşik üzerinde
- Universe dışı varlık [→M1]
- Günlük limit doldu
- Duygusal durum kötüleşti
- Position size hesaplanmadı

---

## POST-TRADE (~5 dk)

```
ENTRY REASON   : [hangi setup koşulu tam tetikledi?]
RULE COMPLIANCE: EVET / HAYIR
DEVIATION      : [HAYIR ise — ne oldu, neden?]
EXIT TYPE      : stop / hedef / zaman / manuel override
EMOTION        : Sakin / Stresli / FOMO / İntikam
EXEC SLIPPAGE  : [intended vs actual fill %]
SAME SETUP?    : evet / hayır / bekle
```

> Kural-break trade sistem performans hesabına girmez.
> Ayrı loglanır → [→M8] davranışsal örüntü analizi için.

---

## END-OF-DAY (~5 dk)

```
Rule-break sayısı    : [sayı]
Chase oldu mu?       : E / H
Universe ihlali?     : E / H
Limit aşıldı mı?     : E / H
Execution sapması ort: [%]
```

Hepsinde H ve sıfır rule-break → Normal.
Herhangi biri E → Haftalık review'de ele alınır.

---

## END-OF-WEEK — Pazartesi sabahı, seans dışında (~20-30 dk)

```
Kural-break oranı    : [%]
Ortak örüntü         : [bir cümle]
Paper vs live sapması: [%]
Tactical watchlist   : güncelle? E / H → [→M1]
Drawdown tetiklendi? : E / H → [→M4 R4.3]
Sistem pause?        : E / H
```

> Pause kararı bu review'de verilir — seansın ortasında değil.

---

## Referans

`[→M0]` Profil bazlı limitler | `[→M1]` Universe ve spread eşikleri
`[→M4 R4.3]` Drawdown protokolü | `[→M8]` Behavioral log
