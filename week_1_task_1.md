#1

```docker build --help | grep "Write the image ID to the file"
      --iidfile string          Write the image ID to the file

```

#2
```docker run -it --entrypoint=/bin/bash python:3.9
root@a78172bab2b3:/# pip list
Package    Version
---------- -------
pip        22.0.4
setuptools 58.1.0
wheel      0.38.4
```

#3
```cat green_tripdata_2019-01.csv | grep -E "(2019-01-15.*){2}" green_tripdata_2019-01.csv | wc -l

20530
```

#4
```
SELECT
  CAST(lpep_pickup_datetime AS DATE) as "day",
  MAX(trip_distance) as "max_distance"
FROM
  yellow_taxi_trips
GROUP BY
  1
ORDER BY
  "max_distance" DESC
LIMIT 1
```

#5
```
SELECT
  count(*)
FROM
  yellow_taxi_trips
WHERE
    CAST(lpep_pickup_datetime AS DATE) = '2019-01-01' and
    passenger_count = 2
```

```
SELECT
  count(*)
FROM
  yellow_taxi_trips
WHERE
    CAST(lpep_pickup_datetime AS DATE) = '2019-01-01' and
    passenger_count = 2
```

#6
```
select *
from (SELECT tip_amount,
                      zpu."Zone" AS "pickup_loc",
                      zdo."Zone" AS "dropoff_loc"
               FROM yellow_taxi_trips t,
                    zones zpu,
                    zones zdo
               WHERE t."PULocationID" = zpu."LocationID"
                 AND t."DOLocationID" = zdo."LocationID") s
where pickup_loc = 'Astoria'
order by tip_amount desc
```