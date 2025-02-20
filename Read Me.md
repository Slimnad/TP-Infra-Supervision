# Mise en place de l'infrastructure de supervision

### LookEverything souhaite surveiller plusieurs services critiques. La première étape est la mise en place de l'infrastructure virtuelle sur Proxmox, en assurant la configuration des machines selon les spécifications fournies.

![Alt text](https://github.com/Slimnad/TP-Infra-Supervision/blob/main/Sch%C3%A9maInfra.PNG?raw=true)


### Le plan d'adressage est le suivant :

* Adresse réseau : 192.168.5.0 /24.

* Adresse de passerelle : 192.168.5.254.

* DNS : 8.8.8.8 dans un premier temps puis votre serveur AD.


Premier temps création d'une VM PFSense afin de faire un point d'accès sécurisé (Isolation des réseaux, Contrôle trafic et gestion LAN et WAN de plus ainsi mettre en place un VPN optionnel pour prendre la main sur les machines depuis nos postes en SSH).

![Alt text](https://github.com/Slimnad/TP-Infra-Supervision/blob/main/PFSENSE_network.png?raw=true)

### Ensuite création des différentes VMs de l'infrastructure fonctionnelle :

- 1 VM Wazuh | G503 G500-Wazuh | 2vCPU - 4 GB RAM - 32 GB HDD
- 1 VM Debian 12.2 (avec serveur web) | 551 G500-Debian  | 2vCPU - 4 GB RAM - 32 GB HDD
- 1 VM DC (Win Server 2022) | 550 G500-Win  | 2vCPU - 4 GB RAM - 32 GB HDD
- 1 VM Suricata | 502 G500-Suricata | 2vCPU - 4 GB RAM - 32 GB HDD

![Alt txt]

### Quelques test ping entre les machines

- Ping entre Win Server, Wazuh et PFSense ( à noter que la machine est sur le réseau VPN pour les prises en main à distance :D)

![Alt text](https://github.com/Slimnad/TP-Infra-Supervision/blob/main/WinSerTOWazuhTOPFSense.png?raw=true)

- Ping entre Debian et Wazuh

![Alt text](https://github.com/Slimnad/TP-Infra-Supervision/blob/main/Ping_DebTOWazuh.png?raw=true)

- Ping entre Wazuh et Win Server

![Alt text](https://github.com/Slimnad/TP-Infra-Supervision/blob/main/Ping_WazuhTOWinServ.png?raw=true)
