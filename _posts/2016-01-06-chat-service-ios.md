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
<span style="color: #008080;"><code>git submodule update --init --recursive</code></span></li>
	<li>Transport Service
<ol>
	<li>สร้าง folder build สำหรับ run make &amp; run cmake
<span style="color: #008080;"><code>cd cw2/datamodel/transportlayer/
mkdir build
cd build
cmake ..
make</code></span></li>
	<li>แก้ config ip, portได้ใน Folder config โดย config file ที่ใช้ปัจจุบันมีสามประเภท คือ
<strong>router</strong> (router.conf) ใช้ router3.conf เมื่อต้องการใช้ shadow ด้วย* router0.conf หากไม่ต้องการ shadow
<strong>client</strong> (config.conf) เมื่อต้องการทดลองใช้ client ส่งข้อความ
<strong>shadow</strong> (ghost.conf)
*หากไม่มี shadow จะส่งหาคนที่ offline ไม่ได้</li>
	<li>ทำการรัน service
<span style="color: #008080;"><code> ./router_client.o</code></span></li>
	<li>เลือกประเภทที่จะรัน
<code><span style="color: #008080;">Select Router or Client</span>
<span style="color: #008080;"> 1: Router</span>
<span style="color: #008080;"> 2: Client</span>
<span style="color: #008080;"> 3: Shadow</span>
<span style="color: #008080;"> 0: Exit</span>
</code></li>
	<li>ใส่path config
<span style="color: #008080;"><code>Select Router or Client
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
tcp://192.168.180.220:5554</code></span></li>
	<li>หากต้องการ gen user ลงใน database ให้ไปที่ cw2/datamodel/transportlayer/ แล้วใช้คำสั่งนี้
<span style="color: #008080;"><code>./adduser.sh build/Router5550.db</code></span></li>
</ol>
</li>
	<li>เปิด Authen
<ol>
	<li>run script ldap
<span style="color: #008080;"><code><span style="color: #008080;">cd cw2/datamodel/transportlayer/authentication/</span>
./script.sh start 0</code></span></li>
	<li>คำสั่ง script อื่นๆ
<span style="color: #008080;"><code>./script.sh adduser 0
./script.sh removeuser 0
./script.sh stop 0</code></span></li>
</ol>
</li>
	<li>Run friend Service
<ol>
	<li>ไปยังที่folderที่ลงorientไว้แล้วใช้คำสั่งดังนี้
<span style="color: #008080;"><code>cd orientdb-community-2.1.1/bin/
./server.sh</code></span></li>
	<li>แก้ config ip, portได้ใน Folder config โดย config file ที่ใช้คือ local0.conf *ใส่port/ipห้ามมีช่องว่างหลัง=</li>
	<li>สร้าง folder build สำหรับ run make &amp; run cmake
<span style="color: #008080;"><code>cd cw2/CWFriendlist/
mkdir build
cd build
cmake ..
make</code></span></li>
	<li>ทำการรัน service
<span style="color: #008080;"><code>./service.out local0</code></span></li>
	<li>ทำการรัน friend node
<span style="color: #008080;"><code>node frnode</code></span>
*control+c 2ครั้งเมื่อต้องการออก</li>
</ol>
</li>
</ol>