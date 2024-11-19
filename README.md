Berikut adalah contoh README yang diformat dengan baik untuk tugas Anda:

# Tugas 7: Elemen Dasar Flutter

## Implementasi

1. Membuat proyek Flutter baru dengan perintah:
   ```sh
   flutter create glowify
   ```

### Membuat tiga tombol sederhana dengan ikon dan teks

1. Membuka file `menu.dart` dan menambahkan daftar item dengan ikon dan teks:
   ```dart
   final List<ItemHomepage> items = [
     ItemHomepage("Lihat Daftar Produk", Icons.mood),
     ItemHomepage("Tambah Produk", Icons.add),
     ItemHomepage("Logout", Icons.logout),
   ];
   ```

2. Menggunakan `GridView` untuk menampilkan tombol-tombol dalam bentuk grid:
   ```dart
   GridView.count(
     primary: true,
     padding: const EdgeInsets.all(20),
     crossAxisSpacing: 10,
     mainAxisSpacing: 10,
     crossAxisCount: 3,
     shrinkWrap: true,
     children: items.map((ItemHomepage item) {
       return ItemCard(item);
     }).toList(),
   );
   ```

### Warna-warna yang berbeda untuk setiap tombol

1. Membuka file menu.dart dan mengatur warna latar belakang untuk setiap ombol di dalam `ItemCard`:
   ```dart
   class ItemCard extends StatelessWidget {
     final ItemHomepage item;

     const ItemCard(this.item, {super.key});

     @override
     Widget build(BuildContext context) {
       return Material(
         color: Theme.of(context).colorScheme.secondary,
         borderRadius: BorderRadius.circular(12),
         child: InkWell(
           onTap: () {
             ScaffoldMessenger.of(context)
               ..hideCurrentSnackBar()
               ..showSnackBar(
                 SnackBar(content: Text("Kamu telah menekan tombol ${item.title}!")),
               );
           },
           child: Container(
             padding: const EdgeInsets.all(8),
             child: Center(
               child: Column(
                 mainAxisAlignment: MainAxisAlignment.center,
                 children: [
                   Icon(
                     item.icon,
                     color: Colors.white,
                     size: 30.0,
                   ),
                   const Padding(padding: EdgeInsets.all(3)),
                   Text(
                     item.title,
                     textAlign: TextAlign.center,
                     style: const TextStyle(color: Colors.white),
                   ),
                 ],
               ),
             ),
           ),
         ),
       );
     }
   }
   ```

### Memunculkan Snackbar 

1. Menambahkan aksi pada setiap tombol di dalam `ItemCard` untuk memunculkan `Snackbar`:
   ```dart
   onTap: () {
     ScaffoldMessenger.of(context)
       ..hideCurrentSnackBar()
       ..showSnackBar(
         SnackBar(content: Text("Kamu telah menekan tombol ${item.title}!")),
       );
   }
   ```

### Personalized untuk Glowify 

1. Membuka file `main.dart` dan mengatur tema aplikasi:
   ```dart
   colorScheme: ColorScheme.fromSwatch(
     primarySwatch: Colors.brown,
   ).copyWith(secondary: Colors.brown[700]),
   useMaterial3: true,
   ```

2. Mengatur `home` untuk menampilkan `MyHomePage`:
   ```dart
   home: MyHomePage(),
   ```

3. Membuka file `menu.dart` dan menambahkan `AppBar` dengan judul:
   ```dart
   appBar: AppBar(
     title: const Text(
       'Glowify',
       style: TextStyle(
         color: Colors.white,
         fontWeight: FontWeight.bold,
       ),
     ),
     backgroundColor: Theme.of(context).colorScheme.primary,
   ),
   ```

4. Menambahkan `InfoCard` untuk menampilkan informasi pengguna:
   ```dart
   Row(
     mainAxisAlignment: MainAxisAlignment.spaceEvenly,
     children: [
       InfoCard(title: 'User Id', content: userId),
       InfoCard(title: 'Username', content: userName),
       InfoCard(title: 'Skintype', content: skinType),
     ],
   ),
   ```

