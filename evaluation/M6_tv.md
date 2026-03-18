# M6 — TradingView Implementation Audit
*Validation'dan önce teknik uyumluluğu belirle.*

---

## R6.1 — Implementation Levels

| Level | Adı | Anlam | Sınır |
|---|---|---|---|
| 1 | Chart Representable | Grafik üzerinde görünür | Pine gerektirmez |
| 2 | Pine Definable | Pine v5/v6 ile yazılabilir | Tester sonuçları kısıtlı |
| 3 | Backtestable | Strategy Tester çalıştırılabilir | Intrabar path, fill sınırları |
| 4 | Alertable | Alert üretilebilir | Mobil+scalp → bu seviye maksimum |
| 5 | Executable | Alert→webhook→bot→fill | Gecikme ve fill sayısal tahmin gerekir |

**Bu sistem Level:** `[1/2/3/4/5]`
Level 5 değilse kısıtlama: `[açıkla]`

---

## R6.2 — Repaint Checklist

- [ ] `request.security()` — lookahead kullanılıyor mu?
- [ ] HTF veri — sadece kapanış onaylı çubuklarda mı?
- [ ] `barstate.isconfirmed` — tüm sinyal mantığı gated mı?
- [ ] Dinamik değişken — geçmişte yeniden hesaplıyor mu?

İşaretlenemeyen → **REPAINT RİSKİ** — kodlamadan önce flag et.

---

## R6.3 — Strategy Tester Sınırlamaları

Her backtest sonucunda kabul et:
- Intrabar fiyat yolu bilinmiyor — OHLC varsayılıyor
- Limit emirler intended fiyatta dolmayabilir
- Slippage modellenmemiş (elle eklenmediyse)
- Funding hariç (elle çıkarılmadıysa)

---

## R6.4 — Execution Guardrails (boş bırakılamaz)

| Parametre | Değer | [→M1] Eşiğiyle tutarlı mı? |
|---|---|---|
| Min 24h hacim | [USD] | [ ] |
| Max spread | [%] | [ ] |
| Funding veto | [%/8h] | [ ] |
| Min listeleme yaşı | [gün] | [ ] |
| No-trade saatleri | [pencereler] | |

---

## R6.5 — Alert Execution Gap

```
TradingView Alert → Webhook → Bot/API → Exchange

Gecikme tahmini       : [ms]
Fill slippage tahmini : [%]
Webhook hazır mı?     : E / H
```

> Bu sistem emir execute etmez — sinyal verir.

---

## R6.6 — Pine Code Skeleton

Amaç: çevrilebilirliği doğrula — bitmiş kod değil.

```pine
//@version=5
indicator("Sistem Adı", overlay=true)

// INPUTS — [M3'teki her parametre]

// SETUP
// setup_cond1 = [stub]
// setup_cond2 = [stub]
// setup_valid = setup_cond1 and setup_cond2

// TRIGGER
// trigger = [stub]

// ALERTS
// alertcondition(trigger and setup_valid,
//   title="Entry", message="confirmed")
```

M3'teki herhangi bir koşul Pine değişkeni olamazsa → `TV-INCOMPATIBLE`

---

## Final Sınıflandırma

| Sınıf | |
|---|---|
| Reject | |
| Research Only | |
| Manual Setup Only | |
| Chart Representable (L1) | |
| Pine Definable (L2) | |
| Backtestable (L3) | |
| Alertable (L4) | |
| Executable (L5) | |
| Executable + Retail-Min Validated | |
| Executable + Advanced-Validated | |

---

## Referans

`[→M1]` Universe guardrails eşikleriyle tutarlılık
`[→M3]` Kural seti Pine uyumu
`[→META]` Final çıktı şablonu
