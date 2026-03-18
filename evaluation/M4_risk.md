# M4 — Portfolio & Risk Architecture
*Önkoşul: M3 tamamlanmış. M5'ten ÖNCE doldurulmalı.*

---

## R4.1 — Position Sizing

| Parametre | Değer | Not |
|---|---|---|
| Yöntem | [sabit % / vol-adj / Kelly] | Retail için sabit % önerilir |
| Trade başına risk | [%] | Önerilen: 0.5%–1% |
| Max açık risk | [%] | Tüm pozisyonlar toplamı |
| Hesap büyüklüğü | [USD] | Position size hesabı için |

**Formül:**
```
Position Size = (Hesap × Risk%) / (Giriş − Stop Loss)

Örnek:
  Hesap: [X] USD | Risk: [Y]%
  Risk tutarı: X × Y / 100 = [Z] USD
  Entry: [P1] | Stop: [P2] | Fark: [P1-P2] USD/coin
  Lot: Z / (P1-P2)
```

---

## R4.2 — Portfolio Heat (başlangıç kuralları)

| Kural | Limit |
|---|---|
| Toplam açık risk | ≤ %4 hesap — her zaman |
| Korelasyon cluster | Max 2 pozisyon aynı BTC-beta yönünde |
| Setup family | Max 2 aktif trade aynı setup tipinden |
| Tek varlık | Max %2 hesap |

---

## R4.3 — Drawdown Protokolü

| Tetikleyici | Aksiyon | Süre |
|---|---|---|
| 2 ardışık kayıp | Boyutu %30 küçült | Sonraki 3 trade |
| 3 ardışık kayıp | Risk %50'ye indir | Drawdown kapanana kadar |
| 5 ardışık kayıp | **Sistem duraklat** | Geri dönüş koşuluna kadar |

**Geri Dönüş Koşulu** (tamamı sağlanmadan resume yasak):
- [ ] Rule-break journal gözden geçirildi
- [ ] Sapma sebebi yazıya döküldü
- [ ] Min 3 gün beklendi
- [ ] Paper trade'de ardışık 5 uyumlu trade tamamlandı

---

## R4.4 — Crypto-Specific Limits

| Parametre | Eşik | Not |
|---|---|---|
| Funding (perp) | >0.1%/8h → no trade | Perp long setup veto |
| Min listeleme yaşı | 90 gün | [→M1]'le tutarlı |
| Spread veto | >0.2% | [→M1]'le tutarlı |
| Exchange konsantrasyonu | Max %70 tek exchange | |

---

## Referans

`[→M3]` Kural tanımı önkoşul | `[→M5]` Validation sonraki adım
`[→M1]` Universe eşikleriyle tutarlılık | `[→M7]` Drawdown protokolü daily workflow'da
