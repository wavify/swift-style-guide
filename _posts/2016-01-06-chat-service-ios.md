---
ID: 5315
post_title: 'Chat Service [iOS]'
author: Kanjana Sirinavasatian
post_date: 2016-01-06 11:10:13
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5315
published: true
---
Install 1-5 ตาม link http://192.168.178.12/?p=5207
<ol>
	<li>Clone project from http://192.168.178.10/git/chat</li>
	<li>update submodule
<code>git submodule update --init --recursive</code></li>
	<li>Transport Service
<ol>
	<li>สร้าง folder build สำหรับ run make &amp; run cmake
<code>cd cw2/datamodel/transportlayer/
mkdir build
cd build
cmake ..
make</code></li>
	<li>แก้ config ip, portได้ใน Folder config โดย config file ที่ใช้ปัจจุบันมีสามประเภท คือ
<strong>router</strong> (router.conf) ใช้ router3.conf เมื่อต้องการใช้ shadow ด้วย* router0.conf หากไม่ต้องการ shadow
<strong>client</strong> (config.conf) เมื่อต้องการทดลองใช้ client ส่งข้อความ
<strong>shadow</strong> (ghost.conf)
*หากไม่มี shadow จะส่งหาคนที่ offline ไม่ได้</li>
	<li>ทำการรัน service
<code> ./router_client.o</code></li>
	<li>เลือกประเภทที่จะรัน
<code>Select Router or Client
1: Router
2: Client
3: Shadow
0: Exit
</code></li>
	<li>ใส่path config
<code>Select Router or Client
1: Router
2: Client
3: Shadow
0: Exit
&gt; 1
config file:
&gt; config/router3.conf
Tue Jan 5 17:29:29 2016 [WARN ] HEADER 4.1.3
Tue Jan 5 17:29:29 2016 [WARN ] LIB 4.1.3
[----Router----]
0: Exit
&gt; Public : tcp://192.168.180.220:5500
tcp://192.168.180.220:5554
tcp://192.168.180.220:5554
tcp://192.168.180.220:5554
tcp://192.168.180.220:5554</code></li>
	<li>หากต้องการ gen user ลงใน database ให้ไปที่ cw2/datamodel/transportlayer/ แล้วใช้คำสั่งนี้
<code>./adduser.sh build/Router5550.db</code></li>
</ol>
</li>
	<li>เปิด Authen
<ol>
	<li>run script ldap
<code>cd cw2/datamodel/transportlayer/authentication/
./script.sh start 0</code></li>
	<li>คำสั่ง script อื่นๆ
<code>./script.sh adduser 0
./script.sh removeuser 0
./script.sh stop 0</code></li>
</ol>
</li>
	<li>Run friend Service
<ol>
	<li>ไปยังที่folderที่ลงorientไว้แล้วใช้คำสั่งดังนี้
<code>cd orientdb-community-2.1.1/bin/
./server.sh</code></li>
	<li>แก้ config ip, portได้ใน Folder config โดย config file ที่ใช้คือ local0.conf *ใส่port/ipห้ามมีช่องว่างหลัง=</li>
	<li>สร้าง folder build สำหรับ run make &amp; run cmake
<code>cd cw2/CWFriendlist/
mkdir build
cd build
cmake ..
make</code></li>
	<li>ทำการรัน service
<code>./service.out local0</code></li>
	<li>ทำการรัน friend node
<code>node frnode</code>
*control+c 2ครั้งเมื่อต้องการออก</li>
</ol>
</li>
</ol>