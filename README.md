# Matrice - clasa a 9-a - 28.03.2025

## Obiective
- Noțiuni teoretice
- Declarare, initializare matrice. Algoritmi fundamentali: citire, afisare
- Matricea transpusă
- Submatrice

## Noțiuni teoretice

Matricea este o colecţie omogenă şi bidimensională de elemente. Acestea pot fi accesate prin intermediul a doi indici, numerotaţi, ca şi în cazul vectorilor, începand de la 0. Declaraţia unei matrice este de forma:

```cpp
<tip_elemente> <nume_matrice>[<dim_1>][<dim_2>];
```

De exemplu, avem:

```cpp
int mat[5][10];
```

## Output și input

std::cout și std::cin sunt redirectate către notebook frontend

```cpp
#include <iostream>
using namespace std;
int x;
cout << "x = " << endl;
cin >> x;
cout << "Valoarea citita pentru x este: " << x;
```

## Citire matrice

```cpp
int MAX = 10;
int noLines, noCols;

cout << "Numar linii = " << endl;
cin >> noLines;

cout << "Numar coloane = " << endl;
cin >> noCols;
```

```cpp
void citeste(int matrice[10][10], int noLines, int noCols) {
    for (int i = 1; i <= noLines; ++i) {
        for (int j = 1; j <= noCols; ++j) {
            cout << "M[" << i << "][" << j << "] = ";
            cin >> matrice[i-1][j-1];
        }
    }
}
```

**Q: Ce trebuia sa se afiseze?**

## Afisare matrice

```cpp
void afiseaza(int matrice[10][10], int noLines, int noCols) {
    cout << endl;
    for (int i = 1; i <= noLines; i++) {
        for (int j = 1; j <= noCols; j++) {
            cout << matrice[i-1][j-1] << " ";
        }
        cout << endl;
    }
}
```

**Q: Ce trebuia sa se afiseze?**

## Test citire/afisare

```cpp
int n, m;

cout << "Nr. linii = ";
cin >> n;

cout << "Nr. coloane = ";
cin >> m;
int M[10][10];

citeste(M, n, m);
afiseaza(M, n, m);
```

## Exerciții

### Exercițiul 1

Inspectați următoarea bucată de cod. Ce se va afișa pentru input n=3? Dar pentru n=100? Justificați.

```cpp
#include <iostream>
using namespace std;
int unit[10][10];
int i, j, n;
int M = 20;

cout << "nr. linii/coloane: ";
cin >> n;
if (n > M) {
    cout << "nr de linii/ coloane depaseste capacitatea declarata";
} else {
    for (i = 1; i <= n; i++) {
          for (j = 1; j <= n; j++) {
            if (i != j) {
                unit[i-1][j-1] = 0;
            } else {
                unit[i-1][j-1] = 1;
            }
          }
    }
    afiseaza(unit, n, n);
}
```

### Exercițiul 2

Următorul program ar trebui să citească și să afișeze o matrice.

**a) Compilați și rulați. Ce observați?**

```cpp
#include <iostream>
using namespace std;
void read_matrix(int a[10][10], int& n) {
    cout << "nr. linii/coloane: ";
	cin >> n;
	for (int i = 1; i <= n; i++) {
    	  for (int j = 1; j <= n; j++) {
        	cout << "A[" << i << "][" << j << "] = ";
            cin >> a[i-1][j-1];
    	  }
	}
}

int a[10][10], n;
read_matrix(a, n);

cout << "MATRICEA CITITA ESTE:" << endl;
afiseaza(a, n, n);
```

**b) Folosind cout, afișați după apelul read_matrix valoarea lui n și a lui a[0][0].**

```cpp
int a[10][10], n;
read_matrix(a, n);

cout << "n=" << n << endl;
cout << "a[0][0]=" << a[0][0] << endl;
```

**c) Identificați problema și rezolvați-o.**

```cpp
// solutii ?
```

### Exercițiul 3

Citiți de la tastatură o matrice. Afișați matricea transpusă.

**Exemplu:**
```
Input:
        2 4		// număr de linii urmat de număr de coloane
        1 2 3 4
		5 6 7 8

Output:
        1 5
		2 6
		3 7
		4 8
```

