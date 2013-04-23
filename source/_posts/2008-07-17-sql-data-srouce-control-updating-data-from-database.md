---
layout: post
title: Sql Data Srouce Control Updating Data From Database
date: 2008-07-17 05:32
comments: true
categories:
- ado.net
- c#
- asp.net
---
hey guyz finally we have to learn how to update our tables in database so only for you guys here is my sample code

string giftId = GridView1.SelectedRow.Cells[0].Text.ToString(); //getting an id
SqlDataSource myDbSource = new SqlDataSource();
myDbSource.ConnectionString = ConfigurationManager.ConnectionStrings["ConnectionString"].ConnectionString;
//myDbSource.InsertCommand = "update gifts set giftActivate=1 where giftId=" + Entrydate + ")";
myDbSource.UpdateCommand = "update gifts set giftActivate='1' where giftId=" + giftId;
myDbSource.ProviderName = "System.Data.SqlClient";
myDbSource.Update();

Well this code set giftActive flag to 1 for all the rows matched with giftid value.
