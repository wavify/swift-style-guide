---
ID: 5304
post_title: Calendar Concept
author: chutima
post_date: 2015-12-25 17:49:19
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5304
published: true
---
<div><b>Calendar</b></div>
<ul>
	<li>Calendar ที่เรา support ในตอนนี้มีเพียง 1 รูปแบบคือ .ics
<ul>
	<li>เวลา import หรือ export จะอยู่ในรูปแบบ .ics</li>
</ul>
</li>
	<li>Calendar ประกอบไปด้วย event ซึ่งทั้ง calendar และ event จะเป็นไปตามที่ RFC ที่กำหนด</li>
</ul>
<div></div>
<div><b>Private &amp; Public Calendar</b></div>
<ul>
	<li>เป็น concept ที่ใช้ในการแบ่งปัน calendar กับผู้อื่น</li>
	<li>ทั้งสองแบบเป็นการ access แบบได้เป็น ics ไฟล์ไป</li>
	<li>Calendar หนึ่งๆจะมี private และ public calendar พร้อมกันได้ ต่างคนต่างทำงาน ไม่เกี่ยวข้องกัน</li>
	<li>Private calendar
<ul>
	<li>คนอื่นจะสามารถ access calendar นี้ได้ผ่าน private link ที่กำหนด</li>
	<li>เมื่อมีการตั้ง private link ใหม่ link อันเก่าจะใช้งานไม่ได้อีก</li>
	<li>Implement โดยการใส่ key แนบท้าย link ไว้ เมื่อมีการ access calendar ผ่าน link จะนำ key ไปตรวจสอบกับ key ที่เก็บอยู่ที่ calendar model ถ้าตรงกันถึงจะอนุญาติให้ access ได้</li>
</ul>
</li>
	<li>Public calendar
<ul>
	<li>เป็นการกำหนดสิทธิ์ในการ access calendar ของ public link</li>
	<li>แบ่งออกเป็น 3 แบบคือ
<ul>
	<li>Private ไม่มีอนุญาติให้ access calendar ผ่านทาง public link
<ul>
	<li>กรณีที่เคยเปิดให้ access ได้ แล้วปิดการ access แม้จะมี public link ก็จะไม่สามารถ access ได้</li>
</ul>
</li>
	<li>Free-busy อนุญาติให้ access calendar ผ่านทาง public link แต่จะแสดงแค่ free-busy
<ul>
	<li>Free-busy คือคนนอกจะเห็นแค่ว่าช่วงเวลาที่มี event นั้นเป็นช่วงเวลาที่เราไม่ว่าง (busy) แต่จะไม่เห็นรายละเอียดของ event</li>
</ul>
</li>
	<li>Detail อนุญาติให้ access calendar ผ่านทาง public link โดยแสดงรายละเอียดของ event ด้วย
<ul>
	<li>รายละเอียดนี้ไม่รวมถึง attachment, location</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
<div></div>
<div><b>Recurrence event</b></div>
<ul>
	<li>ในกรณีที่ต้องการสร้าง event ที่เกิดขึ้นซ้ำๆ เช่น วันเกิด การเรียนภาษาอังกฤษทุกวันศุกร์ เราสามารถใช้ recurrence event ช่วยได้</li>
	<li>สร้าง recurrence event ได้โดยการกำหนด recurrence rule ซึ่งจะแบ่งออกเป็น 2 ส่วน (crossweb/sdk/Web/client/js/views/modal/info/repeat-detail.js)
<ul>
	<li>Repeat เป็นส่วนของ rule ที่กำหนดการ repeat ว่าจะ repeat แบบไหน
<ul>
	<li>freq (ตัวเลขตาม RFC กำหนด): กำหนดว่า repeat ทุกๆอะไร เช่น ทุกวัน ทุกเดือน ทุกปี</li>
	<li>interval (int): กำหนดว่าทุกๆเท่าไร เช่น <b>2</b> วัน, <b>3</b> อาทิตย์</li>
	<li>ถ้า repeat by week
<ul>
	<li>byDay (array ของ ตัวเลขตาม RFC กำหนด): หมายถึงกำหนดว่าเกิดขึ้น ทุกๆวันอะไร เช่น เกิดขึ้นทุกๆวันจันทร์และวันพุธของสัปดาห์</li>
</ul>
</li>
	<li>ถ้า repeat by month
