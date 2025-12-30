# 📘 Manuel d'Utilisation : ICT Assistant Expert

## 1. Installation

### A. Indicateur Visuel (Pour trader)
1. Ouvrez le fichier `indicateur.pine`.
2. Copiez tout le code.
3. Dans TradingView, ouvrez "Pine Editor" (en bas).
4. Collez le code et cliquez sur **"Add to Chart"**.
5. Sauvegardez le script sous le nom "ICT Visual Assistant".
> **⚠️ Important :** L'indicateur est configuré pour n'afficher les signaux QUE sur **EURUSD** et **GBPUSD**. Sur d'autres paires, un message d'avertissement apparaîtra.

### B. Stratégie Backtest (Pour tester)
1. Ouvrez le fichier `strategie.pine`.
2. Copiez tout le code.
3. Dans TradingView, ouvrez un nouvel onglet Pine Editor.
4. Collez le code et cliquez sur **"Add to Chart"**.
5. Vous verrez apparaître les flèches d'achat/vente et le **Strategy Tester** en bas s'ouvrira.

---

## 2. Nouvelles Fonctionnalités

### 📊 Dashboard Multi-Timeframe (MTF)
Le panneau de droite affiche maintenant deux nouvelles lignes :
- **H1 Trend** : Tendance sur 1 heure (🟢 Bull / 🔴 Bear)
- **H4 Trend** : Tendance sur 4 heures (🟢 Bull / 🔴 Bear)
> **Conseil :** Cherchez des signaux M15 qui sont alignés avec la tendance H4 pour augmenter votre probabilité de succès.

### 📋 Journal de Trading Semi-Automatique
1. Créez une alerte sur l'indicateur.
2. Choisissez l'option **"Any function call"**.
3. Quand l'alerte sonne, copiez le message JSON.
4. Ouvrez `trading_journal.html`.
5. Cliquez sur **"Import Signal"** et collez le message.

---

## 3. Comment faire un Backtest ?

1. Affichez le script **"ICT Assistant: Backtest Strategy"** sur votre graphique.
2. Ouvrez les paramètres du script (rouage).
3. Allez dans la section **"Backtesting Date Range"**.
4. Définissez une date de début et de fin.
5. Observez les résultats dans l'onglet **"Strategy Tester"** en bas de TradingView :
   - **Net Profit** : Gain total.
   - **Percent Profitable** : Taux de réussite.
   - **Max Drawdown** : Pire baisse du capital.

> **Note :** La stratégie prend les trades automatiquement selon les mêmes règles que l'indicateur visuel (Killzone + BOS + OB/FVG).

---

## 4. Astuces de Pro

*   **Mode "Replay" :** Utilisez le mode Bar Replay de TradingView couplé à l'indicateur visuel pour vous entraîner à voir les setups se former en temps réel.
*   **Filtre de Tendance :** Si le Dashboard indique **H4 BEAR**, évitez les signaux d'achat (Longs) même si un OB apparait, sauf si vous êtes experts en contre-tendance.
