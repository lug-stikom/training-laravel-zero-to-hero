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
