---
title: Technische Spezifikationen
nav_order: 5
---

# Technische Spezifikationen
{: .no_toc }

Technischen Systemanforderungen und Spezifikationen für den Betrieb von
KomMonitor mit Docker.
{: .fs-6 .fw-300 }

## Inhalt
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Einführung
Dieses Dokument beschreibt die technischen Systemanforderungen und Spezifikationen für den Betrieb von
KomMonitor mit Docker. Es wird davon ausgegangen, dass alle KomMonitor-Komponenten und erforderliche
Drittanbieter-Softwarekomponenten mit Docker Compose bereitgestellt werden.

Docker Compose-Vorlagen für die Bereitstellung von KomMonitor als Docker-Container sind im folgenden 
Repository verfügbar: [https://github.com/KomMonitor/docker](https://github.com/KomMonitor/docker). Die bereitgestellten Konfigurationsdateien 
vereinfachen und beschleunigen die lokale Bereitstellung des gesamten KomMonitor-Stacks über Docker. Für 
den produktiven Betrieb müssen die bereitgestellten Konfigurationsdateien an die jeweilige 
Betriebsumgebung angepasst werden.

Der Betrieb von KomMonitor in einem Kubernetes-Cluster wird in diesem Dokument nicht beschrieben.

## Systemanforderungen
Die wichtigste Anforderung für den Betrieb von KomMonitor ist, dass eine Docker Engine auf dem Server 
verwendet werden kann. Windows Server wird als Betriebssystem nicht unterstützt. Zusätzliche 
Systemanforderungen:
* Server-Betriebssystem: Ubuntu (andere Linux-Distributionen wären ebenfalls möglich, sofern dort eine Docker Engine betrieben werden kann - siehe unterstützte Plattformen: [https://docs.docker.com/desktop/install/linux-install/#supported-platforms](https://docs.docker.com/desktop/install/linux-install/#supported-platforms)
* CPU: 4 Kerne
* Speicher: 12-16 GB RAM
* Speicherplatz: 50 GB SSD (abhängig von der Menge der in KomMonitor zu verwaltenden Daten können höhere Speicheranforderungen erforderlich sein)