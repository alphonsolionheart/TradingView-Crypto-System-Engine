# M1 — Universe Definition
*Her yeni setup değerlendirmesinden ÖNCE yükle.*
*Universe dışındaki varlıklar için sistem çalışmaz.*

---

## R1.1 — Sayısal Eşikler (boş bırakılamaz)

| Parametre | Değer | Önerilen başlangıç |
|---|---|---|
| Min 24h spot hacim | [USD] | $50M+ |
| Min 24h perp hacim | [USD] | $100M+ |
| Max ortalama spread | [%] | <0.15% |
| Min listeleme yaşı | [gün] | 90+ |
| Max universe coin sayısı | [sayı] | 10–15 |

---

## R1.2 — Excluded Classes (istisnasız, her zaman)

- Son 30 günde listelenen tokenlar
- Piyasa değeri < $200M
- Merkezi borsa hacmi < $10M/gün
- Meme coin, stablecoin, wrapped token
- Son 7 günde >%40 pump
- Son 24h haber/listing etkisiyle >%15 hareket

---

## R1.3 — Watchlist Yapısı

| Liste | İçerik | Güncelleme |
|---|---|---|
| **Core** | BTC, ETH + 1-3 likit L1/L2 | Aylık — sadece kriter değişirse |
| **Tactical** | Maks 6-8 coin | **Sadece Pazartesi sabahı** — seans dışında |
| **Do-Not-Trade** | Ani pump/dump, bozuk spread | Anlık — giriş anında |

---

## R1.4 — Universe Drift Koruması

> Sosyal medyada gördüğün bir coin watchlist dışındaysa:
> → O coin için bu sistem çalışmaz.
> → "Ama çok iyi görünüyor" bu kuralı değiştirmez.
> → Ekleme haftalık review'i bekler. [→M7]

Seans sırasında universe değişimi **YASAK**.

---

## Kontrol Sorusu

Fikirdeki varlık şunları karşılıyor mu?
- [ ] R1.1 hacim eşiği üzerinde
- [ ] R1.2 excluded class dışında
- [ ] Core veya Tactical listede

Herhangi biri hayır → [→M2] REJECT (universe ihlali)

---

## Referans

`[→M0]` Profil bazlı universe kısıtı (Chaotic: maks 5)
`[→M2]` Universe ihlali → otomatik reject
`[→M7]` Watchlist güncelleme kuralı
