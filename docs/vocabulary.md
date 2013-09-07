# Open Transport vocabulary

## stop_point

A `stop_point` is the location where a `vehicle` can stop. 

Properties:
 * serves_mode <type of `vehicle`> (can be more than 1)
 * geo location
 * maintained_by <link to `agency`> (can be more than 1)
 * part_of <link to `stop_area`> (can be more than 1)

## stop_area

A `stop_area` is a collection of `stop_point`s. Generally there are at least two `stop_points` per `stop_area`, one per direction of a line. Now think of a hub, you will have more than one `line`. Therefore your `stop_area` will contain more than two `stop_points`. In particular cases your `stop_area` can contain only one `stop_point`.

## connection_link

This object links two `stop_point`s together (named origin and destination). It is the walkable part of a journey.

## vehicle_journey

A `vehicle_journey` is a single run of a `vehicle` along a `journey_pattern`.
For example, `vehicle` bus 23 leaving at 14:20 from `stop` Amsterdam Central
Station.

## journey_pattern

A journey pattern is an ordered list of `stop_point`s. Two `vehicle`s that serve exactly the
same `stop_point`s in exactly the same order belong to to the same `journey_pattern`.

## route

A `route` is a collection of `journey_pattern`s that match the same commercial direction.

## line

A `line` is a collection of `route`s. Most of the time you'll just have just two `route`s.

# stop_time

A `stop_time` represents the time when a `vehicle` is planned to arrive and to leave a `stop_point`.

# vehicle

A `vehicle` is an object which can take one or more people from one place to another.

# agency

An `agency` maintains one or several `mode`s for certain areas.

# mode

A `mode` is a type of transport. (To do: specify all the different `mode`s by comparing Transmodel and GTFS and extending it with private transport `mode`s)

# trip

A `trip` is a path through the transit network that can be used to travel from
the departure location to the arrival location at a certain time. It consists
of an ordered list of `trip_leg`s.

Suppose we plan from `stop_area` Kerkehout, Wassenaar at 22:45 to `stop_area`
Weteringplein, The Hague. The result could be a `trip` with a `trip_leg` from a
`vehicle_journey` of Bus 90 from Kerkehout 22:56 to The Hague Central Station
and a `trip_leg` of Tram 16 from Central Station 23:17 to Weteringplein.

# trip_leg

A `trip_leg` is a segment of a `vehicle_journey` that is used in a `trip`.

# itinerary

An `itinerary` is a human readable description of a `trip`. It commonly
contains a list of directions.
