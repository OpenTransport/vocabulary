# The open transport vocabularies

The "Open Transport vocabularies" is a collection of vocabularies, which each define a set of URIs, used by the open transport community for various purposes:

1. If within your dataset, you use a certain word, you can link this word to a URI defined within this vocabulary. This way, you have disambiguated your word and your dataset has become semantically interoperable with other datasets using this vocabulary (e.g., by adding [JSON-LD](http://www.w3.org/TR/json-ld/) context or adding [RML mapping files](http://rml.io))
2. You can use these URIs within RDF set-ups to: store data, exchange data within hypermedia APIs, etc.

The URIs defined within the vocabularies are linked to existing vocabularies as much as possible and submitted to the [Linked Open Vocabularies project](http://lov.okfn.org).

Want to suggest your own vocabulary to be added in this repository? Contact one of the editors.

### Editors

* Pieter Colpaert (Open Knowledge | iMinds - Ghent University - MultiMedia Lab)
* Andrew Byrd (Conveyal)

### Contributors

* Tristram Gräbener (Capitaine Train)

## Vocabularies

### docs/

In the docs folder you can find a vocabulary for documentation purposes.

### The GTFS vocabulary

The [General Transit Feed Specification (GTFS)](https://developers.google.com/transit/gtfs/reference) defines an open standard data format for public transport schedules. Unlike other public transport data standards, it emerged to meet specific practical needs in passenger information systems and is a relatively simple tabular format. GTFS first appeared in 2005 through cooperation between a public agency and a private company, as a way for Portland, Oregon's TriMet agency to provide schedule data for the then-experimental Google Transit routing service. The standard is now maintained and revised through a public process on the [gtfs-changes mailing list](https://groups.google.com/forum/#!forum/gtfs-changes). For more information on the origins of GTFS, see [chapter 10 of Beyond Transparency](http://beyondtransparency.org/chapters/part-2/pioneering-open-data-standards-the-gtfs-story/).

An analysis of archived public feeds in the summer of 2012 found that after a period of rapid growth, "about one fourth of the agencies in the U.S. have open route and schedule data, representing about 85 percent of the total passenger-miles served." [[1]](http://blog.openplans.org/2012/07/in-public-transit-the-number-of-passenger-miles-served-by-agencies-with-open-data-has-skyrocketed/) Open transit data is also becoming widely available in Europe. Most of this data is provided in the GTFS format either directly by transport agencies or by third party data aggregators.

_src: http://gtfs.org_

In this repository you can find the folder [gtfs/](gtfs/), which contains a file gtfs.ttl which contains the machine-readable RDF version of the GTFS specification, as well a spec.md file which includes a human-readable document on how to create a linked GTFS dataset. It gives a URI to all terms which are defined in the [GTFS](https://developers.google.com/transit/gtfs/reference) specification.

At http://gtfs.org all GTFS archives which promise persistent identifiers will be republished as Linked Open Data. The URIs can then be used within Linked Data applications.

### The stop times vocabulary

The stop times vocabulary is created as a set of URIs to describe the act where a certain vehicle arrives at a certain stop at a certain moment in time and also leaves towards a nextStop and plans to arrive at a certain moment in time.

Just as the linked GTFS specification, you can find in the folder stoptimes 2 files: stoptimes.ttl for the machine-readable description and spec.md for the human-readable specification of how you can use the URIs.

You can use this vocabulary to:
 * annotate your route planning result documents with URIs for a certain stop time, and its predicates and objects,
 * give an overview of the next stop times (arrivals/departures) in a certain stop_area,

Mind that Stop Times is a very uncompressed specification and doesn't contain ways to describe recurring events (you should use GTFS for that).

### Road transport and DATEX2

_TODO: [Datex2](http://www.datex2.eu/) is a specification by [EasyWay](http://www.easyway-its.eu/). It specifies different exchange mechanisms for road transport data. We are **planning** on creating URIs for the data model used in the same way as we did for GTFS._

### Transport Themes

You can find the machine-readable spec in the themes directory.

These transport themes can be used for
 * a [dcat:themeTaxonomy](http://www.w3.org/ns/dcat#themeTaxonomy) to categorize datasets within a data portal. These can then become the main categories on the front page to search through the datasets listed on the Open Data Portal.
 * Other categorizations of transport datasets

## Adopted by

 * http://gtfs.org (GTFS)
 * iRail.be - a transport data broker for Belgium: https://irail.be (StopTimes)
 * Open Transport Net - http://opentnet.eu (Transport Themes)
 * _pull request your own_
