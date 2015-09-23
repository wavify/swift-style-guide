---
ID: 5185
post_title: Certificate
author: chutima
post_date: 2015-09-23 16:48:37
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5185
published: false
---
Certificate ที่ใช้งานอยู่ในปัจจุบันจะมีสองแบบคือ
<ol>
	<li>Self-sign certificate
<ul>
	<li>ในกรณีที่เราไม่ได้ไปขอ cert จากภายนอกมาใส่ เราจะสร้างและ sign cert แล้วใช้งานเอง</li>
	<li>ถ้าใช้งานจะเด้งถามยืนยันความปลอดภัย</li>
	<li><a href="http://192.168.178.12/wp-content/uploads/2015/09/Screen-Shot-2558-09-23-at-4.30.52-PM.png"><img class="alignnone size-full wp-image-5186" src="http://192.168.178.12/wp-content/uploads/2015/09/Screen-Shot-2558-09-23-at-4.30.52-PM.png" alt="Screen Shot 2558-09-23 at 4.30.52 PM" width="675" height="506" /></a></li>
</ul>
</li>
	<li>Certificate แบบคนอื่น sign</li>
</ol>

<hr />

Certificate List

เราสามารถสร้าง cert ได้ 2 แบบคือ
<ol>
	<li>สร้าง Self-sign cert
<ul>
	<li>เมื่อทำการสร้างแล้วสามารถ apply cert เพื่อใช้งานได้เลย</li>
	<li>หากต้องการให้คนอื่น sign cert ให้ (เพราะไม่อยากให้มีเด้งถามความปลอดภัยเวลาใช้งาน) ทำได้ดังนี้
<ul>
	<li>นำ csr ที่ได้จาก cert ไปขอ sign กับคนอื่น</li>
	<li>เมื่อขอแล้วจะได้ cert และ CA มา</li>
	<li>upload cert &amp; CA ที่ได้มาที่เมนู upload certificate file
<ul>
	<li>เมื่อ upload cert ระบบจทำการ validate cert &amp; CA ก่อนการ</li>
</ul>
</li>
	<li>เวลาใช้งานจะไม่มีเด้งถามความปลอดภัยอีก</li>
</ul>
</li>
	<li>สามารถ regenerate cert ได้
<ul>
	<li>Regenerate cert อย่างเดียว ระบบจะ auto apply ไปเลย</li>
</ul>
</li>
</ul>
</li>
	<li>นำเข้า Cert จากภายนอก
<ul>
	<li>สามารถทำได้สองทางคือ
<ul>
	<li>Import cert file</li>
	<li>Add cert by text</li>
</ul>
</li>
	<li>Cert ที่นำเข้าจากภายนอกนี้จะไม่</li>
</ul>
</li>
</ol>
&nbsp;