---
ID: 5176
post_title: Integration Setting
author: chutima
post_date: 2015-09-22 17:25:31
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5176
published: true
---
ในการ integrate ระบบข้างนอกกับ Crossflow package service จำเป็นที่จะต้องใช้ข้อมูลดังต่อไปนี้
<ol>
	<li>Service Address
<ul>
	<li>เมื่อการสั่งซื้อสำเร็จ ระบบจะส่งข้อมูลการซื้อขายกลับไปให้ระบบของ service provider (sp) ผ่านทาง service address ที่ sp กำหนดไว้แล้ว</li>
	<li>Service address นี้เป็น attribute หนึ่งเก็บอยู่ใน ldap</li>
	<li>หากไม่มี service address เมื่อกดสั่งซื้อ package ที่หน้า package จะมี alert ขึ้นว่า fail</li>
	<li>Sp สามารถกำหนด service address ได้ที่ Package service &gt; License management &gt; Integration Setting &gt; Service Address</li>
</ul>
</li>
	<li>Public Key
<ul>
	<li>เพื่อความปลอดภัยของระบบ การคุยกันระหว่าง Crossflow service กับ service ของ sp จะถูก encrypt ด้วย key</li>
	<li>ระบบ key จะประกอบด้วย key 2 ตัวคือ private key (ซึ่งเราจะเก็บไว้) และ public key</li>
	<li>Sp จะต้องนำ public key ไปใช้งาน (ใช้ในการ encrypt ข้อมูลก่อนส่งมาหาเรา และ decrpyt ข้อมูลที่เราส่งไปให้)</li>
	<li>Sp สามารถดู public key ของตัวเองได้ที่ Package service &gt; License management &gt; Integration Setting &gt; Public Key</li>
	<li>Sp สามารถ generate public key ใหม่ได้ที่ Package service &gt; License management &gt; Integration Setting &gt; Public Key</li>
	<li>เมื่อ generate key ใหม่แล้ว key เก่าจะไม่สามารถใช้งานได้อีกต่อไป</li>
</ul>
</li>
	<li>Code integration
<ul>
	<li>การ integration กับระบบของเรามีสองแบบคือ redirect link และ snippet</li>
	<li>Sp สามารถเลือก integration แบบใดก็ได้ และสามารถใช้ทั้งสองแบบได้พร้อมกัน</li>
	<li>Redirect link เป็นการ integrate โดยการนำ package list link ไปใส่ตามที่ sp ต้องการ เมื่อลูกค้ากดซื้อ package browser จะทำการ redirect มายัง Crossflow service แล้วแสดงหน้า package list</li>
	<li>Snippet เป็นการ integrate โดยการนำ code ของ package list ไปใส่ตามที่ sp ต้องการ เมื่อลูกค้ากดซื้อ package ระบบจะแสดง package list ในหน้าของ sp เลย โดยไม่จำเป็นต้อง redirect มายัง Crossflow service</li>
	<li>Sp สามารถดูตัวอย่าง link และ code ที่ใช้ในการ integration ได้ที่ Sp สามารถดู public key ของตัวเองได้ที่ Package service &gt; License management &gt; Integration Setting &gt; Integration Guideline</li>
</ul>
</li>
</ol>