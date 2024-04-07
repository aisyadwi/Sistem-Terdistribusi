# Load Balancing

1. Create microservice3
    
    sudo lxc-create -n microservice3 -t download -- --dist "debian" --release "buster" –arch amd64
    
    sudo lxc-start -n microservice3
    
    sudo lxc-attach microservice3
    
    sudo apt update 
    
    sudo apt install nginx nano
    
    ![1.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/1.png)
    
    ![2.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/2.png)
    
2. Konfigurasi microservice3
    
    sudo nano /etc/hosts
    
    ![3.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/3.png)
    
    ![7.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/7.png)
    
3. sudo lxc-create -n microservice4 -t download -- --dist "debian" --release "buster" –arch amd64
    
    sudo lxc-start -n microservice4
    
    sudo lxc-attach microservice4
    
    sudo apt update 
    
    sudo apt install nginx nano
    
    ![4.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/4.png)
    
4. Konfigurasi microservice4
    
    sudo nano /etc/hosts
    
    ![6.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/6.png)
    
    ![5.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/5.png)
    
5. sudo lxc-create -n microservice5 -t download -- --dist "debian" --release "buster" –arch amd64
    
    sudo lxc-start -n microservice5
    
    sudo lxc-attach microservice5
    
    sudo apt update 
    
    sudo apt install nginx nano
    
    ![8.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/8.png)
    
6. Konfigurasi microservice5
    
    sudo nano /etc/hosts
    
    ![9.png](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/9.png)
    
7. Mengkonfigurasi Host Wsl
    
    sudo nano /etc/hosts
    
    ![10.jpg](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/10.jpg)
    
8. sudo nano /etc/nginx/sites-enabled/sister.local
    
    ![11.jpg](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/11.jpg)
    
    ![12.jpg](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/12.jpg)
    
9. sudo nginx -t
    
    sudo nginx -s reload
    
    ![13.jpg](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/13.jpg)
    
    ![14.jpg](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/14.jpg)
    
10. curl -i app.sister.local
    
    ![15.jpg](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/15.jpg)
    
11. sudo tail -f /var/log/nginx/app.sister.local-access.log
    
    ![16.jpg](https://github.com/aisyadwi/Sistem-Terdistribusi/blob/main/Tugas2/ss/16.jpg)
