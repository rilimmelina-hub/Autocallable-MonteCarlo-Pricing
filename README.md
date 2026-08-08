📊 Autocallable Phoenix : Pricing & Hedging Engine
Ce projet est une simulation complète du cycle de vie d'un produit structuré en salle de marché (Equity Derivatives). Il couvre la structuration, le pricing par Monte Carlo, le calcul des Grecques et la mise en place d'une stratégie de couverture (hedging).

🎯 Contexte
Un client institutionnel souhaite un produit de rendement sur 3 ans indexé à l'Euro Stoxx 50, avec remboursement anticipé (Autocall), mémoire des coupons, et protection du capital sauf en cas de krach (> -40%).

⚙️ Modélisation et Méthodologie
Le payoff étant fortement path-dependent (mémoire des coupons, barrières discrètes), les formules fermées de type Black-Scholes sont inutilisables.

L'approche retenue est la Simulation de Monte Carlo sous la mesure risque-neutre Q :

Modélisation du sous-jacent par un Mouvement Brownien Géométrique (GBM).
Discrétisation d'Euler.
Implémentation de variables antithétiques pour réduire la variance de l'estimateur (division de l'erreur par ~3 sans surcoût CPU).
Calcul des Grecques (Delta, Vega) par méthode Bump and Reprice.

💻 Technologies utilisées
Python (NumPy, Matplotlib)
Concepts : Calcul Stochastique, Monte Carlo, Options Exotiques, Grecques.

📈 Résultats et Visualisations
1. Convergence du prix Monte Carlo
La simulation (400 000 trajectoires) converge vers une Fair Value de 97.83% du nominal.Convergence MC

2. Profil de Delta vs Spot
Le Delta n'est pas linéaire. On observe une chute brutale lorsque le sous-jacent approche de la barrière capital à 60% (risque de perte en capital).Profil Delta

📄 Rapport Complet
Le rapport détaillé (structuration, calcul des réserves, stratégie de delta/vega hedging dynamique) est disponible ici :👉 Lire le rapport PDF

🚀 Comment lancer le code
Cloner le dépôt.
Installer les dépendances : pip install numpy matplotlib
Lancer le script : `python autocall_pricing.py
