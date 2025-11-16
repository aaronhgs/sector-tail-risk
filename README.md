# Uncovering Non-Linear Joint Tail Events in Sector Pairs Using Mutual Information

## Overview

This project investigates non-linear joint tail dependencies across U.S. equity sectors using Mutual Information (MI), and compares its effectiveness to traditional Pearson correlation. While correlation captures only linear co-movement, MI uncovers deeper, asymmetric, and tail-driven relationships that are often hidden, especially during market stress.

The research covers the following:

- How sector dependencies evolve over time using a rolling-window MI  
- Which sector pairs exhibit large dependency gaps, defined as MI - correlation  
- How sector spreads behave during joint tail events (bottom 5% returns)  
- Whether KDE (Kernel Density Estimation) reveals asymmetric tail behaviours  
- The network centrality of sectors using a Minimum Spanning Tree (MST) based on MI

The findings show that mutual information consistently outperforms correlation in detecting hidden dependencies, asymmetric behaviours, and paired crashes during extreme market conditions.

---

## Data

- 12 U.S. equity sectors  
- 1252 unique stocks  
- Cleaned and aligned daily price series (2006–2014)  
- Returns transformed into log returns to ensure stationarity  
- Sector-level time series constructed by averaging log returns across stocks  

---

## Methodology

### 1. Pre-Processing
- Combined individual ticker files into 12 sector-level datasets  
- Converted closing prices into log returns
- Removed unmatched dates and aligned sectors on a common index  
- Constructed sector return series representing each industry’s average daily performance  

### 2. Mutual Information vs Correlation
Dependency for every sector pair was measured using:

- Pearson correlation (linear dependence)  
- Mutual Information (non-linear dependence)

A rolling 60-day window was used to track how dependencies evolve across market regimes.  
Focus was given to periods where both sectors’ returns were in the bottom 5% quantile, representing joint tail events.

### 3. Dependency Gap & Pair Selection
For each pair:
- MI and correlation were averaged during tail events  
- The dependency gap (MI – correlation) was computed  
- Pairs with the highest gaps were selected for deeper analysis  
  (removing overlapping/duplicate sectors)

### 4. Kernel Density Estimation (KDE)
For the top sector pairs, KDE was used to model the spread distribution during joint tail events:

- Captures asymmetry (which sector underperforms)  
- Highlights multimodality and non-linear behaviours  
- Visualises hidden co-movement patterns correlation cannot detect  

### 5. Minimum Spanning Tree (MST)
To understand the broader dependency structure:

- An MST was constructed using inverse MI as edge weights 
- Highly central sectors (low MI-distance) appear as hubs  
- Capital Goods sector emerged as a central node which was consistent with the KDE results. Suggests that it absorbs systemic risk during market stress  

---

## Key Findings

- Mutual Information increases more sharply than correlation during 5% tail events, showing stronger sensitivity to regime changes and hidden dependencies.
- Sector pairs with high dependency gaps exhibit asymmetric spread behaviour in KDEs.
- Across selected pairs, one sector consistently underperforms during crashes, revealing directional co-movement.
- Capital Goods repeatedly appears in high-MI pairs and sits at the centre of the MI-based MST, suggesting it acts as a risk-absorbing hub.
- KDE distributions for all selected pairs successfully pass the Anderson–Darling test when compared to a left-skewed Gumbel distribution, validating the modelling of extreme-value behaviour.

