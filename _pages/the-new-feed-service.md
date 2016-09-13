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
<strong>วิธีการใช้ The New Feed Service (สำหรับ feed service v1.1.0 ขึ้นไป)</strong>
<ul>
	<li><strong>Install PostgresQL with BDR extension</strong></li>
</ul>
<ol>
	<li><del datetime="2016-09-13T09:42:53+00:00">รันคำสั่ง curl -s "http://git.postgresql.org/gitweb/?p=2ndquadrant_bdr.git;a=blob_plain;f=scripts/bdr_quickstart.sh;hb=bdr-plugin/REL0_9_STABLE" | bash</del></li>
	<li>รันคำสั่ง curl -s "https://raw.githubusercontent.com/2ndQuadrant/bdr/bdr-plugin/REL1_0_STABLE/scripts/bdr_quickstart.sh" | bash </li>
	<li>แก้ไฟล์ $HOME/.profile โดยเพิ่ม export PATH=$HOME/2ndquadrant_bdr/bdr/bin:$PATH</li>
</ol>
<ul>
	<li><strong>init database instance</strong></li>
</ul>
<ol>
	<li>ตรวจดูไฟล์ config ว่าตั้งค่าไว้ถูกต้องหรือไม่ file: crossweb/node_modules/feed/bin/initial-script/initial-config/(initdb.conf.js | initdb.conf.prod.js)โดยมีค่าที่สำคัญ คือ
1. base_dir คือ directory ที่จะสร้าง directory ที่เก็บ data ทั้งหมดของ database instance ที่กำลังจะสร้าง
2. dir_name คือ ชื่อ directory ที่จะสร้าง ภายใน directory base_dir (default: feed_db)
3. port คือ หมายเลข port ที่จะรัน database instance เมื่อ init เสร็จเรียบร้อย
4. username คือ username ที่ใช้สร้าง (ต้องใช้ username นี้ ในการเข้าใช้ databasae ในครั้งต่อๆ ไป)</li>
	<li>cd เข้าไปที่ directory: crossweb/node_modules/feed/bin/initial-script</li>
	<li>รันคำสั่ง node init_PGDB_and_modify_config.js -c ./initial-config/(initdb.conf.js | initdb.conf.prod.js)
โดย user ที่สั่งรัน ต้องมี permission ในการ create directory ใน base_dir
เมื่อรัน script นี้แล้ว จะได้ database 1 instance ที่รันอยู่ที่ port ที่ระบุ</li>
</ol>
<ul>
	<li><strong>create feed database with its tables, indices and BDR extension</strong></li>
</ul>
<ol>
	<li>ตรวจดูไฟล์ config ว่าตั้งค่าไว้ถูกต้องหรือไม่
file: crossweb/node_modules/feed/bin/initial-script/initial-config/(create_feed_db.conf.js | create_feed_db.prod.conf.js)
โดยมีค่าที่สำคัญ คือ
1. customer_name คือ customer name (หลัง @ ใน username)
2. postgres คือ ที่อยู่ของ postgresql database instance (ใช้ user เดียวกับ user ขณะ init (default: postgres), ใช้ password เดียวกับ password ขณะ init (default: ""))
3. create_feed_db
3.1 doCreate คือ จะสร้าง feed database หรือไม่ (ควรจะ true)
3.2 proxy คือ ถ้ามีการวาง proxy หน้าเครื่องที่รัน postgresql ก็ให้ระบุที่อยู่ของ proxy นั้นด้วย
3.3 is_cloud_or_local คือ ให้ระบุว่า feed_database ที่สร้างนี้ อยู่บน cloud หรือ local
3.4 cloud คือ ถ้า is_cloud_or_local คือ 'local' ให้ระบุที่อยู่ของ feed postgresql database ที่ customer_name เดียวกัน บน cloud ที่นี่</li>
	<li>cd เข้าไปที่ directory: crossweb/node_modules/feed/bin/initial-script</li>
	<li>รันคำสั่ง node create_feed_PGDB_with_BDR_extension.js -c ./initial-config/(create_feed_db.conf.js | create_feed_db.conf.prod.js)
เมื่อรัน script นี้แล้ว จะได้ feed database ที่กำหนด พร้อมกับสร้าง table, index และพยายามจะ sync cloud-local</li>
</ol>
<ul>
	<li><strong>create history database with its tables, indices</strong></li>
</ul>
<ol>
	<li>ตรวจดูไฟล์ config ว่าตั้งค่าไว้ถูกต้องหรือไม่
file: crossweb/node_modules/feed/bin/initial-script/initial-config/(create_history_db.conf.js | create_history_db.prod.conf.js)
โดยมีค่าที่สำคัญ คือ
1. postgres คือ ที่อยู่ของ postgresql database instance (ใช้ user เดียวกับ user ขณะ init (default: postgres), ใช้ password เดียวกับ password ขณะ init (default: ""))
2. create_history_db
2.1 doCreate คือ จะสร้าง history database หรือไม่ (ควรจะ true)</li>
	<li>cd เข้าไปที่ directory: crossweb/node_modules/feed/bin/initial_script</li>
	<li>รันคำสั่ง node create_history_PGDB.js -c ./initial-config/(create_history_db.conf.js | create_history_db.prod.conf.js)
เมื่อรัน script นี้แล้ว จะได้ history database ที่กำหนด พร้อมกันสร้าง table และ index</li>
</ol>
<ul>
	<li>start service ต่างๆ ของฟีด</li>
</ul>
<ol>
	<li>รัน script ./startAll.sh และ ./startWebService.sh โดยขณะที่รัน ./startAll.sh ห้ามใช้ user root (ห้าม sudo)</li>