5. Menambahkan `GridView` untuk menampilkan tombol-tombol:
   ```dart
   GridView.count(
     primary: true,
     padding: const EdgeInsets.all(20),
     crossAxisSpacing: 10,
     mainAxisSpacing: 10,
     crossAxisCount: 3,
     shrinkWrap: true,
     children: items.map((ItemHomepage item) {
       return ItemCard(item);
     }).toList(),
   );
   ```

## Jawaban dari Pertanyaan Tugas 7

### 1. Stateless widget vs stateful widget
#### Stateless widget
- Widget yang tidak berubah setelah dibuat maupun selama aplikasi berjalan. 
- Contoh, `MyHomePage` adalah contoh stateless widget karena hanya menampirkan informasi statis: userId, userName, dan skinType.
#### Stateful Widget
- Widget yang bisa berubah selama aplikasi berjalan, alias memiliki 'state'. Ketika 'state' berubah, widget akan diperbarui. Berguna untuk menampilkan informasi yang bisa berubah berdasarkan interaksi dengan user.
- Contoh, ketika pertama kali menjalankan `flutter run`, jika kita menekan button, maka counter akan diincrement dan ditmapilkan jumlah berapa kali kita menekan button.

### 2. Widget yang digunakan dalam `Glowify`

**1. MaterialApp**
- Untuk mengatur tema dan rute aplikasi.
  ```dart
  return MaterialApp(
    title: 'Flutter Demo',
    theme: ThemeData(
      colorScheme: ColorScheme.fromSwatch(
        primarySwatch: Colors.brown,
      ).copyWith(secondary: Colors.brown[700]),
      useMaterial3: true,
    ),
    home: MyHomePage(),
  );
  ```

**2. Scaffold**
- Menyediakan struktur dasar untuk halaman, seperti `AppBar`, `Body`, dan `FloatingActionButton`.
  ```dart
  return Scaffold(
    appBar: AppBar(
      title: const Text(
        'Glowify',
        style: TextStyle(
          color: Colors.white,
          fontWeight: FontWeight.bold,
        ),
      ),
      backgroundColor: Theme.of(context).colorScheme.primary,
    ),
    body: Padding(
      padding: const EdgeInsets.all(16.0),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.center,
        children: [
          // Konten lainnya
        ],
      ),
    ),
  );
  ```

**3. AppBar**
- Bagian atas halaman yang menampilkan judul aplikasi.
  ```dart
  appBar: AppBar(
    title: const Text(
      'Glowify',
      style: TextStyle(
        color: Colors.white,
        fontWeight: FontWeight.bold,
      ),
    ),
    backgroundColor: Theme.of(context).colorScheme.primary,
  ),
  ```

**4. Padding**
- Untuk memberikan jarak di sekeliling widget.
  ```dart
  body: Padding(
    padding: const EdgeInsets.all(16.0),
    child: Column(
      crossAxisAlignment: CrossAxisAlignment.center,
      children: [
        // Konten lainnya
      ],
    ),
  ),
  ```

**5. Column**
- Untuk menyusun widget secara vertikal.
  ```dart
  child: Column(
    crossAxisAlignment: CrossAxisAlignment.center,
    children: [
      // Konten lainnya
    ],
  ),
  ```

**6. Row**
- Untuk menyusun widget secara horizontal.
- Kode:
  ```dart
  Row(
    mainAxisAlignment: MainAxisAlignment.spaceEvenly,
    children: [
      InfoCard(title: 'User Id', content: userId),
      InfoCard(title: 'Username', content: userName),
      InfoCard(title: 'Skintype', content: skinType),
    ],
  ),
  ```

**7. InfoCard**
- Widget kustom yang digunakan untuk menampilkan informasi dalam bentuk kartu.
  ```dart
  class InfoCard extends StatelessWidget {
    final String title;
    final String content;

    const InfoCard({super.key, required this.title, required this.content});

    @override
    Widget build(BuildContext context) {
      return Card(
        elevation: 2.0,
        child: Container(
          width: MediaQuery.of(context).size.width / 3.5,
          padding: const EdgeInsets.all(16.0),
          child: Column(
            children: [
              Text(
                title,
                style: const TextStyle(fontWeight: FontWeight.bold),
              ),
              const SizedBox(height: 8.0),
              Text(content),
            ],
          ),
        ),
      );
    }
  }
  ```

