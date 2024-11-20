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

# Tugas 9
1. Jelaskan mengapa kita perlu membuat model untuk melakukan pengambilan ataupun pengiriman data JSON? Apakah akan terjadi error jika kita tidak membuat model terlebih dahulu?
2. Jelaskan fungsi dari library http yang sudah kamu implementasikan pada tugas ini 
3. Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
4. Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.
5. Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
6. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).

Jawaban
1. Kita perlu membuat model untuk pengambilan atau pengiriman data JSON dengan beberapa tujuan berikut:
- Membuat struktur data yang konsisten
Model memastikan bahwa data yang diterima atau dikirim memiliki struktur yang konsisten. Tujuannya adalah menghindari kesalahan yang bisa saja terjadi karena perubahan struktur data. Misalnya, dalam proyek saya, saat kita menerima data JSON yang berisi informasi suatu produk, maka model akan memastikan bahwa setiap produk memiliki atribut name, price, description, category, dan stock.
- Validasi data
Model dapat memvalidasi data sebelum data tersebut digunakan. Tujuannya adalah memastikan bahwa data yang diterima/dikirim sesuai dengan ketentuan. Misalnya, validasi pada field price yang harus berupa angka. Selain itu, ini juga mengurangi risiko serangan injeksi atau data yang tidak valid sehingga program lebih aman.
- Data lebih mudah digunakan
Model membuat data lebih mudah digunakan dalam kode. Daripada mengakses data JSON mentah, kita dapat mengakses atribut data langsung melalui properti model. 
- Maintenance kode lebih mudah, mengurangi duplikasi kode, 
Jika ada perubahan pada struktur data, kita hanya perlu memperbarui model bukan seluruh kode yang menggunakan data tersebut. Dengan menggunakan model sebagai satu-satunya sumber struktur data, dapat dipastikan bagian kode yang menggunakan data tersebut mengacu pada model yang sama.

Jika kita tidak membuat model terlebih dahulu, beberapa kerugian yang bisa kita alami:
- Kesalahan struktur data
Tanpa model, kita bisa saja tidak menyadari perubahan pada struktur data yang diterima dari server sehingga ini bisa mengakibatkan kesalahan saat mengakses atribut data.
- Kesulitan dalam debugging
Tanpa model, debugging menjadi lebih sulit karena kita harus melacak struktur data mentah pada kode kode.
- Kode tidak terstruktur
Tanpa model, kode menjadi tidak terstruktur dan sulit dipahami karena harus mengakses data JSON mentah secara langsung.
- Kurangnya validasi
Tanpa model, kita juga mungkin tidak bisa melakukan validasi data sebelum menggunakannya sehingga menyebabkan kesalahan atau kerentanan keamanan.

2. Library http di Flutter digunakan untuk membuat permintaan HTTP ke server. Dalam proyek ini, library ini digunakan untuk mengirim dan menerima data dari server Django. Berikut ini implementasinya:
1) Mengirim permintaan HTTP dengan metode :
- GET: Mengambil data dari server.
- POST: Mengirim data ke server.
2) Mengatur header dan body Permintaan
- Menambahkan header seperti Content-Type.
- Mengirim data dalam format JSON.
3) Mengatur Respons
- Mengambil data dari respons server.
- Memeriksa status kode respons untuk menentukan apakah permintaan berhasil atau gagal.

Implementasi http :
1) GET request : Di file list_productentry.dart, saya menggunakan CookieRequest untuk mengirim permintaan GET ke server dan mengambil data produk.
2) POST request : Di file productentry_form.dart, saya menggunakan CookieRequest untuk mengirim permintaan POST ke server dan mengirim data produk. Ketika tombol "Save" ditekan, fungsi ini mengirim permintaan POST ke URL http://127.0.0.1:8000/create-flutter/ dan data produk yang dikirim dalam format JSON.
3) Mengatur header dan body request, contohnya : 
final response = await request.postJson(
  "http://127.0.0.1:8000/create-flutter/",
  jsonEncode(<String, String>{
    'name': _name,
    'price': _price.toString(),
    'description': _description,
    'category': _category,
    'stock': _stock.toString(),
  }),
);
Data produk dikonversi menjadi format JSON menggunakan jsonEncode dan dikirim ke server dengan header Content-Type yang menunjukkan data dalam format JSON.

