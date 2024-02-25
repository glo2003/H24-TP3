[← Retour](../README.md)

# Déploiement continu (CD)

Vous devez *packager* votre application et la téléverser dans un registraire afin de pouvoir facilement, uniformément et rapidement utiliser votre application dans n'importe quel environnement.

## *Packaging* avec Docker

En Java, il y a plusieurs façons de *packager* et distribuer une application. La méthode classique consiste à générer un fichier `.jar`, qui correspond à une archive pré-compilée du code. Ce fichier est ensuite interprétable sous différents environnements Java. Cependant, les étapes pour construire un JAR sont souvent obscures et les dépendances ne sont pas toujours bien liées. De plus, les nouvelles versions majeures de Java sont de plus en plus courantes, et même si la majorité du code reste *backward-compatible*, ce n'est pas toujours le cas.

Ainsi, afin de mieux assurer le comportement de l'application, vous la déploierez dans une image Docker. Notez que le fichier de configuration `Dockerfile` vous est déjà fourni et **ne doit pas être modifié**.

## Déploiement (Github Actions)

La construction et le déploiement de votre image Docker doivent se faire à l'aide d'un pipeline automatisé avec Github Actions. Votre déploiement doit se faire :

- À chaque nouveau commit sur votre branche principale
- À chaque nouveau tag
- Manuellement (déploie le dernier commit)

Il est également **absolument impératif** que l'image :

- soit publiée sur le *registry* `ghcr.io` (celui de Github)
- possède le même nom que le repository (en minuscules)
- soit *taggée* avec le hash du commit et, s'il y a lieu, le nom du tag git.

Voici une ressource qui pourrait vous aider : <https://docs.github.com/en/actions/publishing-packages/publishing-docker-images>.

## Variables d'environnement

Finalement, lorsqu'on déploie, on ne peut pas toujours prévoir sur quel port l'application pourra s'exécuter. Il s'agit souvent d'une valeur déterminée par le *runner* (serveur hôte) en fonction des autres applications déjà en cours d'exécution. Ainsi, vous devez récupérer la variable d'environnement `PORT` et démarrer l'application sur ce port. Si vous ne la recevez pas, utilisez la valeur `8080`. Pour la valeur du `host`, utilisez toujours `0.0.0.0`.
