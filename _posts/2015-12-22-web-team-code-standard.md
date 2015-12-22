---
ID: 5296
post_title: '[Web Team] Code Standard'
author: lalanarwon lalanarwon
post_date: 2015-12-22 16:22:09
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5296
published: true
---
<div><b>Variable name</b></div>
<ul>
	<li>CSS
<ul>
	<li>ชื่อเป็นตัวเล็กหมด และแบ่งคำด้วย -</li>
</ul>
</li>
	<li>JavaScript
<ul>
	<li>Camel case</li>
	<li>ชื่อ Class เป็นตัวใหญ่เสมอ</li>
</ul>
</li>
	<li>ชื่อไฟล์ JS / HTML เป็นตัวเล็กให้หมด
<ul>
	<li>แบ่งคำด้วย - ถ้ามีพวก version หรือ extension ให้แบ่งด้วย .</li>
</ul>
</li>
</ul>
<div></div>
<div><b>Double Quote</b></div>
<ul>
	<li>ใช้กับ String ทั้งหมด ถ้าจำเป็นต้องใส่ “ ใน String ให้ใช้ /“ แทน</li>
	<li>tag HTML ทั่วไป</li>
	<li>ถ้ากรณีอื่นๆ ใช้ Single Quote แทนได้</li>
</ul>
<div></div>
<div><b>หลังก่อน/วงเล็บให้เว้นวรรคเสมอ</b></div>
<div>if (true) {</div>
<div>     // do something….</div>
<div>}</div>
<div></div>
<div><b>การใช้ &amp;&amp; กับ cond ยาวๆ</b></div>
<div>if (cond1</div>
<div>     &amp;&amp; cond2) {</div>
<div>     // do something...</div>
<div>}</div>
<div></div>
<div><b>เวลาประกาศ function เว้นวรรค param ด้วย , และ space</b></div>
<div>function (paramA, paramB) {</div>
<div>     // do something...</div>
<div>}</div>
<div></div>
<div>// Google ไม่แนะนำให้ใช้แบบนี้</div>
<div>function name (paramA, paramB) {</div>
<div>
<div>     // do something...</div>
</div>
<div>}</div>
<div></div>
<div>// Google แนะนำให้ใช้แบบนี้</div>
<div>var name = function (paramA, paramB) {</div>
<div>
<div>
<div>     // do something...</div>
</div>
</div>
<div>}</div>
<div></div>
<div><b>เวลาประกาศ Obj</b></div>
<div>var obj = {</div>
<div>     attr1: xxx,</div>
<div>     attr2: yyy</div>
<div>};</div>
<div></div>
<div><b>Inline Condition</b> เว้นวรรคให้หมด</div>
<div>var isTrue ? true : false;</div>
<div></div>
<div>for (var i = 0; i &lt; 10; i++) { // do something สั้นกว่า 80… }</div>
<div></div>
<div>for (var i = 0; i &lt; 10; i++) {</div>
<div>     // do something ยาวกว่า 80…</div>
<div>}</div>
<div></div>
<div><b>กรณีเคส {} ซ้อนกันเยอะมากๆ</b> ให้เคาะเว้นบรรทัด</div>
<div></div>
<div><b>การประกาศตัวแปร</b></div>
<div>var a, b;</div>
<div>var c = 0;</div>
<div></div>
<div><b>Array</b></div>
<div>var array = [a, b, c, d];</div>
<div>var array = [{</div>
<div>     a1: 0,</div>
<div>     a2: 0,</div>
<div>     a3: 0,</div>
<div>     a4: 0</div>
<div>}, {</div>
<div>     b1: 0,</div>
<div>     b2: 0,</div>
<div>     b3: 0,</div>
<div>     b4: 0</div>
<div>}, {</div>
<div>     c1: 0,</div>
<div>     c2: 0,</div>
<div>     c3: 0,</div>
<div>     c4: 0</div>
<div>}];</div>
<div></div>