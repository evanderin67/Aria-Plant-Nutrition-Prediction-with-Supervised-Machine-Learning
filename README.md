# Plant Nutrition Prediction with Supervised Machine Learning

Project ini memiliki tujuan untuk mmembuat model optimal untuk prediksi nutrisi dari tanaman dengan 8 Variabel yang tersedia beserta informasi mengenai lab tempat pengujian.

# Penjelasan File pada Github

Repository ini terdiri dari beberapa file yaitu :

- Folder `deployment` = Berisi mengenai file yang digunakan untuk *deployment* ke `HuggingFace`(berisi model, python application dll)
- `aria_ftds_rmt17_evan_derin_ihsanudin.ipynb` = File ini adalah *notebook* utama yang digunakan untuk pengerjaan model (dari data *exploration*, data *cleaning*, *building model* hingga *model evaluation*)
- `inferencing_aria_ftds_rmt17_evan_derin_ihsanudin.ipynb`= File ini adalah *notebook* yang digunakan untuk *testing inference*. Inferencing dilakukan pada *notebook* terpisah **untuk membuktikan bahwa model dapat berjalan pada *notebook* yang *clean* dari variabel**
- `url.txt` = File ini berisi *deployment* ke `HuggingFace`

# Summary singkat Project

Alur dari *project* ini adalah yang pertama EDA (*Exploratory Data Analysis*) untuk mengetahui gambaran dasar dari *dataset*. Kemudian dilakukan *cleaning* dan *preprocessing* terhadap *dataset*. Dari *preprocessing* saya drop *feature* `sample_type` karena *feature* tersebut tidak mempengaruhi regresi. Kemudian saya melakukan *training* pada 7 model dan dipilihlah model terbaik yaitu **model Random Forest**. Kemudian saya lakukan parameter tuning terhadap model tersebut sehingga **mempunyai nilai MAE yang rendah yaitu 0.12**

# Kesimpulan Project

- Sebelum membuat model maka saya perlu mengetahui dan eksplorasi mengenai data yang tersedia. Hasil eksplorasi adalah sebagai berikut :
    1. Nutrisi tanaman banyak terpusat pada nilai 4,5 - 4,7
    2. Variabel 8 memiliki nilai nilai paling tinggi diantara variabel lainnya. Variabel 1-7 berkisar antara 300-700 sedangkan variabel 8 memiliki nilai di 3.700-5.000
    3. Tanaman yang diuji pada Lab 1 lebih banyak dari pada lab 2 (tidak *balance*)
    4. Lab 1 sering menguji tanaman dengan tingkat nutrisi 4.6 - 4.85
    5. Lab 2 sering menguji tanaman dengan tingkat nutrisi 4.5 - 5
    6. Variabel 1-7 memiliki korelasi negatif terhadap target. Variabel 6 memiliki korelasi negatif paling kuat terhadap target sedangkan Variabel 8 memiliki korelasi positif paling kuat terhadap target
    7. *Multicolinearity* antar variabel kuat
    8. Variabel 1 - variabel 7 saling memiliki *multicolinearity* positif sedangkan variabel 8 memiliki *multicolinearity* negatif terhadap variabel 1- variabel 7
     
- Kemudian saya merancang model dan **dipilihlah Model Random Forest Parameter Tuning**. Berikut kelemahan dan kelebihan dari model :
    
    Kelebihan
    1. Memiliki error yang kecil yaitu 0.12
    2. Model ini tahan terhadap *outlier*
    3. Model ini memiliki bias yang kecil karena sudah ada *rules* untuk regresi-nya

    Kelemahan
    1. Tidak dapat memprediksi diluar *range* data, karena menggunakan algoritma random forest
    2. Waktu untuk *testing* dan *training* cukup lama karena menggunakan algoritma bagging
    3. Susah diinterpretasikan mengapa model dapat memprediksi nutrisi tanaman ke angka tersebut (berbeda dari linear regression yang mudah diinterpretasikan)

- Untuk *continuous improvement*, saran dari saya adalah :
    
    Improvement Model
    1. Karena *multicolinearity* yang kuat, maka perlu memberikan bobot terhadap *variabel* yang memberikan kontribusi besar terhadap perhitungan nutrisi. Akan tetapi bobot tersebut **adalah hasil konsultasi dengan pakar domain** 
    2. Membuat target *regresi* menjadi *categorical* agar lebih umum. Karena setelah saya lihat, nilai antar data tidak berbeda jauh. Oleh karena itu lebih baik dibuat *categorical*, agar prediksi bisa lebih akurat. Sebagai contoh, tanaman yang mempunyai nutrisi 4,9-5 dikategorikan sebagai tanaman bernutrisi/tanaman sehat dll.
    3. Melakukan *feature selection* dengan cara konsultasi ke pakar domain. Jadi *feature* yang tidak berpengaruh lebih baik di-drop atau diberi nilai konstan agar model dapat lebih akurat

    Business Insight
    1. Tanaman yang memiliki prediksi nutrisi tinggi, bisa di-monitor lebih lanjut kemudian *treatment* pada tanaman tersebut dapat diterapkan ke tanaman lain. Dengan harapan, meningkatnya nilai nutrisi pada tanaman lain