# zadanienaInformatyke26


def nwd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

def znajdz_ciag():
    with open('liczby.txt', 'r') as f:
        liczby = list(map(int, f.read().split()))
        
    max_dlugosc = 0
    max_start = 0
    max_nwd = 0
    
    start = 0
    koniec = 1
    aktualny_nwd = liczby[0]
    
    while koniec < len(liczby):
        aktualny_nwd = nwd(aktualny_nwd, liczby[koniec])
        if aktualny_nwd > 1:
            if koniec - start + 1 > max_dlugosc:
                max_dlugosc = koniec - start + 1
                max_start = start
                max_nwd = aktualny_nwd
            koniec += 1
        else:
            start = koniec
            koniec = start + 1
            if start < len(liczby):
                aktualny_nwd = liczby[start]
    
    return liczby[max_start], max_dlugosc, max_nwd

pierwsza_liczba, dlugosc_ciagu, najwiekszy_dzielnik = znajdz_ciag()
print(f"Pierwsza liczba w ciągu: {pierwsza_liczba}")
print(f"Długość ciągu: {dlugosc_ciagu}")
print(f"Największy wspólny dzielnik: {najwiekszy_dzielnik}")
