# Market Basket Analysis

## Business Problem
**DQLab Fashion** adalah sebuah toko fashion yang menjual berbagai produk seperti jeans, kemeja, kosmetik, dan lain-lain. Walaupun cukup berkembang, namun dengan semakin banyaknya kompetitor dan banyak produk yang stoknya akan menjadi kendala dalam penjualan produknya. Salah satu solusi adalah membuat paket yang inovatif. Dimana produk yang sebelumnya tidak terlalu laku tapi punya pangsa pasar malah bisa dipaketkan dan laku, seperti Tas Makeup dan Baju Renang Pria Anak-anak.

## Objective
Membuat kombinasi paket yang inovatif untuk meningkatkan penjualan produk sehingga persediaan stok tidak menumpuk.

## Analysis Approach
Menggunakan metode Market Basket Analysis dengan algoritma Apriori.

<hr>

## Data Understanding
- Dataset yang digunakan pada pembahasan ini adalah `transaksi_dqlab_retail.tsv` dari DQLab Fashion yang terdiri dari 33668 baris dan 2 kolom
- Dataset tersebut berisi tentang data transaksi dan nama barang nya.
- TTidak ditemukan *missing values*

## Exploratory Data Analysis
### Statistik Top 10 Product
![top10](/img/top10_product.png?raw=true)

### Statistik Bottom 10 Product
![bottom10](/img/bottom10_product.png?raw=true)


## Preprocessing
- Melakukan agregasi untuk tiap transaksi dengan fungsi `groupby`
- Melakukan encoding transaksi dengan package berikut

    ```from mlxtend.preprocessing import TransactionEncoder```

### Distribution Product For Each Transactions
![transactions](/img/transactions.png?raw=true)


<hr>

## Modelling
### Setting Parameter
Kombinasi produk menarik yaitu:
* Memiliki asosiasi atau hubungan erat
* Kombinasi produk minimal 2 item, dan maksimum 3 item
* Kombinasi produk itu muncul setidaknya 10 dari seluruh transaksi
* Memiliki tingkat confidence minimal 50 persen

### Evaluation Metric
Dalam MBA ini menggunakan teknik **Association Rules** untuk mengetahui keterkaitan antar produk dengan 3 metric, yaitu
- **support** menunjukkan seberapa populer itemset, yang diukur dengan proporsi transaksi di mana itemset muncul.
- **confidence** menunjukkan seberapa besar kemungkinan item Y dibeli ketika item X dibeli, dinyatakan sebagai {X -> Y}.
- **lift** menunjukkan seberapa besar kemungkinan item Y dibeli ketika item X dibeli, sambil mengontrol seberapa populer item Y tersebut.

### Result
![mba](/img/MBA_result.png?raw=true)
1. Tas Makeup lebih baik dipasangkan dengan Tas Pinggang Wanita dan Baju Renang Anak Perempuan
2. Baju Renang Pria Anak-anak lebih baik dipasangkan dengan Gembok Koper dan Tas Waist Bag.

<hr>

## Recommendation
1. **Membuat berdekatan tempat** Tas Makeup dengan tempat Tas Pinggang Wanita dan Baju Renang Anak Perempuan. Sedangkan tempat Baju Renang Pria Anak-anak berdekatan dengan tempat Gembok Koper dan Tas Waist Bag.
2. **Membuat promosi diskon** pada produk Tas Makeup, Tas Pinggang, Baju Renang Anak Perempuan, Baju Renang Pria Anak-anak, Gembok Koper, dan Tas Waist Bag.
3. Jika DQLab Fashion berjualan secara online, maka produk-produk terpilih tersebut dapat **ditampilkan lebih menarik pada halaman homepage**.

Anda dapat melihat detail pembahasan ini pada artikel saya di link **Medium** [berikut](https://ferids55.medium.com/data-science-in-retail-business-a7d3a57bf959).