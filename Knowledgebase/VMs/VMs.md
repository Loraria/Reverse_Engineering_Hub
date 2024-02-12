## **ArchLinux**
- ISO downloaden und davon booten 
- Tastaturlayout auf Deutsch stellen: 

    ```
    loadkeys de 
    ```

- Paketliste synchronisieren: 

    ```
    pacman  -Sy 

    pacman -Sy archlinux-keyring 
    ```

- Arch installieren: 

    ```
    archinstall
    ```


## **Ubuntu**
### VMware Tools 
https://askubuntu.com/questions/691585/copy-paste-and-dragdrop-not-working-in-vmware-machine-with-ubuntu 
```
sudo apt-get install open-vm-tools-desktop 
sudo systemctl enable open-vm-tools 
sudo systemctl restart open-vm-tools
```



```/usr/bin/vmware-user-suid-wrapper``` in Terminal ausführen 