**8. GridView**
- Untuk menampilkan widget dalam bentuk grid.
  ```dart
  GridView.count(
    primary: true,
    padding: const EdgeInsets.all(20),
    crossAxisSpacing: 10,
    mainAxisSpacing: 10,
    crossAxisCount: 3,
    shrinkWrap: true,
    children: items.map((ItemHomepage item) {
      return ItemCard(item);
    }).toList(),
  );
  ```

**9. ItemCard**
- Widget kustom yang digunakan untuk menampilkan ikon dan teks dalam bentuk kartu.
  ```dart
  class ItemCard extends StatelessWidget {
    final ItemHomepage item;

    const ItemCard(this.item, {super.key});

    @override
    Widget build(BuildContext context) {
      return Material(
        color: Theme.of(context).colorScheme.secondary,
        borderRadius: BorderRadius.circular(12),
        child: InkWell(
          onTap: () {
            ScaffoldMessenger.of(context)
              ..hideCurrentSnackBar()
              ..showSnackBar(
                SnackBar(content: Text("Kamu telah menekan tombol ${item.title}!")),
              );
          },
          child: Container(
            padding: const EdgeInsets.all(8),
            child: Center(
              child: Column(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Icon(
                    item.icon,
                    color: Colors.white,
                    size: 30.0,
                  ),
                  const Padding(padding: EdgeInsets.all(3)),
                  Text(
                    item.title,
                    textAlign: TextAlign.center,
                    style: const TextStyle(color: Colors.white),
                  ),
                ],
              ),
            ),
          ),
        ),
      );
    }
  }
  ```

### Fungsi `setState()` dan variabel apa saja yang terdampak?

**`setState()`**
- Fungsi yang digunakan dalam `StatefulWidget` untuk memberitahu Flutter bahwa ada perubahan pada state yang perlu diperbarui.
- Saat `setState()` dipanggil, Flutter akan menjalankan ulang metode `build()` dari widget tersebut untuk memperbarui tampilan sesuai dengan perubahan state.

**Variabel yang terdampak**
- Semua variabel yang berada dalam kelas `State` dari `StatefulWidget` dapat terdampak oleh `setState()`.
- Misal, ketika pertama kali menjalankan proyek Flutter, disediakan variabel `_counter` yang diubah dalam `setState()`, maka tampilan yang menggunakan `_counter` akan diperbarui.

### Perbedaan antara `const` dengan `final`

**`const`**
- `const` digunakan untuk mendeklarasikan nilai yang bersifat konstan, tidak akan pernah berubah.
- Nilai yang dideklarasikan dengan `const` harus sudah diketahui pada saat di-compile.
- `const` dapat digunakan untuk membuat objek yang bersifat konstan.

**`final`**
- `final` digunakan untuk mendeklarasikan variabel yang nilainya hanya dapat diinisialisasi sekali dan tidak dapat diubah setelah itu.
- Nilai yang dideklarasikan dengan `final` dapat ditentukan pada saat di-compile (runtime).
- `final` sering digunakan untuk variabel yang nilainya baru diketahui pada saat runtime.

**`Const` vs `Final`**
- `const` harus diinisialisasi dengan nilai yang sudah diketahui pada waktu kompilasi, sedangkan `final` dapat diinisialisasi dengan nilai yang diketahui pada waktu runtime.
- `const` digunakan untuk nilai yang benar-benar konstan dan tidak akan pernah berubah, sedangkan `final` digunakan untuk nilai yang hanya diinisialisasi sekali dan tidak dapat diubah setelah itu.

# Tugas 8: Flutter Navigation, Layouts, Forms, and Input Elements

## Jawaban dari Pertanyaan Tugas 8

### 1. Kegunaan `const` di Flutter
Digunakan untuk mendeklarasikan nilai yang bersifat konstan dan tidak akan berubah. Jadi, saat mengcompile, nilainya sudah diketahui.

