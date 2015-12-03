---
ID: 5224
post_title: The New Feed Service
author: Pasit Buranakul
post_date: 2015-11-12 13:49:05
post_excerpt: ""
layout: page
permalink: http://192.168.178.12/?page_id=5224
published: true
---
วิธีการใช้ The New Feed Service (สำหรับ feed service v1.1.0 ขึ้นไป)
<ul>
	<li>Install PostgresQL with BDR extension</li>
</ul>
<ol>
	<li>รันคำสั่ง curl -s "http://git.postgresql.org/gitweb/?p=2ndquadrant_bdr.git;a=blob_plain;f=scripts/bdr_quickstart.sh;hb=bdr-plugin/REL0_9_STABLE" | bash</li>
	<li>แก้ไฟล์ $HOME/.profile โดยเพิ่ม export PATH=$HOME/Desktop/testbdr/bdr-program/bin:$PATH</li>
</ol>
<ul>
	<li>init database instance</li>
</ul>
<ol>
	<li>ตรวจดูไฟล์ config ว่าตั้งค่าไว้ถูกต้องหรือไม่ file: crossweb/node_modules/feed/bin/initial-script/initial-config/(initdb.conf.js | initdb.conf.prod.js)โดยมีค่าที่สำคัญ คือ
1. base_dir คือ directory ที่จะสร้าง directory ที่เก็บ data ทั้งหมดของ database instance ที่กำลังจะสร้าง
2. dir_name คือ ชื่อ directory ที่จะสร้าง ภายใน directory base_dir (default: feed_db)
3. port คือ หมายเลข port ที่จะรัน database instance เมื่อ init เสร็จเรียบร้อย
4. username คือ username ที่ใช้สร้าง (ต้องใช้ username นี้ ในการเข้าใช้ databasae ในครั้งต่อๆ ไป)</li>
	<li>cd เข้าไปที่ directory: crossweb/node_modules/feed/bin/initial-script</li>
	<li>รันคำสั่ง node init_PGDB_and_modify_config.js -c initial-config/(initdb.conf.js | initdb.conf.prod.js)
โดย user ที่สั่งรัน ต้องมี permission ในการ create directory ใน base_dir
เมื่อรัน script นี้แล้ว จะได้ database 1 instance ที่รันอยู่ที่ port ที่ระบุ</li>
</ol>
<ul>
	<li>create feed or history database with its tables, indices and BDR extension</li>
</ul>
<ol>
	<li>ตรวจดูไฟล์ config ว่าตั้งค่าไว้ถูกต้องหรือไม่
file: crossweb/node_modules/feed/bin/initial-script/initial-config/(createdb.conf.js | createdb.prod.conf.js)
โดยมีค่าที่สำคัญ คือ
1. org_name คือ organization name (หลัง @ ใน username)
2. postgres คือ ที่อยู่ของ postgres instance database (ใช้ user เดียวกับ username ขณะ init (default: postgres), ใช้ password เดียวกับ password ขณะ init (default: ""))
3. create_feed_db
3.1 doCreate คือ จะสร้าง feed database หรือไม่
3.2 is_cloud_or_local คือ ให้ระบุว่า feed_database ที่สร้างนี้ อยู่บน cloud หรือ local
3.3 cloud คือ ถ้า is_cloud_or_local คือ 'local' ให้ระบุที่อยู่ของ feed postgres database ที่ org_name เดียวกัน บน cloud ที่นี่
4. create_history_db
4.1 doCreate คือ จะสร้าง history database หรือไม่ (history database ควรจะอยู่เฉพาะบน cloud)</li>
	<li>cd เข้าไปที่ directory: crossweb/node_modules/feed/bin/initial-script</li>
	<li>รันคำสั่ง node initial-script/create_PGDB_with_BDR_extension.js -c initial-config/(createdb.conf.js | createdb.conf.prod.js)
เมื่อรัน script นี้แล้ว จะได้ database ที่กำหนด พร้อมกับสร้าง table, index และพยายามจะ sync cloud-local</li>
</ol>
<ul>
	<li>start service ต่างๆ ของฟีด</li>
</ul>
<ol>
	<li>รัน script ./startAll.sh และ ./startWebService.sh โดยขณะที่รัน ./startAll.sh ห้ามใช้ user root (ห้าม sudo)</li>
</ol>