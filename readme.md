## 🧩 Marzban + Nginx

**Marzban + Nginx Reverse Proxy** in Docker 🐳

Repositori ini berisi setup lengkap menggunakan **Docker Compose** untuk menjalankan [Marzban](https://github.com/Gozargah/Marzban) (panel manajemen Xray) dengan dukungan **reverse proxy Nginx** dan  **sertifikat SSL** .

### ✨ Fitur

* 🔐 Reverse proxy Nginx untuk mengatur trafik VMess, VLESS, Trojan, Shadowsocks
* 📊 Panel Marzban yang bisa diakses melalui port publik (`8899`)
* 🌐 Akses protokol Xray hanya lewat reverse proxy (tidak expose port mentah)
* 📦 Konfigurasi persistensi agar data tidak hilang meski `docker compose down`
* 🔧 Kompatibel untuk server tanpa IP publik, bisa digabungkan dengan Cloudflare Tunnel (opsional)

---

### 📁 Struktur Folder

```
.
├── docker-compose.yml         # File utama Docker Compose
├── nginx.conf                 # Konfigurasi utama Nginx
├── xray.conf                  # Virtual host reverse proxy untuk semua protokol
├── marzban/      
│   └── xray_config.json       # Konfigurasi Xray (VMess, VLESS, dll)
```

---

### 🚀 Cara Penggunaan

```bash
git clone https://github.com/kamu/marzban-nginx.git
cd marzban-nginx
docker compose up -d
```

* Panel Marzban: `http://IP-SERVER:8899`
* Protokol Xray: Lewat path reverse proxy `/vmess`, `/vless`, dll.

---

## ☁️ Akses Marzban Aman & Mudah via Cloudflare Tunnel

Ingin mengakses **panel Marzban** tanpa membuka port dan tetap aman di balik Cloudflare? Gunakan **Cloudflare Tunnel** dengan setting path seperti ini:

### 🌐 Contoh:

![1750771085975](image/readme/1750771085975.png)
Akses Marzban di:

```
https://YOUR_DOMAIN/dashboard
```

### ⚙️ Settings Marzban Panel:

| VMESS                                          | VLESS                                          | TROJAN                                         |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| ![1750772197165](image/readme/1750772197165.png) | ![1750772223378](image/readme/1750772223378.png) | ![1750772237817](image/readme/1750772237817.png) |

### ✨ Kelebihan:

* 🔒  **Aman** : Tidak perlu expose port 80/443 secara langsung
* ☁️  **Stabil** : Lewat jaringan Cloudflare, cocok untuk server tanpa IP publik
* 🎯  **Custom Path** : Panel Marzban bisa ditempatkan di subpath seperti `/dashboard`
* 💡  **Hemat biaya** : Tanpa perlu beli IP statik atau VPS premium

### 🙏 Special Thanks

Project ini terinspirasi dan banyak terbantu dari:

🔗 **[Agunxzzz/MarXray](https://github.com/Agunxzzz/MarXray/tree/main)**

Repositori luar biasa yang menyediakan konfigurasi lengkap Marzban + Nginx + Xray, sangat membantu dalam membangun integrasi otomatis dan struktur sistem reverse proxy yang stabil.

---

> Terima kasih untuk kontribusi komunitas yang terus memperkuat ekosistem open-source Xray dan Marzban! 💪🚀

---
