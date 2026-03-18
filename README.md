# TradingView-Native Crypto System Builder v3.3
**Project Structure — LLM-Ready Modular Architecture**

---

## Nasıl Kullanılır

Bu proje tek bir dev prompt değil.
Her modül ayrı bir dosya. LLM her seferinde sadece ihtiyaç duyduğu modülü yükler.

### İki Motor

| Motor | Amaç | Ne Zaman |
|---|---|---|
| **Evaluation Engine** | Yeni fikri değerlendir | Yeni strateji geldiğinde |
| **Operating Engine** | Günlük sistemi yaşat | Her seans, her trade |

---

## Dosya Haritası

```
README.md          ← Bu dosya — her zaman yükle
SYSTEM.md          ← Temel prensipler — her zaman yükle
META.md            ← Güven etiketleme + başarısızlık modları — her zaman yükle

/evaluation/
  M0_profiling.md  ← Trader profili + baseline — ilk kullanımda
  M1_universe.md   ← Universe tanımı — setup kurmadan önce
  M2_triage.md     ← Fikir eleme — yeni fikir geldiğinde
  M3_rules.md      ← Mekanik kural çıkarımı — triage geçtiyse
  M4_risk.md       ← Risk mimarisi — kurallar tanımlandıktan sonra
  M5_validation.md ← Test protokolü — risk tanımlandıktan sonra
  M6_tv.md         ← TradingView audit — validation öncesi

/operating/
  M7_workflow.md   ← Günlük iş akışı — her gün
  M8_behavior.md   ← Davranış güvenceleri — her trade
```

---

## Yükleme Senaryoları

### Senaryo A: Yeni fikir değerlendiriyorum
```
Yükle: SYSTEM.md + META.md + M0_profiling.md + M1_universe.md + M2_triage.md
```

### Senaryo B: Triage geçti, sistemi inşa ediyorum
```
Yükle: SYSTEM.md + META.md + M3_rules.md + M4_risk.md + M5_validation.md + M6_tv.md
```

### Senaryo C: Sabah seansı başlatıyorum
```
Yükle: SYSTEM.md + M7_workflow.md + M8_behavior.md
```

### Senaryo D: Tam evaluation (ilk kez)
```
Yükle: Tümü — sırayla M0 → M1 → M2 → M3 → M4 → M5 → M6
```

---

## Token Tahmini

| Dosya | ~Token |
|---|---|
| SYSTEM.md | 300 |
| META.md | 400 |
| M0_profiling.md | 500 |
| M1_universe.md | 450 |
| M2_triage.md | 400 |
| M3_rules.md | 600 |
| M4_risk.md | 450 |
| M5_validation.md | 500 |
| M6_tv.md | 550 |
| M7_workflow.md | 700 |
| M8_behavior.md | 400 |
| **Tüm proje** | **~5,250** |
| **v3.2 tek prompt** | **~8,000** |
| **v3.3 tek prompt** | **~11,000** |

---

## Referans Sistemi

Modüller arası referans `[→MX]` formatı kullanır.
Örnek: `[→M4]` = M4_risk.md'e bak.

Kural ID'leri `RX.Y` formatı kullanır.
Örnek: `R4.1` = M4, kural 1.

---

## Versiyon

v3.3 | Evaluation Engine + Operating Engine
Kaynak: v3.0 (koruyucu mekanizmalar) + v3.1 (execution split, portfolio heat)
        + v3.2 (validation tier) + v3.3 (universe sayısal, daily workflow sayısal,
        trader profiling mekanizmalı)
