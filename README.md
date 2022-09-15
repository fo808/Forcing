# Forcing

![CI](https://github.com/fo808/forcing/workflows/CI/badge.svg)
[![Docker](https://img.shields.io/badge/Docker%20Hub-fo808%2Fforcing-blue)](https://hub.docker.com/r/fo808/forcing )

Tindakan Github dengan alat Kubernetes:
kubectl, kustomisasi, helm, kubeval, conftest, kubeconform, jq, yq, go.
Lihat [rilis](https://github.com/fo808/forcing/releases)
halaman untuk daftar alat dan versi yang tersedia.

Contoh Alur Kerja GitHub:

```yaml
nama: CI

pada: [push, pull_request]

pekerjaan:
  uji-aksi:
    berjalan-on: ubuntu-terbaru
    Langkah:
      - menggunakan: tindakan/checkout@v2
      - nama: Jalankan alat Kubernetes
        menggunakan: fo808/forcing@v1
        dengan:
          kubectl: 1.23.0
          sesuaikan: 4.4.1
          kemudi: 2.17.0
          helmv3: 3.7.2
          kubeseal: 0.16.0
          kubeval: v0.16.1
          kontes: 0.28.3
          kubeconform: 0.4.12
          perintah: |
            echo "Jalankan kontes"
            sesuaikan uji build/kustomisasi | conftest tes -p tes/kebijakan -
            echo "Jalankan kubeval"
            helmv3 template ./charts/test | kubeval --ketat
```

Gambar kontainer:

* `ghcr.io/fo808/forcing`
* `docker.io/fo808/forcing`
