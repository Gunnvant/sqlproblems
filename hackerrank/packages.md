You are given three tables: Students, Friends and Packages. Students contains two columns: ID and Name. Friends contains two columns: ID and Friend_ID (ID of the ONLY best friend). Packages contains two columns: ID and Salary (offered salary in $ thousands per month).

Write a query to output the names of those students whose best friends got offered a higher salary than them. Names must be ordered by the salary amount offered to the best friends. It is guaranteed that no two students got same salary offer.

```sql
with 
	t1 as
	(select friends.Id,friends.Friend_Id,
	 packages.id as pkg_id, packages.packages as  self_package
	 from friends
	join packages on friends.Id=packages.Id),
	t2 as 
	(select friends.Id,friends.Friend_Id,
	 packages.id as pkg_id, packages.packages as  frnd_package
	 from friends
	join packages on friends.Friend_Id=packages.Id)
select * from t1
join t2
on t1.Id = t2.Id
join students 
on students.Id=t1.Friend_Id
where t1.self_package<t2.frnd_package;
```