</ol>
&nbsp;
<ul>
	<li><strong>drop feed database (manual)</strong></li>
</ul>
<ol>
	<li>psql เข้าไปที่ default database(default = postgres) ใน instance เดียวกับ feed database ที่จะลบ
(psql -h "hostname" -p "port" -U "user")
เมื่อเรียกสำเร็จ จะขึ้นว่า
<p class="p1"><span class="s1">psql (9.4.1)
</span><span class="s1">Type "help" for help.
</span><span class="s1">postgres=#</span></p>
</li>
	<li>ลองพิมพ์คำสั่ง
postgres=# drop database "feed_database_name";  (ถ้าชื่อ database มีอักขระพิเศษ เช่น "@" จะต้องใส่ "" ด้วย)2.1 ถ้าได้ผลลัพธ์
postgres=# drop database "feed_database_name";
DROP DATABASE
แสดงว่าการ drop database สำเร็จ2.2 ถ้าได้ผลลัพธ์
postgres=# drop database test;
ERROR:  database "test" is being accessed by other users
DETAIL:  There is 1 other session using the database.
แสดงว่ามี session อื่น กำลังใช้ database นั้นอยู่
ถ้าต้องการจะ force drop ให้ทำตามขั้นตอน ดังนี้
2.2.1 พิมพ์คำสั่ง
postgres=# update pg_database set datallowconn = 'false' where datname = '​feed_database_name';
ซึ่งควรจะได้ผลลัพธ์
UPDATE 1
2.2.2 พิมพ์คำสั่ง
postgres=# SELECT pg_terminate_backend(pid) FROM pg_stat_activity WHERE datname = 'feed_database_name';
ซึ่งควรจะได้ผลลัพธ์
pg_terminate_backend
----------------------
t
(1 row)
(จำนวน t และ จำนวน row จะเป็นตามจำนวน session ที่ค้างอยู่)
2.2.3 ทดลอง postgres=# drop database "feed_database_name"; อีกครั้ง2.3 ถ้าได้ผลลัพธ์
postgres=# drop database "feed@crossflow.ws";
ERROR:  database "feed@crossflow.ws" is used by a logical replication slot
DETAIL:  There is 1 slot, 1 of them active.
แสดงว่า database นี้มีการพยายามจะ sync กับ database อื่น
ถ้าต้องการจะ force drop ให้ลอง
(การทำตามนี้ อาจจะทำให้การ sync มีปัญหา และอาจจะต้อง drop database ที่ sync กับ database นี้ ที่อยู่ใน instance อื่นๆ ด้วย)
2.3.1 ปิด database instance ที่ sync กับ database instance ที่จะ drop database ให้หมด (ถ้าไม่ปิด จะ drop replication slot ที่กำลังใช้งานไม่ได้)
2.3.2 พิมพ์คำสั่ง
postgres=# select * from pg_replication_slots; เพื่อดูว่า มีการใช้ replication_slots อย่างไรบ้าง
ซึ่งควรจะได้ผลลัพธ์
<p class="p1"><span class="s1"><span class="Apple-converted-space">                </span>slot_name<span class="Apple-converted-space">                                            </span>| plugin | slot_type | datoid | <span class="Apple-converted-space">    </span>database<span class="Apple-converted-space">      </span>| active | xmin | catalog_xmin | restart_lsn </span></p>
<p class="p1"><span class="s1">-----------------------------------------+--------+-----------+--------+-------------------+--------+------+--------------+-------------</span></p>
<p class="p1"><span class="s1"> bdr_16385_6156417642852889029_1_16385__ | bdr<span class="Apple-converted-space">    </span>| logical <span class="Apple-converted-space">  </span>|<span class="Apple-converted-space">  </span>16385 | feed@crossflow.ws | t<span class="Apple-converted-space">      </span>|<span class="Apple-converted-space">      </span>| <span class="Apple-converted-space">        </span>1061 | 0/18C3C30
</span><span class="s1">(1 row)
(จำนวน row จะตามจำนวน replication_slot)
นำค่าตรงช่อง slot_name สนใจเฉพาะ row ที่มีค่าในช่อง database ตรงกับ database name ที่จะ drop
2.3.3 พิมพ์คำสั่ง
</span><span class="s1">postgres=# select * from pg_drop_replication_slot('slot_name ที่มีค่าใน column database ตรงกับ database name ที่จะ drop');
(ในวงเล็บ ต้องมี '' (single quote ด้วย))
(ถ้ามีหลายค่า ให้สั่งให้ครบ)
ซึ่งควรจะได้ผลลัพธ์
</span><span class="s1">postgres=# select * from pg_drop_replication_slot('bdr_16385_6156417642852889029_1_16385__');</span></p>
<p class="p1"><span class="s1"> pg_drop_replication_slot
</span><span class="s1">--------------------------
</span><span class="s1">(1 row)
2.3.4 ถ้าไม่สามารถปิด instance database ที่ sync อยู่ได้ และทำให้ไม่สามารถ drop replication slots ได้ (</span><span class="s1">ERROR:  replication slot "bdr_18750_6230626751636819266_1_69758__" is already active</span><span class="s1">) ให้ทำตามนี้
</span><span class="s1">1) set wal_sender_timeout to some low value (1); (ในไฟล์ postgresql.conf)
</span><span class="s1">2) reload </span><span class="s1">(postgres=# select pg_reload_conf();)</span><span class="s1">
</span><span class="s1">3) call pg_drop_replication_slot('slotname')</span><span class="s1">
</span><span class="s1">2.3.5 ทดลอง postgres=# drop database "feed_database_name"; อีกครั้ง</span></p>
&nbsp;</li>
</ol>