# Netbox-Inventory, Molecule und Ansible-Sign

<p align="center">
    <a target="_blank" href="https://ansible.readthedocs.io/projects/rulebook/en/latest/"><img style="vertical-align: middle" src="../../assets/images/molecule-logo.png" width="100" alt="Molecule Logo"></a>
    <a target="_blank" href="https://ansible.readthedocs.io/projects/sign/en/latest/index.html"><img style="vertical-align: middle" src="../../assets/images/ansible-logo-clear.png" width="100" alt="Ansible Logo"></a>
    <a target="_blank" href="https://demo.netbox.dev/"><img style="vertical-align: middle" src="../../assets/images/netbox-logo.png" width="100" alt="Netbox Logo"></a>
    <a target="_blank" href="https://galaxy.ansible.com/ui/repo/published/infra/aap_configuration/"><img style="vertical-align: middle" src="../../assets/images/aap-logo.png" width="100" alt="AAP Logo"></a>
    <a target="_blank" href="https://github.com/TimGrt/Ansible-Hackathon"><img style="vertical-align: middle" src="../../assets/images/git-logo.png" width="100" alt="Git Logo"></a>
</p>

## Übersicht

In diesem Use-Case soll auf virtuellen Maschinen ein Webserver mit der Dokumentation des Hackathons konfiguriert werden. Das Inventory soll dabei dynamisch aus der Netbox bezogen werden. Euer Ansible/Repository-Content soll mit Ansible-Sign signiert sein.  
Folgende Tools sollen hier bei zum Einsatz kommen:

* Single Source of Truth Netbox
* SCM nach Wahl
* Ansible Automation Platform
* Ansible Navigator
* Ansible-Sign
* Ansible Builder v3
* Execution Environment (default oder custom)

!!! success "Ziel"
    Die Playbooks befinden sich in einem SCM, der Usecase ist vollautomatisiert (auch alle Konfigurationen in der AAP) und nach Doku Vorgaben zu beschreiben.

## Vorgehen

* [x] **Step 1**  
    Erstellt ein dynamisches Inventory mit Nexbox als Quelle, alle VM-Objekte des Tenants sollen im Ansible/AAP-Inventory automatisch gesynct werden.

    !!! tip
        Man kann alle Objektdaten des Inventory Plugin über ansible-inventory anzeigen.

* [x] **Step 2**  
    Das Team aus Use-Case 1 erstellt VM-Instanzen in OpenShift Virtualization, auf diesen VMs sollt ihr *automatisiert* eine Webserver konfigurieren, welcher die Dokumentation des Projekts anzeigt. Es kann das GitHub Projekt des Hackathon verwendet werden und um die Dokumentation erweitert werden.

    !!! success
        Bis die VMs bereitstehen, sollt ihr euer Playbook lokal, mithilfe von Molecule entwickeln, nutzt dabei die Beschreibung aus dem [Best Practice Guide](https://timgrt.github.io/Ansible-Best-Practices/development/testing/){ target=_blank }.  
        Ein passender Test-Container (UBI8 Init-Container, verhält sich sehr ähnlich zu RHEL8-VM) ist hier zu finden: [ghcr.io/timgrt/rhel8-molecule-test-image:main](https://github.com/TimGrt/rhel8-molecule-test-image/pkgs/container/rhel8-molecule-test-image){ target=_blank }

    ??? abstract "Tipps zum Deployment der Dokumentation"

        Die folgenden Schritte sind für ein *RHEL8*-System zu befolgen:

        :one: Webserver-Paket `httpd` installieren  
        :two: Git-Paket `git` installieren  
        :three: Projekt per HTTPS klonen: `https://github.com/TimGrt/Ansible-Hackathon.git`  
        :four: Notwendige Python-Version `python3.12` und Python-Paket-Manager `python3.12-pip` installieren  
        :five: Python-Dependencies `requirements.txt`des Projekts installieren (passenden Paketmanager auswählen!)  
        :six: MkDocs Projekt bauen: `python3.12 -m mkdocs build --site-dir /var/www/html`  
        :seven: Webserver starten  

        !!! success
            Das Playbook soll natürlich *idempotent* sein!

* [x] **Step 3**  
    Signiert euren Ansible/Repository-Content mit `ansible-sign`. Nur signierter Code soll in der AAP ausführbar sein! Alles soll nach den Tests über die AAP 2.5 funktionieren.

* [x] **Step 4**  
    Erstellt eine Pipeline (Github Actions, Gitlab Pipeline, je nach Wahl eures SCM-Backends), welche bei einem Merge in den **main**-Branch euren Ansible-Content automatisch mit ansible-sign signiert.

## Links

Einige hilfreiche Tipps findet ihr hier:

* [Netbox Collection](https://docs.ansible.com/ansible/latest/collections/netbox/netbox/index.html){ target=_blank }
* [ansible-builder](https://github.com/ansible/ansible-builder){ target=_blank }
* [ansible-navigator](https://github.com/ansible/ansible-navigator){ target=_blank }
* [ansible-sign](https://ansible.readthedocs.io/projects/sign/en/latest/index.html){ target=_blank }