#### Keuntungan menggunakan `const` pada Flutter
- Dalam penggunaan widget, jika dideklarasikan dengan `const`, maka hanya dibuat sekali saja, tidak perlu terus dibuat ulang. Cara ini mengurangi beban kerja pada proses rendering dari Flutter-nya.
- Menghindari bug atau error karena nilai yang dideklarasikan berpotensi berubah selama kode dijalankan. Jika sedari awal saya ingin nilainya tetap konsisten, `const` menjaga nilainya tetap konsisten di manapun digunakan. 

#### Kapan sebaiknya digunakan
Dalam `glowify`, saya menggunakannya pada `Stateless Widget`. Karena selama aplikasi berjalan, nilainya tidak berubah. Misal, dipakai di widget yang hanya menampilkan teks atau ikon statis.

#### Kapan sebaiknya tidak digunakan
- Tentu dalam kebalikannya, `Stateful Widget`. Seperti pertanyaan pada Tugas 7, `Stateful Widget` akan berubah (dinamis) selama aplikasi dijalankan, karena memiliki state. 
- `const` perlu telah diketahui nilainya saat kita ingin compile. Jika tidak, atau kita hanya bisa tau nilainya dalam runtime, gunakan `final` atau variabel biasa, bukan `const`

### 2. Penggunaan `Column` dan `Row` pada Flutter

#### Column
- Widget yang digunakan untuk menata anak-anaknya secara vertikal. Setiap widget anak akan ditempatkan di bawah widget anak yang sebelumnya.
- Pada `MenuScreen`, `Column` digunakan untuk menata widget secara vertikal, seperti teks "Welcome to Glowify!" dan `GridView` yang menampilkan item-item menu.

```dart
Column(
  crossAxisAlignment: CrossAxisAlignment.center,
  children: [
    const Padding(
      padding: EdgeInsets.only(top: 16.0),
      child: Text(
        'Welcome to Glowify!',
        style: TextStyle(
          fontWeight: FontWeight.bold,
          fontSize: 18.0,
        ),
      ),
    ),
    GridView.count(
      primary: true,
      padding: const EdgeInsets.all(20),
      crossAxisSpacing: 10,
      mainAxisSpacing: 10,
      crossAxisCount: 3,
      shrinkWrap: true,
      children: items.map((ItemHomepage item) {
        return ItemCard(item);
      }).toList(),
    ),
  ],
)
```

#### Row
- Widget yang digunakan untuk menata anak-anaknya secara horizontal. Setiap widget anak akan ditempatkan di sebelah kanan widget anak sebelumnya.
- Pada halaman `MenuScreen`, `Row` digunakan untuk menata `InfoCard` secara horizontal. Jadinya, informasi pengguna ditampilkan dalam satu baris.

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    InfoCard(title: 'User Id', content: userId),
    InfoCard(title: 'Username', content: userName),
    InfoCard(title: 'Skintype', content: skinType),
  ],
)
```
#### Perbandingan
- Arah. `Column` secara vertikal, sehingga bertumpuk dari atas ke bawah. `Row` horizontal, sehingga widget berdampingan dari kiri ke kanan.

### 3. Elemen input yang digunakan pada halaman form

Pada halaman form `ProductEntryFormPage` di `glowify`, elemen input yang digunakan:

1. `TextFormField`, untuk input teks biasa (nama produk dan deskripsi produk).
   - Nama produk menggunakan `TextFormField` dengan validasi --> nama produk tidak kosong, memiliki panjang minimal 3 karakter, dan maksimal 50 karakter.
   - Deskripsi menggunakan `TextFormField` dengan validasi --> deskripsi tidak kosong, memiliki panjang minimal 5 karakter, dan maksimal 500 karakter.

2. `TextFormField`, untuk input angka (jumlah produk.)
   - Jumlah enggunakan `TextFormField` dengan tipe input `number` dan validasi --> memastikan jumlah tidak kosong, berupa angka, tidak negatif, dan tidak lebih dari 10000.

3. `ElevatedButton`, untuk menyimpan data yang telah diisi pada form.

#### Elemen input lain yang tidak digunakan

1. `Checkbox`, untuk input boolean, misal untuk memilih opsi ya/tidak.
2. `Radio`, untuk memilih satu dari beberapa opsi.
3. `Switch`, untuk input boolean dengan tampilan switch.
4. `Slider`, untuk input angka dalam rentang tertentu dengan cara menggeser.
5. `DropdownButton`, untuk memilih satu dari beberapa opsi dalam bentuk dropdown.
6. `DatePicker`, untuk input tanggal.
7. `TimePicker`, untuk input waktu.

### 4. Pengaturan Tema
Konsistensi tema app Flutter bisa diatur dengan properti `theme` pada `MaterialApp`. Nanti tema akan diterapkan secara global ke seluruh app, semua widget juga akan mengikuti gaya yang telah diset.

Pada `glowify`, tema diatur di dalam `main.dart` 
- Warna utama dengan `primarySwatch`, yaitu `Colors.brown`.
- Warna sekunder dengan `copyWith(secondary: Colors.brown[200]), supaya tidak monoton dan flat sama semua.
- Properti `useMaterial3` diset `true`.
```dart
import 'package:flutter/material.dart';
import 'package:glowify/screens/menu.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Glowify',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSwatch(
          primarySwatch: Colors.brown,
        ).copyWith(secondary: Colors.brown[200]),
        useMaterial3: true,
      ),
      home: MenuScreen(),
    );
  }
}
```

