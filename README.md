# TokoApp - Daftar Produk Toko

Aplikasi desktop JavaFX untuk mencatat produk toko. Proyek ini adalah hasil modifikasi aplikasi praktikum TiketAppAdvanced menjadi aplikasi pencatatan produk, dengan struktur dan pola kode yang sama (Navigator, controller, FXML, dan CSS).

**Identitas**
- Nama: Muhammad Angger Satrio
- NIM: 2501781
- Tugas: Tugas Individu, Modifikasi Aplikasi Menjadi Daftar Produk Toko

## Fitur

1. **Form tambah produk.** Mengisi nama, kategori (Makanan atau Minuman), dan harga. Kode produk dibuat otomatis dengan format PR001, PR002, dan seterusnya.
2. **Tabel produk.** Menampilkan kode, nama, kategori, dan harga.
3. **Pencarian.** Mencari berdasarkan nama produk lewat tombol Cari. Huruf besar dan kecil tidak berpengaruh. Tombol Reset menampilkan semua produk kembali.
4. **Lihat Detail.** Membuka halaman detail dari produk yang dipilih di tabel.

## Aturan validasi

| Input | Hasil |
|---|---|
| Nama kosong atau hanya spasi | Ditolak, "Nama produk tidak boleh kosong." |
| Harga 0 atau negatif | Ditolak, "Harga harus lebih dari nol." |
| Harga bukan bilangan bulat | Ditolak, "Harga harus berupa bilangan bulat." |
| Kategori selain Makanan atau Minuman | Ditolak, "Kategori harus Makanan atau Minuman." |

## Struktur proyek

```
ProdukTokoApp
|-- pom.xml
`-- src/main
    |-- java/kelas
    |   |-- MainApp.java            titik masuk aplikasi
    |   |-- Navigator.java          perpindahan halaman
    |   |-- model/Produk.java       class Produk (atribut private, constructor, getter)
    |   |-- data/DataProduk.java    penyimpanan data selama aplikasi berjalan
    |   `-- controller
    |       |-- FormController.java
    |       |-- DaftarController.java
    |       `-- DetailController.java
    `-- resources/kelas
        |-- form.fxml
        |-- daftar.fxml
        |-- detail.fxml
        `-- styles/app.css          CSS dari praktikum
```

## Kebutuhan

- JDK 17 atau lebih baru
- Maven (sudah termasuk di NetBeans)
- Koneksi internet saat build pertama agar Maven bisa mengunduh JavaFX 21

## Cara menjalankan

**Lewat NetBeans**
1. Ekstrak zip proyek.
2. Pilih File, lalu Open Project, lalu pilih folder `ProdukTokoApp`.
3. Klik kanan proyek, pilih Clean and Build.
4. Klik kanan proyek, pilih Run.

**Lewat terminal**
```
mvn clean javafx:run
```

## Cara pengujian

1. Buka form lalu tambahkan minimal tiga produk, misalnya:
   - Nasi Goreng, Makanan, 15000
   - Teh Manis, Minuman, 5000
   - Roti Bakar, Makanan, 12000
2. Pastikan ketiga produk muncul di tabel dengan kode PR001 sampai PR003.
3. Ketik "teh" di kolom pencarian lalu klik Cari. Hanya Teh Manis yang tampil.
4. Pilih satu baris lalu klik Lihat Detail. Halaman detail menampilkan produk yang dipilih.
5. Coba simpan dengan nama kosong, harga 0, atau harga berupa huruf. Semuanya harus ditolak dengan pesan yang sesuai.

## Catatan desain

- Halaman detail menerima objek `Produk` yang dipilih dari tabel, bukan data yang ditulis langsung di kode.
- Data hanya tersimpan di memori selama aplikasi berjalan. Tidak ada database, gambar, perhitungan transaksi, maupun inheritance.
- Validasi dilakukan di constructor `Produk`, sehingga objek produk yang tidak valid tidak akan pernah terbentuk.
