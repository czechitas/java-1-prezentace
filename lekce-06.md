---
theme: default
background: https://java.czechitas.cz/data/prezentace/Czechitas-background.jpg
highlighter: prism
fonts:
  sans: 'Open Sans'
---

<div class="white flex flex-col mt-48 text-2xl font-light gap-2">
    <div class="font-bold text-6xl">Java 1 • lekce 6</div>
    <div>Filip Jirsák</div>
    <div>14. 3. 2023</div>
    <div>online</div>
</div>


---

# Typy „tříd“

* class, třída – obsahuje data i kód
  * dědit lze pouze od jedné třídy
* interface, rozhraní – definuje jen kontrakt, tj. dohodu, jaké metody má třída implementovat
  * lze implementovat více rozhraní
* enum – speciální typ třídy, obsahuje výčet hodnot (např. `JARO`, `LETO`, `PODZIM`, `ZIMA`)
* record – speciální typ třídy, obsahuje jenom data (používá se v podobných případech, jako Java Beany)
* anotace – speciální typ rozhraní, umožňuje přidávat uživatelské značky k třídám, metodám, fieldům, parametrům metod, balíčkům
* *abstraktní třída* – třída, která některé metody nemá implementované (jsou abstraktní)

---

# Kolekce (The Java Collections API)

* seznam prvků (objektů, instancí)
* nejčastější typy kolekcí:
  * seznam (list)
  * množina (set)
  * mapa, slovník (map)

---

# Generiky

* generická třída je obecná
* lze ji upřesnit pro konkrétní typ
* specifikace typů je ve špičatých závorkách `<>` za názvem třídy/rozhraní
* `List<?>` – seznam čehokoli
* `List<String>` – seznam stringů

---

# List

* uspořádaný seznam prvků
* prvky se mohou opakovat
* lze požadovat n-tý prvek v pořadí
* nejpoužívanější `ArrayList` a `LinkedList`

---

# ArrayList

* rychlý přístup k n-tému prvku
* pomalé přidání na začátek nebo doprostřed
* někdy pomalé přidání na konec

---

# LinkedList

* rychlý přístup k prvnímu nebo poslednímu prvku
* pomalý přístup k n-tému prvku – seznam se musí projít od začátku
* rychlé přidání na začátek nebo na konec
* může fungovat i jako fronta – přidávání na jeden konec, odebírání z druhého konce (FIFO – first in first out)
* může fungovat i jako zásobník – přidávání i odebíráí z jednoho konce (LIFO – last in first out)

---

<img src="/fronta-zasobnik.drawio.svg" width="700" />

---

# Set

* neuspořádaný seznam prvků
* prvky se nemohou opakovat
* nelze požadovat n-tý prvek v pořadí
* lze rychle zjistit, zda prvek je v množině
* nejpoužívanější `HashSet`

---

# Map

* seznam dvojic *klíč: hodnota*
* lze rychle hledat podle klíče
* nejpoužívanější `HashMap`