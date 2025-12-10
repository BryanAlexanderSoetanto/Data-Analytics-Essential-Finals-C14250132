# Data-Analytics-Essential-Finals-C14250132
UAS DAE Bryan Alexander Soetanto C14250132
Analisa Dataset Titanic Menggunakan KNIME
---

# 🛳️ Analisis Data Titanic Menggunakan KNIME

Workflow ini dibuat untuk menganalisis data penumpang Titanic, dengan fokus pada **status survival** berdasarkan **usia, jenis kelamin, dan kelas penumpang**, serta membangun model klasifikasi decision tree untuk prediksi survival.

---

## 1️⃣ Data Preparation

Bagian ini bertujuan untuk membaca data mentah dan membersihkannya sebelum dilakukan analisis lebih lanjut.

### 1. CSV Reader
<img width="406" height="360" alt="image" src="https://github.com/user-attachments/assets/ccd7636a-d285-4e91-b5b9-c727fbc1b967" />

Node ini digunakan untuk:

* Membaca dataset Titanic dari file `.csv`
* Mengimpor seluruh kolom seperti `survived`, `sex`, `age`, dan `class`
<img width="1834" height="993" alt="image" src="https://github.com/user-attachments/assets/2add5eea-0146-403b-bf0a-5c12385b8084" />

---

### 2. Missing Value
<img width="426" height="509" alt="image" src="https://github.com/user-attachments/assets/43443120-a711-478b-a704-e756d0777022" />


Node ini menangani nilai yang kosong dalam data:
<img width="820" height="238" alt="image" src="https://github.com/user-attachments/assets/4d103cb9-7ed7-4b0f-807b-a31762477cab" />

* Baris dalam kolom bertipe angka integer yang kosong dihapus
* Baris dalam kolom bertipe angka float yang kosong diisi dengan rata-rata/mean data
* Baris dalam kolom bertipe string yang kosong dibiarkan

---

### 3. Column Filter
<img width="355" height="415" alt="image" src="https://github.com/user-attachments/assets/c75a0bf3-4254-414f-a644-258cda989ca3" />

Digunakan untuk:

* Memilih hanya kolom yang relevan sesuai dengan apa yang ingin/akan dicari
(Misal di bagian data classifier):
<img width="498" height="567" alt="image" src="https://github.com/user-attachments/assets/17acf170-9249-4b90-b107-d6d1d7f568c5" />

---

## 2️⃣ Data Processing

Tahap ini bertujuan untuk mentransformasi data agar dapat dianalisis dan divisualisasikan.

### 4. Numeric Binner (Age)
<img width="346" height="322" alt="image" src="https://github.com/user-attachments/assets/30e282ad-d5cf-4d05-8f6a-48c1cc3825b6" />


Node ini membagi data menjadi beberapa kategori (bin), misalnya:
<img width="749" height="628" alt="image" src="https://github.com/user-attachments/assets/464f4ae2-d70c-441c-89cb-40f21dfdb82f" />

---

### 5. GroupBy

Node ini digunakan untuk mengelompokkan data berdasarkan kategori tertentu, misal:

gender/sex dan class, class dan age_sep (separate column, umur yang sudah di bin di numeric binner) untuk di-concentenate/digabungkan untuk mencari jumlah kematian
<img width="976" height="825" alt="image" src="https://github.com/user-attachments/assets/f1012d21-1278-4eb2-b88e-89f415b429a4" />
<img width="980" height="825" alt="image" src="https://github.com/user-attachments/assets/d4c0e7c4-89b8-4c17-8565-acd76e75a37f" />

---

### 6. Rule Engine

Digunakan untuk:

Membuat kolom prediction untuk kategorisasi data
<img width="1823" height="421" alt="image" src="https://github.com/user-attachments/assets/eed73b1d-16de-4b4f-b7d5-51b0b1b2f3fd" />
<img width="1086" height="838" alt="image" src="https://github.com/user-attachments/assets/a742d710-a1ff-4a64-bb13-2621322c5741" />



---

### 7. String Manipulation

Node ini digunakan untuk:

