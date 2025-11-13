Analisis dan Pertanyaan
1. Mapel mana yang memiliki rata-rata nilai tertinggi?
   Mata pelajaran yang memiliki rata-rata nilai tertinggi adalah Matematika, karena dari grafik terlihat nilainya paling tinggi dibanding mapel lain.
2. Mapel mana yang memiliki nilai terendah?
   Mapel yang memiliki nilai terendah adalah Bahasa Indonesia dan Fisika, dengan nilai minimum sekitar 75.
3. Bagaimana visualisasi membantu dalam memahami data?
   Visualisasi membantu supaya kita lebih mudah melihat perbandingan nilai antar mapel. Dengan grafik batang dan boxplot, kita bisa langsung tahu mapel mana yang tinggi, rendah, dan bagaimana persebaran nilainya tanpa harus lihat angka satu-satu.

Refleksi Siswa
1. Apa hal baru yang kamu pelajari dari kegiatan analisis dan visualisasi data?
   Saya belajar cara membaca data pakai Pandas dan membuat grafik dengan Matplotlib dan Seaborn. Jadi sekarang saya paham gimana cara menganalisis data biar hasilnya lebih mudah dilihat.
2. Kesulitan apa yang kamu alami dalam membuat grafik?
   Saya agak kesulitan pas ngatur tampilan grafiknya, kayak label dan judulnya biar bagus. Kadang juga error karena salah ketik atau file CSV-nya belum kebaca.
3. Menurut kamu, apakah AI membantu dalam analisis sebuah data?
   Iya, AI sangat membantu karena bisa menghitung dan menganalisis data dengan cepat, bahkan bisa menemukan pola yang mungkin nggak kelihatan kalau cuma dilihat manual.

Penjelasan Kode
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
- Ini buat import library yang dibutuhin.

data = pd.read_csv('file.csv')
- Ini buat baca file CSV yang isinya data nilai siswa (nama, mapel, nilai).
Jadi data sekarang nyimpen semua isi dari file itu.

data.info()
- Nampilin info umum tentang dataset, kayak jumlah baris, kolom, dan tipe datanya.

data.head()
- Nampilin 5 data teratas, biar bisa lihat sekilas isi tabelnya bener atau belum.

data.describe()
- Buat nampilin statistik deskriptif, kayak:
count: jumlah data,
mean: rata-rata,
min, max, dan std: standar deviasi.
Dari situ keliatan nilai tertinggi 98 dan terendah 75, rata-rata sekitar 86-an.

print("Rata-rata:", data['Nilai'].mean())
print("Median:", data['Nilai'].median())
print("Modus:", data['Nilai'].mode()[0])
- Buat ngitung tiga ukuran statistik utama:
Mean (rata-rata) = 86.3
Median (nilai tengah) = 86.5
Modus (nilai yang paling sering muncul) = 85

matematika = data[data['Mapel'] == 'Matematika']
print(matematika)
- Nyari dan nampilin data yang mapelnya Matematika aja, biar bisa dianalisis terpisah.

data.groupby('Mapel')['Nilai'].agg(['max','min'])
- Ngumpulin data berdasarkan Mapel dan ngambil nilai tertinggi (max) dan terendah (min) dari tiap mapel.
Dari situ ketahuan:
Bahasa Indonesia: max 88, min 75
Bahasa Inggris: max 90, min 78
Fisika: max 95, min 75
Matematika: max 98, min 85
Produktif: max 90, min 80

rata = data.groupby('Mapel')['Nilai'].mean()
rata.plot(kind='bar')
plt.title('Rata-Rata Nilai per Mapel')
plt.xlabel('Mata Pelajaran')
plt.ylabel('Nilai Rata-Rata')
plt.show()
- Ini bikin grafik batang (bar chart) yang nunjukin rata-rata nilai per mapel.
Dari grafik kelihatan kalau Matematika paling tinggi, sedangkan Bahasa Indonesia paling rendah.

sns.boxplot(x='Mapel', y='Nilai', data=data)
plt.title('Sebaran Nilai per Mata Pelajaran')
plt.show()
- Ini bikin boxplot, tujuannya buat lihat persebaran nilai di tiap mapel.
Dari situ kelihatan mapel mana yang nilainya nyebar jauh (banyak variasi), dan mana yang nilainya hampir sama semua.
