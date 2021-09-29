# HillCipher

Per svolgere questo esercizio sono state utilizzate le seguente librerie (che devono essere installate, prima di eseguire il codice):

- `numpy`
- `sympy`

L’obiettivo di questo esercizio era quello di implementare il Cifrario di Hill in modo che permettesse all’utente, utilizzando l’alfabeto inglese “ABCDEFGHIJKLMNOPQRSTUVWXYZ”, di cifrare, decifrare e di eseguire un attacco known plaintext.

Una volta eseguito il codice, l’utente può scegliere tra una lista di funzioni disponibili che vengono stampate a schermo, semplicemente inserendo il numero corrispondente.

![Schermata 2021-04-01 alle 16.13.03.png](https://res.craft.do/user/full/63cec524-c1b6-57b4-8157-df0476f848cb/doc/F2D83C7F-B668-4BFB-B297-5D43AB4A3540/D4516C23-939F-4784-A438-BDEC33465A5E_2)

## 1. Encryption

La funzione di *Encryption* consente di cifrare un messaggio inserito dall’utente (*plaintext*) in base ad una chiave (*key*) anche essa inserita dall’utente. Tali input sono presi tramite il metodo:

```python
def get_text_input(message, alphabet):
	'''some code'''
```

Il plaintext e la chiave devono rispettare l’alfabeto inglese e non devono contenere spazi, numeri o punteggiatura. La chiave inoltre deve avere una lunghezza quadrata, questa viene controllata tramite la funzione:

```python
def is_square(key):
	'''some code'''
```

Una volta inseriti i due input, la funzione stampa a schermo le matrici estrapolate dal plaintext e dalla chiave inserita, tramite le funzioni:

```python
def get_key_matrix(key, alphabet):
	'''some code'''

def get_text_matrix(text, m, alphabet):
	'''some code'''
```

Tali matrici contengono i numeri che corrispondono alla codifica delle lettere in base all’alfabeto scelto. Nel nostro caso:

![equation](https://latex.codecogs.com/gif.latex?%5Cmathbb%7BA%7D%20%3D%20%5C%7BA%2CB%2CC%2C.%20.%20.%2CZ%5C%7D%20%3D%20%5Cmathbb%7BZ%7D_%7B26%7D%20%3D%20%5C%7B0%2C1%2C2%2C.%20.%20.%2C25%5C%7D)

Questa mappatura da lettere a numeri viene fatta tramite la funzione:

```python
def get_from_letters_to_numbers():
	'''some code'''
	return alphabet
```

Dopo questi passaggi, la funzione procede alla cifratura del plaintext tramite la funzione:

```python
def encrypt(key, plaintext, alphabet):
	'''some code'''
	return ciphertext
```

che ritorna la matrice del ciphertext contenente i numeri.

Per riscrivere in lettere il messaggio di ciphertext si utilizza:

```python
def from_matrix_to_text(matrix, order, alphabet):
	'''some code'''
	return text
```

Questo metodo prende in ingresso come alfabeto, l’alfabeto inverso che mappa i numeri nelle lettere, ottenuto tramite la funzione:

```python
def get_from_numbers_to_letters():
	'''some code'''
	return reverse_alphabet
```

In termini matematici l’***encryption*** è definita come segue:

![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BSe%20definiamo%3A%7D%5C%5C%20%5Cbullet%20%5Cquad%20%5Ctext%7BIl%20plaintext%20%7D%20%5CRightarrow%20%5Cquad%20P%20%3D%20%5Cbegin%7Bbmatrix%7D%20x_%7Bi%7D%5C%5C%20%5Cvdots%5C%5C%20x_%7Bm%7D%5C%5C%20%5Cend%7Bbmatrix%7D%20%5Cquad%20%5Ctext%7Bcon%20%7D%20x_%7Bi%7D%20%5Cin%20%5Cmathbb%7BZ%7D_%7B26%7D%5C%5C%20%5Cbullet%20%5Cquad%20%5Ctext%7BLa%20chiave%20%7D%20%5CRightarrow%20%5Cquad%20K%20%3D%20%5Cbegin%7Bbmatrix%7D%20k_%7B11%7D%20%26%20%5Ccdots%20%26%20k_%7B1m%7D%5C%5C%20%5Cvdots%20%26%20%5Cddots%20%26%20%5Cvdots%5C%5C%20k_%7Bm1%7D%20%26%20%5Ccdots%20%26%20k_%7Bmm%7D%5C%5C%20%5Cend%7Bbmatrix%7D%20%5Cquad%20%5Ctext%7Bcon%20%7D%20k_%7Bij%7D%20%5Cin%20%5Cmathbb%7BZ%7D_%7B26%7D%2C%20%5Ctext%7B%20matrice%20%7D%20m%5Ctimes%20m%20%5C%5C)

![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BLa%20cifratura%20data%20da%3A%7D%5C%5C%20E_%7BK%7D%5BP%5D%20%3D%20C%20%3D%20%28K%20%5Ctimes%20P%5C%2C%29%20%5C%2C%20mod%5C%2C26%20%5Cquad%20%5Ctext%7B%20dove%7D%5C%5C%20%5Cbullet%20%5Cquad%20%5Ctext%7BIl%20ciphertext%20%7D%20%5CRightarrow%20%5Cquad%20C%20%3D%20%5Cbegin%7Bbmatrix%7D%20y_%7Bi%7D%5C%5C%20%5Cvdots%5C%5C%20y_%7Bm%7D%5C%5C%20%5Cend%7Bbmatrix%7D%20%5Cquad%20%5Ctext%7Bcon%20%7D%20y_%7Bi%7D%20%5Cin%20%5Cmathbb%7BZ%7D_%7B26%7D%5C%5C)

## 2. Decryption

La funzione di *Decryption* consente di decifrare un messaggio inserito dall’utente (*ciphertext*) in base ad una chiave (*key*) anche essa inserita dall’utente. Tali input sono presi tramite il metodo:

```python
def get_text_input(message, alphabet):
	'''some code'''
```

Il ciphertext e la chiave devono rispettare l’alfabeto inglese e non devono contenere spazi, numeri o punteggiatura. La chiave inoltre deve avere una lunghezza quadrata, questa viene controllata tramite la funzione:

```python
def is_square(key):
	'''some code'''
```

Per la decryption è inoltre necessario controllare che la matrice relativa alla chiave sia **invertibile** e se è invertibile si deve calcolare la matrice inversa. Il metodo che nel codice esegue ciò è il seguente:

```python
def get_inverse_matrix(matrix, alphabet):
	'''some code'''
```

Quindi una volta inseriti i due input (ciphertext e chiave), la funzione stampa a schermo le matrici estrapolate dal ciphertext e dalla chiave inserita, tramite le funzioni:

```python
def get_key_matrix(key, alphabet):
	'''some code'''

def get_text_matrix(text, m, alphabet):
	'''some code'''
```

Tali matrici contengono i numeri che corrispondono alla codifica delle lettere in base all’alfabeto scelto. Nel nostro caso:

![equation](https://latex.codecogs.com/gif.latex?%5Cmathbb%7BA%7D%20%3D%20%5C%7BA%2CB%2CC%2C.%20.%20.%2CZ%5C%7D%20%3D%20%5Cmathbb%7BZ%7D_%7B26%7D%20%3D%20%5C%7B0%2C1%2C2%2C.%20.%20.%2C25%5C%7D)

Questa mappatura da lettere a numeri viene fatta tramite la funzione:

```python
def get_from_letters_to_numbers():
	'''some code'''
	return alphabet
```

Dopo questi passaggi, la funzione procede alla decifratura del ciphertext tramite la funzione:

```python
def decrypt(key_inverse, ciphertext, alphabet):
	'''some code'''
```

che ritorna la matrice del plaintext contenente i numeri.

Per riscrivere in lettere il messaggio di plaintext si utilizza:

```python
def from_matrix_to_text(matrix, order, alphabet):
	'''some code'''
	return text
```

Questo metodo prende in ingresso come alfabeto, l’alfabeto inverso che mappa i numeri nelle lettere, ottenuto tramite la funzione:

```python
def get_from_numbers_to_letters():
	'''some code'''
	return reverse_alphabet
```

In termini matematici la ***decryption*** è definita come segue:

![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BSe%20definiamo%3A%7D%5C%5C%20%5Cbullet%20%5Cquad%20%5Ctext%7BIl%20ciphertext%20%7D%20%5CRightarrow%20%5Cquad%20C%20%3D%20%5Cbegin%7Bbmatrix%7D%20y_%7Bi%7D%5C%5C%20%5Cvdots%5C%5C%20y_%7Bm%7D%5C%5C%20%5Cend%7Bbmatrix%7D%20%5Cquad%20%5Ctext%7Bcon%20%7D%20y_%7Bi%7D%20%5Cin%20%5Cmathbb%7BZ%7D_%7B26%7D%5C%5C%20%5Cbullet%20%5Cquad%20%5Ctext%7BLa%20chiave%20%7D%20%5CRightarrow%20%5Cquad%20K%20%3D%20%5Cbegin%7Bbmatrix%7D%20k_%7B11%7D%20%26%20%5Ccdots%20%26%20k_%7B1m%7D%5C%5C%20%5Cvdots%20%26%20%5Cddots%20%26%20%5Cvdots%5C%5C%20k_%7Bm1%7D%20%26%20%5Ccdots%20%26%20k_%7Bmm%7D%5C%5C%20%5Cend%7Bbmatrix%7D%20%5Cquad%20%5Ctext%7Bcon%20%7D%20k_%7Bij%7D%20%5Cin%20%5Cmathbb%7BZ%7D_%7B26%7D%2C%20%5Ctext%7B%20matrice%20%7D%5C%2C%20m%5Ctimes%20m%5C%5C)

![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BLa%20decifratura%20data%20da%3A%7D%5C%5C%20D_%7BK%7D%5BC%5D%20%3D%20%28K%5E%7B-1%7D%20%5Ctimes%20C%5C%2C%29%5C%2Cmod%5C%2C26%20%3D%20%28K%5E%7B-1%7D%20%5Ctimes%20K%20%5Ctimes%20P%5C%2C%29%5C%2Cmod%5C%2C26%20%3D%20P%20%5Cquad%20%5Ctext%7B%20dove%7D%5C%5C%20%5Cbullet%20%5Cquad%20%5Ctext%7BIl%20plaintext%20%7D%20%5CRightarrow%20%5Cquad%20P%20%3D%20%5Cbegin%7Bbmatrix%7D%20x_%7Bi%7D%5C%5C%20%5Cvdots%5C%5C%20x_%7Bm%7D%5C%5C%20%5Cend%7Bbmatrix%7D%20%5Cquad%20%5Ctext%7Bcon%20%7D%20x_%7Bi%7D%20%5Cin%20%5Cmathbb%7BZ%7D_%7B26%7D%5C%5C)

## 3. Known Plaintext Attack

Funzione che consente all’utente di eseguire l’attacco di tipo *known plaintext* al Cifrario di Hill. Viene richiesto un plaintext, un ciphertext e la dimensione degli m-grammi (**m**) con cui testare l’attacco (ovvero **m** è la grandezza dei blocchi con cui sarà suddiviso il plaintext e il ciphertext).

Il numero di m-grammi generati dal plaintext e dal ciphertext deve essere lo stesso. L'utente deve quindi inserire un plaintext e un ciphertext di lunghezza appropriati altrimenti la funzione ritorna un messaggio di errore.

Quindi una volta inseriti i tre input (plaintext, ciphertext e m), la funzione stampa a schermo le matrici estrapolate dal ciphertext (**C***) e dal plaintext (**P***).

La matrice generata dal plaintext (**P***) deve inoltre risultare invertibile altrimenti l'attacco non può andare a buon fine e dunque in quest'ultimo caso la funzione restituisce un messaggio di errore. Per controllare che sia invertibile e per calcolare la matrice inversa viene utilizzato il seguente metodo:

```python
def get_inverse_matrix(matrix, alphabet):
	'''some code'''
```

Una volta invertita la matrice, la funzione protrà procedere all’esecuzione dell’attacco. Questo viene fatto nel codice tramite il seguente metodo:

```python
def known_plaintext_attack(ciphertext, plaintext_inverse, alphabet):
	'''some code'''
```

Terminato l'attacco, se è andato a buon fine, la funzione stamperà la matrice il testo della chiave trovata. La conversione da numeri a lettere viene eseguita nella stessa maniera esposta nei punti precedenti.

Alcune osserazioni implementative:

- Se durante la creazione degli m-grammi l'ultimo blocco risulta parzialmente vuoto viene inserita un lettera 'Z' (Z=25) per ogni lettera mancante.
- Le matrici del ciphertext e del plaintext si leggono per colonna dall'alto verso il basso, mentre le matrici delle chiavi si leggono per riga da sinistra a destra.

In termini matematici l’attacco ***known plaintext*** è definito come segue:

![equation](https://latex.codecogs.com/gif.latex?%5Ctext%7BSi%20dispone%20di%20%7D%20m%20%5Ctext%7B%20coppie%20di%20plaintext-ciphertext%3A%7D%5C%5C%20%5Clangle%20P_%7B1%7D%2CC_%7B1%7D%5Crangle%5C%5C%20%5Cquad%20%5C%2C%5C%2C%5C%2C%5C%2C%20%5Cvdots%5C%5C%20%5Clangle%20P_%7Bm%7D%2CC_%7Bm%7D%5Crangle%5C%5C)

Allora si costruiscono 2 matrici in questo modo:

![equation](https://latex.codecogs.com/gif.latex?%5Cbullet%20%5Cquad%20P%5E%7B*%7D%3D%5BP_%7B1%7D%7C.%20.%20.%7CP_%7Bm%7D%5D%20%5Cquad%20%5Ctext%7Bmatrice%20%7D%20m%20%5Ctimes%20m%2C%20%5Ctext%7B%20costruita%20mettendo%20in%20fila%20i%20blocchi%20%7D%20P_%7B1%7D%2C.%20.%20.%2CP_%7Bm%7D%5C%5C%20%5Cbullet%20%5Cquad%20C%5E%7B*%7D%3D%5BC_%7B1%7D%7C.%20.%20.%7CC_%7Bm%7D%5D%20%5Cquad%20%5Ctext%7Bmatrice%20%7D%20m%20%5Ctimes%20m%2C%20%5Ctext%7B%20costruita%20mettendo%20in%20fila%20i%20blocchi%20%7D%20C_%7B1%7D%2C.%20.%20.%2CC_%7Bm%7D%5C%5C)

![equation](https://latex.codecogs.com/gif.latex?C%5E%7B*%7D%20%3D%20%28K%20%5Ctimes%20P%5E%7B*%7D%29%5C%2C%20mod%5C%2C26%20%5Cquad%20%5CLongrightarrow%20%5Cquad%20K%20%3D%20C%5E%7B*%7D%20%5Ctimes%20%7BP%5E%7B*%7D%7D%5E%7B-1%7D)

L’attaccante dunque riesce ad ottenere la chiave **K** solo se la matrice **P*** è invertibile modulo 26.

## Run
To run the project:
```
python3 HillCipher.py
```