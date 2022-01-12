# ml-ops-guideline
MLOps guideline how to make your ml project suitable for production


- Test Unitaire des modules pour comprendre ce qu'il se passe car c'est essentiellement technique => surtout penser que demain je ne serais plus

- Ne doit pas être dupliqué (dans un dommaine)
  - le code d'inference 
  - le code de pre-processing
  - le code de post-processing

- Dans l'artifact du model, il faut pousser tout ce qui est nécéssaire à l'inférence :
Par exemple pour un yolov4, il faut le model, la config et la liste des labels
le model : model.weights, yolov4.cfg, obj.data 

Pourquoi => parce que demain si quelqu'un retouche le projet il ne verra peut être pas toutes les duplication et créera des bug

- Le scoring doit utiliser le code d'inférence qui sera hébergé en production
  - si la production est en CPU le scoring doit être réalisé avec du CPU
  - si la production est en GPU le scoring doit être réalisé avec du GPU

Pourquoi => le scoring qui sera annoncé au métier ne sera pas le bon, le même que en production
