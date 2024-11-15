---
title: Latar Belakang
feature_text: |
  ## Secure Connection Prometheus Monitoring Web Server and Container
  By Najwan Octavian Gerrard
feature_image: "https://picsum.photos/1300/400?image=989"
excerpt: 
---

Di zaman modern sekarang yang serba otomatis serta kebutuhan akan monitoring atau pengecekan secara berkala, membuat kebutuhan akan tools automation monitoring yang canggih tanpa adanya campur tangan manusia untuk pengambilan data yang di monitoring tersebut, seperti penggunaan CPU, memory, disk atau traffic jaringan, menjadi semakin meningkat. Prometheus adalah salah satu solusi akan hal tersebut, yang menyediakan cara monitoring real time tanpa perlu adanya campur tangan manusia saat mengambil data yang harus di monitoring.
Dan dibutuhkan juga tools untuk visualisasi agar memudahkan dalam melakukan monitoring suatu system, aplikasi maupun server, Grafana disini berperan sebagai tools visualisasi yang sangat popular, karena kemampuannya dalam menangani visualisasi dengan banyak tools lain, sehingga lebih fleksible.
Serta dibutuhkan juga Alerting agar dapat memberikan peringatan dini terkait semisal adanya ganguan pada system yang menyebabkan system down, atau semisal ada terkait ancaman Cyber crime seprti DoS atau DDoS. Alert Manager Prometheus yang mengambil peran ini, yang nantinya akan mengirimkan peringatan apabila terjadi hal – hal tadi, sehingga meminimalisir terjadinya kerusakan pada system atau aplikasi kita. Alert Manager sendiri dapat di integrasikan dengan beberapa tools untuk notifikasi lain seperti Discord, Email atau WebHook Endpoint. Sehingga lebih fleksible dalam penggunaan alerting nya.
## Tools yang Digunakan.
●	Prometheus – 2.48.1
●	Grafana – 11.2.2
●	Alert Manager – 0.26.0
●	Node Exporter – 1.8.2
●	Nginx – 1.10.0
●	Nginx Exporter – 0.11.0
●	Apache2 – 2.4.52
●	Apache Exporter – 1.0.3
●	Docker – 27.3.1
●	cAdvisor 
●	Python – 3.10.12
●	Discord
●	Email

## Topologi
![Branching](./assets/images/topologi.png)
## Alur kerja
![Branching](./assets/images/alur-kerja.png)


## Prometheus
Prometheus adalah salah satu tools monitoring system yang berbasis Cloud yang open source, yang lebih berfokus pada pengelolaan metrics dari suatu aplikasi atau system. Metrics sendiri merupakan data angka yang menunjukan performa atau nilai kinerja suatu aplikasi atau system. 

## Grafana
Grafana merupakan salah satu tools berbasis Web untuk data analitik dan data visualisasi yang interaktif dan real time, dengan kemampuan integrasi ke banyak tools lain, seperti prometheus, Loki Promtail, AWS IoT SiteWise, Apache Cassandra dan banyak lagi. Dengan kemampuannya tersebut membuat Grafana lebih fleksible, tidak hanya untuk satu atau dua tools saja. Grafana sendiri open source.

## Prometheus Alert Manager
Prometheus Alert Manager merupakan suatu tools yang berguna sebagai peringatan atau alerting, yang dimana nantinya, alert manager ini akan menerima data dari Prometheus, misalkan ada layanan atau aplikasi yang Down, yang nantinya akan di teruskan ke alert manager lalu mengirim ke layanan notifikasi seperti Email, Slack, atau Discord dan masih bayak lagi.

## Apache
Apache adalah salah satu software web server gratis dan open source, yang memungkinkan pengguna mengupload website nya ke internet. Apache sendiri sudah hampir menjadi platform website bagi kurang lebih 33% website di dunia, dengan nama resmi “Apache HTTP Server”. Apache pertama kali dirilis pada tahun 1995 dan dikelola oleh “Apache Software Foundation”.

