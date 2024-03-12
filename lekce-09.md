---
theme: default
background: https://java.czechitas.cz/data/prezentace/Czechitas-background.jpg
highlighter: prism
fonts:
  sans: 'Open Sans'
---

<div class="white flex flex-col mt-48 text-2xl font-light gap-2">
    <div class="font-bold text-6xl">Java 1 • lekce 9</div>
    <div>Filip Jirsák</div>
    <div>12. 3. 2024</div>
    <div>online</div>
</div>

---

# Soubory

* starší `java.io.File`
  * vytváření `new File()`
  * `File` → `Path`: `file.toPath()`
* nové `java.nio.file.Path`
  * vytváření `Path.of`
  * `Path` → `File`: `path.toFile()`

---

# Práce se soubory

## `File`
* zjištění existence, přejmenování, vytvoření adresáře: metody přímo na třídě `File`
* kopírování: ručně přomocí čtení a zápis dat

## `Path`
* třída `java.nio.file.Files`

---

# Serializace (a deserializace)

* **Serializace**: uložení dat z paměti (stromu objektů) do souboru na disk
* **Deserializace**: načtení dat do paměti ze souboru na disku
 
---

# `java.io.Serializable`

* Přímo součástí Javy
* Čitelné jen z Javy
* Bezpečnostní problémy
* → nebudeme se tím zabývat

---

# Formát JSON

* JSON = JavaScript Object Notation (JavaScript ≠ Java)
* Univerzální formát napříč programovacími jazyky, hlavně web
* Různé knihovny pro Javu
  * [Jackson](https://github.com/FasterXML/jackson)
  * [JSON-P](https://jakarta.ee/specifications/jsonp/)

---

# ObjectMapper

Zajišťuje mapování mezi objekty v Javě a formátem JSON.

```java
Type data = objectMapper.readValue(file, Type.class);
objectMapper.writeValue(file, data);
```

Při čtení je nutné specifikovat, jaký typ dat (třídu) očekáváme.
