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
