# TP Réseaux — IP fixe → DHCP → ARP (Template de rapport)

Auteur : Antoine Mathié
Date  : 24/10/25

## 2. Configuration initiale — IP statique (preuve)

<details>
    <summary>Preuve screenshot</summary>
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d573caa1-775c-42d5-97ac-e9bc62533f36" />
</details>

## 3. Observation et manipulation d'ARP

<details>
    <summary>Preuve screenshot</summary>
  <img width="1345" height="834" alt="Screenshot 2025-10-24 154015" src="https://github.com/user-attachments/assets/600c216f-44cb-4ef6-9037-a928a324eb2c" />
</details>

## 4. Installation et configuration du serveur DHCP (sur `ubsky1`)

- Logiciel installé : `isc-dhcp-server`
- Fichier de configuration modifié : `/etc/dhcp/dhcpd.conf`

```config
default-lease-time 43200;
max-lease-time 86400;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.56.255;
option domain-name "local.lan";
authoritative;
subnet 192.168.56.0 netmask 255.255.255.0 {
  range 192.168.56.100 192.168.56.200;
  option routers 192.168.56.1;
  option domain-name-servers 192.168.56.1;
}
```
<details>
  <summary>Preuve screenshot</summary>
  <img width="1920" height="1080" alt="Screenshot 2025-10-24 154730" src="https://github.com/user-attachments/assets/4629444e-62c8-4d36-b457-4f49f4c52a5f" />
</details>

## 5. Passage du client (`ubsky2`) en DHCP (preuve)

- Adresse IP reçue : `192.168.56.100`
- Durée du bail : `12H`

<details>
    <summary>Preuve screenshot</summary>
  <img width="394" height="240" alt="Screenshot 2025-10-24 161246" src="https://github.com/user-attachments/assets/92a0d550-3ea5-4d32-9304-111d44fad0a0" />
  <img width="1920" height="1080" alt="Screenshot 2025-10-24 154730" src="https://github.com/user-attachments/assets/48f6aa2e-12a5-4c71-91cc-250ec94371d8" />
</details>

---

## 7. Checklist (à cocher — rendre avec le TP)
- [x] Deux VM sur le même réseau interne
- [x] IP statiques configurées et connectivité prouvée
- [x] Entrées ARP vérifiées et cache ARP rafraîchi au moins une fois
- [x] Serveur DHCP installé + plage et durée définies
- [x] Client passé en DHCP et bail vérifié sur le serveur
- [ ] Logs/baux fournis en preuve
- [x] Rapport + checklist rendus

---
