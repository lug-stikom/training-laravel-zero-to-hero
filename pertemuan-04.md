# Pertemuan 04

## A. Seeder

Seeder adalah cara Laravel untuk mengisi data awal aplikasi kita.  
Data awal ini bisa berupa: data default yang harus ada, biasanya untuk config; atau data master.

## A.1 Membuat File Seeder

1. Buka `terminal` / `cmd`
2. Masuk ke `online-store`
3. Jalankan: `php artisan make:seeder EmployeesTableSeeder`
4. Jika sukses, akan ada file `EmployeesTableSeeder.php` di dalam `/database/seeds`

## A.2 Mengisi Seeder

1. Buka file `EmployeesTableSeeder.php`
2. Di line 3 tambahkan: `use Carbon\Carbon;`
3. Di dalam fungsi `run()` isikan kode berikut:
```php
DB::table('employees')->insert([
    'nik' => 'N-0001',
    'nama' => 'Kukuh',
    'email' => 'rkukuh@gmail.com',
    'tanggal_lahir' => Carbon::now()->setDate(1987, 1, 31),
    'gaji_pokok' => 10000000,
    'created_at' => new DateTime(),
    'updated_at' => new DateTime(),
]);
```
4. Buka file `DatabaseSeeder.php`
5. Di dalam fungsi `run()` tambahkan: `$this->call(EmployeesTableSeeder::class);`

## A.3 Menjalankan Seeder

1. Buka `terminal` / `cmd`
2. Jalankan: `php artisan migrate:refresh --seed`
3. Buka `PhpMyAdmin`, lalu buka database online store
4. Lihat isi tabel `employees`, seharusnya terisi 1 data di sana

## Tips

Anda bisa membuat multi insert dengan cara seperti ini:

```php
DB::table('employees')->insert([
    [
        'nik' => 'N-0002',
        'nama' => 'Naruto',
        'email' => 'naruto@naruto.com',
        'tanggal_lahir' => Carbon::now()->setDate(1990, 2, 20),
        'gaji_pokok' => 5000000,
        'created_at' => new DateTime(),
        'updated_at' => new DateTime(),
    ],
    [
        'nik' => 'N-0003',
        'nama' => 'Goku',
        'email' => 'goku@goku.com',
        'tanggal_lahir' => Carbon::now()->setDate(1995, 3, 10),
        'gaji_pokok' => 75000000,
        'created_at' => new DateTime(),
        'updated_at' => new DateTime(),
    ]
]);
```

## B. Seeder Untuk Onlie Store

Dengan menggunakan pengetahuan di atas, buatlah seeder untuk aplikasi online store ini dengan ketentuan sebagai berikut:

Tabel __statuses__  

| Kolom          | Value                       |
| :------------- | :-------------------------- |
| name           | `New`, `Paid`, `Canceled`   |

Tabel __gateways__  

| Kolom          | Value                                                         |
| :------------- | :------------------------------------------------------------ |
| name           | `Bank Transfer`, `Cash On Delivery`, `Credit Card`, `Paypal`  |

Tabel __categories__  

*Isinya bebas. Tentukan sendiri kategori dari produk yang ingin Anda jual nanti. Isi minimal 3 data.*

Tabel __products__  

⚠️ Isinya bebas. Tentukan sendiri data produk yang ingin Anda jual nanti. Isi minimal 5 data. ⚠️

Tabel __category_product__  

⚠️ Tautkan data produk di atas, dengan kategorinya di sini ⚠️
