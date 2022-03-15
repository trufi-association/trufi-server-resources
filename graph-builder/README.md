# Graph Data Builder

| &nbsp;                                 | &nbsp;                                                       |
| -------------------------------------- | ------------------------------------------------------------ |
| The following extensions depend on it  | [otp](https://github.com/trufi-association/trufi-server/tree/main/extensions/otp) |
| This depends on the following builders | [map-pbf-builder](../map-pbf-builder) (always), [gtfs-builder](../gtfs-builder) (only if you have no GTFS file already) |

## Description

Builds the graph needed by the routing engine [OpenTripPlanner](https://opentripplanner.org). This uses the [OpenTripPlanner](https://opentripplanner.org) itself to build the graph.

## How to use

```bash
docker-compose --env-file ../$envfile up
```

- The `.obj` file out is located at `../data/<Country-City>/otp/data`