* Menggabungkan label (contoh: age + sex)
<img width="1471" height="959" alt="image" src="https://github.com/user-attachments/assets/26cbc62b-9123-46b3-b6e1-fe80c410bd53" />


---

### 8. Concatenate

Menggabungkan beberapa tabel menjadi satu

<img width="325" height="246" alt="image" src="https://github.com/user-attachments/assets/36b9505c-693e-4194-89c7-38472f94f182" />

---

## 3️⃣ Visualisasi

Bagian ini menghasilkan visualisasi data untuk diinterpretasikan

### 📊 Bar Chart – Survival Rate by Age (%)

Menunjukkan:

* Persentase penumpang yang selamat berdasarkan kelompok rentang usia
<img width="1097" height="208" alt="Survival rate (age)" src="https://github.com/user-attachments/assets/5b854146-cbc1-4459-8d44-b10a7e7acc54" />
Interpretasi:
Kelompok usia muda memiliki tingkat keselamatan yang lebih tinggi dibandingkan usia dewasa, menunjukkan bahwa penumpang anak-anak lebih diprioritaskan dalam proses evakuasi.

---

### 📊 Bar Chart – Survival Rate by Age & Gender

Menunjukkan:

* Perbandingan tingkat survival berdasarkan usia **dan** jenis kelamin
<img width="1097" height="208" alt="Survival rate (age   gender)" src="https://github.com/user-attachments/assets/1ae59f45-d098-4a74-8ad3-0ae91c12026a" />
Interpretasi:
Perempuan di hampir semua kelompok usia memiliki kemungkinan selamat yang lebih tinggi, sedangkan laki-laki dewasa menunjukkan peluang selamat paling rendah.

---

### 📊 Bar Chart – Survival Rate by Gender & Passenger Class

Menunjukkan:

* Tingkat survival berdasarkan kombinasi jenis kelamin dan kelas penumpang
<img width="1097" height="208" alt="Survival rate (passenger class   gender)" src="https://github.com/user-attachments/assets/7cc2ff60-8ce0-499d-abeb-cf7c10ab9a63" />
Interpretasi:
Penumpang perempuan kelas satu dan dua memiliki peluang selamat yang sangat tinggi, sementara laki-laki kelas tiga memiliki peluang selamat terendah.


---

### 📊 Bar Chart – Total Survived by Age & Gender (Sum)

Menunjukkan:

* Jumlah absolut (bukan persentase) penumpang yang selamat
<img width="1097" height="208" alt="Survived (age   gender)" src="https://github.com/user-attachments/assets/a779b015-32e7-4db9-871a-3b4f0132cc0e" />
Interpretasi:
Perempuan dewasa merupakan sebagian besar penumpang yang selamat, diikuti oleh anak-anak, terutama anak perempuan.


---

### 📊 Bar Chart – Total Death

Menunjukkan:

* Total penumpang yang meninggal
<img width="1097" height="208" alt="Amount of death (passenger class   gender)" src="https://github.com/user-attachments/assets/4d7f53d0-fe9c-438f-9764-0db634673cfa" />
Interpretasi:
Kelas penumpang dan gender berpengaruh terhadap keselamatan dengan bukti mayoritas kematian berasal dari penumpang laki-laki kelas tiga


---

### Pie Chart – Death by Class & Gender

Diagram lingkaran yang memperlihatkan:

* Proporsi kematian berdasarkan kelas penumpang dan jenis kelamin
* <img width="1097" height="208" alt="Pie Chart titanic" src="https://github.com/user-attachments/assets/60447a29-e922-4ef2-8b18-8e3f2b9c6e84" />
* <img width="667" height="326" alt="image" src="https://github.com/user-attachments/assets/b72ef9a5-c28b-4363-a397-cf66fdd8278a" />

Interpretasi:
Proporsi kematian paling besar berasal dari laki-laki kelas tiga, sementara perempuan kelas satu memiliki proporsi kematian paling kecil.


---

### 🔵 Scatter Plot – Death by Class & Gender

Menampilkan:

