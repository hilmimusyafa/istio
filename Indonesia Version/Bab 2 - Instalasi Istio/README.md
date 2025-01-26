## Chapter 2 : Instalasi Istio

### 2.1 Persyaratan Sistem

Cluster Kubernetes 1.10+ dengan kontrol akses berbasis peran (RBAC) diaktifkan. Direkomendasikan cluster dengan setidaknya 8GB memori yang tersedia dan 4vCPU.

### 2.2 Instalasi Istio di Kubernetes

1. Memastikan ada Cluster yang aktif

```bash
$ kubectl cluster-info
```

2. Download Istio

Download rilis baru untuk Istio :

```bash
$ curl -L https://istio.io/downloadIstio | sh -
$ cd istio-<version>
$ export PATH=$PWD/bin:$PATH
```
> `<version>` pastikan diubah sesuai nomer versi yang di ubah.

2. Verifikasi Koneksi ke Kluster Kubernetes

```bash
$ kubectl cluster-info
```

3. Jalankan Pemeriksaaan Pra-Instalasi 

```bash
$ kubectl cluster-info
```

4. Instal Istio sesuai Instalasi

```bash
$ istioctl install --set profile=<isto profile> -y
```

> `<istio profile>` pastikan diubah sesuai profile istio yang terjadi.

Disini sebagai saran dapat menggunakan profile demo 

```bash
$ istioctl install --set profile=demo -y
```

5. Verifikasi Instalasi Istio Control Panel

```bash
$ kubectl get pods -n istio-system
```

6. Aktifkan Penyuntikan Sidecar Otomatis

```bash
$ kubectl label namespace <namespace-name> istio-injection=enabled
```

> '<namespace-name>' pastikan nama namespace bisa di ubah, dan di sesuaikan. 
