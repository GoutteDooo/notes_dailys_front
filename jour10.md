# Objectifs journaliers

## 16/12/2024

### DOM :

- [x] Comprendre le DOM (https://javascript.info/browser-environment)
  - [x] Comprendre la façon dont il est construit.
  - [x] Comprendre sa structure.
  - [x] Comprendre l'auto-correction du DOM.
- [x] Savoir naviguer dans le DOM :
  - [x] documentElement
  - [x] childNodes
  - [x] firstChild
  - [x] lastChild
  - [x] siblings
- [x] Savoir récupérer des éléments du DOM :
  - [x] querySelector
  - [x] getElement..
  - [x] Comprendre le principe de 'Live-Collection'.

---

# Savoir naviguer dans le DOM

## documentElement

- Représente l'élément racine du document HTML (la balise <html>)

## childNodes

- Renvoie une liste de tous les noeuds enfants d'un élément, y compris les espaces vides et les retours à la ligne (car ce sont des noeuds de texte)
  - Par exemple :

```html
<div id="container">
  <p>Paragraphe 1</p>
  <p>Paragraphe 2</p>
</div>
```

```js
const container = document.getElementById("container");
console.log(container.childNodes); // Renvoie une NodeList contenant les nœuds enfants (y compris les textes).
```

```log
NodeList(5) [text, <p>, text, <p>, text]
```

- **Où les noeuds text correspondent aux retours à la ligne ou espaces dans le HTML**

## firstChild & lastChild

- firstChild renvoie au premier noeud enfant
- lastChild, au dernier

## Siblings

- nextSibling renvoie au **node** suivant (prend en compte les nodes textes)
- previouSibling "" précédent
- nextElementSibling renvoie à l'**élément** suivant
- previousElementSibling "" précédent

# Savoir récupérer les éléments du DOM

## querySelector

- Sélectionne le premier élément trouvé correspondant à un sélecteur CSS.
  - **RETOURNE** un élément HTML ou `null` si aucun élément trouvé
- **querySelectorAll** sélectionne tout les éléments correspondant à un sélecteur CSS
  - **RETOURNE** une **NodeList** (statique, contrairement à la Live Collection)

## getElement...

### ...byID

- Sélectionne un élément unique en fonction de son attribut `id`
  - **RETOURNE** un élément HTML ou `null` si aucun élément trouvé.

### ...byClassName

- Sélectionne tous les éléments ayant une classe spécifique
  - **RETOURNE** une **Live Collection** (à voir en dessous)

### ...byTagName

- Sélectionne tous les éléments d'un type de balise spécifique (par ex, tous les `<p>` ou `<div>`)
  - **RETOURNE** une **Live Collection**

## Live-Collection

- Qu'est-ce que c'est ?
- C'est une **collection dynamique** qui se met à jour automatiquement si des éléments sont ajoutés ou supprimés du DOM. (getElementsByClassName)

- Il y'a une différence cruciale avec la **NodeList** qui est une **collection statique**. Elle ne se met donc pas à jour après sa création. (querySelectorAll)

## Conseils

- Il est plus pertinent d'utiliser `querySelector` ou `querySelectorAll` car plus modernes et supportent les sélecteurs CSS modernes.
- Eviter d'utiliser les `Live Collections` sauf en cas de besoin de comportement dynamique.
