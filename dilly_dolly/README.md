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

# Tugas 8
1. Apa kegunaan const di Flutter? Jelaskan apa keuntungan ketika menggunakan const pada kode Flutter. Kapan sebaiknya kita menggunakan const, dan kapan sebaiknya tidak digunakan?
2. Jelaskan dan bandingkan penggunaan Column dan Row pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!
3. Sebutkan apa saja elemen input yang kamu gunakan pada halaman form yang kamu buat pada tugas kali ini. Apakah terdapat elemen input Flutter lain yang tidak kamu gunakan pada tugas ini? Jelaskan!
4. Bagaimana cara kamu mengatur tema (theme) dalam aplikasi Flutter agar aplikasi yang dibuat konsisten? Apakah kamu mengimplementasikan tema pada aplikasi yang kamu buat?
5. Bagaimana cara kamu menangani navigasi dalam aplikasi dengan banyak halaman pada Flutter?

Jawaban
1. const digunakan untuk mendeklarasikan value yang sifatnya konstan dan tidak berubah selama aplikasi berjalan. Keuntungan dari penggunaan const adalah dapat menghemat penggunaan memori dan mempercepat proses rendering sebab objek const hanya perlu dibuat sekali dan dapat digunakan kembali (reuse) tanpa perlu membuat objek baru. Dengan tidak membuat objek ulang, aplikasi berjalan lebih cepat dan responsif.

const sebaiknya digunakan pada widget yang nilai variabelnya sudah pasti tidak akan berubah (statis), seperti teks atau ikon. Sebaliknya, const sebaiknya tidak digunakan pada widget yang nilai variabelnya berubah-ubah berdasarkan interaksi pengguna (dinamis), seperti nilai counter yang berubah tiap tombol ditekan.

2. Column dan Row digunakan untuk menyusun tata letak elemen secara vertikal dan horizontal.
- Column digunakan untuk menyusun widget atau elemen secara vertikal. Ketika kita ingin menampilkan beberapa elemen yang disusun berurutan secara vertikal, seperti form input, daftar teks, dan lain sebagainya, kita dapat menggunakan Column.
- Row digunakan untuk menyusun widget atau elemen secara horizontal. Ketika kita ingin menampilkan beberapa elemen yang sejajar dalam satu baris, misalnya card nama dan npm yang disusun sejajar di halaman utama dan lainnya, kita dapat menggunakan Row.

Contoh implementasi :
- menu.dart : 
1) Column pertama berada di dalam body halaman. Column ini menyusun elemen-elemen secara vertikal, seperti Row, SizedBox, dan Center. Elemen ini diatur agar berada di tengah dengan crossAxisAlignment: CrossAxisAlignment.center. 
2) Pada bagian Center, terdapat Column lain yang menyusun teks dan grid item secara vertikal. 
3) Di dalam widget InfoCard, Column juga digunakan untuk menyusun teks title dan content dengan jarak vertikal antara keduanya. 
4) Row digunakan untuk menampilkan InfoCard secara horizontal, masing-masing berisi informasi tentang nama, npm, dan kelas. 
- productentry_form.dart :
1) Column digunakan untuk menyusun widget-widget secara vertikal di dalam halaman ProductEntryFormPage. Di dalam widget Form, Column menyusun Padding yang mengandung TextFormField untuk setiap atribut produk, seperti Product, Price, Description, Category, dan Stock.
2) Column digunakan untuk menampilkan isi dialog konfirmasi saat produk berhasil disimpan. Dalam AlertDialog, Column mengatur teks seperti Product, Price, Description, Category, dan Stock secara vertikal.
- product_cart.dart :
Dalam kode ItemCard di atas, Column digunakan untuk menyusun widget Icon dan Text secara vertikal dalam kartu (ikon dan teks ditampilkan satu di atas yang lain).
- left_drawer.dart :
widget Column digunakan di dalam DrawerHeader untuk menyusun dua widget Text secara vertikal di bagian header drawer. Text pertama menampilkan nama aplikasi ("Dilly Dolly") dalam ukuran font yang lebih besar dan tebal. Text kedua adalah teks slogan dalam ukuran yang lebih kecil dan gaya normal.

