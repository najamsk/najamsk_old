---
layout: post
title: Sql Data Srouce Control Inserting Data Into Database
date: 2008-07-17 05:07
comments: true
categories:
- ado.net
- c#
- asp.net
---
hey guyz how are you ??

Me back with my sqldatasource  series. Today i will show you how to fire insert query using sqldatasource control into code behind i am using c#.

Below is the sample code UserID is the parameter passing into a function as an argument.

{% codeblock lang:c# %}
DateTime Entrydate = DateTime.Today;
SqlDataSource myDbSource = new SqlDataSource();
myDbSource.ConnectionString = ConfigurationManager.ConnectionStrings["ConnectionString"].ConnectionString;
myDbSource.InsertCommand = "insert into tbl_invoices (user,Entrydate) values (" + UserID + ",'" + Entrydate + "')";
myDbSource.ProviderName = "System.Data.SqlClient";
myDbSource.Insert();

myDbSource.SelectCommand = "SELECT IDENT_CURRENT('tbl_invoices')";
DataView dv = (DataView)myDbSource.Select(new DataSourceSelectArguments());
DataTable dt = dv.Table;
string invNumber = dt.Rows[0][0].ToString();
return invNumber.ToString();
//return string.Empty;
{% endcodeblock %}

Code above is very simple what it does simple take UserID as an argument and then insert a new record into tbl_invoices table and then after it i am firing a select statement that returns the latest ID into tbl_invoices table. SELECT IDENT_CURRENT('table name') return the id of the last record inserted into the table.

Happy coding bye