### 3. Handle navigasi dengan app banyak halaman

Di `glowify`, navigasi antar halaman dihandle dengan `Navigator` dan `MaterialPageRoute`
- `navigator.push` akan navigate ke halaman baru, lalu menambah halaman tersebut ke stack navigasi.
- `navigator.pushReplacement` menavigasi ke halaman baru, lalu replace halaman saat ini di stack navigasi.


1. Untuk navigasi dari `MenuScreen` ke `ProductEntryFormPage` ketika user tekan tombol `Tambah Produk`.
```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => const ProductEntryFormPage(),
  ),
);
```
2. Untuk navigasi dari `LeftDrawer` ke halaman page item menu yang sesuai dipilih user.
```dart
ListTile(
  leading: const Icon(Icons.home_outlined),
  title: const Text('Halaman Utama'),
  onTap: () {
    Navigator.pushReplacement(
      context,
      MaterialPageRoute(
        builder: (context) => MenuScreen(),
      ),
    );
  },
),
ListTile(
  leading: const Icon(Icons.shopping_bag),
  title: const Text('Tambah Produk'),
  onTap: () {
    Navigator.pushReplacement(
      context,
      MaterialPageRoute(
        builder: (context) => const ProductEntryFormPage(),
      ),
    );
  },
),
```

# Tugas 9: Integrasi Layanan Web Django dengan Aplikasi Flutter

## Implementasi Checklist

### 1. Implementasi Sistem Autentikasi
- Membuat halaman login di `login.dart` dengan fitur
  ```dart
  class LoginPage extends StatefulWidget {
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        body: Card(
          child: Column(
            children: [
              TextFormField(
                controller: _usernameController,
                decoration: InputDecoration(labelText: "Username"),
              ),
              TextFormField(
                controller: _passwordController,
                obscureText: true,
                decoration: InputDecoration(labelText: "Password"),
              ),
              ElevatedButton(
                onPressed: () async {
                  final response = await request.login(
                    "http://127.0.0.1:8000/auth/login/",
                    {'username': username, 'password': password}
                  );
                },
                child: Text("Login"),
              ),
            ],
          ),
        ),
      );
    }
  }
  ```

- Membuat halaman register di `register.dart` untuk membuat akun baru
- Menghubungkan dengan endpoint Django `/auth/login/` dan `/auth/register/`
- Menggunakan `CookieRequest` untuk manajemen session

### 2. Pembuatan Model Kustom
- Membuat model `ProductEntry` yang sesuai dengan model Django
  ```dart
  class ProductEntry {
    String? model;
    String pk;
    Fields fields;

    ProductEntry({
      this.model,
      required this.pk,
      required this.fields,
    });
  }
  ```

