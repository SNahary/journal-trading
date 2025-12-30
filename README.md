# ICT Assistant: Full Visual [Expert]

Un indicateur Pine Script complet pour le **day trading ICT (Inner Circle Trader)**. Cet outil identifie automatiquement les setups à haute probabilité basés sur la méthodologie ICT.

---

## 🆕 Changelog v2.0 - Dark Mode Edition

### 🎨 Nouvelle Palette de Couleurs (Dark Mode)
Toutes les couleurs ont été optimisées pour une visibilité maximale sur fond noir avec bougies vertes/rouges.

| Élément | Couleur | Code Hex |
|---------|---------|----------|
| BSL | Rouge Corail | `#FF6B6B` |
| SSL | Cyan Turquoise | `#4ECDC4` |
| BOS Bull | Vert Néon | `#00FF88` |
| BOS Bear | Rouge Vif | `#FF4757` |
| FVG Box | Or Doré | `#FFE66D` |
| BPR Box | Violet Électrique | `#A855F7` |
| OB Bull | Bleu Ciel | `#38BDF8` |
| OB Bear | Rose Corail | `#FB7185` |
| Daily Open | Indigo | `#818CF8` |

### 🔷 Filtrage Intelligent des Order Blocks
Les OB ne sont plus affichés partout ! Ils n'apparaissent que s'ils répondent à l'un des critères :
- **Proximité liquidité** : L'OB est à moins de X% d'un niveau BSL ou SSL
- **Confirmation BOS** : Un Break of Structure récent valide l'OB

> **Nouveau paramètre** : "OB Proximity to Liquidity (%)" - défaut 0.5%, ajustable de 0.1% à 2%

### 📦 Marquage Visuel du BOS avec Rectangles
Le BOS est maintenant clairement visible avec :
- **Rectangle coloré** encadrant la zone de cassure
- **Bordure** de couleur vive (vert/rouge)
- **Texte** "⬆ BOS" ou "⬇ BOS" intégré

### 🕯️ Coloration des Bougies FVG
Les bougies présentant un Fair Value Gap sont maintenant colorées différemment :
- **FVG Haussier** : Bougie en **Jaune Doré** `#FFD93D`
- **FVG Baissier** : Bougie en **Orange** `#FF8C42`

---

## 🎯 Fonctionnalités

### 📍 Concepts ICT Détectés

| Concept | Description | Visuel |
|---------|-------------|--------|
| **Daily Open** | Ligne de référence Premium/Discount | Ligne indigo |
| **BSL/SSL** | Zones de liquidité (Buy-Side/Sell-Side) | Lignes pointillées corail/cyan |
| **BOS** | Break of Structure | Rectangle + Label coloré |
| **FVG** | Fair Value Gap | Box or + bougie colorée |
| **BPR** | Balanced Price Range | Box violette |
| **Order Blocks** | Empreinte institutionnelle (filtré) | Box bleu/rose avec ✓ |

### 📊 Gestion du Risque

- **ATR-based Stop Loss** : Calcul automatique basé sur ATR × multiplicateur
- **Take Profit** : Niveaux TP1 (R:R 1:1) et TP2 (R:R configurable)
- **Position Sizing** : Calcul de la taille de position recommandée
- **Dashboard** : Tableau Dark Mode avec toutes les métriques

### ⏱️ Adaptation Automatique au Timeframe

| Mode | Timeframes | Pivot Lookback | OB Confirm | BOS Lookback | Reference |
|------|------------|----------------|------------|--------------|-----------|
| **Scalping** | 1m, 3m, 5m | 5 | 3 | 5 | Daily Open |
| **Intraday** | 15m, 30m, 1H | 10 | 5 | 8 | Daily Open |
| **Swing** | 2H, 4H | 15 | 8 | 12 | Daily Open |
| **Position** | D, W, M | 20 | 10 | 15 | Weekly/Monthly Open |

> **Note** : Les Killzones sont automatiquement désactivées sur les timeframes Daily et supérieurs.

### Hiérarchie des Signaux

1. **OB (Order Block)** ⭐⭐⭐ - Taille normale - Bleu/Rose
2. **BPR (Balanced Price Range)** ⭐⭐ - Taille small - Violet
3. **FVG (Fair Value Gap)** ⭐ - Taille tiny - Vert/Rouge

---

## ⚙️ Configuration

### Time & Session
| Paramètre | Default | Description |
|-----------|---------|-------------|
| Filter by Killzones | ✅ | Filtrer les signaux par session |
| London | 02:00-05:00 | Session de Londres |
| New York | 07:00-11:00 | Session de New York |

### Liquidity & Structure
| Paramètre | Default | Description |
|-----------|---------|-------------|
| Auto-adapt to Timeframe | ✅ | Adaptation auto des paramètres |
| Pivot Lookback | 10 | Nombre de bougies pour détecter les pivots |
| BSL Color | 🔴 #FF6B6B | Couleur des lignes BSL |
| SSL Color | 🔵 #4ECDC4 | Couleur des lignes SSL |
| BOS Bull Color | 🟢 #00FF88 | Couleur BOS haussier |
| BOS Bear Color | 🔴 #FF4757 | Couleur BOS baissier |