## Nginx
NGINX (Engine-X) adalah salah satu web server yang banyak digunakan untuk membuat suatu website, dan digunakan hampir 34% dari seluruh website yang ada di internet. Nginx memiliki daya tarik karena sifatnya sebagai server HTTP, Reverse proxy, dan load balancer.

## Container
Container adalah sebuah unit yang mengemas code dan semua dependensinya. Sehingga dapat berjalan atau berpindah environment dengan lebih cepat dan efisien. Container tersebut sangat ringan tidak seperti Virtual Machine (VM) yang memerlukan OS untuk setiap VM nya, karena dalam container hanya berisikan source code dan dependensinya saja, jadi memungkinkan menginstal apa yang di perlukan saja.

## Docker
Docker adalah salah satu platform software yang digunakan untuk membuat, mengelola aplikasi yang nantinya dikemas dalam sebuah wadah yang terisolasi yaitu container. Docker nantinya akan mengemas aplikasi berserta dependensi yang diperlukan dalam satu paket yang ringan. Sehingga dapat dijalankan secara konsisten tanpa mengubah konfigurasi.

## Exporter Prometheus
Exporter Prometheus adalah suatu tools yang digunakan untuk mengubah data metrics dari suatu layanan aplikasi atau sistem yang tadinya tidak bisa di baca oleh Prometheus menjadi bisa di baca, bertindak sebagai perantara untuk layanan yang di pantau dengan Prometheus.

## CAdvisor
Cadvisor (Container Advisor) adalah suatu tools yang digunakan untuk memonitoring atau memantau performa / kinerja dari suatu container, serta mengambil data metrics dari Container, seperti penggunaan CPU, Memory, Traffic jaringan atau Disk I/O dari setiap container yang ada.

## SSL (Secure Sockets Layer)
SSL merupakan Protocol keamanan yang digunakan untuk mengenkrip si data seperti informasi pribadi, password, rekening, dan data lain yang bersifat sensitif, saat data dikirim kan ke server, data tersebut akan di enkripsi untuk menjaga keamanan dari data tersebut. SSL sertifikat yaitu sertifikat digital digunakan untuk autentikasi indentitas dari situs web yang memungkinkan koneksi enkripsi yang aman. Dan sering digunakan untuk menjaga keamanan data pengguna yang perlu memverifikasi kepemilikan situs website. 

## Implementasi
1. Konfigurasi SSH ke All Node
   - Buat directory untuk menyimpan CA di dalam directory “/etc/ssl/” agar lebih rapi serta mudah di identifikasi.
     1. Node Monitoring
        ```
        sudo mkdir -p /etc/ssl/prometheus
        sudo mkdir -p /etc/ssl/prometheus/cert/
        sudo mkdir -p /etc/ssl/prometheus/cert/<IP atau Domain dari Prometheus>/
        ```
        ```
        sudo mkdir -p /etc/ssl/node_exporter/
        sudo mkdir -p /etc/ssl/apache_exporter/
        sudo mkdir -p /etc/ssl/nginx_exporter/
        ```
     2. Node Client 1
        ```
        sudo mkdir -p /etc/ssl/node_exporter/
        ```
        ```
        sudo mkdir -p /etc/ssl/apache/
        sudo mkdir -p /etc/ssl/apache/client/
        ```
        ```
        sudo mkdir -p /etc/ssl/nginx
        ```
     4. Node Client 2
   - Buat file IP SAN untuk setiap Server / Node.
     ```
     sudo nano /etc/ssl/IP_SANS.txt

     subjectAltName=IP:<IP dari setiap Server / Node>
     ```
   - Buat Certificate untuk beberapa layanan berikut :
     1. 
3. Konfigurasi SSL Certificate untuk layanan
4. 

Here are a few examples of Alembic out in the wild being used in a variety of ways:

