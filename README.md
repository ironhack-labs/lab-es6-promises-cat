![logo_ironhack_blau 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# LAB | #Prometeu-me un sopar

## Introducció

A causa de la naturalesa asíncrona de JavaScript, les promeses i les devolució de trucades són molt importants. Tots dos ens permeten controlar el flux de les operacions i executar tasques en seqüència.

<p align="center">

<img src="https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-cover.png" alt="Lab Promise me sopar - resultat final" width="500"/>

<p>

## Requisits

- Bifurca aquest repo
- Clona aquest repo

## Submissió

En finalitzar, executeu les ordres següents:

```shell
$ git add .
$ git commit -m "done"
$ git push origin master
```

Creeu Pull Request perquè els vostres TA puguin comprovar el vostre treball.

## Instruccions

### Iteració 0 | El codi d'inici

Us hem proporcionat un codi d'inici:

- `javascript/data.js` : conté quatre matrius amb passos per preparar 4 aliments diferents: _puré de patates_ , _bistec_ , _cols de Brussel·les_ i _bròquil_ .

- `javascript/getInstruction.js` : conté una funció **`getInstruction`** que **utilitza devolucions** de trucada per recuperar de manera asíncrona els passos d'instrucció per a qualsevol aliment. Utilitza `setTimeout` per imitar una operació asíncrona.

  ```js
   getInstruction(food, step, callback, errorCallback)
  ```

  :exclamation: **No hauríeu de fer cap canvi en aquest fitxer.**

- `javascript/obtainInstruction.js` : té una funció **`obtainInstruction`** que **utilitza promeses** per recuperar de manera asíncrona els passos d'instrucció per a qualsevol aliment. També utilitza `setTimeout` per imitar una operació asíncrona.

  ```js
   obtainInstruction(food, step)
  ```

  :exclamation : **tampoc no hauríeu de fer cap canvi a aquest fitxer.**

- `javascript/index.js` : en aquest fitxer hem deixat un exemple per mostrar-vos com s'ha d'executar el codi. Tanmateix, el codi proporcionat encara no utilitza devolucions de trucada ni promeses imbricades, per _això_ els passos no s'imprimiran en l'ordre correcte. La vostra tasca a la primera iteració serà fer-ho correctament, però en parlarem més endavant.

- `index.html` : conté una estructura HTML bàsica necessària, de manera que no cal afegir-hi cap codi. Els fitxers JavaScript esmentats anteriorment ja estan enllaçats a `index.html` . El `data.js` carrega primer per assegurar-se que les matrius que contenen instruccions ja estan carregades i es poden utilitzar en altres fitxers, on les necessitem.  
  :exclamation: **no hauríeu de fer cap canvi a aquest fitxer.**

### No sincronitzat

**Hauríeu d'escriure el vostre codi _només_ al fitxer `javascript/index.js` .**

Ara, obriu el fitxer i mireu el codi d'inici que s'hi proporciona. El codi proporcionat no utilitza devolucions de trucada imbricades per aplicar una seqüència d'execució, per això els passos no es mostren en l'ordre correcte.

Avança i obriu la pàgina `index.html` al navegador. Observeu com els passos de cocció es mostren fora d'ordre.

<details><summary> <b>Captura de pantalla</b> </summary>

![Passos fora de sincronització](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-out-of-sync.gif)

</details>

:exclamation: abans de començar a treballar en la iteració 1, comenta el codi inicial a `javascript/index.js` .

<br/>

## Iteració 1 | Feu el puré de patates amb trucades

Utilitzant devolucions de trucada imbricades, imprimiu els passos de cocció per fer puré de patates en l'ordre correcte. Escriviu el vostre JavaScript al fitxer `javascript/index.js` proporcionat. Una vegada més, un recordatori de no alterar el fitxer `getInstruction.js` .

```javascript
// Iteration 1 - using callbacks
getInstruction('mashedPotatoes', 0, (step0) => {
  document.querySelector("#mashedPotatoes").innerHTML += `<li>${step0}</li>`
  // ... Your code here
    // ...
});
```

Després de l'últim pas, hauríeu de mostrar un``- ``addicional amb el text: El `Mashed potatoes are ready!` .

<details><summary> <b>Resultat Esperat</b> </summary>

![Resultat esperat de la iteració 1](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-1-result.gif)

</details>

## Iteració 2 | Apostar amb promeses

Utilitzant promeses i la declaració `then()` imprimiu les instruccions per mostrar les instruccions de cuina de l'estaca en l'ordre correcte. Aquesta vegada, haureu de cridar a la funció `obtainInstruction` que retorna una promesa pendent.

Continueu treballant al `javascript/index.js` . No hauríeu d'alterar el fitxer `obtainInstruction.js` .

```javascript
// Iteration 2 - using promises
obtainInstruction('steak', 0)
  .then( (step0) => {
    document.querySelector("#steak").innerHTML += `<li>${step0}</li>`
    //  ... Your code here
  })
  // ... Your code here
```

Després de l'últim pas, hauríeu de mostrar un `<li>` addicional amb el text: La `Stake is ready!` .

<details><summary> <b>Resultat Esperat</b> </summary>

![Resultat esperat de la iteració 2](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-2-result.gif)

</details>

## Iteració 3 | Feu el bròquil amb async/wait

Utilitzant promeses amb la sintaxi `async` i `await` imprimiu les instruccions per fer cols de Brussel·les en l'ordre correcte. Necessitareu la funció `obtainInstruction` que retorna una promesa pendent.

```javascript
async function makeBroccoli() {
  // ... Your code here
}
```

Després de l'últim pas, hauríeu de mostrar un `<li>` addicional amb el text: El `Broccoli is ready!` .

<details><summary> <b>Resultat Esperat</b> </summary>

![Resultat esperat de la iteració 3](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-3-result.gif)

</details>

## Bonificació 1

Quan el menjar específic estigui llest per ser servit (s'enumeren tots els passos), elimineu l'atribut `hidden` de l'element `<img />` que representa el menjar, de manera que es mostri la imatge.

<details><summary> <b>Resultat Esperat</b> </summary>

![Resultat esperat de la iteració de bonificació 1](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-bonus-1-result.gif)

</details>

## Bonificació 2

Amb `Promise.all` mostreu els passos de cocció per fer les cols de Brussel·les en l'ordre correcte.

Després de l'últim pas, hauríeu de mostrar un `<li>` addicional amb el text: `Brussels sprouts are ready!` .

**El resultat final hauria de ser així, amb tots els passos de cocció que es mostren en l'ordre correcte** :

![Resultat esperat de la iteració de bonificació 2](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/labs/lab-promise-me-dinner-bonus-2-result.gif)

<br/>

**Feliç codificació!** :blue_heart: