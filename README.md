StockWatch
StockWatch est une application légère et open source qui vous permet d'analyser en temps réel des actions grâce à des indicateurs techniques clés. Construit avec FastAPI et yfinance, ce mini-dashboard calcule et affiche le prix actuel, le RSI (14), le SMA(50) et le SMA(200) d’un stock, en y ajoutant un signal simple (Overbought / Undervalued). Chaque analyse est également loguée dans un fichier pour un suivi historique.

Fonctionnalités
Récupération de données : Récupère l’historique des cours d’une action (sur 6 mois) via l’API yfinance.

Calcul d'indicateurs techniques :

Prix actuel.

RSI (14 périodes).

Moyennes mobiles SMA(50) et SMA(200).

Signal simple : Détermine si une action est surachetée (RSI > 70) ou sous-évaluée (RSI < 30).

Visualisation : Génère un graphique combiné du cours et des indicateurs techniques à l’aide de matplotlib, encodé en base64.

Journalisation : Enregistre l'analyse dans un fichier texte (stock_analysis_log.txt) pour un suivi ultérieur.

API REST : Expose des endpoints via FastAPI pour interagir facilement avec l’application.

Prérequis
Python 3.7+

Les packages suivants (installables via pip) :

fastapi

uvicorn

yfinance

pandas

numpy

matplotlib

pydantic

Installation
Cloner le dépôt et se positionner dans le répertoire :

bash
Copier
git clone <URL_DU_DEPOT>
cd StockWatch
Créer un environnement virtuel (optionnel mais recommandé) :

bash
Copier
python -m venv venv
source venv/bin/activate   # Sur Windows : venv\Scripts\activate
Installer les dépendances :

bash
Copier
pip install fastapi uvicorn yfinance pandas numpy matplotlib pydantic
Vous pouvez aussi utiliser un fichier requirements.txt (si disponible) :

bash
Copier
pip install -r requirements.txt
Utilisation
Lancer l'application :

bash
Copier
uvicorn stockwatch:app --reload --host 0.0.0.0 --port 8000
Accéder à la documentation interactive :

Ouvrez votre navigateur à l’adresse http://localhost:8000/docs pour explorer les endpoints de l’API.

Analyser un ticker :

Envoyez une requête POST à l’endpoint /analyze_stock avec un JSON comme celui-ci :

json
Copier
{
    "ticker": "AAPL"
}
La réponse inclura :

Les indicateurs calculés (prix actuel, RSI, SMA50, SMA200, signal).

Une image encodée en base64 du graphique généré.

Logs :

Chaque analyse est enregistrée dans le fichier stock_analysis_log.txt avec la date, l’heure et les détails de l’analyse.

Structure du Projet
stockwatch.py : Fichier principal contenant l’implémentation de l’API FastAPI et du pipeline d’analyse.

stock_analysis_log.txt : Fichier log où sont stockées toutes les analyses.

requirements.txt : (Optionnel) Liste des dépendances pour le projet.

Contribuer
Les contributions sont les bienvenues ! Si vous souhaitez améliorer le projet ou ajouter de nouvelles fonctionnalités, merci de soumettre vos issues et pull requests via GitHub.

Licence
Ce projet est protégé par la Licence Exclusive "ProtègeMonTaf" v1.0. Pour plus de détails, consultez le fichier LICENSE.
