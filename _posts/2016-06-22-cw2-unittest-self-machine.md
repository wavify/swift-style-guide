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

Backend required:
&nbsp;&nbsp;&nbsp;&nbsp;http://192.168.178.12/?p=5207
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;cmake
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;hiredis
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;curl
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sqlite
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;jansson
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ZMQ + libsodium
&nbsp;&nbsp;&nbsp;&nbsp;http://192.168.178.12/?p=4869
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Xcode 7.3.1
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Command Line Tools
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BerkeleyDB
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OpenLDAP
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Redis
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OrientDB
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PostgreSQL

Config Service
&nbsp;&nbsp;&nbsp;&nbsp;OrientDB
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. set root password to "1234"
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5.1 open config file "orientdb-server-config.xml"
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5.2 edit line <user resources="*" password="" name="root"/> to <user resources="*" password="1234" name="root"/>

Step การรัน
&nbsp;&nbsp;&nbsp;&nbsp;1. ไม่ต้องเปิด service ของ cw2
&nbsp;&nbsp;&nbsp;&nbsp;2. cd crossproject/cw2/scripts
&nbsp;&nbsp;&nbsp;&nbsp;3. ./testCW2.sh -orientp "1234"
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Requirements
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [service] orientdb (Datamodel, Friend, Chat)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;จำเป็นต้อง start OrientDB และต้องระบุ option -orientp "1234" ตามหลัง
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;./testCW2.sh datamodel -orientp "1234"
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [service] cassandra (Transport)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- [service] ldap with data org throughwave.co.th (Friend)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ต้องการ test service ไหนให้ระบุ ตามหลัง เช่น "./testCW2.sh datamodel" โดย service ที่มีได้แก่ cw2, cwmq, transport, datamodel, friend, chat
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Unit Test CWMQ ( cw2/shared/cwmq/ )
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Unit Test Transport ( cw2/transportlayer )
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Unit Test Datamodel ( cw2/datamodel )
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Unit Test Friend ( cw2/CWFriendlist )
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- Unit Test Chat ( cw2/RemoteChat )
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ถ้าไม่ระบุ service ใดๆจะรันทั้งหมด
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ไม่ต้องการ run service เพียงบาง service ให้ระบุ -d <service>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;./testCW2.sh -d cw2 -d friend
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ถ้าต้องการ run transport โดยใช้ cassandra ใส่ --cassandra จะเป็นการใช้ database เดียวกับเครื่อง production (จำเป็นต้องลง cassandra) แต่ถ้าไม่ระบุ default จะใช้ sqlite
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ./testCW2.sh --help เพื่อดูตัวอย่าง
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- ต้อง Build cw2 ก่อนอย่างน้อย 1 เครื่องจึงจะสามารถรันเทสอื่นๆได้

Successfully Example Result
&nbsp;&nbsp;&nbsp;&nbsp;return 0
&nbsp;&nbsp;&nbsp;&nbsp;All passed

Error
&nbsp;&nbsp;&nbsp;&nbsp;limit open file descriptor ไม่พอ
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Message
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Error: Can't create table 'user' in './46574400-0000-0000-0000-000000000000-5599.db' dbFile (14): unable to open database file
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Bad file descriptor (src/signaler.cpp:155)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;test_funcs.sh: line 114:  9535 Abort trap: 6           ./allTest.o
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/Users/abc/crossproject/cw2/scripts
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WARNING: Your file descriptor maybe not enough to run this test.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;        Type './testCW2.sh --help' for more detail.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Build / Test TransportLayer failed.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;วิธีแก้
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ulimit -n 1024