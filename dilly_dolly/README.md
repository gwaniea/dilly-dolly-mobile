# Tugas 7
1. Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.
2. Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.
3. Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.
4. Jelaskan perbedaan antara const dengan final.
5. Jelaskan bagaimana cara kamu mengimplementasikan checklist-checklist di atas.

Jawaban
1. Stateless Widget adalah widget yang tidak memiliki state yang berubah setelah widget dibuat sehingga tampilannya statis dan tidak berubah ketika interaksi dengan pengguna/seiring waktu. Contohnya : Text, Icon, RaisedButton

Stateful Widget adalah widget yang memiliki state yang berubah ketika interaksi dengan pengguna/seiring waktu (tampilannya bisa berubah/dinamis). Contohnya : Checkbox, Slider, TextField

Perbedaan keduanya :
a. Stateless Widget tidak bisa diubah setelah dirender dan hanya dirender sekali, sedangkan Stateful Widget bisa diubah tampilannya sesuai dengan perubahan yang terjadi pada variabel-variabel tertentu (state).
b. Stateless Widget tidak dapat menyimpan data yang berubah seiring waktu, sedangkan Stateful Widget dapat menyimpan data yang mungkin berubah-ubah.
c. Stateful Widget lebih kompleks dibanding Stateless Widget sebab memerlukan lebih banyak memori serta pemrosesan untuk melacak perubahan pada state.

2. Widget yang digunakan :
- MaterialApp: widget utama yang berfungsi sebagai dasar aplikasi berbasis Material Design. Gunanya untuk mengatur judul, halaman awal yang akan ditampilkan, dan lain sebagainya.
- Scaffold: menyediakan struktur dasar halaman aplikasi dengan AppBar (bagian atas) dan body (isi utama).
- AppBar: menampilkan bagian atas halaman dengan judul aplikasi ("Dilly Dolly") dan memberikan akses untuk mengubah warna, teks, serta berbagai elemen lainnya.
- Padding: memberikan jarak di sekitar widget.
- Column: menyusun widget-widget secara vertikal (misalnya InfoCard dan komponen lain seperti GridView)
- Row: Menyusun widget-widget secara horizontal (misalnya terdapat 3 InfoCard dalam satu baris)
- InfoCard: widget yang meng-extend Stateless Widget untuk menampilkan informasi NPM, nama, dan kelas. 
- GridView.count: membuat layout dalam bentuk grid dengan jumlah kolom tetap.
- ItemCard: widget yang meng-extend Stateless Widget untuk menampilkan nama dan ikon untuk setiap widget.
- Material: digunakan sebagai dasar untuk membuat tampilan kartu yang responsif terhadap klik-an.
- InkWell: memberikan efek klik pada widget supaya menjadi interaktif. Dalam konteks proyek ini, menambahkan aksi ketika kartu ditekan yang menampilkan SnackBar.
- SnackBar: menampilkan pesan di bagian bawah layar ketika ItemCard ditekan.
- Text: Menampilkan teks pada layar.
- Icon: Menampilkan ikon pada layar.
- SizedBox: membuat jarak antar elemen-elemen widget, seperti antar teks di dalam InfoCard.

3. Fungsi setState():
setState() adalah metode dalam Stateful Widget yang digunakan untuk memperbarui state. Ketika setState() dipanggil, Flutter akan rebuild widget sesuai dengan perubahan state terbaru sehingga tampilannya menyesuaikan/dinamis. Variabel yang terpengaruh metode ini adalah semua variabel yang merupakan bagian dari state dalam widget tersebut.

4. Perbedaan const dan final :
- final : nilai variabel final hanya dapat diinisialisasi sekali dan tidak dapat diubah setelah itu. final dapat digunakan untuk variabel yang nilainya diketahui pada saat runtime.
Contoh : 
final int x = 10;
final DateTime now = DateTime.now(); 
(Nilai ditentukan saat runtime)
- const : nilai variabel const harus diketahui pada saat kompilasi dan bersifat konstan sepanjang waktu. const digunakan untuk nilai yang benar-benar konstan dan tidak akan pernah berubah. const juga dapat digunakan untuk membuat objek immutable.
Contoh : 
const int y = 20;
const pi = 3.14; 
(Nilai ditentukan saat kompilasi)

5. Jelaskan bagaimana cara kamu mengimplementasikan checklist-checklist di atas.
1) Membuat sebuah program Flutter baru dengan tema E-Commerce yang sesuai dengan tugas-tugas sebelumnya.
Pertama, saya menginstall flutter dan menambahkannnya ke variabel PATH. Selanjutnya, pada cmd direktori dilly-dolly-mobile saya menjalankan perintah "flutter create dilly_dolly".
2) Membuat tiga tombol sederhana dengan ikon dan teks serta mengimplementasikan warna-warna yang berbeda untuk setiap tombol.
Sama seperti tutorial 6, saya mengikuti langkah-langkah dalam merapikan struktur proyek, membuat widget, dan lainnya, tetapi bedanya pada kelas tombol saya menambahkan atribut warna agar ketiganya dapat memiliki warna yang berbeda. Pertama, saya buat kelas model untuk tombol (ItemHomePage). kelas ini gunanya untuk menyimpan informasi tentang setiap tombol, seperti nama, ikon, dan warna. Kedua, buat widget (ItemCard) untuk menampilkan tombol dengan ikon, teks, dan warna yang berbeda. Ketiga, saya menambahkan tombol-tombol tersebut ke halaman utama di MyHomePage.
3) Memunculkan Snackbar ketika tombol ditekan.
Pertama, saya modifikasi onTap pada ItemCard untuk menampilkan pesan yang sesuai pada SnackBar :
onTap: () {
    ScaffoldMessenger.of(context)
    ..hideCurrentSnackBar()
    ..showSnackBar(
        SnackBar(content: Text("Kamu telah menekan tombol ${item.name}!"))
    );
},
Karena ini mengambil name dari objek item yang merupakan instansiasi dari kelas ItemHomePage, saya harus memastikan bahwa properti name pada kelas tersebut sesuai. Ketika sudah sesuai, maka SnackBar akan muncul dengan pesan yang sesuai ketika tombol "Lihat Daftar Produk", "Tambah Produk", atau "Logout" ditekan.