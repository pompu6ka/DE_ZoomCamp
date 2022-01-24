# DE_ZoomCamp_HW_1
Week 1 Homework
-- Question 3: Count records 
select sum(1),count(distinct index)
from public.yellow_taxi_trips
where tpep_pickup_datetime >= date '2021-01-15'
and  tpep_pickup_datetime < date '2021-01-16'

-- Question 4: Largest tip for each day 
select date_trunc('day',tpep_pickup_datetime) max_dt
	, max(tip_amount)
from public.yellow_taxi_trips
group by  date_trunc('day',tpep_pickup_datetime) 
order by 2 desc

-- Question 5: Most popular destination 
select zdo."Zone"
	, sum(1)
from public.yellow_taxi_trips t
join public.zones zpu on t."PULocationID" = zpu."LocationID"
left join public.zones zdo on t."DOLocationID" = zdo."LocationID"
where tpep_pickup_datetime >= date '2021-01-14'
and  tpep_pickup_datetime < date '2021-01-15'
and zpu."Zone" = 'Central Park'
group by zdo."Zone"
order by 2 desc

-- Question 6: Most expensive route
select zpu."Zone"
	, zdo."Zone"
	, avg(total_amount) avg_amount
from public.yellow_taxi_trips t
left join public.zones zpu on t."PULocationID" = zpu."LocationID"
left join public.zones zdo on t."DOLocationID" = zdo."LocationID"
group by zpu."Zone"
	, zdo."Zone"
order by 3 desc	
