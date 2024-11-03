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

## Jawaban dari Pertanyaan

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

