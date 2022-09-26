# Membuat Layanan Mikroservice Sederhana
## Download Maven Projek Menggunakan Spring
**Langkah 1:**<br>
Buat proyek Maven menggunakan Spring Initializr https://start.spring.io/<br>

**Langkah 2:**<br>
Pilih Spring Boot versi **2.2.0** M6 atau versi yang lebih tinggi. Jangan memilih versi snapshot. Disini saya mengunakan versi <b>2.6.11</b>.<br>

**Langkah 3:**<br>
Berikan nama <b>Grup</b> . Dalam kasus saya <b>com.iqbal</b><br>

<b>Langkah 4:</b><br>
Berikan <b>Artifact id</b>. Disini saya membuat <b>latihan2-service</b><br>

<b>Langkah 5:</b><br>
Pilih Java sesuai dengan yang dipakai pada komputer.<br>

<b>Langkah 6:</b><br>
Tambahkan dependensi berikut: <b>Spring Web</b>.<br>
![limit4](https://user-images.githubusercontent.com/113502513/192170943-c5dfcfb1-d1a8-415f-94bf-7d2256850e80.JPG)<br>

<b>Langkah 7:</b><br>
Klik tombol Generate the project . File zip akan diunduh, ekstrak ke dalam hard disk.<br>

<b>Langkah 8:</b><br>
Open projek yang telah di ekstrak tadi di <b>Acapche NetBeans</b><br>

<b>Langkah 9:</b><br>
Klik kanan di projek <b>latihan2-service</b> pilih <i>Build with Dependencies</i>. Tunggu proses Build.<br>
## Projek Spring Boot Baru
<b>Langkah 1: Mulai proyek Spring Boot Baru</b><br>
Menggunakan https://start.spring.io untuk membuat proyek "web". Dalam dialog "Dependencies" cari dan tambahkan ketergantungan "web" seperti yang ditunjukkan pada tangkapan layar. Tekan tombol "Generate", unduh zip, dan buka kemasannya ke dalam folder di komputer Anda.<br>
![server](https://user-images.githubusercontent.com/113502513/192148872-4b7f400e-42b4-4853-b212-d0a2cd541b5a.JPG)<br>
Proyek yang dibuat oleh https://start.spring.io berisi Spring Boot,framework yang membuat Spring siap bekerja di dalam aplikasi Anda, tetapi tanpa banyak kode atau konfigurasi yang diperlukan. Spring Boot adalah cara tercepat dan terpopuler untuk memulai proyek Spring.<br>

<b>Langkah 2: Tambahkan kode Anda</b><br>
Buka proyek di IDE Anda dan cari file <b>Latihan2ServiceApplication.java</b> di <b>Source Packages</b> pada folder <b>com.iqbal.latihan2.service</b>. Sekarang ubah isi file dengan menambahkan metode tambahan dan anotasi yang ditunjukkan pada kode di bawah ini. Anda dapat menyalin dan menempelkan kode atau cukup mengetiknya.<br>
```javascript
package com.iqbal.latihan2.service;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class LatihanServiceApplication {

    public static void main(String[] args) {
        SpringApplication.run(LatihanServiceApplication.class, args);
    }

    @GetMapping("/hello")
    public String hello(@RequestParam(value = "name", defaultValue = "Latihan 2") String name) {
        return String.format("Hello %s!", name);
    }

}
```
Metode hello() yang di tambahkan dirancang untuk mengambil parameter String yang disebut name, dan kemudian menggabungkan parameter ini dengan kata "Hello"dalam kode. Ini berarti bahwa jika Anda menyetel nama Anda ke “Latihan 2” dalam permintaan, responsnya adalah “Hello Latihan 2”.<br>
Anotasi @RestController memberi tahu Spring bahwa kode ini menjelaskan titik akhir yang harus tersedia melalui web. @GetMapping(“/hello”) memberi tahu Spring untuk menggunakan method hello() untuk menjawab permintaan yang dikirim ke alamat http://localhost:8011/hello. Akhirnya, @RequestParamSpring memberi tahu Spring untuk mengharapkan nilai name dalam permintaan, tetapi jika tidak ada, itu akan menggunakan kata "Dunia" secara default.<br>

<b>Langkah 3: Cobalah !</b><br>
Run file <b>LatihanServiceApplication.java</b>. Beberapa baris terakhir di sini memberi tahu kami bahwa Spring telah dimulai. Server Apache Tomcat tertanam pada Spring Boot bertindak sebagai server web dan mendengarkan permintaan pada localhost port 8011. Buka browser Anda dan di bilah alamat di bagian atas enter http://localhost:8011/halo. Anda harus mendapatkan respons ramah yang bagus seperti ini:<br>
![limit5](https://user-images.githubusercontent.com/113502513/192171264-672dfa06-c88a-4893-adb2-2fbc4d41b449.JPG)

