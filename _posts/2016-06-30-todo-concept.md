---
ID: 5413
post_title: Todo Concept
author: tanate.me
post_date: 2016-06-30 15:47:54
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5413
published: true
---
<strong>การอัพเดท unread category icon (จุดแดง)</strong>

<img class="alignnone size-full wp-image-5414" src="http://192.168.178.12/wp-content/uploads/2016/06/Screen-Shot-2559-06-30-at-3.32.46-PM.png" alt="Screen Shot 2559-06-30 at 3.32.46 PM" width="271" height="34" />
<ul>
	<li>Attributes ที่เกี่ยวข้อง
<ul>
	<li>_isRead ใน categoryModel</li>
	<li>_isChildrenRead ใน categoryModel</li>
	<li>_unreadCount หรือ _unreadUndoneCount ใน categoryModel และ customQueryModel (* attribute _unreadCount จะถูกใช้เมื่อผู้ใช้งานเซ็ทค่าที่เมนู Setting &gt; To Do Display &gt; Show Done Task เป็น Enable ส่วน_unreadUndoneCount จะตรงข้ามกัน)</li>
</ul>
</li>
	<li>_isRead (Boolean) เป็น attribute ที่บอกว่า category นั้นๆ ได้ถูกเปิดดูโดยผู้ใช้งานแล้วหรือยัง</li>
	<li>_isChildrenRead (Boolean) เป็น attribute ที่บอกว่า tasks ทั้งหมดใต้ category นั้นๆ ได้ถูกเปิดอ่านหมดแล้วหรือยัง</li>
	<li>_unreadCount และ _unreadUndoneCount (Int)</li>
</ul>