* Sebaran kematian berdasarkan kelas dan gender
<img width="1097" height="208" alt="Scatter Plot titanic" src="https://github.com/user-attachments/assets/e3f637b8-9a7a-4da2-b1e2-0443481da3d3" />
Interpretasi:
Titik-titik kematian terkonsentrasi pada kelompok laki-laki di kelas tiga, memperkuat pola bahwa gender dan kelas berpengaruh terhadap keselamatan.

---

## 4️⃣ Klasifikasi (Decision Tree)

Bagian ini digunakan untuk membangun model prediksi survival.

### 9. Number to String
<img width="168" height="205" alt="image" src="https://github.com/user-attachments/assets/eaf7d730-476f-413e-9222-3f4f5fd3fd29" />

Mengubah kolom target `survived`:

<img width="494" height="518" alt="image" src="https://github.com/user-attachments/assets/d2d57263-fa39-485b-a690-15fcea8250d2" />

(untuk mengubah data numerik menjadi kategorik agar bisa digunakan decision tree learner)

---

### 10. Decision Tree Learner
<img width="650" height="891" alt="image" src="https://github.com/user-attachments/assets/0e4e5a4b-cd09-4b8a-8dc1-e159f77d7ecc" />

---

## Decision Tree Learner Configuration

Node **Decision Tree Learner** digunakan untuk membangun model klasifikasi yang memprediksi status keselamatan penumpang Titanic (`survived`). Konfigurasi berikut dipilih untuk menghasilkan model yang stabil dan sesuai dengan dataset Titanic.

---

### Class Column: `survived`

Kolom `survived` digunakan sebagai target klasifikasi karena merepresentasikan kondisi akhir penumpang:

* `0` = Meninggal
* `1` = Selamat

---

### Quality Measure: **Gini Index**

Gini Index dipilih sebagai ukuran kualitas pemisahan node karena:

* Umum digunakan untuk decision tree klasifikasi
* Efektif untuk dataset dengan distribusi kelas yang tidak seimbang
  
---

### Pruning Method & Reduced Error Pruning

* **Pruning method: No pruning**
* **Reduced Error Pruning: Enabled**
* **Minimum number of records per node: 20**

Keputusan ini diambil karena:

* Dataset Titanic relatif kecil sehingga pruning agresif berisiko menghilangkan pola penting
* Reduced Error Pruning tetap digunakan untuk menghindari data ekstrem

---

### Average Split Point

Opsi **Average split point** diaktifkan untuk:

* Menentukan titik pemisahan numerik yang lebih stabil
* Mengurangi sensitivitas terhadap nilai ekstrem (outlier)
* Menghasilkan batas split usia yang lebih realistis

---

### Number of Threads: 12

Penggunaan multi-thread dilakukan untuk:

* Mempercepat proses pelatihan model

---

### Skip Nominal Columns Without Domain Information

Opsi ini diaktifkan untuk:

* Menghindari error atau split yang tidak jelas pada kolom kategorikal
* Memastikan hanya atribut nominal dengan domain yang valid digunakan dalam pembentukan tree

---

## Root Split Configuration

### Force Root Split Column: Disabled

Opsi ini **tidak diaktifkan** agar:

* Model secara otomatis memilih fitur paling informatif sebagai root node
* Tidak ada bias manual pada struktur awal tree

---

## Binary Nominal Splits

### Binary Nominal Splits: Enabled

### Max #nominal: 4

Pengaturan ini dipilih karena:

* Mempermudah interpretasi tree
* Menghasilkan cabang yang lebih sederhana

---

### Filter Invalid Attribute Values in Child Nodes: Disabled

Opsi ini tidak digunakan karena:

* Dataset sudah melalui tahap pembersihan data
* Tidak terdapat nilai atribut tidak valid yang signifikan

---

### 11. Decision Tree Predictor

Digunakan untuk:

* Memprediksi status survival pada data
* Membandingkan hasil prediksi dengan data aktual

---

### 12. Scorer

untuk mengukur performa model:

* Akurasi
<img width="1846" height="436" alt="image" src="https://github.com/user-attachments/assets/c4a42744-56e3-4736-8061-4dabd23f2285" />

* Confusion matrix
<img width="1836" height="401" alt="image" src="https://github.com/user-attachments/assets/0deabd72-3617-49ba-91bf-ad4da1358d71" />