3. CookieRequest adalah kelas yang digunakan untuk mengatur permintaan HTTP yang memerlukan autentikasi berbasis cookie. Biasanya berhubungan dengan aplikasi yang menyimpan status login pengguna. Fungsi utama:
1) Mengelola Cookie
- Menyimpan Cookie: CookieRequest menyimpan cookie yang diterima dari server setelah pengguna login atau permintaan lainnya.
- Mengirim Cookie: CookieRequest mengirim cookie yang disimpan bersama dengan permintaan HTTP.
2) Autentikasi Pengguna:
- Login: CookieRequest digunakan untuk mengirim permintaan login dan menyimpan cookie session yang diterima dari server.
- Logout: CookieRequest dapat digunakan untuk mengirim permintaan logout dan menghapus cookie session yang disimpan.
3) Mengirim Permintaan HTTP:
- GET: Mengirim permintaan GET dengan cookie yang disimpan.
- POST: Mengirim permintaan POST dengan cookie yang disimpan.
- Mengelola Header dan Body: CookieRequest mengelola header dan body permintaan, termasuk menambahkan header Content-Type dan mengirim data dalam format JSON (seperti di soal sebelumnya).

Instance CookieRequest perlu dibagikan ke semua komponen di aplikasi flutter untuk mencapai beberapa hal ini:
1) Status login yang konsisten
Dengan membagikan instance CookieRequest ke semua komponen, dapat dipastikan bahwa status login pengguna konsisten di seluruh aplikasi. Pengguna tidak perlu login ulang setiap kali mereka mengakses page berbeda dari aplikasi.
2) Memudahkan proses manage session pada aplikasi
CookieRequest mengatur sesi pengguna dengan menyimpan dan mengirim cookie secara otomatis.
3) Memudahkan penggunaan
Dengan menggunakan Provider untuk membagikan instance CookieRequest, mengakses aplikasi dari mana saja menjadi lebih mudah tanpa perlu mengirim instance tersebut melalui constructor atau parameter. Contohnya di file main.dart, saya pakai Provider untuk membagikan instance CookieRequest ke seluruh aplikasi.

4. Mekanisme pengiriman data :
- Input data : Pengguna isi form di flutter
Implementasi : productentry_form.dart akan menampilkan form yang bisa diisi oleh pengguna.
- Kirim data : Ketika pengguna menekan tombol "Save", data dari formulir dikirim ke server Django menggunakan permintaan POST. Data dikirim dalam format JSON.
Implementasi : ketika klik tombol "Save" di productentry_form.dart, maka fungsi onPressed: () async {...} akan jalan yang tujuannya adalah untuk mengirim data (JSON) dari form ke Django.
- Proses data : Server Django menerima permintaan POST, memproses data, dan menyimpannya ke dalam database. Jika data berhasil disimpan, server mengirimkan respons JSON dengan status "success".
Implementasi : pada views.py di main pada proyek Django, terdapat fungsi untuk menyimpan data ke database. Fungsi ini bernama create_product_flutter. Fungsi ini akan mengirimkan respons JSON dengan status yang sesuai (success/error).
- Tampilkan data : Setelah data berhasil disimpan, pengguna diarahkan kembali ke halaman utama. Data produk yang baru ditambahkan diambil dari server dan ditampilkan di halaman daftar produk.
Implementasi : Pada list_productentry.dart pengguna dapat melihat produk yang sudah ditambahkan oleh dirinya sendiri. Pengguna dapat klik produk yang sudah mereka tambahkan tersebut, lalu akan diarahkan ke sebuah halaman (product_detail.dart) yang berisi detail mengenai produk tersebut.

5. Mekanisme autentikasi dari login, register, hingga logout:
1) Register
- Input data akun di Flutter: Pengguna mengisi form registrasi di aplikasi Flutter dengan memasukkan username, password, dan konfirmasi password. Implementasi kode ada dalam file register.dart.
- Proses register di Django: Server Django menerima permintaan POST, memproses data, dan membuat pengguna baru di database. Selanjutnya, Django mengirimkan pesan error/success. Implementasi ada di views.py dalam direktori authentication di proyek Django.
2) Login
- Input data akun di Flutter: Pengguna mengisi formu login dengan memasukkan username dan password. Implementasi kode ada di login.dart.
- Proses login di Django : Server Django menerima permintaan POST, memverifikasi data pengguna (mengecek apakah data yang diterima sesuai dengan kredensial pengguna), dan mengirimkan pesan error/success. Jika sukses, pengguna diarahkan ke halaman utama di Flutter. Impementasi ada di views.py dalam direktori authentication di proyek Django.
3) Logout
- Proses logout di Flutter: Pengguna menekan tombol logout yang akan mengirimkan permintaan logout ke server Django. Jika sukses, pengguna diarahkan kembali ke halaman login di Flutter. Implementasi tombol logout ada di product_cart.dart.
- Proses logout di Django: Server Django menerima permintaan logout dan menghapus cookie session pengguna. Impementasi ada di views.py dalam direktori authentication di proyek Django.

