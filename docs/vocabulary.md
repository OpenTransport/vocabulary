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
 
## journey_pattern

A journey pattern is an ordered list of `stop_point`s. Two `vehicle`s that serve exactly the
same `stop_point`s in exactly the same order belong to to the same `journey_pattern`.

## journey

A `journey` is a single run of a `vehicle` along a `journey_pattern`. For example, `vehicle` bus 23 leaving at 14:20 from `stop_area` Amsterdam Central Station.

## route

A `route` is a collection of `journey_pattern`s that match the same commercial direction.
The direction is given by the operator and does not necessarily match any physical reality.

A route can be `north bound`, `express`, `east branch`, etc.

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
