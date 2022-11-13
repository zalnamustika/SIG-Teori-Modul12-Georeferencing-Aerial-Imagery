# SIG-Teori-Modul12-Georeferencing-Aerial-Imagery

## Data

Silahkan Unduh data berikut :

[newyorkcity-washingtonsquarepark.jpg](https://www.qgistutorials.com/downloads/newyorkcity-washingtonsquarepark.jpg)

## Prosedur 

1. Kami akan menggunakan peta dasar dari OpenStreetMap untuk menangkap koordinat georeferensi. QGIS3 hadir dengan dukungan built-in untuk lapisan petak. Ini umumnya dikenal sebagai lapisan 'XYZ' karena dibuat menggunakan petak peta individual untuk setiap tingkat zoom (z) pada petak koordinat ax,y. Anda dapat menemukan OpenStreetMaplapisan di bawah Ubin XYZ di Panel Peramban . Seret layer ke kanvas utama. Setelah dimuat, catat Sistem Referensi Koordinat (CRS) untuk lapisan ini di corder kanan bawah. Ini diatur sebagai . Ini penting karena koordinat yang kita simpulkan dari lapisan ini selama georeferensi akan berada di CRS ini.EPSG 3857 Pseudo Mercator

-------------------------

Catatan :
Lihat [halaman ini](https://www.spatialbias.com/2018/02/qgis-3.0-xyz-tile-layers/) untuk detail lebih lanjut tentang lapisan XYZ dan cara menambahkan peta dasar lain di QGIS.

--------------------------

2. Gambar yang kami georeferensi adalah untuk . Anda dapat memperbesar/menggeser untuk menemukan taman ini di peta. Tapi itu rumit dan tidak praktis. Dari QGIS versi 3.20 dan seterusnya, ada dukungan bawaan untuk Nominatim Geocoder berbasis OpenStreetMap. Klik bilah pencarian di kiri bawah jendela QGIS. Untuk menggunakan ini sebagai awalan geocoder, tempat pencarian dengan . Pencarian akan memunculkan daftar alamat yang dapat dipilih. Klik alamat pertama.Washington Square Park, New York>> Washington Square Park.

3. Kanvas peta akan dipusatkan ke Square Park. Sekarang mari kita mulai georeferensi. Luncurkan Georeferencer dari Raster Georeferencer .

------------------------------

Catatan :

Dari QGIS versi 3.26 dan seterusnya, Georeferencer dapat diluncurkan dari Layer Georeferencer.

------------------------------

4. Untuk georeferensi gambar udara, kita harus memilih titik koordinat dari OpenStreetMap, jadi pertama-tama mari kita masukkan alat Georeferencer ke jendela utama QGIS. Pilih Konfigurasi Georeferensi dari Pengaturan Konfigurasikan Georeferensi .

5. Centang Show georeferencer window docked dan klik OK .

6. Jendela Georeferencer akan ditempatkan di bagian bawah jendela utama QGIS. Mari kita memuat file gambar dengan mengklik ikon Open Raster di jendela Georeferencer dan menavigasi ke file JPG yang diunduh. Klik Buka.

7. Sebelum menambahkan Titik Kontrol Tanah (GCP), kita perlu menentukan Pengaturan Transformasi. Klik ikon Pengaturan Transformasi untuk membuka dialog Pengaturan Transformasi. Pilih jenis Transformasi sebagai . Lihat Dokumentasi QGIS untuk mempelajari tentang berbagai jenis transformasi dan kegunaannya. Seperti disebutkan sebelumnya, peta dasar kita ada di CRS, jadi tetapkan itu sebagai Target CRS . Anda dapat membiarkan nama raster Output ke default dan memilih sebagai Compression . Periksa Gunakan 0 untuk transparansi bila diperlukan . Periksa Simpan poin GCPPolynomial 2EPSG 3857 Pseudo MercatorLZWuntuk menyimpan poin sebagai file terpisah untuk tujuan di masa mendatang. Pastikan opsi Muat di QGIS saat selesai dicentang. Klik Oke .

8. Sekarang klik tombol Add Point pada toolbar dan pilih lokasi yang mudah dikenali pada gambar. Sudut, persimpangan, tiang dll, membuat titik kontrol yang baik. Setelah Anda mengklik gambar di lokasi titik kontrol, Anda akan melihat pop-up yang meminta Anda untuk memasukkan koordinat peta. Klik tombol Dari kanvas peta .

9. Di OpenStreetMaplapisan, klik pada lokasi yang tepat di lapisan referensi. Koordinat akan terisi otomatis dari klik Anda pada kanvas peta. Klik Oke .

-----------------

Catatan :

Tips: Saat memilih GCP pada gedung, selalu pilih bagian bawah gedung. Sebagian besar citra udara dan satelit memiliki bangunan miring, jadi memilih titik di atap akan menimbulkan kesalahan.

--------------------------

10. Demikian pula, pilih setidaknya 6 titik pada gambar dan tambahkan koordinatnya dari lapisan referensi. Setelah Anda menambahkan jumlah minimum poin yang diperlukan untuk transformasi, Anda akan melihat bahwa GCP sekarang memiliki nilai bukan nol dX, dY, dan Residualkesalahan. Jika GCP tertentu memiliki nilai kesalahan yang sangat tinggi, itu biasanya berarti kesalahan manusia dalam memasukkan nilai koordinat. Jadi, Anda dapat menghapus GCP tersebut dan merekamnya kembali.

11. Setelah Anda puas dengan GCP, klik Mulai georeferensi . Ini akan memulai proses membengkokkan gambar menggunakan GCP dan membuat raster target. Setelah proses selesai, Anda akan melihat layer dimuat di QGIS. Tutup jendela Georeferensi .

12. Sekarang klik pada ikon panel penataan lapisan Terbuka dan Beralih ke tab Transparansi . Tambahkan 255sebagai nilai tambahan tanpa data . Ini akan menghapus batas putih di sekitar gambar. Sekarang Anda akan melihat gambar georeferensi Anda dilapis dengan baik pada lapisan dasar.

---------------------------

Catatan :

Citra 8-bit memiliki nilai piksel dalam rentang 0-255. 0 berwarna hitam dan 255 berwarna putih.

---------------------------

13. selesai.