6. Implementasi checklist:
1) Mengimplementasikan fitur registrasi akun pada proyek tugas Flutter.
- Pertama, saya membuat file registrasi.dart dan membuat form register. Untuk menyimpan/meng-assign value dari input pengguna, saya menggunakan TextEditingController(). Saya membuat elemen tampilan lain pada halaman ini, seperti button register, field untuk mengisi username dan password, button untuk kembali ke login page.
- Kemudian, saya menambahkan fungsi register di views.py pada direktori authentication di proyek Django saya untuk menangani permintaan registrasi.
- Saya menambahkan URL yang sesuai pada register.dart ("http://127.0.0.1:8000/auth/register/") untuk mengirimkan data ke fungsi registrasi yang telah saya buat sebelumnya.
2) Membuat halaman login pada proyek tugas Flutter.
- Pertama, saya membuat file login.dart dan membuat form login. Untuk menyimpan/meng-assign value dari input pengguna, saya menggunakan TextEditingController(). Saya membuat elemen tampilan lain pada halaman ini, seperti button register, field untuk mengisi username dan password, button untuk kembali ke login page.
- Kemudian, saya menambahkan fungsi login di views.py pada direktori authentication di proyek Django saya untuk menangani permintaan login.
- Saya menambahkan URL yang sesuai pada login.dart ("http://127.0.0.1:8000/auth/login/") untuk mengirimkan data ke fungsi login yang telah saya buat sebelumnya.
3) Mengintegrasikan sistem autentikasi Django dengan proyek tugas Flutter.
saya menggunakan CookieRequest untuk mengelola login session pengguna di Flutter. Saya juga menggunakan CookieRequest dalam komponen untuk mengirim permintaan login dan logout. Tidak lupa, sebelumnya, saya menambahkan URL yang sesuai untuk logout di product_cart (http://127.0.0.1:8000/auth/logout/) dan membuat fungsi logout di views.py pada direktori authentication di proyek Django saya.
Intinya:
1. Endpoint Django
Saya membuat endpoint untuk registrasi, login, dan logout di Django pada direktori authentication. Saya menggunakan csrf_exempt untuk mengizinkan permintaan dari aplikasi Flutter.
2. Halaman Flutter
Saya membuat halaman registrasi, login, dan logout di Flutter. Lalu, saya menggunakan CookieRequest untuk mengirim permintaan HTTP ke endpoint Django.Kemudian akan ditampilkan pesan sukses atau gagal berdasarkan respons dari server.
4) Membuat model kustom sesuai dengan proyek aplikasi Django.
Saya mendefinisikan model di product_entry.dart. Model yang saya gunakan didapatkan dari endpoint JSON pada proyek Django saya. Pertama, saya menambahkan produk pada proyek Django lalu saya mengakses data JSON-nya dan saya melakukan parsing JSON di web quicktype. Kemudian, hasil kodenya saya pakai untuk model kustom di proyek Flutter.
5) Membuat halaman yang berisi daftar semua item yang terdapat pada endpoint JSON di Django yang telah kamu deploy.
Pertama, saya membuat file di lib/screens yang bernama list_productentry.dart. Kemudian saya menggunakan CookieRequest untuk mengambil data dari endpoint JSON di Django (final response = await request.get('http://127.0.0.1:8000/json/');). Pada proyek Django, fungsi show_Json sudah didefinisikan dan fungsi ini akan menngembalikan data seluruh produk yang terasosiasi dengan pengguna yang sedang login. Setelah data diambil dari endpoint JSON, data akan ditampilkan di aplikasi Flutter dengan keterangan name, price, dan description.
6) Membuat halaman detail untuk setiap item yang terdapat pada halaman daftar Item.
Pertama, saya membuat file product_detail.dart. Pada list_productentry.dart, ketika produk (yang isinya hanya name, price, dan desc) diklik, pengguna akan diarahkan ke page product_detail.dart. Implementasi pada kode, yaitu pada ListView.builder(...), onTap menandakan ketika container diklik maka pengguna akan diarahkan ke ProductDetailPage(product: snapshot.data![index]) menggunakan Navigation.push. Page ini berisi semua atribut yang dimiliki oleh produk, seperti name, price, description, category, dan stock. Pada halaman ini juga ada tombol back (berbentuk panah) untuk kembali ke halaman daftar produk (secara otomatis ditambahkan karena saya menggunakan Navigation.push).
7) Melakukan filter pada halaman daftar item dengan hanya menampilkan item yang terasosiasi dengan pengguna yang login.
Seluruh produk yang ditampilkan di halaman daftar produk adalah produk yang terasosiasi dengan user yang sedang login saja. Hal ini disebabkan Flutter mengambil data dari Django melalui URL 'http://127.0.0.1:8000/json/'. Pada proyek Django saya, URL ini mengarah ke fungsi show_Json yang gunanya untuk mengambil seluruh data produk yang difilter berdasarkan usernya :
def show_json(request):
  data = Product.objects.filter(user=request.user)
  return HttpResponse(serializers.serialize("json", data), content_type="application/json")
Fungsi ini akan mengembalikan data dalam format Json dan data ini dipastikan hanya berisi item yang terasosiasi dengan penggna yang login.



