---
ID: 5185
post_title: Certificate
author: chutima
post_date: 2015-09-23 17:04:07
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
	<li><a href="http://192.168.178.12/wp-content/uploads/2015/09/Screen-Shot-2558-09-23-at-4.52.08-PM.png"><img class="alignnone size-full wp-image-5189" src="http://192.168.178.12/wp-content/uploads/2015/09/Screen-Shot-2558-09-23-at-4.52.08-PM.png" alt="Screen Shot 2558-09-23 at 4.52.08 PM" width="86" height="47" /></a><a href="http://192.168.178.12/wp-content/uploads/2015/09/Screen-Shot-2558-09-23-at-4.30.52-PM.png"><img class="alignnone size-full wp-image-5186" src="http://192.168.178.12/wp-content/uploads/2015/09/Screen-Shot-2558-09-23-at-4.30.52-PM.png" alt="Screen Shot 2558-09-23 at 4.30.52 PM" width="675" height="506" /></a></li>
</ul>
</li>
	<li>Certificate แบบคนอื่น sign
<ul>
	<li>ไม่มีเด้งถามความปลอดภัย ถ้าเข้าเวปจะเป็นสีเขียวสวยๆ</li>
	<li><a href="http://192.168.178.12/wp-content/uploads/2015/09/Screen-Shot-2558-09-23-at-4.52.37-PM.png"><img class="alignnone size-full wp-image-5188" src="http://192.168.178.12/wp-content/uploads/2015/09/Screen-Shot-2558-09-23-at-4.52.37-PM.png" alt="Screen Shot 2558-09-23 at 4.52.37 PM" width="87" height="50" /></a></li>
</ul>
</li>
</ol>

<hr />

<strong>Certificate</strong>

เราสามารถสร้าง cert ได้ 2 แบบคือ
<ol>
	<li>สร้าง Self-sign cert
<ul>
	<li>เมื่อทำการสร้างแล้วจะได้ self-sign cert มา และสามารถ apply cert เพื่อใช้งานได้เลย</li>
	<li>เมื่อสร้าง cert แล้วจะได้
<ul>
	<li>Key</li>
	<li>CSR</li>
</ul>
</li>
	<li>หากต้องการให้คนอื่น sign cert ให้ (เพราะไม่อยากให้มีเด้งถามความปลอดภัยเวลาใช้งาน) ทำได้ดังนี้
<ul>
	<li>นำCSR ที่ได้จาก cert ไปขอ sign กับคนอื่น</li>
	<li>เมื่อขอแล้วจะได้ cert และ CA มา</li>
	<li>upload cert &amp; CA ที่ได้มาที่เมนู upload certificate file
<ul>
	<li>เมื่อ upload cert ระบบจะทำการ validate cert &amp; CA ด้วย</li>
</ul>
</li>
	<li>เวลาใช้งานจะไม่มีเด้งถามความปลอดภัยอีก</li>
</ul>
</li>
	<li>สามารถ regenerate cert ได้
<ul>
	<li>Regenerate cert อย่างเดียว ระบบจะ auto apply ไปเลย</li>
	<li>Regenerate ทั key, CSR และ cert ระบบจะ auto apply ไป แต่จะส่งผลให้กลายเป็น self-sign ด้วย
<ul>
	<li>จำเป็นต้องเอา csr ไปขอ cert ใหม่ เพราะ key เปลี่ยน</li>
</ul>
</li>
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
	<li>ไม่มี csr</li>
	<li>ไม่สามารถ regenerate cert ได้</li>
	<li>ยังสามารถ update certificate ได้อยู่</li>
</ul>
</li>
</ol>
&nbsp;