
# Télécharger les 2 fichiers
- [x] Le userXX.conf  
- [x] Le northsec-E1.cert  

# Installer le certificat
### sur Kali et wsl  
sudo cp northsec-E1.crt /usr/local/share/ca-certificates/my-custom-ca/  
sudo update-ca-certificates  

> [!NOTE]  
Il est possible que le répertoire my-custom-ca n'existe pas sur les versions récentes de Kali. simplement drop le certificat dans ca-certificates  

### Sur Windows ou Mac
double click et install

# Installer WireGuard et utiliser

## Sur Windows et Mac :

Télécharger wireguard pour le VPN  
https://www.wireguard.com/install/  
Importer le fichier .conf  
cliquer sur Activer  
Ouvrir un navigateur et aller sur https://test.nsec/  

## Sur Kali et WSL :  
Update du system... we never know  
``
sudo apt update
sudo apt upgrade
``  
installation de wireguard et dépendance  
``
sudo apt install -y wireguard-tools wireguard-go iproute2 resolvconf  
``  
copie du .conf au bon endroit et ajout de droit  
``
sudo cp ~/path/to/userXX.conf /etc/wireguard/userXX.conf  
sudo chmod 600 /etc/wireguard/userXX.conf
``  
lancer le VPN avec votre config  
``
sudo -E wg-quick up userXX  
``  
tester la connection  
``
curl https://test.nsec  
``  
fermer la connection VPN  
``
sudo -E wg-quick down userXX  
``  
> [!NOTE]  
Alternative Kali: utiliser la fonction de VPN de base pour ajouter le fichier de conf
