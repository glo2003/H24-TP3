[← Retour](../README.md)

# Tests

## Tests unitaires

Vous devez continuer à effectuer des tests unitaires pour l'ensemble de la logique de votre code.

## Tests d'intégration de persistence

Vous devez tester **toutes** vos fonctions de persistance, de la sauvegarde aux requêtes de filtrage. Afin de garantir que vos implémentations *Mongo* et *in-memory* respectent les mêmes exigences, vous pouvez vous inspirer de la technique des tests abstraits, qui sera présentée dans un laboratoire. Cette méthode requiert que les classes testées implémentent une même interface et permet de définir l'ensemble des tests une seule fois, peu importe les implémentations.

### Librarie TestContainers

Pour éviter d'avoir à installer et à supprimer manuellement la base de données entre chaque test, vous utiliserez la librairie [TestContainers](https://java.testcontainers.org/). Celle-ci utilise Docker pour démarrer automatiquement des versions conteneurisées de Mongo pour chaque test.

## Clean code

L'ensemble de vos tests doit continuer de respecter les meilleures pratiques en matière de Clean Code.
