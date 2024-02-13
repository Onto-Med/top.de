---
layout: page
title: Home 
order: 5
---

![Terminology- and Ontology-based Phenotyping (TOP) Framework Overview: TOP enables phenotypic queries on patient or study database and ontology-based document search for medical documents.](public/framework_overview.svg)

[Deutsche Version unten.](#nachwuchsgruppe-top)

---

# Junior research group TOP

The goal of the project is the development and application of an ontology-based framework for complex patient phenotypes (TOP Framework).
The project is based on the structured medical data of the data integration centres of the [Medical Informatics Initiative (MII)](https://www.medizininformatik-initiative.de/en/consortia/data-integration-centres).
The concept is developed alongside the use cases of the [SMITH Consortium](https://www.smith.care),
though it is not limited to these and is to be applicable for many use cases of the MII Consortia and comparable projects in the medical domain in the future.
For this, a concept of a modular web application will be implemented, which combines many software tools and services for algorithmical phenotyping.
These tools and services provide data entities and phenotype-algorithms in standardized repositories and feature interfaces for linking external data repositories and importing existing metadata. 
The framework wants to support medical and clinical experts (medical staff, biometricians, student assistants, statisticians, etc.) in identifying patients and proposoti relevant for further analyses and studies.
It allows to select the data relevant for this group at a data integration centre and provide it for following steps.
By this, the data can be analyzed to calculate derivatives, scores and further classfications.
The specified metadata and phenotype algorithms/models will be published in a web repository and will be made accessible by standardized interfaces.

---

# Nachwuchsgruppe TOP
Die Nachwuchsgruppe arbeitet an der Entwicklung eines Ontologie-basierten Frameworks zur Bestimmung und Analyse von Phänotypen (Phänotypisierung).
Dabei bilden die im Rahmen der Medizininformatik-Initiative verfügbaren Daten
der [Datenintegrationszentren](https://www.medizininformatik-initiative.de/de/konsortien/datenintegrationszentren) die Grundlage.
Die entwickelten Modelle und Algorithmen werden in einem Webportal veröffentlicht und durch standardisierte Schnittstellen und Formate verfügbar gemacht.

## ZIELE DER NACHWUCHSGRUPPE INNERHALB DER [MEDIZININFORMATIK-INITIATIVE (MII)](https://www.medizininformatik-initiative.de/de/)

Ziel des Förderkonzepts Medizininformatik ist die Unterstützung der medizinischen Forschung
und die Verbesserung der Versorgung von Patientinnen und Patienten durch IT-Lösungen.
Es soll der Austausch und die Nutzung von Daten aus Krankenversorgung, klinischer und biomedizinischer Forschung
über die Grenzen von Institutionen und Standorten hinweg ermöglicht werden.
Dadurch soll die Medizininformatik-Initiative (MII) daran mitwirken, dass Ärztinnen und Ärzte, Patientinnen und Patienten sowie Forschende in Zukunft
schnell und effizient den Zugang zu den für sie erforderlichen Informationen erhalten.
Dies kann passgenaue und personalisierte Diagnose- und Behandlungsentscheidungen unterstützen,
neue Erkenntnisse für die wirksame und nachhaltige Bekämpfung von Krankheiten schaffen und dazu beitragen, die Versorgung stetig zu verbessern.

Die Bestimmung und Analyse von Phänotypen auf der Basis einer automatisierten Auswertung von Daten aus elektronischen Gesundheitsakten
sowie Forschungsdatenbanken durch geeignete IT-Lösungen spielt dabei eine entscheidende Rolle.
Für diesen Zweck werden sogenannte Phänotyp-Algorithmen entwickelt, die aus strukturierten Filterkriterien und Regeln bestehen und dazu dienen,
Individuen mit bestimmten Merkmalen zu identifizieren, beziehungsweise weitere Merkmale abzuleiten.
Der Implementierungsaufwand solcher Algorithmen in einer Programmiersprache oder einer Statistik-Software (z. B. SPSS oder R) kann sehr hoch sein:
Zum einen müssen etablierte medizinische Terminologien integriert und referenziert werden, um relevante Merkmale eindeutig und semantisch zu identifizieren,
damit die Vergleichbarkeit der Eingangsdaten und der Ergebnisse sichergestellt wird.
Zum anderen müssen verschiedene Datenquellen angebunden und Abfragen in entsprechenden Abfragesprachen definiert werden können,
was normalerweise nur durch IT-Fachleute durchgeführt werden kann, aber eine enge Zusammenarbeit mit Domänenexpertinnen und Domänenexperten erfordert,
die über das entsprechende Fachwissen verfügen.

In diesem Sinne hat sich die MII-Nachwuchsgruppe *Terminologie- und Ontologie-basierte Phänotypisierung* (TOP) zum Ziel gesetzt,
ein einfach zugängliches Ontologie-basiertes Framework (TOP Framework) zur Modellierung und Ausführung von Phänotyp-Algorithmen zu implementieren
und der Community zur Verfügung zu stellen.
Das Konzept wird entlang der Use Cases entwickelt, die im Konsortium SMITH im Fokus stehen, bleibt aber nicht auf diese beschränkt
und soll später für andere Use Cases der [MII-Konsortien](https://www.medizininformatik-initiative.de/de/konsortien)
sowie vergleichbare Projekte im medizinischen Bereich anwendbar sein.
Das Framework wird als eine modulare Webanwendung implementiert, die verschiedene Software-Tools und Services zur algorithmischen Phänotypisierung vereint.

## KONZEPT
In der Nachwuchsgruppe wurde ein modularer Ansatz entwickelt, der es ermöglicht, Phänotyp-Klassen auf einer abstrakten Ebene ontologisch zu modellieren
([Beger et al., Applied Sciences 2022](publications#app12105214); [Uciteli et al., GMS MIBE 2021](publications#mibe000219);
[Uciteli et al., JBMS 2020](publications#s13326-020-00230-0)).
Phänotyp-Klassen können genutzt werden, um beobachtbare Eigenschaften von Individuen (z. B. Patientinnen und Patienten sowie Teilnehmende an Studien)
zu beschreiben und zu klassifizieren.
Dieses Wissen kann in existierende Abfragesprachen wie SPARQL für RDF- oder OWL-basierte Daten, SQL für relationale Datenbankmanagementsysteme (RDMS)
oder HL7 FHIR Search für FHIR-Systeme transformiert werden.
Die generierten Abfragen lassen sich direkt innerhalb entsprechender Datenquellen ausführen, um nach Personen mit gewünschten Phänotypen zu suchen.
Für die Anbindung neuer Datenquellen müssen Adapter implementiert werden, die das Mapping der Daten auf die Phänotyp-Klassen ermöglichen
und das phänotypische Wissen in gewünschte Abfragesprachen übersetzen.
Der wichtigste Vorteil dieses Ansatzes ist eine klare Trennung zwischen der Modellierung des Fachwissens
(durch medizinisches Personal, Biometrikerinnen und Biometriker, etc., also Nicht-IT-Fachleute)
und der Implementierung der Adapter (durch Informatikerinnen oder Informatiker).
Die semantisch beziehungsweise ontologisch modellierten Phänotyp-Algorithmen sind dadurch unabhängig von der Struktur der Daten, Abfragesprachen
sowie weiteren technischen Aspekten und können durch geeignete Adapter auf verschiedenen Quellsystemen ausgeführt werden.

Ein weiteres Modul des Frameworks wird eine semantische Suche und Klassifikation von Textdokumenten (zum Beispiel Arztbriefe) unterstützen.
Dabei wird die Methode der Search Ontology ([Uciteli et al., JBMS 2019](https://doi.org/10.1186/s13326-019-0203-7)) zur Spezifikation und Generierung von Suchanfragen
mit einem auf Word Embeddings basierenden Ansatz zum inhaltlichen Dokumenten-Clustering (Bildung von Mengen ähnlicher Dokumente) verknüpft.
Die Search Ontology unterstützt eine effiziente und strukturierte Verwaltung von Suchtermen (d.h. Schlüsselwörter, Labels von Konzepten, Strings)
sowie ihre Verknüpfung mit den entsprechenden Such-Konzepten (d.h. Suchbegriffe können durch mehrere Terme/Labels repräsentiert werden),
was eine semantische konzeptbasierte Suche ermöglicht.
Die Erzeugung der Word Embeddings, um inhärente semantische Relationen zwischen Begriffen in Texten zu extrahieren, kann auf unterschiedliche Art erfolgen;
nicht zuletzt als ein Nebenprodukt aktueller und äußerst potenter Transformer-Modelle
([Vaswani et al., Advances in Neural Information Processing Systems 2017](https://papers.nips.cc/paper_files/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html)).
Die Embeddings – also vereinfacht ausgedrückt, die mathematischen Repräsentationen von Wörtern – werden wiederum
unter anderem durch gängige Cluster-Verfahren (Agglomerative, KMeans) in Konzept-Gruppen zusammengefasst.
In einem nächsten Schritt werden aus diesen Konzept-Clustern durch die Anwendung verschiedener Algorithmen,
Netzwerk-Repräsentationen erzeugt, die eine effiziente Suche nach relevanten Dokumenten ermöglichen sollen.

## ERGEBNISSE
Zur Modellierung und Klassifikation von Phänotypen haben wir
die Core Ontology of Phenotypes (COP) entwickelt ([Uciteli et al., JBMS 2020](publications#s13326-020-00230-0)).
Dabei betrachten wir Phänotypen als individuelle Eigenschaften, wie z. B. das Gewicht einer konkreten Person,
aber auch komplexe (zusammengesetzte bzw. abgeleitete) Merkmale wie der BMI-Wert oder der SOFA-Score einer Person.
Abstrakte Entitäten, die durch Phänotypen instanziiert werden, nennen wir *Phänotyp-Klassen*.
Wir unterscheiden zwischen *atomaren* (z. B. Alter, Gewicht, Größe) und *zusammengesetzten Phänotypen* (z. B. BMI, SOFA-Score, Typ 2 Diabetes Mellitus), 
die aus weiteren Phänotypen bestehen.
Die zusammengesetzten Phänotypen werden durch einen auswertbaren Ausdruck spezifiziert,
der entweder einen Phänotyp, eine Konstante oder eine Funktion mit einer beliebigen Anzahl von Argumenten repräsentiert.
Beispielsweise kann der Ausdruck des Phänotyp BMI wie folgt dargestellt werden:
`Quotient (Gewicht, Potenz (Größe, 2))`.
Es werden nicht nur mathematische, sondern auch logische und ontologische Funktionen unterstützt.
Phänotyp-Algorithmen können durch Angabe von (atomaren oder zusammengesetzten) Phänotypen als Ein-/Ausschlusskriterien definiert werden.
Zur Modellierung und Ausführung von Phänotyp-Algorithmen haben wir das Terminologie- und Ontologie-basierte (TOP) Framework entwickelt.
Das Framework kann in Krankenhausinformationssysteme integriert werden und ermöglicht somit die Ausführung der Algorithmen auf Versorgungs- und Forschungsdaten.
Dabei wird für jedes Ein-/Ausschlusskriterium eine Abfrage generiert, die mit Hilfe eines Adapters in die entsprechende Abfragesprache des Quellsystems übersetzt
und ausgeführt wird ([Beger et al., Applied Sciences 2022](publications#app12105214); [Uciteli et al., GMS MIBE 2021](publications#mibe000219)).
Für SQL und FHIR Search haben wir generische Java-basierte Adapter entwickelt, die mit einem Mapping konfiguriert werden können.
Die Abfrageergebnisse werden für die Auswertung von Ausdrücken der zusammengesetzten Phänotypen genutzt.

## ACKNOWLEDGEMENT
Gefördert durch das
<a href="https://www.bmbf.de/" target="_blank">
Bundesministerium für Bildung und Forschung (BMBF).
</a>

Text vorher erschienen in IMISE-Broschüre/text originally published in IMISE-brochure<br/>
*30 Jahre Institut für medizinische Informatik, Statistik und Epidemiologie und seine Wissenschaftsfamilie*, S.77ff.

<a href="https://www.imise.uni-leipzig.de" target="_blank"><img src="public/imise-logo.svg" alt="IMISE Logo" style="float:left;height:6em;"/></a>
<a href="https://www.bmbf.de/" target="_blank"><img src="public/bmbf-logo.svg" alt="BMBF Logo" style="float:right;height:8em;"/></a>