<ul>
	<li>byMonthDay (array ของ int): กำหนดว่าเกิดขึ้นทุกวันที่เท่าไรของเดือน เช่น วันที่ <b>10 และ 15</b> ของเดือน</li>
	<li>byDay (array ของ ตัวเลขตาม RFC กำหนด): หมายถึงกำหนดว่าเกิดขึ้น ทุกๆวันอะไร เช่น เกิดขึ้นทุกๆวันจันทร์และวันพุธ</li>
	<li>bySetPos (int): ใช้ร่วมกับ byDay ในการกำหนดว่า จะให้เกิดขึ้นทุกๆวัน (byDay) ที่ เท่าไรของเดือน เช่น เกิดขึ้นทุกๆวันจันทร์และพุธที่สองของเดือน</li>
</ul>
</li>
	<li>ถ้า repeat by year
<ul>
	<li>byMonth (ตัวเลขตาม RFC กำหนด): เกิดขึ้นทุกๆเดือนอะไร</li>
	<li>byDay (array ของ ตัวเลขตาม RFC กำหนด): หมายถึงกำหนดว่าเกิดขึ้น ทุกๆวันอะไร เช่น เกิดขึ้นทุกๆวันจันทร์และวันพุธ</li>
	<li>bySetPos (int): ใช้ร่วมกับ byDay ในการกำหนดว่า จะให้เกิดขึ้นทุกๆวัน (byDay) ที่ เท่าไรของเดือน เช่น เกิดขึ้นทุกๆวันจันทร์และพุธที่สองของเดือน</li>
</ul>
</li>
</ul>
</li>
	<li>Ending กำหนดว่าการ repeat นั้นจะมีการสิ้นสุดหรือไม่
<ul>
	<li>ไม่สิ้นสุด</li>
	<li>count (int): สิ้นสุดเมื่อเกิดไป n ครั้ง</li>
	<li>until (timestamp): สิ้นสุดเมื่อถึงเวลาที่กำหนด</li>
</ul>
</li>
	<li>ส่วนที่เป็น bySetPos ของระบบเรายังไม่สมบูรณ์</li>
</ul>
</li>
	<li>ระบบของเราจะเก็บ event จริงๆแค่ตัวเดียวคือ root event เมื่อจะต้องนำมาแสดง ถึงจะแตก recurrence event ออกมาเพื่อแสดง แต่ไม่ได้เก็บลง db ดังนั้น attribute ต่างๆของ recurrence event จะเป็น attribute ของ root event ทั้งหมด ยกเว้น star/due date และ reminder (ตอนนี้น่าจะยังไม่ได้ทำ แต่จำเป็นต้องเปลี่ยน reminder ตาม start/due ด้วย) ที่เปลี่ยนไปตาม recurrence rule
<ul>
	<li>การเปลี่ยนแปลง data ที่เกิดขึ้น ก็ต้องทำกับ root event แทน เช่น จะแก้ไขชื่อของ event จะต้องไปแก้ไขที่ root event จะแก้ที่ recurrence event แล้ว save ลงไปตรงๆไม่ได้ เพราะด้านหลังไม่มี data ของ recurrence อยู่จริง</li>
	<li>doAction() (crossweb/sdk/Web/client/js/models/event.js)</li>
</ul>
</li>
</ul>
<div></div>
<div><b>Subscribed Calendar</b></div>
<ul>
	<li>เป็น calendar ที่เรา subscribe ไว้ ซึ่งอาจจะเป็น calendar ภายในระบบ หรือ calendar ภายนอกระบบก็ได้</li>
	<li>Link ที่ใช้ subscribed จะต้องเป็น .ics link</li>
	<li>ระบบจะทำการ fetch data ของ calendar นั้นเพื่อทำการ update ui ทุกๆ 20 นาที (crossweb/calendar/client/calendar/js/views/left/calendarItem.js)</li>
	<li>Subscribed calendar จะมี type เป็น 0</li>
	<li>Event ของ subscribed calendar จะไม่มีอยู่จริงในระบบ แต่จะ generate ขึ้นมา on time ที่ต้องการจะ render
<ul>
	<li>Calendar node เป็นคน generate</li>
	<li>Event object ที่ได้มาจากด้านหลังก็จะไม่เหมือนกับ event object ของ CF ต้องทำการ parse ก่อนใช้งาน
<ul>
	<li>queryItems() (crossweb/sdk/Web/client/js/models/calendar.js)</li>
</ul>
</li>
	<li>เนื่องจากไม่มีอยู่จริงในระบบ event ของ subscribed calendar จึง view ได้อย่างเดียว</li>
</ul>
</li>
</ul>