### ICT Zones (FVG/BPR)
| Paramètre | Default | Description |
|-----------|---------|-------------|
| FVG Box | #FFE66D | Couleur des box FVG |
| BPR Box | #A855F7 | Couleur des box BPR |
| Daily Open | #818CF8 | Couleur du Daily Open |
| FVG Bull Candle | #FFD93D | Couleur bougie FVG haussier |
| FVG Bear Candle | #FF8C42 | Couleur bougie FVG baissier |

### Order Blocks
| Paramètre | Default | Description |
|-----------|---------|-------------|
| Show Order Blocks | ✅ | Afficher les OB filtrés |
| OB Confirmation Candles | 5 | Bougies pour confirmation |
| **OB Proximity (%)** | 0.5 | Distance max aux zones de liquidité |
| Bullish OB Box | #38BDF8 | Couleur OB haussier |
| Bearish OB Box | #FB7185 | Couleur OB baissier |

### Risk Management
| Paramètre | Default | Description |
|-----------|---------|-------------|
| Show SL/TP Levels | ✅ | Afficher les niveaux SL/TP |
| ATR Length | 14 | Période ATR |
| SL = ATR × | 1.5 | Multiplicateur pour le Stop Loss |
| Risk:Reward Ratio | 2.0 | Ratio risque/récompense |
| Account Size ($) | 10000 | Taille du compte |
| Risk per Trade (%) | 1.0 | Risque par trade |

---

## 📈 Stratégie de Trading

### Conditions d'Achat (BUY)
```
✅ Prix < Daily Open (Zone Discount)
✅ Dans une Killzone (Londres ou New York)
✅ BOS haussier récent (< 8 bougies)
✅ Présence d'un OB valide, BPR, ou FVG haussier
```

### Conditions de Vente (SELL)
```
✅ Prix > Daily Open (Zone Premium)
✅ Dans une Killzone (Londres ou New York)
✅ BOS baissier récent (< 8 bougies)
✅ Présence d'un OB valide, BPR, ou FVG baissier
```

### Critères de Validité des Order Blocks
Un OB est affiché (avec marqueur ✓) uniquement si :
```
✅ L'OB est à moins de 0.5% d'un niveau BSL ou SSL
   OU
✅ Un BOS récent confirme la direction de l'OB
```

---

## 🔔 Alertes Disponibles

| Alerte | Message |
|--------|---------|
| `ENTRY BUY OB` | High Probability Buy (Order Block) |
| `ENTRY SELL OB` | High Probability Sell (Order Block) |
| `ENTRY BUY BPR` | Buy Signal (BPR) |
| `ENTRY SELL BPR` | Sell Signal (BPR) |
| `ENTRY BUY FVG` | Buy Signal (FVG) |
| `ENTRY SELL FVG` | Sell Signal (FVG) |
| `ANY BUY SIGNAL` | Tout signal d'achat |
| `ANY SELL SIGNAL` | Tout signal de vente |

---

## 📋 Trading Journal

Un journal de trading HTML est inclus (`trading_journal.html`) pour enregistrer vos opportunités confirmées.

### Fonctionnalités
- ✅ Enregistrement des trades confirmés
- ✅ Statistiques automatiques (Win Rate, Total, etc.)
- ✅ Sauvegarde locale (localStorage)
- ✅ Export CSV pour analyse Excel
- ✅ Catégorisation par type de signal (OB/BPR/FVG)
- ✅ Suivi par session (London/NY/Asian)

---

## 📋 Installation

1. Ouvrir **TradingView**
2. Aller dans **Pine Editor** (en bas de l'écran)
3. Copier/coller le contenu de `indicateur.pine`
4. Cliquer sur **"Add to Chart"**
5. Activer le **Dark Mode** dans TradingView pour une expérience optimale

---

## ⚠️ Avertissement

Cet indicateur est un **outil d'aide à la décision**. Il ne garantit pas de profits et ne constitue pas un conseil financier. Utilisez-le en complément de votre propre analyse et gestion du risque.

---

## 📚 Concepts ICT Expliqués

### Order Block (OB)
La dernière bougie de couleur opposée avant un mouvement impulsif. Représente l'empreinte des ordres institutionnels.

> **v2.0** : Les OB sont maintenant filtrés pour n'afficher que ceux proches des zones de liquidité ou confirmés par un BOS.

### Fair Value Gap (FVG)
Un espace de prix non tradé entre 3 bougies consécutives. Zone d'inefficience où le prix tend à revenir.

> **v2.0** : Les bougies avec FVG sont maintenant colorées en jaune (bull) ou orange (bear).

### Balanced Price Range (BPR)
Le chevauchement entre un FVG haussier et un FVG baissier. Zone de haute probabilité car double confirmation.

### Break of Structure (BOS)
Cassure d'un swing high (bullish) ou swing low (bearish). Signale un changement potentiel de tendance.

> **v2.0** : Le BOS est maintenant encadré par un rectangle coloré avec bordure et texte.

### Killzones
Fenêtres temporelles où les mouvements institutionnels sont les plus probables (Londres, New York).

---

## 📁 Fichiers du Projet

| Fichier | Description |
|---------|-------------|
| `indicateur.pine` | Indicateur principal avec tous les visuels |
| `strategie.pine` | Version stratégie pour backtesting |
| `trading_journal.html` | Journal de trading interactif |
| `README.md` | Ce fichier de documentation |
