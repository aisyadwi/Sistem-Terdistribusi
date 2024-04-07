# Load Balancing

1. Create microservice3
    
    sudo lxc-create -n microservice3 -t download -- --dist "debian" --release "buster" –arch amd64
    
    sudo lxc-start -n microservice3
    
    sudo lxc-attach microservice3
    
    sudo apt update 
    
    sudo apt install nginx nano
    
    ![1.png](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/1.png)
    
    ![2.png](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/2.png)
    
2. Konfigurasi microservice3
    
    sudo nano /etc/hosts
    
    ![3.png](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/3.png)
    
    ![7.png](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/7.png)
    
3. sudo lxc-create -n microservice4 -t download -- --dist "debian" --release "buster" –arch amd64
    
    sudo lxc-start -n microservice4
    
    sudo lxc-attach microservice4
    
    sudo apt update 
    
    sudo apt install nginx nano
    
    ![4.png](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/4.png)
    
4. Konfigurasi microservice4
    
    sudo nano /etc/hosts
    
    ![6.png](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/6.png)
    
    ![5.png](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/5.png)
    
5. sudo lxc-create -n microservice5 -t download -- --dist "debian" --release "buster" –arch amd64
    
    sudo lxc-start -n microservice5
    
    sudo lxc-attach microservice5
    
    sudo apt update 
    
    sudo apt install nginx nano
    
    ![8.png](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/8.png)
    
6. Konfigurasi microservice5
    
    sudo nano /etc/hosts
    
    ![9.png](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/9.png)
    
7. Mengkonfigurasi Host Wsl
    
    sudo nano /etc/hosts
    
    ![10.jpg](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/10.jpg)
    
8. sudo nano /etc/nginx/sites-enabled/sister.local
    
    ![11.jpg](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/11.jpg)
    
    ![12.jpg](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/12.jpg)
    
9. sudo nginx -t
    
    sudo nginx -s reload
    
    ![13.jpg](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/13.jpg)
    
    ![14.jpg](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/14.jpg)
    
10. curl -i app.sister.local
    
    ![15.jpg](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/15.jpg)
    
11. sudo tail -f /var/log/nginx/app.sister.local-access.log
    
    ![16.jpg](Load%20Balancing%200ea1a1731725450bbf6af3ce8ff5d878/16.jpg)