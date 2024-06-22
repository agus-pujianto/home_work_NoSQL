##set up mongodb

1. Instal MongoDB Database Tools

Untuk Ubuntu (atau distribusi berbasis Debian):


Salin kode :
wget https://fastdl.mongodb.org/tools/db/mongodb-database-tools-ubuntu2004-x86_64-100.5.2.deb

Salin kode :
sudo dpkg -i mongodb-database-tools-ubuntu2004-x86_64-100.5.2.deb
Ganti URL dengan versi terbaru dari MongoDB Database Tools jika diperlukan.

2. Periksa PATH
Pastikan bahwa direktori yang berisi mongoimport ada di PATH Anda. Jika Anda menginstal MongoDB Database Tools ke lokasi default, Anda mungkin perlu menambahkan path ke ~/.bashrc atau ~/.profile.

Tambahkan baris berikut ke file ~/.bashrc atau ~/.profile:

sh
Salin kode
export PATH=$PATH:/usr/local/bin/mongo-tools/bin
Kemudian, muat ulang file:

sh
Salin kode
source ~/.bashrc

3. Verifikasi Instalasi
Cek apakah mongoimport dapat ditemukan setelah instalasi:

sh
Salin kode
mongoimport --version

4. Jalankan mongoimport
Setelah mongoimport berhasil diinstal dan tersedia di PATH, jalankan kembali perintah:

sh
Salin kode
mongoimport --db library --collection books --file ~/books.json --jsonArray
Contoh Seluruh Proses:
Unduh dan Instal MongoDB Database Tools:

sh
Salin kode
wget https://fastdl.mongodb.org/tools/db/mongodb-database-tools-ubuntu2004-x86_64-100.5.2.deb
sudo dpkg -i mongodb-database-tools-ubuntu2004-x86_64-100.5.2.deb
Tambahkan PATH (jika diperlukan):

sh
Salin kode
echo 'export PATH=$PATH:/usr/local/bin/mongo-tools/bin' >> ~/.bashrc
source ~/.bashrc
Verifikasi mongoimport:

sh
Salin kode
mongoimport --version
Jalankan mongoimport:

sh
Salin kode
mongoimport --db library --collection books --file ~/books.json --jsonArray


##running mongosh

Langkah 1: Masuk ke mongosh:

sh
Salin kode
mongosh


Langkah 2: Pilih database dan jalankan query untuk tugas 1:

sh
Salin kode
use library
db.books.find({ 
    author: "Author 5", 
    borrowed: true, 
    returned: false 
}).pretty()


Langkah 3: Jalankan query untuk tugas 2:

sh
Salin kode
db.books.find({ 
    publishedYear: { $lt: 1980 }, 
    copiesAvailable: { $gt: 5 } 
}).pretty()


Langkah 4: Jalankan query untuk tugas 3:

sh
Salin kode
db.books.find({ 
    genre: "Fantasy" 
}).sort({ publishedYear: -1 }).limit(5).pretty()
Langkah 5: Jalankan query untuk tugas 4:

sh
Salin kode
db.books.aggregate([
    { 
        $group: { 
            _id: "$genre", 
            totalBooks: { $sum: 1 } 
        } 
    }
])


Langkah 6: Jalankan query untuk tugas 5:

sh
Salin kode
db.books.find({ 
    borrowed: false 
}).pretty()
