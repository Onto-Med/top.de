---
layout: page
title: Home 
order: 5
---

![Terminology- and Ontology-based Phenotyping (TOP) Framework Overview: TOP enables phenotypic queries on patient or study database and ontology-based document search for medical documents.](public/top-framework-overview.svg)

[Deutsche Version unten.](#nachwuchsgruppe-top)

---

# Junior Research Group TOP

The junior research group is working on the development of an ontology-based framework for the determination and analysis of phenotypes (phenotyping).
The project is based on the structured medical data of the [data integration centres](https://www.medizininformatik-initiative.de/en/consortia/data-integration-centres) of the Medical Informatics Initiative.
The models and algorithms developed are published in a web portal and made available via standardized interfaces and formats.

## OBJECTIVES OF THE JUNIOR RESEARCH GROUP WITHIN THE [MEDICAL INFORMATICS INITIATIVE (MII)](https://www.medizininformatik-initiative.de/en/)
The aim of the medical informatics funding concept is to support medical research
and the improvement of patient care through IT solutions.
The exchange and use of data from patient care, clinical and biomedical research across the boundaries of institutions and locations is to be made available.
In this way, the MII will help to ensure that doctors, patients and researchers will in future be able to and efficient access to the information they need.
This can support tailored and personalized diagnosis and treatment decisions,
create new insights for the effective and sustainable fight against diseases and contribute to the continuous improvement of care.

The determination and analysis of phenotypes on the basis of automated evaluation of data
from electronic health records and research databases using suitable IT solutions is key.
For this purpose, so-called phenotype algorithms are being developed, which consist of structured filter criteria and rules
and are used to identify individuals with certain characteristics or derive further characteristics.
The implementation effort of such algorithms in a programming language or statistical software (e.g. SPSS, R) can be very high:
Firstly, established medical terminologies must be integrated and referenced in order to identify relevant characteristics clearly and semantically,
to ensure the comparability of the input data and the results.
Secondly, it must be possible to connect various data sources and define queries in respective query languages.
This can normally only be done by IT specialists, but requires close collaboration with domain experts, who have the relevant specialised knowledge.

With this in mind, the MII junior research group *Terminology- and Ontology-based Phenotyping* (TOP) has set itself the goal of
implementing an easily accessible ontology-based framework (TOP Framework) for modelling and executing phenotype algorithms and making it available to the community.
The concept is being developed adjacent but not limited to the use cases in focus of the SMITH consortium
and will later be applicable to other use cases of the [MII consortia](https://www.medizininformatik-initiative.de/en/node/5)
and comparable projects in the medical field.
The framework will be implemented as a modular web application that combines various software tools and services for algorithmic phenotyping.

## CONCEPT
The junior research group has developed a modular approach that enables phenotype classes to be modelled ontologically at an abstract level
([Beger et al., Applied Sciences 2022](publications#app12105214); [Uciteli et al., GMS MIBE 2021](publications#mibe000219);
[Uciteli et al., JBMS 2020](publications#s13326-020-00230-0)).
Phenotype classes can be used to describe and classify observable characteristics of individuals (e.g. patients and study participants).
This knowledge can be integrated into existing query languages such as SPARQL for RDF- or OWL-based data,
SQL for relational database management systems (RDMS) or HL7 FHIR Search for FHIR systems.
The generated queries can be executed directly within corresponding data sources to search for persons with desired phenotypes.
To connect new data sources, adapters must be implemented that enable the data to be mapped to the phenotype classes
and translate the phenotypic knowledge into the desired query languages.
The most important advantage of this approach is a clear separation between the modelling of expert knowledge
(by medical staff, biometricians, etc., i.e. non-IT specialists) and the implementation of the adapters (by computer scientists).
The semantically or ontologically modelled phenotype algorithms are therefore independent of the structure of the data, query languages and other technical aspects,
while still being able to be executed on different source systems using suitable adapters.

Another module of the framework will support the semantic search and classification of text documents (e.g. doctor's letters).
The Search Ontology ([Uciteli et al., JBMS 2019](https://doi.org/10.1186/s13326-019-0203-7)) method for the specification and generation of search queries is combined
with an approach based on word embeddings for content-related document clustering (formation of sets of similar documents).
The Search Ontology supports efficient and structured management of search terms (i.e. keywords, concept labels, strings)
as well as their linking with the corresponding search concepts (i.e. search terms can be represented by several terms/labels),
which enables a semantic concept-based search.
The generation of word embeddings to extract inherent semantic relations between terms in texts can be done in different ways;
not least as a by-product of current and extremely powerful transformer models ([Vaswani et al., Advances in Neural Information Processing Systems 2017](https://papers.nips.cc/paper_files/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html)).
The embeddings - i.e. in simple terms, the mathematical representations of words -
are in turn summarised into concept groups using common clustering methods (Agglomerative, KMeans).
In the next step, these concept clusters are used to generate network representations by applying various algorithms,
which should enable an efficient search for relevant documents.

## RESULTS
For the modelling and classification of phenotypes, we have developed the Core Ontology of Phenotypes (COP)
([Uciteli et al., JBMS 2020](publications#s13326-020-00230-0)).
We consider phenotypes as individual characteristics, such as the weight of a specific person,
but also complex (composite or derived) characteristics such as a person's BMI or SOFA score.
We call abstract entities that are instantiated by phenotypes *phenotype classes*.
We distinguish between *atomic* (e.g. age, weight, height) and *composite phenotypes* (e.g. BMI, SOFA score, type 2 diabetes mellitus),
which consist of additional phenotypes.
The composite phenotypes are specified by an analysable expression,
which represents either a phenotype, a constant or a function with any number of arguments.
For example, the expression of the phenotype BMI can be represented as follows:
`Divide (Weight, Power (Height, 2))`.
Not only mathematical, but also logical and ontological functions are supported.
Phenotype algorithms can be defined by specifying (atomic or composite) phenotypes as inclusion/exclusion criteria.
We have developed the terminology and ontology-based (TOP) framework for modelling and executing phenotype algorithms.
The framework can be integrated into hospital information systems and thus enables the algorithms to be executed on care and research data.
A query is generated for each inclusion/exclusion criterion, which is translated into the corresponding query language of the source system
and executed with the help of an adapter ([Beger et al., Applied Sciences 2022](publications#app12105214); [Uciteli et al., GMS MIBE 2021](publications#mibe000219)).
For SQL and FHIR Search, we have developed generic Java-based adapters that can be configured with a mapping.
The query results are used to evaluate expressions of the composite phenotypes.

## ACKNOWLEDGEMENT
Funded by the
<a href="https://www.bmbf.de/bmbf/en/" target="_blank">
Federal Ministry of Education and Research (BMBF).
</a>

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
Dadurch soll die MII daran mitwirken, dass Ärztinnen und Ärzte, Patientinnen und Patienten sowie Forschende in Zukunft
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
In einem nächsten Schritt werden aus diesen Konzept-Clustern durch die Anwendung verschiedener Algorithmen
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
