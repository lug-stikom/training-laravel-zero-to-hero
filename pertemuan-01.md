# Pertemuan 01

## A. Pre-requisites

Berikut adalah hal-hal yang sudah **harus** Anda miliki / instal:

1. Web Server  
    XAMPP, MAMP, LAMP, Valet, Homestead, atau yang lainnya
2. Composer
    Cara instal: https://getcomposer.org
3. Code Editor
    Rekomnedasi: Atom, Sublime, PhpStorm
    Tidak direkomendasikan: Notepad++
4. Laravel Installer
    4.1 Buka `terminal` / `cmd`
    4.2 Jalankan `composer global require "laravel/installer"` <kbd>enter</kbd>
5. Tunggu sampai download selesai  
6. Tes dengan perintah `laravel` <kbd>enter</kbd>

## B. Install Laravel
1. Buka `terminal` / `cmd`
2. Masuk ke directory web root
    Biasanya: htdocs, /var/www, ~/code
3. Jalankan perintah `laravel new online-store` <kbd>enter</kbd>
4. Pastikan dalam directory web root terdapat folder **online-store**
5. Melalui `terminal` / `cmd`, masuklah ke dalam folder **online-store** ini
6. Jalankan perintah `php artisan serve` <kbd>enter</kbd>
7. Jika sukses, buka web browser, arahkan ke alamt: `localhost:8000` atau `127.0.0.1:8000`
8. Selamat! Laravel berhasil terinstal dan berjalan di local Anda

## C. Laravel Auth

Auth singkatan dari Authentication dan Authorization.  
Authentication adalah "apakah benar bahwa user ini adalah user A?"  
Authorization adalah "bolehkah user A melakukan hal ini?"

Secara default Laravel sudah membuat scaffolding untuk Auth ini, yang terdiri dari:
1. Pembuatan tabel `users`
2. Pembuatan tabel `password_reset`
2. Tampilan dan Proses: Register, Login, Logout, Forgot Password

### C.1 Konfigurasi Database (MySQL)

1. Buka code editor
2. Masuk ke folder `online-store`
3. Buka file `.env`
4. Konfigurasi:
```
DB_DATABASE=onlinestoredb
DB_USERNAME=isi dengan username mysql Anda
DB_PASSWORD=isi dengan password mysql Anda
```        
5. Buka phpmyadmin
6. Create database baru dengan nama: `onlinestoredb`
7. Kembali ke `terminal` / `cmd`
8. Jalankan perintah `php artisan migrate`
9. Jika sukses (tidak ada), akan muncul 3 tabel dalam database onlinestoredb
    Tabel: `users`, `password_reset`, dan `migrations`

### C.2 Muncul Error, atau Hanya Muncul 2 Tabel ?

Bagi yang muncul error dan hanya muncul 2 tabel, lakukan ini:

1. Buka file `app/Providers/AppServiceProvider.php`
2. Di line 4 tambahkan kode `use Illuminate\Support\Facades\Schema;`
3. Di dalam fungsi `boot()` isi dengan kode: `Schema::defaultStringLength(191);`
4. Jalankan perintah `php artisan migrate:refresh`
5. Pastikan sekarang ada 3 tabel dalam database onlinestoredb


### C.3 Memigrasi tabel `users`

1. Jalankan server laravel: `php artisan serve`
2. Jalankan `php artisan make:auth`
3. Jika sukses (tidak ada error), kembali ke browser, refresh
4. Melalui menu baru yang muncul di atas kanan, kini Anda sudah bisa melakukan proses auth: Register, Login, dan Forgot Password
