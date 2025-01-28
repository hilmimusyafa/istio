## Bab 4 : Observabilitas

### 4.1 Perbedaan Antara Pemantauan (monitoring) Aplikasi monolitik dan Observabilitas untuk Arsitektur Microservices

Karena monolitik sudah ada lebih lama, alat untuk memantau dan mendiagnosis masalah sudah lebih berkembang, seperti :

- Profilers: Untuk memantau penggunaan memori, mendeteksi kebocoran memori, dan mengoptimalkan performa.
- CPU Utilization Monitoring: Memantau penggunaan CPU dan metrik vital lainnya seperti thread dan operasi garbage collection.
- Debuggers: Memungkinkan pengembang untuk memeriksa kode, menampilkan stack trace, dan menelusuri hierarki panggilan (call hierarchy) dengan mudah.

Dengan itu tantangan dalam Microservices memiliki perubahan fundamentai, yaitu : 

- Call stack yang terdistribusi : Alih-alih rantai panggilan metode dalam satu proses, sekarang ada serangkaian "hop" jaringan antar layanan.
- Tidak ada proses tunggal : Kita tidak lagi memantau satu aplikasi, tetapi banyak layanan yang harus dipantau secara terpisah dan digabungkan untuk mendapatkan gambaran lengkap sistem.

### 4.2 Monitoring vs. Observability

Observabilitas memiliki ruang lingkup lebih luas dibading monitoring. Tidak sekedar mengecek dan memonitor saja, tetapi membantu Engineer atau Developer memahami perilaku sistem.

Observabilitas dalam layanan mikro tidak hanya mencakup pengumpulan dan visualisasi metrik, tetapi juga agregasi log dan dasbor yang membantu memvisualisasikan jejak terdistribusi.

Setiap aspek observabilitas saling melengkapi. Dasbor yang memperlihatkan metrik dapat mengindikasikan masalah kinerja di suatu tempat dalam sistem. Jejak terdistribusi dapat membantu menemukan hambatan kinerja pada layanan tertentu. 

Terakhir, log layanan dapat menyediakan konteks yang diperlukan untuk menentukan apa yang mungkin menjadi masalah secara spesifik. Metrik, Log, dan Jejak Terdistribusi merupakan fondasi bagi observabilitas sistem terdistribusi modern.

### 4.3 Bagaimana Service Meshes Menyederhanakan dan Meningkatkan Observabilitas

Sebelum service mesh, seperti seperti menangkap, ekspos, dan mempublikasikan meteik adalah beban developer. Juga dengan memonitor kesehatan aplikasi. Hal ini tidak ideal, karena dapat menyebabkan ketidakseragaman data metrik.

Tapi denngan Istio, solusi masalah lintas fungsi seperti observabilitas benar-benar diperhatikan untuk aplikasi itu sendiri. Melalui Envoy Sidecar, istio dapat untuk mengkolekasi metrik dan mengekspos kumpulan serangkaian metrik.

### 4.5 Pecobaan Bagaimana Istio Mengeskpos Metrik Beban Kerja

Perocbaan ini akan menunjukkan cara Istio mengumpulkan dan mengekspos metrik workload menggunakan Envoy sidecar dan Prometheus scrape endpoint.

Oke, mari kita mulai untuk percobaan ini :

1. Install Istio dengan Profil demo 

Hal ini dipastikan istio mendukung hanya untuk testing dengan tingkat traffic rendah.

```bash
$ istioctl install --set profile=demo
```

2. Labelkan Namespace Default dengan Istio Injection (Aktifkan Sidecar Injection)

```bash
$ kubectl label ns default istio-injection=enabled
```

3. 