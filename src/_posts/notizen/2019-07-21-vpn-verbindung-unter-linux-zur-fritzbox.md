---
title: Linux ➔ Fritzbox-VPN
excerpt: >
  Wie richte ich die VPN-Verbindung zu meiner Fritzbox auf meinem Linux-Rechner
  unter Gnome ein?
categories: [notizen]
tags: [linux, vpn, gnome]
# toc: true
# support: true
# comments: true
# comments_locked: true
# published: false
# last_modified_at: 
---

Das geht ganz einfach, es fehlt lediglich ein Paket namens
`network-manager-vpnc-gnome`.

``` terminal
# apt install network-manager-vpnc-gnome
```

{% figure class:"gallery-2-col" caption:"Jetzt kann man in den Netzwerkeinstellungen unter VPN auch den
**Cisco-kompatiblen Client (vpnc)** auswählen." %}
  ![Beispielfoto](/assets/images/vpnc-linux-example.jpg)
  ![Beispielfoto Konfiguration](/assets/images/vpn-konfiguration-example.jpg)
{% endfigure %}

{% notice info %}
Die Beispielbilder stammen von Kali Linux (Debian). Auf anderen Distributionen
könnte das Paket natürlich anders heißen.

Unter Gnome kann man ohne diesem Paket nur Einstellungen von einer Datei
importieren!

Das Einrichten einer VPN-Verbindung zu deiner Fritzbox kannst du auf deiner
Fritzbox nachlesen. Melde dich dort an und gehe zu _System / Fritz!Box-Benutzer_.
Bearbeite deinen Benutzer und scrolle ganz nach unten. Aktiviere das Kästchen
vor _VPN_ und klicke auf den Link _VPN-Einstellungen anzeigen_.
{% endnotice %}
