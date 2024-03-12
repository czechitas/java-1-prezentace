---
theme: default
background: https://java.czechitas.cz/data/prezentace/Czechitas-background.jpg
highlighter: prism
fonts:
  sans: 'Open Sans'
---

<div class="white flex flex-col mt-48 text-2xl font-light gap-2">
    <div class="font-bold text-6xl">Java 1 • lekce 8</div>
    <div>Filip Jirsák</div>
    <div>5. 3. 2024</div>
    <div>online</div>
</div>

---

# Optional

* `java.util.Optional<T>`
* lepší náhrada za `null`
* explicitně říká „návratová hodnota nemusí existovat“
* např. `Optional<String> email`

---

# Optional – vytvoření

* `Optional.empty()`
* `Optional.of()`
* `Optional.ofNullable()`

---

# Optional – zjištění přítomnosti hodnoty

* `Optional.isPresent()`
* `Optional.isEmpty()`

---

# Optional – čtení

* `Optional.get()`
* `Optional.orElse()`
* … a další

---

# Lambda výrazy

Samostatné metody, bez jména a bez objektu.

* `(x, y) -> x + y`
* ```java
  (x, y) -> {
    if (x > y) {
      return x;
    } else {
      return y;
    }
  }
  ```
* Pokud je parametr jeden, mohou se kulaté závorky vynechat
  * `text -> System.out.println(text)`
* Tam, kde se očekává lambda výraz, můžu vložit odkaz na metodu: `this::metoda`

---

# „Fluent“ zápis kódu

Návratová hodnota se neukládá do proměnné, ale hned se na ní volá další metoda. Pozor na `null` hodnoty!

```java
seznam.filter(…).sort().print(…);

seznam
  .filter(…)
  .sort()
  .print(…);
```

* Vezmi seznam, vyber z něj jen některé prvky, výsledek rovnou seřaď, výsledek rovnou vypiš.
* Středník je až za posledním příkazem v řadě.
* Výše uvedené je jen ukázka, ne všechny uvedené metody v Javě existují.


---

# Streamy 1

Stream je potenciálně nekonečný seznam – podporuje funkci „dej mi další hodnotu“.

* Neplést s IO streamy – ty slouží pro čtení a zápis do souborů nebo komunikaci po síti.
* Je možné je vytvořit např. z `List`u.
* Podpora pro funkcionální programování.
* `java.util.Stream<T>`

---

# Streamy 2

```java
Stream<Svatek> svatky = …;

svatky
  .filter( /* funkce pro filtrování */ )
  .sorted( /* funkce pro porovnání dvou prvků */))
  .forEach( /* funkce pro konečné zpracování */ );
```

---

# Streamy 3

```java
Stream<Svatek> svatky = …;
Collator collator = Collator.getInstance(new Locale("cs", "CZ"));

svatky
  .filter( (svatek) -> svatek.getGender() == Gender.ZENA )
  .sorted( (a, b) -> collator.compare(a.getJmeno(), b.getJmeno()))
  .forEach( svatek -> System.out.printf("%s má svátek %s", svatek.getJmeno(), svatek.getDen()).println() );
```