```cpp
#include <iostream>
using namespace std;

void citeste(int matrice[10][10], int noLines, int noCols) {
    for (int i = 1; i <= noLines; ++i) {
        for (int j = 1; j <= noCols; ++j) {
            cout << "M[" << i << "][" << j << "] = ";
            cin >> matrice[i-1][j-1];
        }
    }
}

void afiseaza(int matrice[10][10], int noLines, int noCols) {
    cout << endl;
    for (int i = 1; i <= noLines; i++) {
        for (int j = 1; j <= noCols; j++) {
            cout << matrice[i-1][j-1] << " ";
        }
        cout << endl;
    }
}

void transpune(int matrice[10][10], int noLines, int noCols) {
    // TODO
}

int n, m;

cout << "Nr. linii = ";
cin >> n;

cout << "Nr. coloane = ";
cin >> m;
int M[10][10];

citeste(M, n, m);
transpune(M, n, m);
afiseaza(M, m, n);
```

### Exercițiul 4

Se citesc două matrice de la tastatură. Verificați dacă a prima matrice este submatrice a celei de a doua matrice.

**Exemplul 1:**
```
Input:  2 2		// număr de linii urmat de număr de coloane
        1 2
        3 4

        2 2		// număr de linii urmat de număr de coloane
        5 6
        7 8
 Output: Fals
```

**Exemplul 2:**
```
 Input:  2 2      // număr de linii urmat de număr de coloane
         1 2
     	3 4

     	3 3		// număr de linii urmat de număr de coloane
         5 6 4
     	1 2 5
     	3 4 6
Output: Adevarat
```

```cpp
#include <iostream>
using namespace std;

void citeste(int matrice[10][10], int noLines, int noCols) {
    for (int i = 1; i <= noLines; ++i) {
        for (int j = 1; j <= noCols; ++j) {
            cout << "M[" << i << "][" << j << "] = ";
            cin >> matrice[i-1][j-1];
        }
    }
}

void afiseaza(int matrice[10][10], int noLines, int noCols) {
    cout << endl;
    for (int i = 1; i <= noLines; i++) {
        for (int j = 1; j <= noCols; j++) {
            cout << matrice[i-1][j-1] << " ";
        }
        cout << endl;
    }
}

cout << "Size of bool: " << sizeof(bool) << " byte(s)" << endl;

bool is_submatrix(int A[10][10], int noLinesA, int noColsA, int B[10][10], int noLinesB, int noColsB) {
    // TODO
}

int A[10][10];
int B[10][10];
int noLinesA, noColsA;

cout << "PRIMA MATRICE" << endl;
cout << "Nr. linii = ";
cin >> noLinesA;

cout << "Nr. coloane = ";
cin >> noColsA;
citeste(A, noLinesA, noColsA);
afiseaza(A, noLinesA, noColsA);

int noLinesB, noColsB;

cout << "A 2-a MATRICE" << endl;
cout << "Nr. linii = ";
cin >> noLinesB;

cout << "Nr. coloane = ";
cin >> noColsB;
citeste(B, noLinesB, noColsB);
afiseaza(B, noLinesB, noColsB);

if (is_submatrix(A, noLinesA, noColsA, B, noLinesB, noColsB)) {
        cout << "Adevarat" << endl;
    } else {
        cout << "Fals" << endl;
}
```

### Exercițiul 5 (Bonus)

Se citește o matrice A. Obțineți B cu proprietatea că B[i][j] = max(A[0..i][0..j]), unde max(A[0..i][0..j]) înseamnă elementul maxim din submatricea A care are colțul stânga sus în A[0][0] și colțul dreapta jos în A[i][j].

**Exemplu:**
```
Input:  3 4		// număr de linii urmat de număr de coloane
        1 2 5 2 
		6 3 9 8
		4 0 4 5

Output:
        1 2 5 5
		6 6 9 9
		6 6 9 9
```

```cpp
int noLinesA, noColsA;
int A[10][10];

cout << "PRIMA MATRICE" << endl;
cout << "Nr. linii = ";
cin >> noLinesA;

cout << "Nr. coloane = ";
cin >> noColsA;

citeste(A, noLinesA, noColsA);
afiseaza(A, noLinesA, noColsA);

void max_submatrice(int A[10][10], int n, int m) {
    int B[10][10];

    // init primul element stanga sus

    // init prima linie (max depinde doar de elementul din stanga)

    // init prima coloana (max depinde doar de elementul de deasupra)

    // umplem matricea cu relatia de recurenta

    afiseaza(B, n, m);
}

max_submatrice(A, noLinesA, noColsA);
```

## Recap

- Variabile trebuie sa aiba nume sugestive
- Fiecare functie indeplineste un singur rol
- ⚠️ Pasarea prin valoare vs pasarea prin referinta
- Dupa ce rezolvati o problema ganditi-va daca solutia mai poate fi optimizata
