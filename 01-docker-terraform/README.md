### Question 1
docker run --rm python:3.13 python -m pip --version
--> 25.3

### Question 2
postgres:5432

### Question 3  

```sql
select count(*) from green_tripdata_2025_11 
where lpep_pickup_datetime>='2025-11-01' and lpep_pickup_datetime<'2025-12-01'
and trip_distance<=1
-- 8,007
```

### Question 4

```sql
select date(lpep_pickup_datetime) from green_tripdata_2025_11 where trip_distance = 
(select max(trip_distance) from green_tripdata_2025_11
where trip_distance<100)
--2025-11-14
```

### Question 5

```sql
select pulocationid, sum(total_amount) total_amount  from green_tripdata_2025_11
where lpep_pickup_datetime>='2025-11-18' and lpep_pickup_datetime<'2025-11-19'
group by pulocationid
order by total_amount desc
limit 1;
select * from taxi_zone tz  where locationid  = 74
-- East Harlem North
```

### Question 6

```sql
select dolocationid  from green_tripdata_2025_11 where tip_amount=(select max(tip_amount) from green_tripdata_2025_11 where pulocationid  = 74);
select * from taxi_zone tz  where locationid  = 263;
-- Yorkville West
```

### Question 7

terraform init, terraform apply -auto-approve, terraform destroy
