Konfigurasi: Cara aktivasi modem gpon di OLT Zte C300:
```code
Jasa setting mikrotik dan OLT +62822-3348-3221 (PURWANTO)
---
utk SuryaNET, Beji, Pasuruan, Jawa Timur
---

```code
conf t
interface gpon-olt_1/2/1
onu 58 type ALL sn RTEGCA96C032
exit

interface gpon-onu_1/2/1:58
name M. Zainul
desc isi dengan keterang pelanggan anda
tcont 1 profile 1G
gemport 1 tcont 1
service-port 1 vport 1 user-vlan 300 vlan 300
exit

pon-onu-mng gpon-onu_1/2/1:58
service 1 gemport 1 vlan 300
wan-ip 1 mode pppoe username Nabillah password dss12345 vlan-profile pppoe300 host 1
tr069-mgmt 1 acs http://192.168.17.45:7547
tr069-mgmt 1 tag pri 0 vlan 300 state unlock
wan-ip 1 ping-response enable traceroute-response enable
wan 1 ssid 1 service internet host 1
security-mgmt 2 ingress-type wan mode forward state enable protocol web
exit sampai muncul # saja, lalu write
```
