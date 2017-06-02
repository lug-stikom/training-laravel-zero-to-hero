# Pertemuan 03

## A. Migration

Migration adalah cara Laravel untuk membuat semua orang (end-user maupun anggota tim) mendapatkan struktur database yang sama.  

Migration ditulis dalam bahasa PHP dengan menggunakan syntax/method dari Laravel.  

### Contoh menulis migration

Ambil contoh kita akan membuat tabel `employees`. Tabel ini akan berisi kolom-kolom sebagai berikut:  
- `id` : primary key, auto-increment
- `nik`: string, unique
- `nama`: string
- `email`: string, unique
- `tanggal_lahir`: date
- `gaji_pokok`: double

Maka pembuatan migration-nya adalah sebagai berikut:
1. Buka `terminal` / `cmd`
2. Masuk ke folder aplikasi `online-store`
3. Jalankan: `php artisan make:migration create_employees_table --create=employees`
4. Akan muncul file baru dengan nama sama seperti di atas dalam `/database/migrations`
5. Buka file baru tersebut (`yyyy_mm_dd_hhiiss_create_employees_table.php`)
6. Di dalam method `up()`, isikan kode berikut:
```php
Schema::create('employees', function (Blueprint $table) {
    $table->increments('id');
    $table->string('nik')->unique();
    $table->string('nama');
    $table->string('email')->unique();
    $table->date('tanggal_lahir');
    $table->double('gaji_pokok');
    $table->timestamps();
});
```
