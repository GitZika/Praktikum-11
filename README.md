## Praktikum-11
## Pertemuan 15

#### Nama  = Azhyka Rizki Ramadhan
#### NIM   = 312210287
#### Kelas = TI.22.A3

# WebScrapping

Web scraping adalah sebuah metode yang dapat memudahkan kamu dalam proses riset. Dibandingkan kamu harus melakukan survei secara manual, web scraping bisa mengambil 
data secara lebih praktis bahkan dalam waktu yang lebih singkat.

---


bahan yang dibutuhkan adalah 
1 Panda
2 BeautifulSoup
3 Requests

untuk install Panda gunakan

    pip install panda

untuk install BeautifulSoup gunakan

    pip install BeautifulSoup4

untuk install Requests gunakan

    pip install requests
    
 ![tugas 1](https://user-images.githubusercontent.com/118233561/213087209-1562671f-4fed-4a55-ac13-1b0d5e41a687.png)

# Latihan

    import pandas as pd
    
import pandas as pd digunakan untuk mengimport library pandas dan menyebutnya sebagai pd. Library pandas digunakan untuk memanipulasi data dalam bentuk tabel (dataframe) dan digunakan untuk data analysi

    from bs4 import BeautifulSoup as bs
    
from bs4 import BeautifulSoup as bs digunakan untuk mengimport class BeautifulSoup dari package BeautifulSoup4 dan menyebutnya sebagai bs. Class BeautifulSoup digunakan untuk mengelola dan mengolah data dari HTML atau XML.

    import requests as req

import requests as req digunakan untuk mengimport libary request dan menyebutnya sebagai req

Ambil contoh web marketplace Ebay lalu salin link ke variable URL 

```
URL = "https://www.ebay.com/sch/i.html?_from=R40&_trksid=p2334524.m570.l1313&_nkw=watch&_sacat=0&LH_TitleDesc=0&_odkw=jam+tangan&_osacat=0&LH_PrefLoc=2"
page = req.get(URL)
soup = bs(page.content, 'html.parser')
```

Soup akan menganalisis konten nya dengan html 

---

Gunakan soup untuk mencari item produknya 

    produk = soup.find_all('li', attrs={'class': 's-item'})

buat list nya dan tambahkan list nya 

```
nama_produk = []
harga_produk = []
for item in produk:
  nama = item.find('div', attrs={'class': 's-item__title'}).text
  harga = item.find('span', attrs={'class': 's-item__price'}).text
  nama_produk.append(nama)
  harga_produk.append(harga)
```
---

buat dataframe untuk list menggunakan panda

```
df = pd.DataFrame({'Barang': nama_produk, 'Harga': harga_produk})

print(df)
```

![tugas 2](https://user-images.githubusercontent.com/118233561/213087247-4c211c2b-c059-4c0d-8aff-8828d073ebc9.png)

## OUTPUT 

<img width="427" alt="Screenshot 2023-01-18 115906" src="https://user-images.githubusercontent.com/118233561/213090876-7b036dc5-72e8-400f-8b0e-9174c9cb0802.png">