### 3. Halaman Daftar Produk
-  `list_productentry.dart` untuk menampilkan produk
- Menggunakan `FutureBuilder` untuk fetch data asinkronus
  ```dart
  Future<List<ProductEntry>> fetchProduct(request) async {
    final response = await request.get('http://127.0.0.1:8000/json/');
    return data.map((item) => ProductEntry.fromJson(item)).toList();
  }
  ```
- Menampilkan nama, harga, dan deskripsi dalam bentuk card
- Filter otomatis berdasarkan user yang login (dihandle oleh Django backend)

### 4. Halaman Detail Produk
- Membuat `view_productentry.dart` dengan tampilan
  - Gambar produk full width
  - Nama produk (ukuran besar)
  - Harga dalam format Rupiah
  - Volume dengan icon
  - Deskripsi lengkap
- Navigasi dari list ke detail 
  ```dart
  Navigator.push(
    context,
    MaterialPageRoute(
      builder: (context) => ViewProductEntryPage(product: product),
    ),
  );
  ```
- Tombol back di AppBar untuk kembali ke list

### 5. Implementasi Fitur Logout
- Menambahkan tombol logout di menu utama
- Integrasi dengan endpoint `/auth/logout/`
  ```dart
  final response = await request.logout("http://127.0.0.1:8000/auth/logout/");
  if (response['status']) {
    Navigator.pushReplacement(
      context,
      MaterialPageRoute(builder: (context) => const LoginPage()),
    );
  }
  ```

### Filter Produk Berdasarkan User
- Filter produk sudah terimplementasi secara otomatis karena:
  1. Saat create product, setiap produk diasosiasikan dengan `request.user`
  2. Endpoint JSON di Django memfilter produk berdasarkan user yang login
  3. Flutter app hanya menampilkan produk yang dikembalikan oleh endpoint
  4. Setiap user hanya bisa melihat produk yang mereka buat sendiri

## Jawaban dari Pertanyaan Tugas 9

### 1. Perlunya membuat model untuk data JSON
Dibutuhkan model dalam `glowify` karena:
- Flutter jadi bisa memahami struktur data produk (nama, harga, deskripsi, dll)
- Mengubah JSON dari Django menjadi objek Dart 
- Memberikan type safety, sehingga tidak ada data yang salah format
- Permudah akses data (contoh: `product.fields.name` jadi lebih mudah dibaca)

Tanpa model, harus manual parsing JSON dan rawan error karena:
- Tidak ada validasi tipe data, rawan error
- Akses data lebih rumit (`jsonData['fields']['name']`)

### 2. Fungsi Library http dalam Glowify
Library http digunakan untuk
- Komunikasi dengan Django backend
- Send request GET untuk mengambil data produk
- Send request POST saat login/register
- Handle response dari server
- Atur headers dan cookies untuk autentikasi

### 3. Pentingnya CookieRequest
- Menyimpan session user yang login
- Digunakan di semua halaman yang perlu autentikasi
- User tetap login saat pindah halaman
- Handle cookies Django untuk security

Dibagikan ke semua komponen agar
- Tidak perlu login ulang di setiap halaman
- State login konsisten di seluruh aplikasi
- Tidak perlu buat instance baru

### 4. Mekanisme Pengiriman Data di Glowify
1. User input data produk di form
2. Data dikumpulkan saat tombol `Save` ditekan
3. Flutter mengubah data jadi JSON
4. Dikirim ke Django via POST request
5. Django memproses dan simpan ke database
6. Flutter fetch data terbaru
7. Data ditampilkan dalam bentuk card

### 5. Mekanisme Autentikasi
Login
1. User input username & password
2. Data dikirim ke endpoint Django `/auth/login/`
3. Django validasi kredensial
4. Jika valid, buat session & kirim cookie
5. Flutter simpan cookie di CookieRequest
6. Redirect ke menu utama

Register
1. User isi form registrasi
2. Data dikirim ke `/auth/register/`
3. Django validasi & buat user baru
4. Redirect ke login page

Logout
1. User tekan tombol logout
2. Request ke `/auth/logout/`
3. Django hapus session
4. Flutter hapus cookie
5. Kembali ke login page


