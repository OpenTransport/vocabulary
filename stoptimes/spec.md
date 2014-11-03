# The Specification

## Prefixes used

| namespace prefix | URI |
|----:|:----|
| st: |`http://semweb.mmlab.be/ns/stoptimes#` |
| gtfs: |`http://vocab.gtfs.org/terms#` |
| dct:| `http://purl.org/dc/terms/` |
| xsd:| `http://www.w3.org/2001/XMLSchema#`|
| rdfs:| `http://www.w3.org/2000/01/rdf-schema#`|
| foaf:| `http://xmlns.com/foaf/0.1/`|

## Schema overview

![Schema](https://docs.google.com/drawings/d/1uLXAtV9wpD1Mm7FJQ_vEpFNdBarG8oXhdAloyo9VIkY/pub?w=924&h=355)

In the stoptimes ontology, every stop a certain vehicle does or is schedules to do, gets a certain URI. A [st:StopTime](http://semweb.mmlab.be/ns/stoptimes#StopTime) has to have a [st:arrivalTime](http://semweb.mmlab.be/ns/stoptimes#arrivalTime) and/or a [st:departureTime](http://semweb.mmlab.be/ns/stoptimes#departureTime). If one of these is not set, it may indicate the vehicle is at a terminus or it is starting its service.

The [st:StopTime](http://semweb.mmlab.be/ns/stoptimes#StopTime) also refers through [gtfs:stop](http://vocab.gtfs.org/terms#stop) to a [gtfs:Stop](http://vocab.gtfs.org/terms#Stop), pointing to the exact location where passengers can disembark and embark. Mind that the [gtfs:stop](http://vocab.gtfs.org/terms#stop) can change over time for the same [st:StopTime](http://semweb.mmlab.be/ns/stoptimes#StopTime). For example, one [gtfs:Stop](http://vocab.gtfs.org/terms#Stop) can be "platform A of Paris Gare du Nord", but due to the late announcement of the exact platform at Paris Gare du Nord, first the [gtfs:Station](http://vocab.gtfs.org/terms#Station) "Paris Gare du Nord" can be mentioned before the precise [gtfs:Stop](http://vocab.gtfs.org/terms#Stop) is mentioned.

The [st:StopTime](http://semweb.mmlab.be/ns/stoptimes#StopTime) may refer, using the predicate [st:nextStopTime](http://semweb.mmlab.be/ns/stoptimes#nextStopTime), to the next [st:StopTime](http://semweb.mmlab.be/ns/stoptimes#StopTime). Mind that this can also change over time, e.g., for an extra stop being introduced on the current [gtfs:Trip](http://vocab.gtfs.org/terms#Trip).

[gtfs:headSign](http://vocab.gtfs.org/terms#headSign) is a predicate from the GTFS ontology and gives a label to the current trip which can be shown to the end-user to refer to the right vehicle at that station.

[gtfs:route](http://vocab.gtfs.org/terms#route) is a predicate to link a stoptime with a certain Route. Also [gtfs:trip](http://vocab.gtfs.org/terms#trip) may be used.

# Usage

## Departure or Arrival indicators

Use a JSON-LD context and mark up your JSON:
```json
{
  "@context" : {
    "gtfs" : "http://vocab.gtfs.org/terms#",
    "st": "http://semweb.mmlab.be/ns/stoptimes#",
    "arrivaltime" : "st:arrivalTime",
    "departuretime" : "st:departureTime",
    "stop" : {
      "@id" : "gtfs:stop",
      "@type" : "@id"
    },
    "nextstoptime" : {
      "@id" : "st:nextStopTime",
      "@type" : "@id"
    },
    "headsign" : "gtfs:headSign",
    "route" : {
      "@id" : "gtfs:route",
      "@type" : "@id"
    },
    "trip" : {
      "@id" : "gtfs:trip",
      "@type" : "@id"
    },
    "accessibility" : {
      "@id" : "gtfs:wheelchairAccessible",
      "@type" : "@id"
    },
    "name" : "http://xmlns.com/foaf/0.1/name"
  },
  "@graph" : {
    "@id" : "http://example.com/stoptimes/1",
    "@type" : "st:StopTime",
    "arrivaltime" : "2014-11-03T19:14:00+01:00",
    "departuretime" : "2014-11-03T19:16:00+01:00",
    "stop" : {
      "@id" : "http://irail.be/stations/NMBS/008896412",
      "@type" : "gtfs:Station",
      "name" : "Comines",
      "accessibility" : "gtfs:WheelchairAccessible"
    },
    "nextstoptime" : "http://example.com/stoptimes/2",
    "headsign" : "Poperinge",
    "wheelchairaccessible" : "gtfs:WheelchairAccessible",
    "route" : "http://example.com/routes/1"
  }
}
```

## Archives

For archiving purposes, which may be interesting for comparing stop time announcements over time, we introduce the [st:StopTime](http://semweb.mmlab.be/ns/stoptimes#StopTime) as a [prov:Entity](http://www.w3.org/ns/prov#Entity). When used in combination with Prov, each [st:StopTime](http://semweb.mmlab.be/ns/stoptimes#StopTime) becomes an observation or prediction of a stoptime as done by a certain Activity at a certain moment (e.g., scraping of a website every night or calculated through a time schedule).
