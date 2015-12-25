---
ID: 5292
post_title: Share process and Policy
author: chutima
post_date: 2015-12-21 20:16:03
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5292
published: true
---
<div>
<div><b>ระบบ Share</b></div>
<ul>
	<li>ระบบ share คือระบบที่ผู้ใช้งานสามารถแบ่งปัน item ต่างๆในระบบกับเพื่อนได้ เมื่อมีการเปลี่ยนแปลงเกิดขึ้นกับ item คนที่สามารถเข้าถึง item ได้ จะเห็นการเปลี่ยนแปลงนั้นเหมือนกัน</li>
</ul>
<div></div>
<div><b>Item ที่สามารถแบ่งปันได้</b></div>
<ul>
	<li>Task
<ul>
	<li>Subtask ของ task ใดจะถูก share ไปพร้อมกับ task เสมอ โดยมองว่า subtask เป็นส่วนหนึ่งของ task</li>
	<li>Subtask ไม่มี permission ของตัวเอง</li>
	<li>สิทธิ์ edit ของ task แม่ จะทำให้สามารถแก้ไข และเพิ่ม/ลบ subtask ได้</li>
</ul>
</li>
	<li>Category
<ul>
	<li>State ของ category จะถูก share ไปพร้อมกันกับ category เสมอ โดยมองว่า state เป็นส่วนหนึ่งของ category</li>
	<li>State ไม่มี permission ของตัวเอง</li>
	<li>สิทธิ์ edit ของ category จะทำให้สามารถแก้ไข และเพิ่ม/ลบ state ได้</li>
	<li>เมื่อทำการ share category, task ที่อยู่ใต้ category นั้นจะถูก share ไปด้วย
<ul>
	<li>เว้นแต่กรณีที่ผู้ใช้ไม่มีสิทธิ์ share task ผลจะเป็นว่า task ก้อนนั้นจะไม่ถูก share ไปด้วย</li>
</ul>
</li>
</ul>
</li>
	<li>Event
<ul>
	<li>Recurrence event จะตามไปด้วย*</li>
</ul>
</li>
	<li>Calendar
<ul>
	<li>เมื่อทำการ share calendar, event ที่อยู่ใต้ calendar นั้นจะถูก share ไปด้วย
<ul>
	<li>เว้นแต่กรณีที่ผู้ใช้ไม่มีสิทธิ์ share event ผลจะเป็นว่า event ก้อนนั้นจะไม่ถูก share ไปด้วย</li>
</ul>
</li>
</ul>
</li>
</ul>
<div></div>
<div><b>Permission</b></div>
<ul>
	<li>ผู้ใช้สามารถกำหนดสิทธิ์การเข้าถึง item ของเพื่อนได้ โดยการกำหนด permission ในการเข้าถึง ซึ่งสามารถกำหนดได้ ทั้งจังหวะที่ share ของให้เพื่อน และหลังจาก share ให้เพื่อนไปแล้ว</li>
	<li>Permission จะถูกเก็บเป็น bit string ซึ่งจริงๆเก็บเป็น int ตัวนึง</li>
	<li>Permission object จะมีหน้าตาดังนี้
<ul>
	<li>Key: username</li>
	<li>Value: policy (int)</li>
</ul>
</li>
	<li>Permission ที่ใช้งาน
<ul>
	<li>Read
<ul>
	<li>0 (CLPolicyRead)</li>
</ul>
</li>
	<li>Write
<ul>
	<li>Update item data</li>
	<li>Update subitem data
<ul>
	<li>Task &gt; subtask (add/reorder/delete)</li>
	<li>Category &gt; state (add/reorder/delete)</li>
</ul>
</li>
	<li>1 (CLPolicyEditData)</li>
</ul>
</li>
	<li>Share
<ul>
	<li>Share item</li>
	<li>Edit permission</li>
	<li>3 (CLPolicyCanShare)</li>
	<li>8 (CLPolicyUnshareData)</li>
	<li>10 (CLPolicyCanShareClone)</li>
	<li>11 (CLPolicyEditPolicy)</li>
</ul>
</li>
	<li>Delete
<ul>
	<li>Delete item</li>
	<li>7 (CLPolicyDeleteData)</li>
</ul>
</li>
</ul>
</li>
	<li>การแก้ไข permission จะต้องหา diff แล้ว save เฉพาะการเปลี่ยนแปลง permission เท่านั้น ห้าม save ทับ</li>
	<li>Default permission
<ul>
	<li>เป็น permission เบื้องต้นในการ share</li>
	<li>ไม่ว่าจะ share ด้วยทางใด เช่นกด share ตรงๆ หรือว่า share ผ่านทางการเซต assignee, ui จะ auto set permission ในการ share เป็น default permission เสมอ ซึ่งถ้า user อยากได้ permission แบบอื่น ก็กดแก้ไขได้</li>
</ul>
</li>
</ul>
<div></div>
<div><b>File ที่เกี่ยวข้อง</b></div>
<ul>
	<li>sharable.js (crossweb/sdk/Web/client/js/models/sharable.js)
<ul>
	<li>Item ที่สามารถ share ได้จะ extend ต่อจาก model นี้</li>
	<li>Method ที่เกี่ยวข้องกับ permission ของ model จะอยู่ใน class นี้</li>
</ul>
</li>
	<li>detail-view.js (crossweb/sdk/Web/client/js/views/modal/detail-view.js)
<ul>
	<li>คุม permission ของหน้า item detail view ทั้งของ container model (category/calendar) และของ item model (task/event)</li>
</ul>
</li>
	<li>item-detail-view.js (crossweb/sdk/Web/client/js/views/modal/item-detail-view.js)
<ul>
	<li>คุม permission ของหน้า item detail view ทั้งของ item model (task/event)</li>
</ul>
</li>
	<li>นอกจากนี้ยังมีกระจายอยู่ที่จุดอื่นๆอีก เช่นส่วนที่เป็น centre.js (crossweb/todo/client/todo/js/views/center/center.js) ที่ต้องคอย hide/show ปุ่ม add task กรณีที่ category นั้นเป็น read-only เป็นต้น</li>
</ul>
</div>