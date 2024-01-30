---
theme: default
background: https://java.czechitas.cz/data/prezentace/Czechitas-background.jpg
highlighter: prism
fonts:
  sans: 'Open Sans'
---

<div class="white flex flex-col mt-48 text-2xl font-light gap-2">
    <div class="font-bold text-6xl">Java 1 • lekce 10</div>
    <div>Filip Jirsák</div>
    <div>18. 4. 2023</div>
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

---

# Výjimky (exceptions)

* Pokud dojde k chybě (např. neexistuje soubor, který chceme číst), dojde k tzv. „vyhození výjimky“ (throw exception).
* Výjimka probublává zpět aplikací, dokud nenarazí na místo, kde je zachycena a zpracována.
* Pokud není zachycena nikde, aplikace se ukončí.

## Zpracování výjimky
```java
try {
  // kód, kde může dojít k výjimce
} catch (Exception e) {
  // zpracování výjimky
}
```

## Vyhození výjimky
```java
throw new Exception();
// Nebo libovolný jiný typ výjimky.
```

---

# Typy výjimek

Všechny výjimky: `java.lang.Throwable`

* **Kontrolované (checked)**: `java.lang.Exception`
  * Metoda musí deklarovat pomocí `throws`, které kontrolované výjimky může vyhazovat
  * Volající musí výjimku zpracovat nebo deklarovat, že ji vyhazuje dál
* **Nekontrolované (unchecked)**: `java.lang.RuntimeException`
  * Mohou být vyhozeny kdykoli
* **Chyby (error)**: `java.lang.Error`
  * Např. nedostatek paměti, poškozený program apod.
  * V aplikaci se obvykle nezachycují, protože se s nimi nedá mnoho udělat
