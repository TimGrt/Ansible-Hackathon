# Event-Driven Automation mit Netbox, Ansible Automation Platform und Openshift

## Übersicht:

In diesem Usecase soll auf verschiedene Events reagiert werden, um einen optimalen Betrieb von Container oder virtuellen Maschinen zu garantieren. Folgende Tools sollen hier bei zum Einsatz kommen:

- Single Source of Truth Netbox
- SCM nach Wahl
- Ansible Automation Platform
- OpenShift / OpenShift
- Event driven Ansible
- Ansible Navigator
- Ansible Builder v3
- Execution Environment (default oder custom)

**Ziel:**
Die Playbooks befinden sich in einem SCM, der Usecase ist vollautomatisiert und nach [Doku Vorgaben](../docu_pattern/index.md) zu dokumentiert.

## Vorgehen:

**Step 1:**
Es sollen mehrere simple Device Objekte, ohne viel Individualisierung, in der Netbox angelegt werden. Die Anlage, der zu erstellende Objekte, kann durch ein Playbook mit Hilfe der Netbox Collection erfolgen. Zur Orientierung gibt es auf Github vordefinierte Device Types GitHub

- [netbox-community Devicetype-library](https://github.com/netbox-community/devicetype-library/tree/master)

DeviceType definitions for import to NetBox

*Hinweis:*
Man kann alle Objektdaten des Inventory Plugin über ansible-inventory anzeigen.

**Step 2:**
Über einen Webhook, aus der Netbox, soll ein Playbook für die Erstellung eines Containers oder VM getriggert werden. Hier zu werden alle Daten (IP, Hostname usw.) über ein dynamisches Inventory, aus der Netbox verwendet.

**Step 3:**
Event driven Automation Rulebook erstellen und auf ein beliebiges Event hören z.B. Prozess oder Änderung des Netboxobjekt. Durch das getriggerte Event wird ein Playbook ausgeführt und der Container oder die VM repariert. Hierzu kann der Container oder die VM auch einfach gelöscht und neu erstellt werden. Alles soll nach den Tests über die AAP 2.5 funktionieren.

**Step 4:**
In der VM soll ein Webserver installiert werden, mit der Dokumentation des Projekts. Es kann das GitHub Projekt des Hackathon verwendet werden und um die Dokumentation erweitert werden.

### Links:

- [netbox-community Devicetype-library](https://github.com/netbox-community/devicetype-library/tree/master)
- [ansible-builder](https://github.com/ansible/ansible-builder)
- [ansible-navigator](https://github.com/ansible/ansible-navigator)
- [event-driven-ansible](https://github.com/ansible/event-driven-ansible)
