# ml-ops-guideline
MLOps guideline how to make your ml project suitable for production


## Règle a vérifier pour valider une PullRequest

- Python 3.8 minimum

Pourquoi => pour des raisons de sécurité (version non maintenu) et d'obsolecenses des applications (mise à jour trés coûteuse)

- Test Unitaire des modules pour comprendre ce qu'il se passe car c'est essentiellement technique => surtout penser à son collègue qui reprendra le projet quand vous ne serrez pas ou plus là

- Le code + dépendance (indérence, pre-proecessing, post-processing) qui sera en production doit être le même exactement que pour le train
Pourquoi => Le projet ne fonctionnera pas ou pas comme attendu en production

- Ne doit pas être dupliqué (dans un domaine fonctionel)
  - le code d'inference 
  - le code de pre-processing
  - le code de post-processing

Pourquoi => parce que demain si quelqu'un retouche le projet il ne verra peut-être pas toutes les duplications et créera des bogues

- Dans l'artifact du model, il faut pousser tout ce qui est nécéssaire à l'inférence :
Par exemple pour un yolov4, il faut le model, la config et la liste des labels
le model : model.weights, yolov4.cfg, obj.data 

Pourquoi => parce que demain si quelqu'un retouche le projet il ne verra peut-être pas toutes les duplications et créera des bogues

- Le scoring doit utiliser le code d'inférence qui sera hébergé en production
  - si la production est en CPU le scoring doit être réalisé avec du CPU
  - si la production est en GPU le scoring doit être réalisé avec du GPU

Pourquoi => le scoring qui sera annoncé aux utilisateurs ne sera pas le bon, le même que en production
