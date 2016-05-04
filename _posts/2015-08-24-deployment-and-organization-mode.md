---
ID: 5160
post_title: Deployment and Organization Mode
author: chutima
post_date: 2015-08-24 15:46:39
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5160
published: true
---
ในระบบของเรา deployment และ organization จะมี mode ต่างๆดังนี้
<h2>Deployment</h2>
Deployment จะแบ่งออกเป็น 4 ประเภทคือ
<ol>
	<li>Default (mode = 0) จะเป็น cloud deployment หลักของแต่ละระบบ</li>
	<li>Local (mode = 1) เป็น deployment ที่ผูกกันกับเครื่อง local เครื่องอื่นๆ
<ol>
	<li>จะมีสองแบบคือ
<ol>
	<li>แบบ sync กับ cloud
<ul>
	<li>สร้าง org ได้ทั้งแบบ both และ local only</li>
</ul>
</li>
	<li>แบบ ไม่ sync กับ cloud (standalone local only deployment)
<ul>
	<li>สร้าง org แบบ local only ได้อย่างเดียว</li>
</ul>
</li>
</ol>
</li>
	<li>แบบของ deployment กำหนดโดย license</li>
</ol>
</li>
	<li>Public cloud (mode = 2) เป็น cloud deployment เช่นเดียวกัน แต่ไม่ใช่ deployment หลัก</li>
	<li>Stand Alone (mode = 3) เป็น local only คือจะไม่มีการยิงอะไรขึ้นมาบน cloud อีก สร้าง org หรือ set config ที่เครื่องตัวเองได้เลย</li>
</ol>
<ul>
	<li>ในระบบหนึ่งๆจะมี cloud deployment ได้มากกว่าหนึ่ง</li>
	<li>Standalone local only deployment เป็น deployment ที่มี mode เป็น mode แบบไม่ sync data ขึ้น cloud
<ul>
	<li>แต่ในจังหวะแรกที่ทำการติดตั้งระบบ และ drop ship appliance ไปให้ลูกค้าก็ยังต้องต่อกับ cloud เพื่อทำการดึง config อยู่ดี</li>
	<li>เมื่อทำการติดตั้งระบบเรียบร้อยแล้ว จะตัด connection กับ cloud</li>
	<li>เมื่อตัดแล้วจะไม่สามารถต่อกลับขึ้น cloud ได้อีก</li>
</ul>
</li>
	<li>การจะต่อกับ cloud เพื่อ sync จำเป็นต้องทำทั้งเครื่อง ไม่สามารถระบุเป็น per org ได้
<ul>
	<li>ผลคือ ถ้า deployment เป็นแบบ sync กับ cloud และตั้ง org เป็น local only ข้อมูลของ local only org ก็ยังจะ sync ขึ้นไปบน cloud</li>
</ul>
</li>
</ul>
<h2>Organization</h2>
Organization จะแบ่งออกเป็น 4 ประเภทคือ
<ol>
	<li>Local (mode = 1) ใช้ได้แต่ที่ local เท่านั้น</li>
	<li>Cloud (mode = 2) ใช้ได้ที่ cloud เท่านั้น</li>
	<li>Both (mode = 3) ใช้ได้ทั้งที่ cloud และ local</li>
	<li>Public cloud (mode = 5) ใช้ได้ที่ public cloud เท่านั้น (แยก mode ออกจาก cloud only เพื่อ support feature list org บน หน้า um)</li>
</ol>
ตารางแสดงความสัมพันธ์ของ deployment และ organization
<table>
<tbody>
<tr>
<td><strong>Deployment</strong></td>
<td><strong>Organization</strong></td>
</tr>
<tr>
<td>Default</td>
<td>Cloud</td>
</tr>
<tr>
<td>Local</td>
<td>Local หรือ
Both (กรณีที่ deployment มี license failover ด้วย)</td>
</tr>
<tr>
<td>Public cloud</td>
<td>Public cloud</td>
</tr>
</tbody>
</table>
&nbsp;