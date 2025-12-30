# Sql-Practice-Sets
<img width="678" height="480" alt="image" src="https://github.com/user-attachments/assets/2c1bba60-03e8-4854-9c23-fe019b7b7da1" />
<img width="673" height="807" alt="image" src="https://github.com/user-attachments/assets/9abab017-6e7e-47a5-8804-d86c3d83de4e" />

## Solution
select 
P.product_id,
P.product_name
from product P 
inner join sales S on P.product_id = S.product_id 
group by 
P.product_id, P.product_name
having 
Min(S.sale_date)>= '2019-01-01'
and Max(S.sale_date)<= '2019-03-31';

<img width="690" height="775" alt="image" src="https://github.com/user-attachments/assets/9919e690-32cd-48af-9a60-b5b20f529a2f" />

## Solution
select distinct
A.author_id as ID
From Views A
inner join Views B on 
A.author_id = B.viewer_id
order by A.author_id;

<img width="618" height="892" alt="image" src="https://github.com/user-attachments/assets/d4c1b3b7-b9a4-42d1-8ce7-be65afffc75a" />

## Solution
SELECT 
  ROUND(
    100 * COUNT(CASE WHEN order_date = customer_pref_delivery_date THEN 1 END) / COUNT(*),
    2
  ) AS immediate_percentage
FROM 
  Delivery;

  <img width="496" height="908" alt="image" src="https://github.com/user-attachments/assets/78b3e7d0-5587-4171-9576-f806ad41749d" />

## Solution
select ad_id,
	round(
			case when (sum(action = 'Clicked') + sum(action = 'Viewed')) = 0 then 0
            else (sum(action = 'Clicked') / (sum(action = 'Clicked') + sum(action = 'Viewed'))) * 100
            end, 2) as ctr
from Ads
where action in ('Clicked', 'Viewed')
group by ad_id
union all
select ad_id, 0.00 as ctr
from Ads
where ad_id not in
	(select ad_id from Ads where action in ('Clicked', 'Viewed'))
group by ad_id
order by ad_id asc, ctr desc;

<img width="593" height="858" alt="image" src="https://github.com/user-attachments/assets/09a15eb9-adbd-43d9-b967-8d8892c3ac54" />

## Solution
select a.employee_id, count(b.employee_id) as team_size
from Employee a
left join Employee b on a.team_id = b.team_id
group by employee_id;

<img width="613" height="898" alt="image" src="https://github.com/user-attachments/assets/a3aaf5f4-4a3b-4509-8e2d-0ad042d35b57" />
<img width="648" height="742" alt="image" src="https://github.com/user-attachments/assets/45d732a2-a8ee-441b-b99a-a0aa909c8503" />

## Solution
select C.country_name,
case when avg(W.weather_state) <= 15 then 'Cold'
	 when avg(W.weather_state) >= 25 then 'Hot'
     else 'Warm' 
     end as weather_type
from Countries C join Weather W on
C.country_id = W.country_id
where W.day >= '2019-11-01' and W.day < '2019-12-01'
group by C.country_name order by C.country_name desc;

<img width="610" height="758" alt="image" src="https://github.com/user-attachments/assets/f760e305-764a-4ea4-b02f-c40949179ce3" />
<img width="542" height="318" alt="image" src="https://github.com/user-attachments/assets/b802daed-70a0-47f5-b8a3-06dc3c422c2f" />

## Solution
select P.product_id, 
Round(sum(U.units * P.price)/sum(U.units),2) as average_price
from price P join UnitsSold U on
P.product_id = U.product_id
and U.purchase_date between P.start_date and P.end_date
group by P.product_id;

<img width="575" height="562" alt="image" src="https://github.com/user-attachments/assets/99098f73-2382-49e4-b164-ee55e12fa375" />
<img width="452" height="130" alt="image" src="https://github.com/user-attachments/assets/737e5cd2-3a61-4df8-bf6f-72e77616eef2" />

## Solution
select player_id,
min(event_date) as first_login
from Activity
group by player_id;

<img width="662" height="753" alt="image" src="https://github.com/user-attachments/assets/e38cc85f-b4a9-4c52-b0a6-2a9e9d1d2311" />

## Solution
select player_id, device_id
from Activity
where (player_id, event_date) in (
	select player_id,
    min(event_date)
    from Activity
	group by player_id
    );

<img width="473" height="576" alt="image" src="https://github.com/user-attachments/assets/b8687d69-f5c3-45b4-b696-c4d500979803" />
<img width="407" height="411" alt="image" src="https://github.com/user-attachments/assets/96d1dbe7-41fb-4b3b-8922-053afd33ca95" />

## Solution
select P.product_name,
sum(O.unit) as Unit
from Products P join Orderss O on
P.product_id = O.product_id
where O.order_date >= '2020-02-01' and O.order_date < '2020-03-01'
group by P.product_name
having sum(O.unit) >= 100;

<img width="547" height="322" alt="image" src="https://github.com/user-attachments/assets/e107dac5-a784-4d0a-bf5f-7d0c8fc97c5b" />
<img width="391" height="547" alt="image" src="https://github.com/user-attachments/assets/96a4a2ed-6092-48bd-86d3-9e6da90ecc99" />

## Solution
SELECT
  user_id,
  name,
  mail
FROM
  Users
WHERE
  mail REGEXP '^[A-Za-z][A-Za-z0-9_.-]*@leetcode\\.com$';

#### REGEXP checks if the email matches the pattern for a valid email.
#### ^[A-Za-z] ensures the prefix starts with a letter.
#### [A-Za-z0-9_.-]* allows letters, digits, underscore (_), period (.), and dash (-) in the prefix after the first character.
#### @leetcode\.com$ guarantees the domain is exactly @leetcode.com.

<img width="551" height="817" alt="image" src="https://github.com/user-attachments/assets/2f2ae0e1-e4cb-4126-bcea-f65fb401f82d" />
<img width="443" height="813" alt="image" src="https://github.com/user-attachments/assets/76c5c599-20b4-49ce-bf8b-4e96b4aceb39" />

## Solution
select C.customer_id, C.name from Customers C 
join Orderz O on C.customer_id = O.customer_id
join Productss P on O.product_id = P.product_id
where O.order_date >= '2020-06-01' and O.order_date < '2020-08-01'
GROUP BY
  c.customer_id,
  c.name
HAVING
  SUM(CASE WHEN MONTH(o.order_date) = 6 THEN o.quantity * p.price ELSE 0 END) >= 100
  AND
  SUM(CASE WHEN MONTH(o.order_date) = 7 THEN o.quantity * p.price ELSE 0 END) >= 100;

<img width="647" height="477" alt="image" src="https://github.com/user-attachments/assets/79560602-bc9f-434a-a242-0292d39d03fe" />
<img width="632" height="857" alt="image" src="https://github.com/user-attachments/assets/e3824fcc-8c01-4173-8ce4-e8c0246a2738" />

## Solution
select distinct C.title from Content C 
join TVProgram T on C.content_id = T.content_id
where T.program_date >= '2020-06-01' and T.program_date < '2020-07-01' 
and C.Kids_content = 'Y';

30.
<img width="572" height="693" alt="image" src="https://github.com/user-attachments/assets/e9ab512f-d40b-46d8-aaff-f13027e69803" />
<img width="566" height="480" alt="image" src="https://github.com/user-attachments/assets/8ed508fb-4989-4929-903c-3daabf53f6e6" />
