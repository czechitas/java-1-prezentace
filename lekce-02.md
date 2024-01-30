---
theme: default
background: https://java.czechitas.cz/data/prezentace/Czechitas-background.jpg
highlighter: prism
fonts:
  sans: 'Open Sans'
---

<div class="white flex flex-col mt-48 text-2xl font-light gap-2">
    <div class="font-bold text-6xl">Java 1 • lekce 2</div>
    <div>Filip Jirsák</div>
    <div>23. 1. 2024</div>
    <div>online</div>
</div>


---

# Třída

Třída je základní jednotka aplikace v Javě.

```java {4,9}
// Soubor Hlavni.program.java v adresáři cz/czechitas/java/lekce02.
package cz.czechitas.java.lekce02;

public class HlavniProgram {

  public static void main(String[] args) {
    System.out.println("Ahoj světe!");
  }
}
```

* Běžné třídy musí být uložené v souboru, který se jmenuje stejně, jako třída (včetně velikosti písmen) + přípona `.java`.
  * Např. třída `HlavniProgram` bude v souboru `HlavniProgram.java`.
* Adresáře odpovídají `package` v záhlaví třídy. Jendotlivé adresáře jsou v package oddělené tečkou `.`.
* Názvy tříd se píšou *CamelCase* (počáteční písmena slov jsou velká) s velkým písmenem na začátku.

---

# Spouštěcí metoda aplikace

```java {3-5}
public class Application {

  public static void main(String[] args) {
    System.out.println("Ahoj světe!");
  }
}
```

* Vždy veřejná statická metoda pojmenovaná `main`
  * Nemusí mít žádný argument
  * Nebo má jeden argument typu pole řetězců `String[]`
* V aplikaci jich může být víc, spouští se konkrétní třída
* V IntelliJ stačí napsat `psvm` a stisknout <kbd>Tab</kbd>

---
layout: image-right
image: https://images.unsplash.com/photo-1495578942200-c5f5d2137def?auto=format&fit=crop&w=1920&q=80
---

# Základní stavební bloky

* Výrazy (expressions)
* Příkazy (statements)
* Bloky (blocks)

---

# Výrazy (expressions)

Výsledkem výrazu je vždy nějaká hodnota.

* Hodnotu je možné uložit do proměnné.
* Hodnotu je možné předat jako parametr do metody.
* Hodnotu je možné hned zapomenout (když není potřeba a někdo nám ji *vnutil*).

```java
"Nějaký text"   //text, řetězec znaků, string
42    //celé číslo
123.45    //desetinné číslo
true    //logická hodnota – pravda
false   //logická hodnota – nepravda
'c'   //znak (vždy právě jeden)
Math.random()   //volání metody, která vrací hodnotu
null    //speciální neexistující hodnota
5 + 7   //aritmetické operace s čísly
14 > 23   //porovnání čísel – výsledkem je logická hodnota
"Ahoj " + "světe!"    //spojování řetězců 
"Ahoj" + ' ' + "světe!"   //k řetězci lze připojit i znak
"Odpověď na otázku života, vesmíru a vůbec je: " + 42    //k řetězci lze připojit i číslo, ale nedělá se to
```

---

# Příkazy (statements)

Příkaz je něco, co samo o sobě něco udělá. Například:

* Uloží hodnotu do proměnné.
* Zavolá metodu.
* Vyhodnotí podmínku.

```java
var text = "Nějaký text";   //do proměnné pojmenované `text` uloží text/string "Nějaký text"
var cislo = 42;
var nahodneCislo = Math.random();   //volání metody a uložení výsledku
System.out.println("Ahoj světe");   //volání metody, která nic nevrací – voláme ji proto, že sama něco dělá

//podmíněný příkaz
if (cislo < 100>) {
  System.out.println("Číslo je menší než sto.");
}
```

Příkaz (kromě bloku) se ukončuje středníkem `;`.

💡 V IntelliJ Idea stačí napsat `sout` a stisknout <kbd>Tab</kbd>, Idea sama vypíše celý příkaz `System.out.println();`.

---

# Bloky (blocks)
Používají se tam, kam by normálně patřil jeden příkaz, ale my tam potřebujeme uvést více příkazů.

```java {3-6}
int vek = 17;
System.out.println("Jak je to s tvým věkem?");
if (vek > 12 && vek <= 18) {
  System.out.println("Už nejsi malé dítě.");
  System.out.println("Ale ještě nejsi dospělý.");
}
System.out.println("Ale nic si z toho nedělej.");
```

