---
ID: 4869
post_title: 'Backend setup &#8211; OSX (for dev environment)'
author: Pornchai kornpraserttaworn
post_date: 2013-07-01 18:18:38
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=4869
published: true
---
<a name="top-page"></a>
<h1>การ setup เพื่อให้สามารถ run service ต่างๆ ได้</h1>
<ol>
	<li>ติดตั้ง Program ต่างๆ ได้แก่ <span style="color: #999999;">(คลิกที่ชื่อ program เพื่อดูวิธีการติดตั้ง)</span>
<ul>
	<li><a href="#xcode-installation">Xcode</a>
<ul>
	<li><a href="#command-line-tools-installation">Command Line Tools</a></li>
</ul>
</li>
	<li><a href="#osx-gcc-installer-installation">osx-gcc-installer</a></li>
	<li><a href="#nodejs-installation">NodeJS</a> (v5.0.0)</li>
	<li><a href="#bdb-installation">BerkeleyDB</a></li>
	<li><a href="#openldap-installation">OpenLDAP</a> &gt; 2.4.28</li>
	<li><a href="#redis-installation">Redis</a></li>
	<li><a href="#mongo-installation">MongoDB</a></li>
	<li><a href="#haproxy-installation">HAProxy</a> 1.5-dev18 (<a href="http://192.168.178.4/trac/cross/ticket/4711">#4711</a>)</li>
	<li><a href="#graphicsmagick-installation">GraphicsMagick</a> (ใช้สร้าง thumbnail ของ email attachment)</li>
	<li><a href="#postgresql-installation">PostgreSQL</a> (ใช้เก็บ Feed)</li>
	<li>pkg-config, cmake, hiredis, curl, sqlite, jansson (install by home-brew (<a href="http://brew.sh/">http://brew.sh</a>))</li>
	<li><a href="#zmq-installation">ZMQ</a> version &gt; 4.1.3 and compile with libsodium</li>
</ul>
</li>
	<li>ติดตั้ง Node Module ต่างๆ ได้แก่
<ul>
	<li>node module ของ crossweb ติดตั้งโดยคำสั่ง <strong>npm install</strong> ที่ path <strong>/crossweb</strong></li>
	<li>node module ของ iphone service ติดตั้งโดยคำสั่ง <strong>npm install</strong> ที่ path <strong>/iphone-service</strong></li>
	<li>node module ของ module appinfo ติดตั้งโดยคำสั่ง <strong>npm install</strong> ที่ path <strong>/iphone-service/node_modules/appinfo</strong></li>
	<li>หมายเหตุ
<ul>
	<li>ต้องใช้ <strong>npm</strong> ที่ version 3.3.6</li>
	<li><strong>npm</strong> <strong>-g install npm@3.3.6</strong> &gt;&gt; เพื่อ update version ของ <strong>npm</strong></li>
</ul>
</li>
</ul>
</li>
	<li>build RemoteCL โดยคำสั่ง <strong>./build-debug.sh</strong> ที่ path <strong>/crossweb/sdk/RemoteCL</strong></li>
	<li>เพิ่ม <strong>127.0.0.1 beta.crossflow.ws</strong> ใน hosts file (<strong>/etc/hosts</strong>)<code>sudo vi /etc/hosts</code></li>
</ol>
<h1>การ start service ต่างๆ</h1>
<ol>
	<li>ถ้าเพิ่ง clone/pull มาใหม่ ต้องทำ <strong>./rebuildChat.sh</strong> เพื่อ build service ของ friendserver, router, shadow</li>
	<li><span style="line-height: 15px;">start dependency service โดยคำสั่ง <strong>./startAll.sh</strong> ที่ path <strong>/crossweb/tests/services</strong>
คำสั่งนี้จะทำการ start mongod, init mail mongo, init quota, slapd, redis-server, postgres, HAProxy, IPS, LG, friendserver, router, shadow, add app info, add license info ตามลำดับ</span></li>
	<li>start web service โดยคำสั่ง <strong>./startWebService.sh</strong> ที่ path <strong>/crossweb/tests/services</strong>
คำสั่งนี้จะทำการ start UM, Todo, Contact, Friend, Mail-Client, Publisher และ Subscriber ตามลำดับ</li>
</ol>
<h1>การ stop service ต่างๆ</h1>
<ol>
	<li><span style="line-height: 15px;">stop web service โดยคำสั่ง <strong>./stopWebService.sh</strong> ที่ path <strong>/crossweb/tests/services</strong>
คำสั่งนี้จะทำการ stop Subscriber, Publisher, Mail-Client, Friend, Contact, Todo และ UM ตามลำดับ</span></li>
	<li>stop dependency service โดยคำสั่ง <strong>./stopAll.sh</strong> ที่ path <strong>/crossweb/tests/services</strong>
คำสั่งนี้จะทำการ stop HAProxy, LG, IPS, mongod, slapd, redis-server, postgres, friendserver, router, shadow ตามลำดับ</li>
</ol>
<h1><strong>การดู status service ต่างๆ</strong></h1>
<ul>
	<li><strong>./statusBackend.sh</strong> สำหรับดู status ของ service ที่เปิดด้วย startAll (HAProxy, LG, IPS, mongod, slapd, redis-server, postgres, friendserver, router, shadow)</li>
	<li><strong>./statusWebService.sh</strong> สำหรับดู status ของ service ที่เปิดด้วย startWebService (UM, Todo, Contact, Friend, Mail-Client, Publisher, Subscriber)</li>
	<li><strong>./statusAll.sh</strong> สำหรับดู status ของ service ทั้งหมด</li>
</ul>
<h1>การลบ user data</h1>
<ol>
	<li><span style="line-height: 15px;">ลบ store ของ user และ data ที่เก็บใน mongodb โดยคำสั่ง <strong>./clearUserData.sh</strong> ที่ path <strong>/crossweb/tests/services</strong></span></li>
</ol>
<h1>การเข้าใช้งานหน้าเว็บ</h1>
<ul>
	<li><span style="line-height: 15px;">เข้าเว็บจาก url -&gt; https://beta.crossflow.ws/login</span></li>
</ul>
<h1>เพิ่มเติม</h1>
<ul>
	<li><span style="line-height: 15px;">store ของ user ของ process RemoteCL1 จะอยู่ที่ path <strong>/crossweb/tests/services/remoteCL/storage1</strong></span></li>
	<li>store ของ user ของ process RemoteCL2 จะอยู่ที่ path <strong>/crossweb/tests/services/remoteCL/storage2</strong></li>
	<li>file database ของ mongodb จะอยู่ที่ path <strong>/crossweb/tests/services/mongodb</strong></li>
	<li>log ของ service ต่างๆ จะอยู่ที่ path <strong>/crossweb/tests/services/log</strong></li>
	<li>process id ของ service ต่างๆ จะอยู่ที่ <strong>/crossweb/tests/services/running</strong></li>
</ul>
<a name="xcode-installation"></a>
<h1>Xcode Installation</h1>
<ul>
	<li><span style="line-height: 15px;">Install จาก App-Store</span></li>
</ul>
<p style="text-align: right;"><a href="#top-page">^ top</a></p>
<a name="command-line-tools-installation"></a>
<h1>Xcode Command Line Tools</h1>
<ol>
	<li><span style="line-height: 15px;">เปิดโปรแกรม Xcode</span></li>
	<li>ไปที่ เมนู Xcode &gt; Preferences เลือกแถบ Downloads จากนั้นกดปุ่ม install ที่บรรทัด Command Line Tools</li>
</ol>
<p style="text-align: right;"><a href="#top-page">^ top</a></p>
<a name="osx-gcc-installer-installation"></a>
<h1>osx-gcc-installer Installation</h1>
<ol>
	<li><span style="line-height: 15px;">ถ้าลง Xcode Command Line Tools แล้วไม่จำเป็นต้องลง OSX GCC</span></li>
	<li><span style="line-height: 15px;">download gcc-osx-installer ที่ <a href="https://github.com/kennethreitz/osx-gcc-installer">https://github.com/kennethreitz/osx-gcc-installer</a></span></li>
	<li>จะได้ไฟล์ .pkg เป็น pakage file สามารถ double click เพื่อติดตั้งได้เลย</li>
</ol>
<p style="text-align: right;"><a href="#top-page">^ top</a></p>
<a name="nodejs-installation"></a>
<h1>NodeJS Installation</h1>
<ol>
	<li>download <a href="https://nodejs.org/dist/v5.0.0/node-v5.0.0.pkg">https://nodejs.org/dist/v5.0.0/node-v5.0.0.pkg</a></li>
	<li>install โดย double คลิกที่ไฟล์ได้เลย เนื่องจากเป็น package file อยู่แล้ว</li>
</ol>
<p style="text-align: right;"><a href="#top-page">^ top</a></p>
<a name="bdb-installation"></a>
<h1>BerkeleyDB Installation</h1>
<ol>
	<li>download <a href="http://download.oracle.com/berkeley-db/db-6.0.20.tar.gz">http://download.oracle.com/berkeley-db/db-6.0.20.tar.gz</a></li>
	<li>extract file and install<code>tar -xvzf db-6.0.20.tar.gz
cd db-6.0.20/build_unix
../dist/configure
make
sudo make install</code></li>
</ol>
<p style="text-align: right;"><a href="#top-page">^ top</a></p>
<a name="openldap-installation"></a>
<h1>OpenLDAP Installation</h1>
<ol>
	<li>download <a href="http://www.openldap.org/software/download/OpenLDAP/openldap-release/openldap-2.4.34.tgz">http://www.openldap.org/software/download/OpenLDAP/openldap-release/openldap-2.4.34.tgz</a></li>
	<li>extract file and install (** ตั้งแต่ milestone 1.24.0 เป็นต้นไป ให้เพิ่ม
<code>--enable-ldap --enable-overlays --enable-ppolicy</code>
ไปตอน ./configure ด้วย [บรรทัดที่ 3])
<code>tar -xvzf openldap-2.4.34.tgz
cd openldap-2.4.34
env CPPFLAGS=-I/usr/local/BerkeleyDB.6.0/include LDFLAGS=-L/usr/local/BerkeleyDB.6.0/lib ./configure --enable-sssvlv --enable-unique
make depend
make
sudo make install</code></li>
</ol>
<p style="text-align: right;"><a href="#top-page">^ top</a></p>
<a name="redis-installation"></a>
<h1>Redis Installation</h1>
<ol>
	<li>download <a href="http://redis.googlecode.com/files/redis-2.4.18.tar.gz">http://redis.googlecode.com/files/redis-2.4.18.tar.gz</a></li>
	<li>extract file and install<code>tar -xvzf redis-2.4.18.tar.gz
cd redis-2.4.18
make
make install</code></li>
</ol>
<p style="text-align: right;"><a href="#top-page">^ top</a></p>
<a name="mongo-installation"></a>
<h1>MongoDB Installation</h1>
<ol>
	<li>download <a href="http://downloads.mongodb.org/osx/mongodb-osx-x86_64-2.6.2.tgz">http://downloads.mongodb.org/osx/mongodb-osx-x86_64-2.6.2.tgz</a></li>
	<li>extract<code>tar -xvzf mongodb-osx-x86_64-2.6.2.tgz</code></li>
	<li>create symbolic links to the MongoDB programs in your /usr/local/bin (ในที่นี้สมมติว่า source ที่ extract แล้ว อยู่ที่ path /Users/alice/Source<code>ln -s /Users/alice/Source/mongodb-osx-x86_64-2.6.2/bin/mongod /usr/local/bin/mongod</code></li>
</ol>
<p style="text-align: right;"><a href="#top-page">^ top</a></p>
<a name="haproxy-installation"></a>
<h1>HAProxy Installation</h1>
<ol>
	<li>download <a href="http://haproxy.1wt.eu/download/1.5/src/devel/haproxy-1.5-dev18.tar.gz">http://haproxy.1wt.eu/download/1.5/src/devel/haproxy-1.5-dev18.tar.gz</a></li>
	<li>extract file and install<code>tar -xvzf haproxy-1.5-dev18.tar.gz
cd haproxy-1.5-dev18
make TARGET=generic USE_OPENSSL=YES USE_ZLIB=YES
sudo make install</code></li>
	<li>create symbolic links to the HAProxy programs in your /usr/local/bin<code> ln -s /usr/local/sbin/haproxy /usr/local/bin/haproxy</code></li>
</ol>
<p style="text-align: right;"><a href="#top-page">^ top</a></p>
<a name="graphicsmagick-installation"></a>
<h1>GraphicsMagick Installation</h1>
<ol>
	<li>ติดตั้งด้วย <a href="http://brew.sh">homebrew</a>
<code>brew install graphicsmagick</code></li>
</ol>
<p style="text-align: right;"><a href="#top-page">^ top</a></p>
ปัญหาที่อาจเกิดขึ้นระหว่างการติดตั้ง
<ul>
	<li>Error: No developer directory found at /Developer. Run /usr/bin/xcode-select to update the developer directory path.
วิธีแก้
<code>sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer</code></li>
</ul>
<p style="text-align: right;"> <a href="#top-page">^ top</a></p>
<a name="postgresql-installation"></a>
<h1>PostgreSQL Installation</h1>
<ul>
	<li><code>$ curl -s "http://git.postgresql.org/gitweb/?p=2ndquadrant_bdr.git;a=blob_plain;f=scripts/bdr_quickstart.sh;hb=bdr-plugin/REL0_9_STABLE" | bash</code></li>
	<li><code>export PATH=$HOME/2ndquadrant_bdr/bdr/bin:$PATH</code></li>
	<li><code>mkdir -p /usr/local/var/postgreSQL</code></li>
	<li><code>initdb -D /usr/local/var/postgreSQL -A trust -U postgres
</code></li>
</ul>
<a name="zmq-installation"></a>
<h1>ZMQ Installation</h1>
<ul>
	<li><code>brew install libsodium</code></li>
	<li><code>curl -O http://download.zeromq.org/zeromq-4.1.3.tar.gz</code></li>
	<li><code>tar -zxvf zeromq-4.1.3.tar.gz</code></li>
	<li><code>cd zeromq-4.1.3</code></li>
	<li><code>export sodium_LIBS="-L/usr/local/lib/ -lsodium"</code></li>
	<li><code>export sodium_CFLAGS="-I/usr/local/include"</code></li>
	<li><code>./configure --with-libsodium=/usr/local/</code></li>
	<li><code>make &amp;&amp; make install
</code></li>
</ul>
&nbsp;