3. Elemen input pada halaman form:
1) TextFormField, digunakan untuk input berikut:
- Product: TextFormField untuk input teks nama produk.
- Price: TextFormField untuk input harga dalam bentuk angka.
- Description: TextFormField dengan maxLines: 5 untuk input deskripsi produk.
- Category: TextFormField untuk input kategori produk.
- Stock: TextFormField untuk input stok dalam bentuk angka.
2) ElevatedButton, digunakan untuk menyimpan data yang diisi dalam form.

Adapun beberapa elemen input lain di Flutter yang tidak digunakan dalam halaman form adalah:
- DropdownButtonFormField: memilih satu opsi dari suatu daftar (misal memilih kategori produk).
- Checkbox: digunakan untuk input tipe boolean, bisa pilih lebih dari 1.
- Radio: memilih satu opsi dari bseberapa pilihan.
- Slider: untuk input angka dalam rentang tertentu.
- Switch: untuk pilihan boolean (seperti on/off).
- DatePicker: untuk input tanggal.

4. Ya, saya mengimplementasikan tema pada aplikasi Flutter yang saya buat. Tujuan saya mengimplementasikan tema adalah untuk membantu menjaga konsistensi tampilan di aplikasi. Mengatur tema dalam aplikasi Flutter dilakukan di main.dart. Berikut ini caranya:
1) Definisikan tema aplikasi di dalam widget MaterialApp pada main.dart.
2) Gunakan prperti ThemeData untuk mengatur berbagai aspek tema, contohnya mengatur warna utama (primarySwatch) dan warna aksen (secondary)
3) Gunakan tema yang telah didefinisikan di atas pada widget, misalnya di AppBar dan DrawerHeader
appBar: AppBar(
  title: const Text(
    'Dilly Dolly',
    style: TextStyle(
      color: Colors.white,
      fontWeight: FontWeight.bold,
    ),
  ),
  backgroundColor: Theme.of(context).colorScheme.primary,
  iconTheme: const IconThemeData(color: Colors.white),
),
dan 
DrawerHeader(
  decoration: BoxDecoration(
    color: Theme.of(context).colorScheme.primary,
  ),
    ...
),

5. Untuk menangani navigasi dalam aplikasi Flutter dengan banyak halaman, saya menggunakan Navigator dan MaterialPageRoute (keduanya dipakai bersamaan). Berikut ini penjelasan mengenai Navigator :
- Navigator.push: menambahkan halaman baru ke tumpukan navigasi.
- Navigator.pushReplacement: menggantikan halaman saat ini dengan halaman baru.
- Navigator.pop: kembali ke halaman sebelumnya.
Berikut ini adalah langkah-langkahnya:
- Buat halaman baru sebagai widget.
- Gunakan Navigator.push atau Navigator.pushReplacement bersama dengan MaterialPageRoute untuk berpindah ke halaman baru.
- Gunakan Navigator.pop untuk kembali ke halaman sebelumnya.

Contoh Implementasi :
Dalam proyek ini, saya memiliki dua halaman, yaitu MyHomePage dan ProductEntryFormPage. Saya gunakan Navigator.push untuk menambahkan halaman baru ke tumpukan navigasi, atau Navigator.pushReplacement untuk menggantikan halaman saat ini dengan halaman baru (tidak ada tombol back pada pushReplacement). Misal pada left_drawer.dart, Navigator.push digunakan untuk pindah ke halaman menambah product entry (ada tombol back untuk kembali), sedangkan Navigator.pushReplacement untuk menggantikan halaman saat ini dengan halaman MyHomePage. Selain itu, saya menggunakan Navigator.pop untuk kembali ke halaman sebelumnya, contohnya yaitu di ProductEntryFormPage. 