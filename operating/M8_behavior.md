# M8 — Behavioural Guardrails
*Her trade öncesi ve sonrasında aktif. M7 ile birlikte yükle.*

---

## R8.1 — Cooldown Kuralları (sayısal, istisnasız)

| Tetikleyici | Aksiyon |
|---|---|
| Stop sonrası | Min 2 bar bekle — yeniden giriş yok |
| Kural-break sonrası | Günlük review tamamlanmadan sonraki trade yok [→M7] |
| 3 ardışık kayıp | Risk %50 — sonraki 5 trade [→M4 R4.3] |
| 5 ardışık kayıp | Sistem duraklat [→M4 R4.3] |
| FOMO/revenge duygu | O seans için trade yok [→M7] |

---

## R8.2 — Missed Trade Kuralı

> Giriş çubuğu kapandıktan sonra kaçırılan setup **chase edilemez**.
> "Kaçırıldı" loglanır — üzerine işlem yapılmaz.
>
> Kaçırılan setup'lar sıklaşıyorsa: alert kurulumunu gözden geçir — kuralları değil.

---

## R8.3 — Rule-Break Journal

Her kural-break için:

```
Tarih/Saat   : [zaman]
Hangi kural  : [spesifik kural adı — genel değil]
Neden kırıldı: [dürüst bir cümle]
Sonuç        : [kazanıldı/kaybedildi]
```

> **Not:** Kural-break'ten kazanmak kuralı doğrulamaz.
> Kural-break'ten kaybetmek ihlal etmenin tek riski değildir.

---

## R8.4 — Social Media Firewall

| Durum | Aksiyon |
|---|---|
| Sosyal medyada coin gördüm — watchlist içinde | Haftalık review'e not al. Bugün değil. [→M7] |
| Sosyal medyada coin gördüm — watchlist dışında | Bu konuşma orada bitti. [→M1] |
| "Herkes alıyor" | Sistemin kuralını değiştirmez |
| "Çok güçlü görünüyor" | Sistemin kuralını değiştirmez |

---

## R8.5 — Behavioural Metrics (haftalık track)

| Metrik | Tanım | Hedef |
|---|---|---|
| FOMO trade oranı | Kural dışı trade / toplam | < %10 |
| Revenge trade | Kayıp sonrası hızlı giriş sayısı | = 0 |
| Off-plan trade | Universe/setup dışı trade % | < %5 |
| Rule-break after loss | Kayıp sonrası rule-break sayısı | = 0 |

---

## Referans

`[→M4 R4.3]` Drawdown protokolü | `[→M7]` Post-trade log ve weekly review
`[→M1]` Universe koruması | `[→M0]` Profil bazlı kısıtlar
