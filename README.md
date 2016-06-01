Résumé de Siyao 25 mai
===================

Jusqu'au 25 Mai, j'ai finis de implémenter le DANN pour les données EEG, et aussi refaire les expériences réaliser par Vincent et Ilaï.

----------


 <i class="icon-hdd"></i>Travail réaliser 
-------------

Je vais lister les travails réaliser dessous:

> **Liste:**

> - Apprendre Lua et Torch pour implémenter les DANN.
> - Lire la rapport et discuter avec Gaetan pour comprendre le structure de auto-encoder.
> - Faire marcher les code
> - Chercher et trouver le librairie **csvigo** pour traiter les données produit
> - Utiliser **seaborn** et **matplotlib** pour visualizer le résultats   

----------

<i class="icon-file"></i> Résultat 
-------------

Il y a deux expériences dans le rapport.


####<i class="icon-folder-open"></i> Expérience 1

Le expé 1 est trouver le relation entre le learning rate, si learning rate est plus grand, le vitesse de êntraine est plus vite mais il risque que le procédure d'êntraine est moins de précise. donc le rapport propose 6 stratégies différent pour le valeur de learning rate.
 > - η = 1 (exp1) or 0.1 (exp2)

>- η(nepoch) = 1/√nepoch (exp3) or 0.1/√nepoch (exp4)

> - η(nepoch) = 1/nepoch (exp5) or 0.1/nepoch (exp6)

J'ai ajouté le exp7 qui est un idée de Gaetan, si l'erreur diminue, puis multiplier le taux d'apprentissage précédent de 1,2; d'autre, diviser par 2. Voilà le résultat


![](https://cloud.githubusercontent.com/assets/3332561/15592961/395d8f1c-23a8-11e6-90e2-93b0b3c618ca.png)

on peut voir que cette schéma est présque le même comme en rapport, le nouveau exp7 est me semble mieux parceque il converge plus vite est le érreur est petit.
#### <i class="icon-pencil"></i> Expérience 2

Exp2 est manipuler le structure de NN, notre structure est 56-n-56, donc on veut voir si on change le n, comment le performance de NN.

![](https://cloud.githubusercontent.com/assets/3332561/15592962/39625498-23a8-11e6-9868-b730bad3092d.png)
<center> Reconstruction loss per number of units D in a single hidden layer, with different values of λ.</center>

Comme on voie, le Reconstruction loss ne dépend pas de hidden units number. et sur le rapport, si D est entre 47 et 56, c'est possible que le loss devient 0 sans reason. Mais je peut pas pu reprodu le résultat comme rapport, je pense mon résultat est plus logique.


![](https://cloud.githubusercontent.com/assets/3332561/15592960/395a3862-23a8-11e6-802e-8545c883803e.png)
<center> Domain classifier loss per number of units D in a single hidden layer, with different values of λ.</center>
Le domain classifier loss est un constant pour D différents, mais pour le Domain Lambda de 10, le loss varie entre -1.9 et 55, ça est un phénomène bizarre.

![](https://cloud.githubusercontent.com/assets/3332561/15705499/e772b500-27ef-11e6-8d15-8b2e836a181b.png)
<center> reconstruction error et discrimination error en cas de lambda differents </center>

Pour visualiser le front de pareto. 
