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
<a href="http://192.168.178.12/?p=5207">http://192.168.178.12/?p=5207</a>
cmake
hiredis
curl
sqlite
jansson
ZMQ + libsodium
<a href="http://192.168.178.12/?p=4869">http://192.168.178.12/?p=4869</a>
Xcode 7.3.1
Command Line Tools
BerkeleyDB
OpenLDAP
Redis
OrientDB
PostgreSQL

Config Service
OrientDB
1. set root password to "1234"
5.1 open config file "orientdb-server-config.xml"
5.2 edit line to

Step การรัน
1. ไม่ต้องเปิด service ของ cw2
2. cd crossproject/cw2/scripts
3. ./testCW2.sh -orientp "1234"
- Requirements
- [service] orientdb (Datamodel, Friend, Chat)
จำเป็นต้อง start OrientDB และต้องระบุ option -orientp "1234" ตามหลัง
./testCW2.sh datamodel -orientp "1234"
- [service] cassandra (Transport)
- [service] ldap with data org throughwave.co.th (Friend)
- ต้องการ test service ไหนให้ระบุ ตามหลัง เช่น "./testCW2.sh datamodel" โดย service ที่มีได้แก่ cw2, cwmq, transport, datamodel, friend, chat
- Unit Test CWMQ ( cw2/shared/cwmq/ )
- Unit Test Transport ( cw2/transportlayer )
- Unit Test Datamodel ( cw2/datamodel )
- Unit Test Friend ( cw2/CWFriendlist )
- Unit Test Chat ( cw2/RemoteChat )
- ถ้าไม่ระบุ service ใดๆจะรันทั้งหมด
- ไม่ต้องการ run service เพียงบาง service ให้ระบุ -d
./testCW2.sh -d cw2 -d friend
- ถ้าต้องการ run transport โดยใช้ cassandra ใส่ --cassandra จะเป็นการใช้ database เดียวกับเครื่อง production (จำเป็นต้องลง cassandra) แต่ถ้าไม่ระบุ default จะใช้ sqlite
- ./testCW2.sh --help เพื่อดูตัวอย่าง
- ต้อง Build cw2 ก่อนอย่างน้อย 1 เครื่องจึงจะสามารถรันเทสอื่นๆได้

Successfully Example Result
return 0
All passed

Error
limit open file descriptor ไม่พอ
Message
Error: Can't create table 'user' in './46574400-0000-0000-0000-000000000000-5599.db' dbFile (14): unable to open database file
Bad file descriptor (src/signaler.cpp:155)
test_funcs.sh: line 114: 9535 Abort trap: 6 ./allTest.o
/Users/abc/crossproject/cw2/scripts
WARNING: Your file descriptor maybe not enough to run this test.
Type './testCW2.sh --help' for more detail.
Build / Test TransportLayer failed.
วิธีแก้
ulimit -n 1024