---

# Bloky (blocks)
Patří ke slušnému vychování psát bloky i tam, kde použijeme jen jeden příkaz.

<div class="w-full gap-4" flex="~ basis-1/2" m="b-4">
  <div bg="green-300/50" flex="grow" p="2" rounded="md">

  ## ✔ Takhle ano
  ```java {2-4}
  int vek = 23;
  if (vek >= 18) {
    System.out.println("Už jsi dospělý.");
  }
  ```
  </div>
  <div bg="red-300/50" flex="grow" p="2" rounded="md">

  ## ❌ Takhle ne
  ```java {2-3}
  int vek = 23;
  if (vek >= 18)
    System.out.println("Už jsi dospělý.");
  ```

  ```java {2}
  int vek = 23;
  if (vek >= 18) System.out.println("Už jsi dospělý.");
  ```
  </div>
</div>

## ❗ Pak se totiž snadno stane chyba
```java {2-4}
int vek = 23;
if (vek >= 18)
  System.out.println("Už jsi dospělý.");
  System.out.println("Takže můžeš k volbám.");

```

---

# Podmínka

<div class="columns-2">
  <div style="break-inside: avoid-column;">
```java
if (cislo < 100>) {
  System.out.println("Číslo je menší než sto.");
}
```

```java
if (cislo < 100>) {
  System.out.println("Číslo je menší než sto.");
} else {
  System.out.println("Číslo je 100 nebo více.");
}
```
  </div>
  <div style="break-inside: avoid-column;">
```java
if (cislo < 100>) {
  System.out.println("Číslo je menší než sto.");
} else if (cislo < 1000>) {
  System.out.println("Číslo je menší než tisíc.");
}
```

```java
if (cislo < 100>) {
  System.out.println("Číslo je menší než sto.");
} else if (cislo < 1000>) {
  System.out.println("Číslo je menší než tisíc.");
} else {
  System.out.println("Číslo je tisíc nebo více.");
}
```
  </div>
</div>

---

# Cyklus `while`

„Dokud je splněna podmínka, opakuj cyklus.“

```java
var random = new Random();

var cislo = random.nextInt(6) + 1;
while (cislo != 6>) {
  System.out.println("Padlo číslo " + cislo + ". Hoď ještě jednou.");
  cislo = random.nextInt(6) + 1;
}
System.out.println("Hodil jsi 6, nasaď figurku a hraj.");
```

❗ Pozor na nekonečný cyklus!

💡 Znak ≠ se zapisuje jako `!` následovaný `=` – některé programy tuto kombinaci znaků zobrazí jako `!=`.

---

# Cyklus `for`

„Opakuj cyklus *n*-krát.“

<div class="columns-2">

```java
for (var i = 0; i < 10; i++) {
  System.out.println("Opiš 10× za trest.");
}
```

```java
int i = 0;
while (i < 10) {
  System.out.println("Opiš 10× za trest.");
  i++;
}
```
</div>

<div class="w-full gap-4" flex="~ basis-1/3" m="y-8">
  <div flex="grow" border="~ rounded silver-200" bg="silver-100" p="1">Nastav výchozí hodnotu.</div>
  <div flex="grow" border="~ rounded silver-200" bg="silver-100" p="1">Opakuj, dokud je splněna podmínka.</div>
  <div flex="grow" border="~ rounded silver-200" bg="silver-100" p="1">Proveď na konci každé obrátky cyklu.</div>
</div>

<arrow v-click="1" x1="160" y1="260" x2="120" y2="160" color="red" width="3" arrowSize="1" />
<arrow v-click="2" x1="350" y1="260" x2="205" y2="160" color="red" width="3" arrowSize="1" />
<arrow v-click="3" x1="700" y1="260" x2="262" y2="152" color="red" width="3" arrowSize="1" />

`i++` znamená *vem hodnotu z `i`, přičti k ní jedničku a výsledek ulož zpět do `i`*.

💡 V IntelliJ Idea stačí napsat `fori` a stisknout <kbd>Tab</kbd>, Idea vytvoří kostru cyklu. Pomocí <kbd>Tab</kbd> pak procházíte jednotlivá místa, která je potřeba doplnit.

💡 Programátoři často počítají od `0`. Když začnete počítat od `0` a v podmínce použijete `<` místo `<=` (psáno jako `<` a `=`), bude v podmínce to číslo (tady `10`), kolikrát se má cyklus opakovat.