---

### 13. Decision Tree to Image

---
<img width="1170" height="1085" alt="Screenshot 2025-12-10 095841" src="https://github.com/user-attachments/assets/8eabd14a-75af-4da1-a803-d898ccff87fd" />

## 1. Gambaran umum survival

Di bagian paling atas:

**0 (549/891)**

Interpretasi:

* **Hasil mayoritas** adalah **0 = Meninggal**
* Dari **891 penumpang**, **549 meninggal** (~61,6%) dan **342 selamat** (~38,4%)

---

## 2. Jenis kelamin menjadi penentu survival

```
sex isIn [male]        |       sex isIn [female]
```

### Penumpang laki-laki:

**0 (468/577)**

* 81,1% meninggal
* 18,9% selamat

### Penumpang perempuan:

**1 (233/314)**

* 74,2% selamat
* 25,8% meninggal

### Interpretasi:

> Penumpang perempuan memiliki tingkat keselamatan yang jauh lebih tinggi dibandingkan penumpang laki-laki, sehingga dapat disimpulkan jenis kelamin merupakan faktor paling dominan dalam menentukan survival/keselamatan.

---

## 3. Cabang laki-laki – Usia berpengaruh

Untuk **penumpang laki-laki**, pemisahan berikutnya adalah:

```
age ≤ 6.5        |        age > 6.5
```

### Anak laki-laki (≤ 6,5 tahun):

**1 (16/24)**

* 66,7% selamat
* 33,3% meninggal

✅ Anak laki-laki memiliki peluang selamat yang lebih baik.

### Laki-laki dewasa > 6,5 tahun:

**0 (460/553)**

* 83,2% meninggal
* 16,8% selamat

❌ Sebagian besar laki-laki dewasa meninggal.

---

## 4. Pengaruh kelas penumpang - Laki-laki

```
class isIn [First]        |        class isIn [Third, Second]
```

### Laki-laki dewasa kelas satu:

**0 (77/120)**

* 35,8% selamat
* 64,2% meninggal

Lebih baik dari rata-rata, tapi risikonya masih tinggi.

### Laki-laki dewasa kelas dua & tiga:

**0 (383/433)**

* 11,5% selamat
* 88,5% meninggal

❌ Tingkat survival rendah.

---

## 5. Pengaruh kelas penumpang - Perempuan
batas:
```
class isIn [Third]        |        class isIn [First, Second]
```

### Perempuan kelas tiga:

**0/1 ~ sekitar 50/50**

* Setengah selamat dan setengah meninggal

### Perempuan kelas satu & dua:

**1 (161/170)**

* 94,7% selamat
* Hanya 5,3% meninggal

✅ Peluang selamat lebih tinggi.

---

## 6. Pengaruh usia pada penumpang perempuan

```
age ≤ ~29.85   |   age > ~29.85
```

* Perempuan yang lebih muda memiliki peluang selamat sedikit lebih tinggi dibandingkan perempuan yang lebih tua, terutama pada kelas penumpang yang lebih rendah.

---

## 7. Kesimpulan model

* **Jika perempuan dan berada di kelas 1 atau 2 → sangat besar peluang selamat**
* **Jika laki-laki dan berusia > ~6 tahun → sangat besar peluang meninggal**
* **Jika anak laki-laki → peluang selamat lebih tinggi**
* **Penumpang kelas tiga → peluang selamat lebih rendah terlepas dari jenis kelamin**

---

## Kesimpulan utama

Jenis kelamin sebagai faktor paling berpengaruh terhadap tingkat keselamatan penumpang. Penumpang perempuan memiliki tingkat survival yang jauh lebih tinggi dibandingkan penumpang laki-laki. Pada penumpang laki-laki, usia menjadi faktor penting, di mana anak-anak memiliki peluang selamat yang lebih tinggi dibandingkan laki-laki dewasa. Selain itu, kelas penumpang juga berpengaruh signifikan, dengan penumpang kelas satu dan dua memiliki tingkat survival yang lebih tinggi dibandingkan kelas tiga.

---