- [bawejakunal.github.io](https://bawejakunal.github.io/)
- [case2111.github.io](https://case2111.github.io/)
- [karateca.org](https://www.karateca.org/)

## Installation

### Quick setup

To give you a running start I've put together some starter kits that you can download, fork or even deploy immediately:

- ⚗️🍨 Vanilla Jekyll starter kit  
  [![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/daviddarnes/alembic-kit){:style="background: none"}
- ⚗️🌲 Forestry starter kit  
  [![Deploy to Forestry](https://assets.forestry.io/import-to-forestry.svg)](https://app.forestry.io/quick-start?repo=daviddarnes/alembic-forestry-kit&engine=jekyll){:style="background: none"}  
  [![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/daviddarnes/alembic-forestry-kit){:style="background: none"}
- ⚗️💠 Netlify CMS starter kit  
  [![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/daviddarnes/alembic-netlifycms-kit&stack=cms){:style="background: none"}

- ⚗️:octocat: GitHub Pages with remote theme kit  
  {% include button.html text="Download kit" link="https://github.com/daviddarnes/alembic-kit/archive/remote-theme.zip" color="#24292e" %}
- ⚗️🚀 Stackbit starter kit  
  [![Create with Stackbit](https://assets.stackbit.com/badge/create-with-stackbit.svg)](https://app.stackbit.com/create?theme=https://github.com/daviddarnes/alembic-stackbit-kit){:style="background: none"}

### As a Jekyll theme

1. Add `gem "alembic-jekyll-theme"` to your `Gemfile` to add the theme as a dependancy
2. Run the command `bundle install` in the root of project to install the theme and its dependancies
3. Add `theme: alembic-jekyll-theme` to your `_config.yml` file to set the site theme
4. Run `bundle exec jekyll serve` to build and serve your site
5. Done! Use the [configuration](#configuration) documentation and the example [`_config.yml`](https://github.com/daviddarnes/alembic/blob/master/_config.yml) file to set things like the navigation, contact form and social sharing buttons

### As a GitHub Pages remote theme

1. Add `gem "jekyll-remote-theme"` to your `Gemfile` to add the theme as a dependancy
2. Run the command `bundle install` in the root of project to install the jekyll remote theme gem as a dependancy
3. Add `jekyll-remote-theme` to the list of `plugins` in your `_config.yml` file
4. Add `remote_theme: daviddarnes/alembic@main` to your `_config.yml` file to set the site theme
5. Run `bundle exec jekyll serve` to build and serve your site
6. Done! Use the [configuration](#configuration) documentation and the example [`_config.yml`](https://github.com/daviddarnes/alembic/blob/master/_config.yml) file to set things like the navigation, contact form and social sharing buttons

### As a Boilerplate / Fork

_(deprecated, not recommended)_

1. [Fork the repo](https://github.com/daviddarnes/alembic#fork-destination-box)
2. Replace the `Gemfile` with one stating all the gems used in your project
3. Delete the following unnecessary files/folders: `.github`, `LICENSE`, `screenshot.png`, `CNAME` and `alembic-jekyll-theme.gemspec`
4. Run the command `bundle install` in the root of project to install the jekyll remote theme gem as a dependancy
5. Run `bundle exec jekyll serve` to build and serve your site
6. Done! Use the [configuration](#configuration) documentation and the example [`_config.yml`](https://github.com/daviddarnes/alembic/blob/master/_config.yml) file to set things like the navigation, contact form and social sharing buttons

## Customising

When using Alembic as a theme means you can take advantage of the file overriding method. This allows you to overwrite any file in this theme with your own custom file, by matching the file name and path. The most common example of this would be if you want to add your own styles or change the core style settings.

To add your own styles copy the [`styles.scss`](https://github.com/daviddarnes/alembic/blob/master/assets/styles.scss) into your own project with the same file path (`assets/styles.scss`). From there you can add your own styles, you can even optionally ignore the theme styles by removing the `@import "alembic";` line.

If you're looking to set your own colours and fonts you can overwrite them by matching the variable names from the [`_settings.scss`](https://github.com/daviddarnes/alembic/blob/master/_sass/_settings.scss) file in your own `styles.scss`, make sure to state them before the `@import "alembic";` line so they take effect. The settings are a mixture of custom variables and settings from [Sassline](https://medium.com/@jakegiltsoff/sassline-v2-0-e424b2881e7e) - follow the link to find out how to configure the typographic settings.
