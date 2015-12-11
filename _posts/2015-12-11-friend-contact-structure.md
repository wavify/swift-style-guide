---
ID: 5258
post_title: 'Friend &#038; Contact Structure'
author: lalanarwon lalanarwon
post_date: 2015-12-11 17:59:53
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5258
published: true
---
<strong>Friend</strong> จะแบ่งเป็น 3 ส่วนหลัก
<ul>
	<li>Controller
<ul>
	<li>เป็นคนคุมการทำงานของ view และ model ทั้งหมด, view จะไม่สามารถคุม model ตรงๆได้ ต้องทำผ่าน controller</li>
	<li>view กับ controller เรียกกันด้วยการใช้ event trigger function ที่ต้องการ</li>
</ul>
</li>
	<li>View
<ul>
	<li>เน้นเอา model มา render</li>
</ul>
</li>
	<li>Collection &amp; Model</li>
</ul>
<img class="alignnone size-full wp-image-5259" src="http://192.168.178.12/wp-content/uploads/2015/12/Friend-Contact-Diagram1.png" alt="Friend &amp; Contact Diagram1" width="821" height="1124" />

<strong>Contact </strong>จะมีโครงสร้างคล้าย Todo และแบ่งเป็น 2 ส่วนหลักเหมือนกัน คือ
<ul>
	<li>View</li>
	<li>Collection &amp; Model</li>
</ul>
<img class="alignnone size-full wp-image-5260" src="http://192.168.178.12/wp-content/uploads/2015/12/Friend-Contact-Diagram2.png" alt="Friend &amp; Contact Diagram2" width="821" height="933" />