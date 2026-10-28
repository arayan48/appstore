# Apps arayan48

Store d'applications pour ZimaOS (et CasaOS), au format v2 du
[store officiel](https://github.com/IceWhaleTech/CasaOS-AppStore). Il est publié sur GitHub Pages à chaque
modification de `main`.

| App | Description |
| --- | --- |
| [Flyto](https://github.com/arayan48/flyto) | Partage de fichiers auto-hébergé |

## Ajouter le store à ZimaOS

1. Ouvre l'**App Store** de ZimaOS, puis le menu des sources (bouton à côté de la recherche).
2. Ajoute cette adresse :

   ```
   https://arayan48.github.io/appstore/store.json
   ```

3. Les apps du store apparaissent avec les autres. Quand une nouvelle version est publiée ici,
   ZimaOS propose la mise à jour depuis l'App Store.

## Ajouter une application

1. Crée un dossier `Apps/<NomDeLApp>/` avec :
   * `docker-compose.yml` : la configuration Docker habituelle, plus un bloc `x-casaos` à la fin
     (voir [Apps/Flyto/docker-compose.yml](Apps/Flyto/docker-compose.yml)) ;
   * `icon.png` ou `icon.svg`, et si possible `screenshot-1.png`.
2. Dans `x-casaos`, donne un `id` unique (`io.github.arayan48.<app>`), une `category` parmi
   `Media`, `Productivity`, `Home`, `Networking`, `AI`, `Finance`, `Social`, `Developer`, `Others`,
   et une `version` au format `1.2.3`.
3. Ouvre une PR : le workflow *Validate* vérifie le compose et construit le store. Une fois fusionnée,
   *Publish* met le store en ligne.

Pour une nouvelle version d'une app, change le tag de l'image, `version` et `update_at` : ZimaOS
détecte le changement et propose la mise à jour.

Le détail des champs est dans la
[documentation du format](https://github.com/IceWhaleTech/CasaOS-AppStore/blob/main/docs/specs/compose-and-x-casaos.md).

## Flyto

`Apps/Flyto` est mis à jour automatiquement par la release de Flyto (workflow *Build and Release* du dépôt
[arayan48/flyto](https://github.com/arayan48/flyto)), qui pousse ici avec une clé de déploiement.
