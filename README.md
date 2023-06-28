# Spécification du Composant HMACSHA512 en C++ et Python

## Auteurs
Ali BOUKHELIFA 

## Historique des versions
| Version | Date       | Description                 |
|---------|------------|-----------------------------|
| 1.0     | 29/05/2023 | version initiale|

## Description

### Contexte
Le composant HMACSHA512 implémente la fonction de hachage HMAC-SHA512 (Hash-based Message Authentication Code using SHA-512) en Python. Cette fonction permet de générer un code d'authentification de message en utilisant une clé secrète et l'algorithme de hachage SHA-512.

### En détails : 

Ce composant est utilisé dans les systèmes de sécurité et de vérification d'intégrité des données. Il peut être utilisé pour vérifier l'authenticité d'un message et détecter toute altération ou manipulation.
Schéma bloc incluant les composants connexes: [Vous pouvez fournir un schéma bloc décrivant la place du composant HMACSHA512 dans le système ou l'architecture globale.]
Interface et interaction avec chaque autre composant: Le composant HMACSHA512 peut être utilisé indépendamment des autres composants. Il prend en entrée un message et une clé secrète, et renvoie le code d'authentification HMAC-SHA512 correspondant.
Résumé: Déclarations de fonctions Python d'interface et leurs arguments:
Fonction generate_hmac_sha512(message: bytes, key: bytes) -> bytes: Cette fonction prend un message (sous forme de bytes) et une clé secrète (sous forme de bytes) en entrée, et renvoie le code d'authentification HMAC-SHA512 correspondant (sous forme de bytes).
Cas d'erreurs: Le composant peut générer une exception Python en cas d'erreur, par exemple, si le message ou la clé sont de mauvais types, ou si une erreur se produit lors du calcul du code d'authentification.

### Schéma bloc incluant les composants connexes
```
[Application] --> [HMACSHA512 Composant] --> [SHA512]
```
L'application interagit avec le composant HMACSHA512, qui à son tour utilise le composant SHA512.

### Que fait le composant HMACSHA512 ?
Le composant HMACSHA512 implémente la fonction de hachage HMAC-SHA512 en utilisant l'algorithme de hachage SHA-512. Cette fonction permet de générer un code d'authentification de message en utilisant une clé secrète. Le code d'authentification HMAC-SHA512 est utilisé pour vérifier l'authenticité et l'intégrité des données.

Quelles sont ses interfaces ?
Le composant HMACSHA512 expose une interface sous la forme d'une fonction Python:
def generate_hmac_sha512(message: bytes, key: bytes) -> bytes:
    """
    Génère le code d'authentification HMAC-SHA512 pour un message donné et une clé secrète.

    Arguments:
    - message: Le message à authentifier, sous forme de bytes.
    - key: La clé secrète utilisée pour l'authentification, sous forme de bytes.

    Retourne:
    Le code d'authentification HMAC-SHA512, sous forme de bytes.
    """


### Cas d’erreurs
Le composant HMACSHA512 peut générer des exceptions Python dans les situations suivantes:
Si le message ou la clé fournis ne sont pas de type bytes, une exception de type TypeError sera levée. Vous pouvez gérer cette exception en vérifiant le type des arguments avant de les utiliser.
Si une erreur se produit lors du calcul du code d'authentification, une exception de type Exception sera levée. Vous pouvez gérer cette exception en affichant un message d'erreur approprié ou en propageant l'exception vers le niveau supérieur.

## Test

### Plan de test
Pour tester le composant HMACSHA512, vous pouvez suivre les étapes suivantes:
Importez le composant dans votre programme de test.
Utilisez la fonction generate_hmac_sha512() avec différents jeux de données de test pour générer les codes d'authentification HMAC-SHA512.
Comparez les résultats obtenus avec des valeurs de référence pour vérifier si les codes d'authentification sont corrects.
Affichez le résultat du test (passé ou échoué) pour chaque jeu de données de test.

On peut aussi tester la fonction en utilisant différents cas de test :       
            Des données d'entrée valides avec une clé secrète valide.
            Des données d'entrée vides avec une clé secrète valide.
            Des données d'entrée valides avec une clé secrète vide.

### Programme de test
```python
import hmac
import hashlib

def generate_hmac_sha512(message: bytes, key: bytes) -> bytes:
    return hmac.new(key, message, hashlib.sha512).digest()

# Test cases
test_cases = [
    {
        'message': b'Hello, world!',
        'key': b'secret_key',
        'expected_hmac': b'\x04\x82K\xfc\x11N#\x98\xe4\x97\x05d\xdb\xb1x\x80\xc2\xd7\xe4a2r+\x90\xff\xabI#\x05\xec\xe1\x9d\xd5\xf0\xcc\x04\xc9L\x8eJ\xe0\x82\xa3\x9f\x84\xeb\x14V\xd5\xe7d\x1e\x90',
    },
    # Add more test cases here
]

# Run the tests
for i, test_case in enumerate(test_cases):
    hmac_result = generate_hmac_sha512(test_case['message'], test_case['key'])
    if hmac_result == test_case['expected_hmac']:
        print(f"Test case {i+1}: Passed")
    else:
        print(f"Test case {i+1}: Failed")


```
### Mode d'emploi
Pour exécuter les tests, utilisez simplement la commande `python -m test test_hmac_sha512`. 
Après avoir définit les données d'entrée et la clé secrète, on appelle la fonction hmac_sha512 en fournissant les données et la clé secrète en tant qu'arguments.
