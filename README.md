# Orion-Nexus-Homelab
Infrastructure de niveau entreprise : Cluster Proxmox, Routage L3 Cisco, et services sécurisés via Keycloak/pfSense.


🚀 Projet Orion-Nexus : Enterprise Homelab Deployment

Bienvenue dans le dépôt officiel du projet Orion-Nexus. Ce projet consiste à concevoir, déployer et maintenir une infrastructure de services de niveau entreprise au sein d'un environnement de laboratoire personnel (Homelab).

L'objectif est de simuler un centre de données réel pour maîtriser la segmentation réseau, la haute disponibilité, la sécurité périmétrique, la gestion d'identité (IAM) et la surveillance de sécurité (SOC).

🏗️ Architecture Matérielle (Hardware)

Cœur de Réseau : Cisco SG500-52P (52 Ports Gigabit, L3, PoE). Gère le routage inter-VLAN matériel et la sécurité 802.1X.

Nœud de Calcul Principal : Lenovo ThinkStation D20 (2x Intel Xeon E5620 - 16 vCores, 32 Go RAM, 4x 500 Go HDD en ZFS RAIDZ1). Dédié à la puissance brute : SOC (Wazuh), Active Directory et stockage de masse.

Nœud Infrastructure : HP Laptop (Intel Core i7, 16 Go RAM, 1 To SSD). Héberge les services critiques (pfSense, Domotique). Sa batterie intégrée sert d'onduleur (UPS) pour maintenir le réseau en cas de coupure.

Réseau Secondaire : MikroTik hAP lite (Point d'accès / Routage secondaire).

Accès Internet (WAN) : FAI Togocom.

🛠️ Stack Technologique (Software)

Virtualisation : Proxmox VE (Cluster HA entre le D20 et le Laptop).

Réseautage : VLANs, Routage Inter-VLAN L3, LACP, QoS, MikroTik.

Sécurité & SOC : pfSense (Firewall), Wazuh (SIEM/SOC) pour la surveillance et détection d'intrusions.

Identité : Active Directory (Gestion des utilisateurs/ordinateurs) & Keycloak (SSO/IAM).

Gestion du trafic : Nginx Proxy Manager / HAProxy (Reverse Proxy).

Services Core : DNS (Pi-hole & AdGuard Home), Home Assistant, CasaOS.

Productivité & Dev : Nextcloud, Code-Server.

Communication : Stack VoIP & Visioconférence.

📅 Roadmap du Projet

Phase 1 : Core Network & Connectivity (En cours 🟡)

[x] Accès sécurisé SSH (Hardening RSA 2048).

[ ] Passage du Cisco SG500 en mode Layer 3.

[ ] Configuration du plan d'adressage IP et des VLANs.

[ ] Configuration du MikroTik et de la liaison WAN Togocom.

Phase 2 : Virtualisation & Cluster

[ ] Installation de Proxmox sur le D20 et le HP Laptop.

[ ] Mise en cluster des nœuds et configuration de la réplication ZFS.

[ ] Déploiement de pfSense virtualisé sur le nœud Laptop.

Phase 3 : Services de Sécurité & Identité

[ ] Déploiement de l'Active Directory.

[ ] Mise en place du serveur RADIUS pour le Dot1x.

[ ] Installation de Wazuh (SIEM) pour le monitoring de sécurité.

[ ] Déploiement de Keycloak pour le Single Sign-On (SSO).

Phase 4 : Déploiement des Services Web & Comm

[ ] Reverse Proxy avec certificats SSL.

[ ] Déploiement Nextcloud, VoIP et serveurs Web.

📔 Journal de bord & Troubleshooting

Incident #001 : Négociation SSH échouée

Problème : Impossible de se connecter au Cisco SG500 depuis un client moderne (No matching key exchange method).
Solution : Ajustement des KexAlgorithms et Ciphers dans la configuration client pour supporter les algorithmes hérités tout en conservant une sécurité RSA 2048.

📂 Structure du Dépôt

/network-configs : Configurations Cisco, MikroTik et pfSense.

/virtualization : Scripts d'automatisation Proxmox et templates.

/security : Configuration Wazuh, AD et RADIUS.

/services : Fichiers Docker Compose et YAML.

/docs : Schémas d'architecture et guides.

Projet maintenu par [Ton Nom/Pseudo]. Suivez l'évolution sur LinkedIn !
