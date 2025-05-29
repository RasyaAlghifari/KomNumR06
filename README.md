## Anggota Kelompok 
- 5053241048	Alfarel Sandriano Subektiansyah
- 5053241013	Alief Rif'an Madhani
- 5053241004	Muhammad Rasya Alghifari
- 5053241009	Muhammad Ilham Akbar
- 5053241050	Ararya Arka Anugraha

## Soal
Cari luas dan error dari persamaan $$f(x) = 3x^5 - 8x^4$$ dengan cara Integral Gasuss dengan 2 titik! (Diketahui batas atas = 16 dan batas bawah = 4)

## Diketahui:  
- Batas bawah: $$a = 4$$
- Batas atas: $$b = 16$$
- Nilai eksak (true value): $$L_{\text{true}} = 6710476.8$$

## Ditanya
1. Hitung luas integral $$L$$ menggunakan metode Gauss 2 titik.  
2. Hitung galat relatif $$E_t$$ dibandingkan $$L_{\text{true}}$$.

## Penyelesaian

### Hitung Manual Integral

Hitung  
$$L = \int_{4}^{16} 3x^5 - 8x^4 \, dx$$

Diketahui:
$$f(x) = 3x^5 - 8x^4$$  
$$a = 4, \quad b = 16$$

Nilai konversi variabel:
$$x = \frac{1}{2} (b - a) u + \frac{1}{2} (b + a)$$  
$$x = \frac{1}{2} (16 - 4) u + \frac{1}{2} (16 + 4)$$  
$$x = \frac{1}{2} (12) u + \frac{1}{2} (20)$$  
$$x = 6u + 10$$

Fungsi dalam bentuk $u$:

$g(u) = \frac{1}{2}(b-a)f(x)$  
$g(u) = \frac{1}{2}(16-4)[3(6u+10)^5 - 8(6u+10)^4]$  
$g(u) = 6[3(6u+10)^5 - 8(6u+10)^4]$


Hasil integral aproksimasi dengan Gaussian 2 titik
$$L = g\left( -\frac{1}{\sqrt{3}} \right) + g\left( \frac{1}{\sqrt{3}} \right)$$  
$$L = x + y$$  
$$L = z$$



### Kode Python
```python
from math import sqrt

class TwoPointGaussianQuadrature():
    def __init__(self, f, a, b):
        self.f = f
        self.a = a
        self.b = b

    def convert_x(self, u):
        return (1/2) * (self.b - self.a) * u + (1/2) * (self.b + self.a)

    def calculate_f(self, x):
        return self.f(x)

    def g_of_u(self, u):
        x = self.convert_x(u)
        f = self.calculate_f(x)
        return (1/2) * (self.b - self.a) * f

    def l(self):
        u1 = -1 / sqrt(3)
        u2 = 1 / sqrt(3)
        return self.g_of_u(u1) + self.g_of_u(u2)
```
### Definisikan fungsi f(x) dan batas-batas integral
```python
luas = TwoPointGaussianQuadrature(lambda x: 3 * x**5 - 8 * x**4, 4, 16)
```

### Hitung luas integral dengan Gauss 2 titik
```python
L = luas.l()
print("Luas integral (aproksimasi):", round(L, 2))
```

### Hitung error relatif terhadap nilai eksak
```python
L_true = 6710476.8
Et = (abs(L_true - L) / L_true) * 100
print("Error relatif (%):", round(Et, 2))
```
