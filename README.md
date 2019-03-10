#  SQL Query and Report

@ MS-SQL 2017 , MS Report Builder 2016
 
<b> Objective </b>

  -Understanding Database Structure 
  -Creating Queries (select statement, joins, grouping) 
  -Report Building using MS Report Builder 

<b>Table Structure </b>

<image src='tables.JPG' width='600px'>
 
 
<b>Query</b>

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

<b>Table report</b>

<image src='report1.JPG' width='500px'>
 
 <b>Query 2</b>

/*Show Sales Volume of Canada*/

<image src='query2.JPG' width='500px'>      

<b>Table report</b>

<image src='report2.JPG' width='500px'>
