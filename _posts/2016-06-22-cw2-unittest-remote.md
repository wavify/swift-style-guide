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
1. เปิดเครื่อง 10.10.5.141
- การเปิด
1. open Browser and ไปที่ 10.10.5.245/ui
2. login ด้วย user: root password: password
3. เปิดเครื่อง Freebsd10.2_141
2. ssh เข้าเครื่อง 10.10.5.141 user root
- ssh opal@10.10.5.141
- password: "1opal;"
- su
- password: "root"
3. รัน script ที่โฟลเดอร์ script ใน directory cw2
- cd /usr/home/opal/project/cw2/scripts
- checkout branch / pull commit ที่ต้องการ
./testCW2.sh -orientp 772A6E0DD76A6C92E6C45376F16495AB03A01AD34B2D9C8610ED5BA8F53BBD4D