# M0 — Trader Profiling & Baseline
*İlk kullanımda veya profil güncellemesinde yükle.*
*Sonuç: tüm diğer modülleri kalibre eden profil ataması.*

---

## Girdi (kullanıcıdan al)

| Alan | Format | Not |
|---|---|---|
| Haftalık trade sayısı | Sayı | |
| Ortalama tutma süresi | dakika / saat / gün | |
| Stop loss kullanımı | her zaman / bazen / nadiren / hiç | |
| Trade başına risk | % hesap | "bilmiyorum" geçersiz — tahmin ettir |
| Giriş tetikleyicisi | grafik / haber / sosyal medya / indicator | |
| TradingView kullanımı | mobil / masaüstü / her ikisi | |
| Pine Script | evet / hayır / kısmen | |

---

## Profil Kriterleri

| Profil | Kriterler | [→M7] Günlük limit |
|---|---|---|
| **Chaotic Overtrader** | 15+ trade/hafta, stop nadiren/hiç, sosyal medya tetikleyici | 2 trade/gün |
| **FOMO/News Chaser** | Haber/sosyal medya tetikleyici, tutma saatler | 2 trade/gün |
| **Indicator Dependent** | Indicator tetikleyici, Pine yok, saatler-günler tutma | 3 trade/gün |
| **Semi-Systematic** | Grafik+indicator mix, stop çoğunlukla var, 3-10 trade/hafta | 4 trade/gün |
| **Low-Freq Rule Follower** | 1-4 trade/hafta, stop her zaman, net kural odaklı | 5 trade/gün |

---

## Profil Bazlı Sistem Uyarıları

**Chaotic Overtrader**
- [→M2] Triage: kör kural testi FAIL → canlıya geçme
- [→M1] Universe: maks 5 coin
- [→M7] Günlük maks 2 trade — istisna yok

**FOMO/News Chaser**
- [→M2] Haber/sosyal medya kaynaklı fikir → otomatik REJECT, triage'a girmez

**Indicator Dependent**
- [→M3] Her indicator sayısal threshold zorunlu — "RSI yüksek" geçersiz
- [→M3] Hidden Discretion Score > 3 → Manual Setup Only

**Semi-Systematic**
- Tüm modüller tam uygulanabilir

**Low-Freq Rule Follower**
- [→M5] Advanced validation tier hedefle

---

## Çıktı

```
TRADER PROFILE    : [profil adı]
BASELINE RISK     : Low / Medium / High
WITHOUT SYSTEM    : [mevcut alternatif davranış — bir cümle]
MIN IMPROVEMENT   : [net pozitif için tek somut kriter]
IMPROVEMENT POT   : High / Medium / Low
CONFIDENCE        : [HIGH/MED/LOW]
```

---

## Referans

`[→M1]` Universe kısıtı için | `[→M2]` Triage filtresi için
`[→M3]` Kural kalitesi için | `[→M7]` Günlük limitler için
