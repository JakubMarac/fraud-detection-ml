🧠 Credit Card Fraud Detection — Projekt edukacyjny

🎯 Cel projektu

Celem projektu jest wykrywanie transakcji fraudowych (oszustw kartowych) z wykorzystaniem klasycznych modeli uczenia maszynowego.
Projekt został wykonany w ramach nauki metod klasyfikacji i analizy niezrównoważonych danych (ang. imbalanced data).

Priorytetem oceny modeli było zwiększenie Recall (czułości), czyli minimalizacja liczby błędnie sklasyfikowanych oszustw (False Negative).

📊 Opis danych

W projekcie wykorzystano publiczny zbiór danych z transakcjami kartowymi:

Każda obserwacja reprezentuje pojedynczą transakcję z oznaczeniem 0 (transakcja prawidłowa) lub 1 (oszustwo).

Charakterystyka:

Dane silnie niezrównoważone — liczba fraudów stanowi poniżej 0.2% wszystkich przypadków,

Cechy zostały wcześniej przekształcone metodą PCA (anonimizacja danych finansowych),

Zmienna celu: Class

0 → normalna transakcja

1 → fraud

⚙️ Zastosowane metody

W projekcie zaimplementowano i porównano kilka klasyfikatorów:

Model	Resampling	Hiperparametryzacja	Metryka główna
Logistic Regression	SMOTE	RandomizedSearchCV	Recall
K-Nearest Neighbors (KNN)	SMOTE	GridSearchCV	Recall
Decision Tree	SMOTE	RandomizedSearchCV	Recall

Dodatkowo przetestowano warianty z parametrem class_weight='balanced'.

🧩 Przebieg pracy

Eksploracja danych (EDA) – analiza rozkładów i zrównoważenia klas.

Podział na zbiory train/test (stratyfikowany split).

Resampling danych metodą SMOTE – tylko wewnątrz foldów walidacji (bez „leaku”).

Uczenie modeli bazowych:

Logistic Regression,

KNN,

Decision Tree.

Hiperparametryzacja (GridSearchCV / RandomizedSearchCV).

Ewaluacja modeli:

macierze pomyłek,

metryki (Precision, Recall, F1-score, ROC-AUC, PR-AUC).

Porównanie wyników i wnioski.


🧠 Wnioski

W przypadku niezrównoważonych danych kluczowe jest użycie SMOTE lub ważenia klas.

Sama dokładność (accuracy) nie nadaje się do oceny — zamiast tego użyto Recall i PR-AUC.

Hiperparametryzacja (np. RandomizedSearchCV) poprawia wyniki o kilka punktów procentowych.

Modele drzewiaste mają tendencję do przeuczenia, dlatego stosowano ograniczenia (max_depth, ccp_alpha).
📌 Główny wniosek: model regresji logistycznej z class_weight='balanced' i dobranym C najlepiej wykrywa fraudy, mimo niskiej precyzji.

📚 Dalsze kroki

Przetestować modele ensemble: Random Forest, XGBoost, LightGBM

Dodać automatyczny raport w formacie .pdf

Spróbować oversamplingu metodą ADASYN

Przeprowadzić analizę wpływu progu decyzyjnego (threshold tuning)  
