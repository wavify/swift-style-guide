---
ID: 5397
post_title: CW2 UnitTest (Self Machine)
author: tinnapan siripanparwan
post_date: 2016-06-22 04:33:33
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5397
published: true
---
<strong>Backend required</strong>
<ol>
	<li><a href="http://192.168.178.12/?p=5207">http://192.168.178.12/?p=5207</a>
<ul>
	<li>cmake</li>
	<li>hiredis</li>
	<li>curl</li>
	<li>sqlite</li>
	<li>jansson</li>
	<li>ZMQ + libsodium</li>
</ul>
</li>
	<li><a href="http://192.168.178.12/?p=4869">http://192.168.178.12/?p=4869</a>
<ul>
	<li>Xcode 7.3.1</li>
	<li>Command Line Tools</li>
	<li>BerkeleyDB</li>
	<li>OpenLDAP</li>
	<li>Redis</li>
	<li>OrientDB</li>
	<li>PostgreSQL</li>
</ul>
</li>
</ol>
<strong>Config Service</strong>
<ul>
	<li>OrientDB</li>
	<li>set root password to "1234"
<ol>
	<li>open config file "orientdb-server-config.xml"</li>
	<li>edit line <span style="font-family: Monaco, Consolas, 'Andale Mono', 'DejaVu Sans Mono', monospace; font-size: 13px; font-style: normal; font-weight: normal; line-height: normal;">&lt;user resources="*" password="" name="root"/&gt; </span>to <span style="font-family: Monaco, Consolas, 'Andale Mono', 'DejaVu Sans Mono', monospace; font-size: 13px; font-style: normal; font-weight: normal; line-height: normal;">&lt;user resources="*" password="1234" name="root"/&gt;</span></li>
</ol>
</li>
</ul>
<strong>Step การรัน</strong>
<ol>
	<li>ไม่ต้องเปิด service ของ cw2</li>
	<li>cd crossproject/cw2/scripts</li>
	<li>./testCW2.sh -orientpass "1opal;" -ldapport "8389"
<ul>
<ul>
	<li> Requirements</li>
	<li>[service] orientdb (Datamodel, Friend, Chat)</li>
</ul>
</ul>
จำเป็นต้อง start OrientDB และต้องระบุ option -orientpass "xxxx" ตามหลัง./testCW2.sh ถ้าหาก password ของ OrientDB ที่เปิดไม่ใช่ "1234" (Default)
./testCW2.sh datamodel -orientpass “1opal;”
<ul>
	<li>[service] cassandra (Transport)</li>
	<li>[service] ldap (Friend)

จำเป็นต้อง start ldap และต้องระบุ option -ldapport "xxxx" ตามหลัง./testCW2.sh ถ้าหาก password ของ ldap ที่เปิดไม่ใช่ "389" (Default)
./testCW2.sh friend -orientpass “1opal;” -ldapport "8389"</li>
</ul>
</li>
	<li>ต้องการ test service ไหนให้ระบุ ตามหลัง เช่น "./testCW2.sh datamodel" โดย service ที่มีได้แก่ cw2, cwmq, transport, datamodel, friend, chat
<ul>
	<li>Unit Test CWMQ ( cw2/shared/cwmq/ )</li>
	<li>Unit Test Transport ( cw2/transportlayer )</li>
	<li>Unit Test Datamodel ( cw2/datamodel )</li>
	<li>Unit Test Friend ( cw2/CWFriendlist )</li>
	<li>Unit Test Chat ( cw2/RemoteChat )</li>
	<li>ถ้าไม่ระบุ service ใดๆจะรันทั้งหมด</li>
</ul>
</li>
	<li>ไม่ต้องการ run service เพียงบาง service ให้ระบุ -d
./testCW2.sh -d cw2 -d friend</li>
	<li>ถ้าต้องการ run transport โดยใช้ cassandra ใส่ --cassandra จะเป็นการใช้ database เดียวกับเครื่อง production (จำเป็นต้องลง cassandra) แต่ถ้าไม่ระบุ default จะใช้ sqlite</li>
	<li>./testCW2.sh --help เพื่อดูตัวอย่าง</li>
	<li>ต้อง Build cw2 ก่อนอย่างน้อย 1 เครื่องจึงจะสามารถรันเทสอื่นๆได้</li>
</ol>
<strong>Successfully Example Result</strong>
<code>return 0
All passed</code>

<strong>Error</strong>
<ol>
	<li>limit open file descriptor ไม่พอ
<code>Error: Can't create table 'user' in './46574400-0000-0000-0000-000000000000-5599.db' dbFile (14): unable to open database file
Bad file descriptor (src/signaler.cpp:155)
test_funcs.sh: line 114: 9535 Abort trap: 6 ./allTest.o
/Users/abc/crossproject/cw2/scripts
WARNING: Your file descriptor maybe not enough to run this test.
Type './testCW2.sh --help' for more detail.
Build / Test TransportLayer failed.</code>
วิธีแก้
<code>ulimit -n 1024</code></li>
</ol>