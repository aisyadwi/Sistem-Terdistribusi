# Sistem Terdistribusi

1. Download wsl
    
    “wsl —install -d Ubuntu”, perintah untuk mengecek apakah wsl sudah berhasil didownload
    
    ![b15a27f4-d994-470d-8e28-5da2d2ca7f7b.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/b15a27f4-d994-470d-8e28-5da2d2ca7f7b.png)
    

2. Persiapan install *Server host*

sudo apt install -y build-essential linux-headers-$(uname -r)

![2.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/2.png)

1. Mengganti *source list* ubuntu 22.04
    
    ![3.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/3.png)
    
2. Sudo apt update; sudo apt upgrade -y
    
    ![4.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/4.png)
    
    ![5.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/5.png)
    
3. Installasi lxc 
    
    sudo apt-get install lxc lxctl lxc-templates net-tools
    
    ![6.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/6.png)
    
4. Lalu, Check Konfigurasi
    
    sudo lxc-checkconfig
    
    ![7.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/7.png)
    
5. Menampilkan template container yang tersedia
    
    sudo ls /usr/share/lxc/templates/
    
    ![8.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/8.png)
    
6. Membuat container Ubuntu
    
    sudo lxc-create -n namakontainer -t template
    
    ![9.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/9.png)
    
7. Installasi nginx
    
    sudo apt install nginx nginx-extras
    
    ![10.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/10.png)
    
8. Kemudian pindah ke direktori “sites-enabled”
    
    cd /etc/nginx/sites-enabled/
    
    ls -la, untuk menampilkan daftar isi dari sebuah direktori
    
    sudo cp default sister.local, untuk membuat salinan dari file “default” dan diberi nama “sister.local”.
    
    lalu masu ke, “nano sister.local”
    
    ![11.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/11.png)
    
    ![12.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/12.png)
    
9. Tes konfigurasi
    
    sudo nginx -t
    
    sudo nginx -s reload
    
    Kemudian masuk ke direktori var/www/html
    
    sudo cp index.nginx-debian.html index.html
    
    lalu masuk ke, sudo nano index.html
    
    ![13.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/13.png)
    
    ![14.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/14.png)
    
10. Kemudian masuk ke, ssd C - windows - System32 - drivers - etc - hosts, buka file hosts pada notepad, kemudian tambahkan seperti gambar dibawah
    
    ![15.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/15.png)
    
11. Masuk ke web browser denge mengetikkan “sister.local”, maka akan muncul tampilan 
    
    ![16.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/16.png)
    
12. cat index.html
    
    untuk menampilkan isi dari file di terminal
    
    ![17.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/17.png)
    
13. sudo lxc-create -n microservice1 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --server [images.linuxcontainers.org](http://images.linuxcontainers.org/)
    
    sudo lxc-create -n microservice2 -t download -- --dist ubuntu --release bionic --arch amd64 --force-cache --server [images.linuxcontainers.org](http://images.linuxcontainers.org/)
    
    perintah diatas digunakan untuk membuat sebuah kontainer lxc
    
    ![18.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/18.png)
    
14. sudo lxc-start -n microservice2
    
    sudo lxc-attach -n microservice2
    
    sudo lxc-ls -f, untuk mengecek status mcsv2 apakah sudah running
    
    perintah diatas juga berlaku untuk microservice1
    
    ![19.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/19.png)
    
    ![29.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/29.png)
    
15. Check ip pada mcsv2 dan mcsv1
    
    ip a
    
    ![20.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/20.png)
    
    ![27.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/27.png)
    
16. apt install nano pada mcsv1 dan mcsv2
    
    ![21.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/21.png)
    
    ![26.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/26.png)
    
17. sudo nano /etc/netplan/10-lxc.yaml 
    
    perintah diatas untuk mcsv1 dan mcsv2
    
    ![23.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/23.png)
    
    ![24.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/24.png)
    
    ![27.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/27.png)
    
    ![28.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/28.png)
    
18. sudo netplan apply
    
    pada mcsv1 dan mcsv2
    
    ![5cf33165-aae9-410d-9ac6-b065bc1e8820.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/5cf33165-aae9-410d-9ac6-b065bc1e8820.png)
    
    ![27.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/27.png)
    
19. ping google.com
    
    pada mcsv1 dan mcsv2
    
    ![30.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/30.png)
    
    ![31.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/31.png)
    
20. apt update; apt upgrad -y;
    
    pada mcsv1 dan mcsv2
    
    ![32.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/32.png)
    
21. sudo apt install nginx nginx-extras
    
    pada mcsv1 dan mcsv2
    
    ![33.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/33.png)
    
    ![34.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/34.png)
    
22. Masuk ke direktori var/www/html
    
    cd /var/www/html/
    
    berlaku pada mcsv1 dan mcsv2
    
    ![35.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/35.png)
    
23. ls
    
    nano index.nginx-debian.html
    
    kemudian merubah isinya seperti gambar dibawah
    
    pada mcsv1 dan mcsv2
    
    ![36.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/36.png)
    
    ![37.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/37.png)
    
    ![39.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/39.png)
    
24. curl localhost
    
    untuk mengirim permintaan HTTP ke alamat localhost
    
    pada mcsv1 dan mcsv2
    
    ![40.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/40.png)
    
    ![41.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/41.png)
    
25. Masuk ke direktori sites-enabled
    
    cd sites-enabled
    
    ls
    
    cp default mcsv1.local
    
    nano mcsv1.local
    
    berlaku juga untuk mcsv2
    
    ![9651c00d-88b7-411c-8251-51dec539c279.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/9651c00d-88b7-411c-8251-51dec539c279.png)
    
    ![45.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/45.png)
    
    ![43.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/43.png)
    
    ![44.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/44.png)
    
26. sudo nginx -t
    
    sudo nginx -s reload
    
    ![46.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/46.png)
    
    ![49.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/49.png)
    
27. sudo nano /etc/hosts
    
    pada mcsv1 dan mcsv2
    
    ![47.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/46.png)
    
    ![50.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/50.png)
    
28. sudo nano /etc/hosts
    
    pada terminal ubuntu
    
    ![62.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/62.png)
    
29. curl mcsv1.local
    
    curl mcsv2.local
    
    pada terminal ubuntu
    
    ![61.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/61.png)
    
    ![63.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/63.png)
    
30. sudo nano sister.local
    
    ![64.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/64.png)
    
    ![65.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/65.png)
    
    setelah itu
    
    sudo nginx -t
    
    sudo nginx -s reload
    
    ![64.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/64%201.png)
    
31. curl sister.local/blog
    
    ![66.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/66.png)
    
    lalu buka web browser ketik “sisterl.local/blog”, akan muncul tampilan seperti dibawah
    
    ![67.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/67.png)
    
32. curl sister.local/aboutus
    
    ![68.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/68.png)
    
    lalu buka web browser ketik “sisterl.local/aboutus”, akan muncul tampilan seperti dibawah
    
    ![69.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas1/assets/69.png)
