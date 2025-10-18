# Tugaspertemuan-9
1. Pengertian

JasperReport merupakan salah satu library open-source berbasis Java yang digunakan untuk membuat dan menampilkan laporan (report) dari berbagai sumber data. JasperReport mampu menghasilkan laporan dalam berbagai format seperti PDF, HTML, Excel, dan Word. Laporan ini biasanya diambil dari data pada database dan ditampilkan secara otomatis melalui antarmuka aplikasi Java.

2. Kegunaan

JasperReport berfungsi untuk membantu pengembang aplikasi dalam membuat laporan hasil pengolahan data yang rapi dan dinamis. Dengan JasperReport, laporan dapat dibuat secara otomatis dari hasil query database tanpa perlu menulis format laporan secara manual. Alat ini sangat berguna dalam pembuatan sistem informasi yang membutuhkan laporan seperti nota transaksi, daftar barang, data karyawan, dan sebagainya.

A. Langkah Instalasi JasperReport di NetBeans

Pastikan NetBeans dan JDK sudah terinstal dengan versi yang sesuai.
Unduh JasperReport library (misalnya versi 6.0.0) serta iReport plugin.
Buka NetBeans → Tools → Plugins → Downloaded, lalu tambahkan plugin iReport sesuai versi NetBeans.
Tambahkan library berikut ke project Java kamu:

jasperreports-x.x.x.jar (library utama JasperReport)

   - jasperreports-x.x.x.jar (library utama)
   - commons-beanutils.jar
   - commons-collections.jar
   - commons-digester.jar
   - commons-logging.jar


Klik kanan pada project → Properties → Libraries → Add JAR/Folder, lalu tambahkan semua library di atas.
Klik OK, lalu Clean and Build Project agar semua dependensi dikenali.

B. Langkah Penggunaan / Pengaplikasian JasperReport

Langkah ini menjelaskan bagaimana cara membuat laporan dari data yang sudah ada di database hingga menampilkannya di GUI.

a. Membuat Laporan di iReport

Buka aplikasi iReport Designer.
Pilih File → New Report → Report Wizard.
Pilih Database JDBC Connection dan hubungkan ke database yang ingin digunakan.
Pada bagian SQL Query, tuliskan query yang menampilkan data yang akan dilaporkan, contohnya:

SELECT * FROM barang;


Desain tampilan laporan sesuai kebutuhan (misalnya tambahkan judul “Laporan Data Barang” dan tabel data).
Simpan file hasil desain dengan ekstensi .jrxml (misalnya reportBarang.jrxml).

b. Mengintegrasikan ke Aplikasi Java

Tempatkan file reportBarang.jrxml di folder src/report/ pada project.
Kompilasi laporan ke format .jasper dengan kode berikut:

JasperReport jasperReport = JasperCompileManager.compileReport("src/report/reportBarang.jrxml");


# Buat koneksi ke database:

Connection conn = DriverManager.getConnection(
    "jdbc:postgresql://localhost:5432/db_penjualan",
    "postgres", "password"
);


# Isi data ke laporan dan tampilkan:

JasperPrint print = JasperFillManager.fillReport(jasperReport, null, conn);
JasperViewer.viewReport(print, false);



Klik kanan pada project → Properties → Libraries → Add JAR/Folder, lalu tambahkan semua library di atas.

Klik OK, lalu Clean and Build Project agar semua dependensi dikenali.
