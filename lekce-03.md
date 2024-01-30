---
theme: default
background: https://java.czechitas.cz/data/prezentace/Czechitas-background.jpg
highlighter: prism
fonts:
  sans: 'Open Sans'
---

<div class="white flex flex-col mt-48 text-2xl font-light gap-2">
    <div class="font-bold text-6xl">Java 1 • lekce 3</div>
    <div>Filip Jirsák</div>
    <div>30. 1. 2024</div>
    <div>online</div>
</div>


---

# Proměnné

Proměnná je pojmenované místo v paměti, ve kterém je uložený nějaký údaj nebo soubor údajů.

```java
String jmeno;
int vek;
LocalDate datum;
```

Hodnota se nastavuje pomocí `=`. 

```java
jmeno = "Eva";
vek = 23;
datum = LocalDate.now();
```

Spolu s vytvořením proměnné se může rovnou nastavit i hodnota. Následující dva zápisy jsou ekvivalentní:
```java
String jmeno;
jmeno = "Eva";
```

```java
String jmeno = "Eva";
```

---

# Proměnné – klíčové slovo `var`

Pokud do proměnné rovnou přiřazujeme hodnotu, můžeme místo typu použít klíčové slovo `var`.

Následující dva zápisy jsou ekvivalentní:

```java
String jmeno = "Eva";
```

```java
var jmeno = "Eva";
```

---

# Platnost proměnných (scope)

Proměnná platí v rámci bloku, kde je deklarována.

* Pokud je deklarována na úrovni celé třídy, existuje v rámci celé třídy → členská proměnná, field.
* Pokud je deklarována v metodě, platí od místa deklarace do konce metody, s ukončením metody zanikne → (běžná) proměnná.

---

# Parametry metod

Parametr metody je speciální proměnná, jejíž hodnota se předává při volání metody.

```java {4-6|13}
public class Osoba {
  private LocalDate datum;

  public void nastavDatumNarozeni(LocalDate datumNarozeni) {
    this.datumNarozeni = datumNarozeni;
  }

}

// použití
Osoba uzivatel = new Osoba();
var datum = LocalDate.of(2001, 2, 21);
uzivatel.nastavDatumNarozeni(datum);
```

---

# Objekt

Objekt – data (údaje, hodnoty) spolu s akcemi (činnostmi), které se s daty dají provádět.

* členská proměnná (field) – data, údaje, hodnoty
* metoda (method) – akce, činnost, výkonný kód

```java {3-5|7-14}
public class Osoba {

  private String jmeno;
  private String prijmeni;
  private LocalDate datumNarozeni;
  
  public String getCeleJmeno() {
    return jmeno + " " + prijmeni;
  }

  public int getVek() {
    Period period = datumNarozeni.until(LocalDate.now());
    return period.getYears();
  }
}
```

---

# Třída

Třída – objekty, které mají stejné akce.

* Definuje se klíčovým slovem `class`.
* Jednotlivé objekty, vznikající z dané třídy, se nazývají **instance třídy**.

Různé objekty stejného typu se liší údaji, metody mají stejné.

```java {4-5}
var jenicek = new Osoba("Jan", "Myslivec");
var marenka = new Osoba("Marie", "Myslivcová");

jenicek.getCeleJmeno();
marenka.getCeleJmeno();
```

---

# Konstruktor

Konstruktor je speciální metoda, která slouží pro vytvoření objektu.

* Jmenuje se stejně, jako název třídy.
* Nemá žádný návratový typ
* Konstruktor se volá s klíčovým slovem `new`.

```java {7-11|16-17}
public class Osoba {

  private String jmeno;
  private String prijmeni;
  private LocalDate datumNarozeni;
  
  public Osoba(String jmeno, String prijmeni, LocalDate datumNarozeni) {
    this.jmeno = jmeno;
    this.prijmeni = prijmeni;
    this.datumNarozeni = datumNarozeni;
  }

}

//použití
var jenicek = new Osoba("Jan", "Myslivec");
var marenka = new Osoba("Marie", "Myslivcová");
```

---

# Datové typy

* primitivní typy – pouze hodnota (číslo, znak, logická hodnota ano/ne)
* objektové typy – vše ostatní (včetně `String`u)
* speciální hodnota objektových typů: `null`
  * znamená „prázdno, nic, nezadaná nebo neznámá hodnota“
  * je to něco jiného než `0` nebo `""`

---

| <span style="font-size: 70%">**Primitivní typ**</span> | **Třída**  | **Popis** | **Rozsah**               | **Zápis**                             |
|----------------|-----------|---------------------|---------------------------------------------------------|---------------------------------------|
| byte           | Byte      | celé číslo          | -128 až 127                                             | zapisuje se jako int                  |
| short          | Short     | celé číslo          | -32 768 až 32 767                                       | zapisuje se jako int                  |
| int            | Integer   | celé číslo          | cca ±2,1 miliardy (-2³¹ až 2³¹ − 1)                     | 123, -123                             |
| long           | Long      | celé číslo          | cca ±9 trilionů (-2⁶³ až 2⁶³ − 1)                       | 123l, 123L, -123L                     |
| float          | Float     | desetinné číslo     | - ∞ až + ∞ (nepřesné❗)                                  | 15f, 15.0f, -15.23f                   |
| double         | Double    | desetinné číslo     | - ∞ až + ∞ (nepřesné❗)                                  | 15d, 15.0d, -15.23d                   |
| char           | Character | jeden znak          | 65 536 variant                                          | 'x', nelze ''                         |
| boolean        | Boolean   | logická hodnota     | true, false                                             | true, false                           |
| *neexistuje*   | String    | text, řetězec znaků |                                                         | "text"<br>"""<br>Víceřádkový<br>text<br>"""  |