# EDA mit Netbox, AAP und Openshift

<p align="center">
    <a target="_blank" href="https://ansible.readthedocs.io/projects/rulebook/en/latest/"><img style="vertical-align: middle" src="../../assets/images/ansible-eda-logo.png" width="100" alt="EDA Logo"></a>
    <a target="_blank" href="https://demo.netbox.dev/"><img style="vertical-align: middle" src="../../assets/images/netbox-logo.png" width="100" alt="Netbox Logo"></a>
    <a target="_blank" href="https://galaxy.ansible.com/ui/repo/published/infra/aap_configuration/"><img style="vertical-align: middle" src="../../assets/images/aap-logo.png" width="100" alt="AAP Logo"></a>
    <a target="_blank" href="https://docs.redhat.com/en/documentation/openshift_container_platform/4.19#Virtualization"><img style="vertical-align: middle" src="../../assets/images/openshift-logo.png" width="100" alt="OpenShift Logo"></a>
    <a target="_blank" href="https://github.com/TimGrt/Ansible-Hackathon"><img style="vertical-align: middle" src="../../assets/images/git-logo.png" width="100" alt="Git Logo"></a>
</p>

## Übersicht

In diesem Use-Case soll mit Event-Driven Ansible auf Events in der Netbox reagiert werden, bei Anlage eines VM Objekts soll automatisiert eine virtuelle Maschine über OpenShift Virtualization im OpenShift Cluster erstellt werden.  
Folgende Tools sollen hier bei zum Einsatz kommen:

* Single Source of Truth Netbox
* SCM nach Wahl
* Ansible Automation Platform
* OpenShift / OpenShift Virtualization
* Event-Driven Ansible
* Ansible Navigator
* Ansible Builder v3
* Execution Environment (default oder custom)

!!! success "Ziel"
    Die Playbooks befinden sich in einem SCM, der Usecase ist vollautomatisiert (auch alle Konfigurationen in der AAP) und nach Doku Vorgaben zu beschreiben.

## Vorgehen

* [x] **Step 1**  
    Es sollen mehrere simple Device Objekte, ohne viel Individualisierung, in der Netbox angelegt werden. Die Anlage, der zu erstellende Objekte, kann durch ein Playbook mit Hilfe der Netbox Collection erfolgen. Zur Orientierung gibt es auf Github vordefinierte Device Types GitHub

    !!! tip
        Man kann alle Objektdaten des Inventory Plugin über ansible-inventory anzeigen.

* [x] **Step 2**  
    Über einen Webhook, aus der Netbox, soll ein Playbook für die Erstellung eines Containers oder VM getriggert werden.

* [x] **Step 3**  
    Event-Driven Automation Rulebook erstellen und auf ein beliebiges Event hören z.B. Prozess oder Änderung des Netboxobjekt. Durch das getriggerte Event wird ein Playbook (lokal) oder ein Job/Workflow-Template in der AAP ausgeführt werden. Alles soll nach den Tests über die AAP 2.5 funktionieren.

    !!! success
        Hier müsst ihr mit dem Team von *Use-Case 2* zusammenarbeiten, sie sollen auf der von euch erstellten virtuellen Maschine Konfigurationen durchführen! Erstellt ein gemeinsamen Workflow, das andere Team erstellt unter anderem ein dynamisches Netbox-Inventory.

## Links

Einige hilfreiche Tipps findet ihr hier:

* [netbox-community Devicetype-library documentation](https://github.com/netbox-community/devicetype-library/tree/master){ target=_blank }
* [Ansible Builder documentation](https://github.com/ansible/ansible-builder){ target=_blank }
* [Ansible Navigator documentation](https://github.com/ansible/ansible-navigator){ target=_blank }
* [Event-Driven Ansible documentation](https://github.com/ansible/event-driven-ansible){ target=_blank }
