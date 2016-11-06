1) Реализованный алгоритм имеет сложность = o(n) и использует дополнительно ~k*n памяти
2) 
 select s.ProductId, count(*) as cnt
 from Sales as s
 inner join (
	select CustomerId, min(DateCreated) as DateCreated
	from Sales as s
	group by CustomerId, DateCreated
 ) as s2 on s.CustomerId = s2.CustomerId and s.DateCreated = s2.DateCreated
 group by s.ProductId
 order by cnt desc
