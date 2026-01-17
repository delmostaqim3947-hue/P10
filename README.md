import numpy as np

# --- ÉTAPE 1 : Définition des données ---
A = np.array([10, 20, 30, 40, 50])
M = np.array([
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12]
])

# --- ÉTAPE 2 : Indexation simple ---
valeur_specifique = M[1, 2]     # Ligne index 1, Col index 2 -> 7
dernier_A = A[-1]               # Dernier élément de A -> 50

# --- ÉTAPE 3 & 4 : Slicing (Plages de valeurs) ---
# Format : [début : fin_exclue]
segment_A = A[1:4]              # [20, 30, 40]
sous_bloc_M = M[0:2, 1:]        # Lignes 0-1, Colonnes 1 à la fin

# Extraire une colonne complète (la 3ème)
colonne_3 = M[:, 2]             # [3, 7, 11]

# --- ÉTAPE 6 & 7 : Vue vs Copie (Crucial) ---
# 1. La VUE : modifie l'original
vue = M[0:2, 1:3]
vue[0, 0] = 999                 # Ceci modifie M[0, 1] !

# 2. La COPIE : indépendante
M_original = np.array([[1,2,3,4],[5,6,7,8],[9,10,11,12]]) # Reset
copie = M_original[0:2, 1:3].copy()
copie[0, 0] = 888               # M_original ne change pas.

# --- ÉTAPE 8 : Exercice d'application ---
# Multiplier la dernière colonne par 10
M[:, -1] = M[:, -1] * 10

print("Matrice M finale :\n", M)
