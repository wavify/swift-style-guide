---
ID: 5401
post_title: CW2 UnitTest (Remote)
author: tinnapan siripanparwan
post_date: 2016-06-22 04:35:16
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5401
published: true
---

Step
&nbsp;&nbsp;&nbsp;&nbsp;1. เปิดเครื่อง 10.10.5.141
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- การเปิด
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. open Browser and ไปที่ 10.10.5.245/ui
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. login ด้วย user: root password: password
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3. เปิดเครื่อง Freebsd10.2_141
&nbsp;&nbsp;&nbsp;&nbsp;2. ssh เข้าเครื่อง 10.10.5.141 user root
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ssh opal@10.10.5.141
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- password: "1opal;"
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- su
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- password: "root"
&nbsp;&nbsp;&nbsp;&nbsp;3. รัน script ที่โฟลเดอร์ script ใน directory cw2
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- cd /usr/home/opal/project/cw2/scripts
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- checkout branch / pull commit ที่ต้องการ
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;./testCW2.sh -d transport --noshadow -orientp 772A6E0DD76A6C92E6C45376F16495AB03A01AD34B2D9C8610ED5BA8F53BBD4D
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ต้องใส่ -d transport --noshadow ก่อนเนื่องจากตอนนี้รัน shadow บน freebsd แล้วเมมพุ่ง (แต่ถ้าอยากลองให้เมมพุ่งก็ไม่ต้องใส่)