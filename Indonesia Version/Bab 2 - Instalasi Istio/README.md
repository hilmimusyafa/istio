## Chapter 2 : Instalasi Istio

### 2.1 Persyaratan Sistem

Cluster Kubernetes 1.10+ dengan kontrol akses berbasis peran (RBAC) diaktifkan. Direkomendasikan cluster dengan setidaknya 8GB memori yang tersedia dan 4vCPU.

### 2.2 Instalasi Istio di Kubernetes

1. Memastikan ada Cluster yang aktif

```bash
kubectl cluster-info
```

2. Download Istio

Download rilis baru untuk Istio :

```bash
$ curl -L https://istio.io/downloadIstio | sh -
cd istio-<version>
export PATH=$PWD/bin:$PATH
```
> `<version>` pastikan diubah sesuai nomer versi yang di ubah.

2. Verifikasi Koneksi ke Kluster Kubernetes
### 2.3 Memverifikasi Instalasi

### 2.4 Instalasi Control Plane dan Data Plane
