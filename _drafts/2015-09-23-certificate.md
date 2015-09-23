---
ID: 5185
post_title: Certificate
author: chutima
post_date: 2015-09-23 16:39:52
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
	<li>เมื่อทำการสร้าง self-sign cert แล้วสามารถ apply cert เพื่อใช้งานได้เลย (โดยปกติ cert ที่สร้างขึ้นด้วยวิธีนี้จะ</li>
	<li>หากต้องการให้คนอื่น sign cert ให้ สามารถ</li>
</ul>
</li>
	<li>นำเข้า Cert จากภายนอก
<ul>
	<li>Import cert file</li>
	<li>Add cert by text</li>
</ul>
</li>
</ol>
&nbsp;