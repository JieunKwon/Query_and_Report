#  SQL Query and Report

@ MS-SQL 2017 , MS Report Builder 2016
 
<b> Objective </b>

  -Understanding Database Structure 
  -Creating Queries (select statement, joins, grouping) 
  -Report Building using MS Report Builder 

<b>Table Structure </b>

<image src='tables.JPG' width='600px'>
 
 
<b>Queries</b>

/*Show SalesPerson with their full name and Quota and Territory*/

     select 
       sp.BusinessEntityID as EntityID, 
       p.FirstName, 
       p.MiddleName, 
       p.LastName,
       sp.SalesQuota,
      (select st.name 
       from Sales.SalesTerritory st
       where sp.TerritoryID = st.TerritoryID) 
       as "Territory Name"
     from 
       Sales.SalesPerson sp, Person.Person p
     where 
       sp.BusinessEntityID = p.BusinessEntityID
     Order by 
       "Territory Name", p.FirstName;

Table report
