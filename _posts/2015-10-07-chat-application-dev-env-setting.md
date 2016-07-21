---
ID: 5207
post_title: Chat application dev env setting
author: chutima
post_date: 2015-10-07 18:34:01
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5207
published: true
---
<strong>Required</strong>
<ol>
	<li>Nodejs version 5.0.0  (<a href="https://nodejs.org/dist/v5.0.0/node-v5.0.0.pkg ">download</a>)</li>
	<li>pkg-config, cmake, hiredis, curl, sqlite, jansson (install by home-brew (<a href="http://brew.sh">http://brew.sh</a>))</li>
	<li>ZMQ version &gt; 4.1.3 compile with libsodium
<pre>brew install libsodium
curl -O http://download.zeromq.org/zeromq-4.1.3.tar.gz
tar -zxvf zeromq-4.1.3.tar.gz
cd zeromq-4.1.3
export sodium_LIBS="-L/usr/local/lib/ -lsodium"
export sodium_CFLAGS="-I/usr/local/include"
./configure --with-libsodium=/usr/local/
make &amp;&amp; make install</pre>
</li>
	<li>openldap and berkeley-db (installation guide in <a href="http://192.168.178.12/?p=4869">http://192.168.178.12/?p=4869</a>)</li>
	<li>Download orient-db (<a href="http://orientdb.com/download.php?email=unknown@unknown.com&amp;file=orientdb-community-2.1.12.tar.gz&amp;os=multi">download</a>)</li>
</ol>
ถ้า brew Permissions Denied  แก้ตามนี้
<pre>~ $ sudo chown -R `whoami` /usr/local
Password:
~$ brew link --overwrite node
Linking /usr/local/Cellar/node/0.10.4... 5 symlinks created</pre>
&nbsp;

<strong>Installation</strong>
<ol>
	<li>Clone project from http://192.168.178.4/git/chat
*If you use git command line, you need to use
<pre>git submodule update --init --recursive</pre>
</li>
	<li>Switch branch to 'web-react'</li>
	<li>Clone project from http://192.168.178.4/git/crossproject
*If you use git command line, you need to use
<pre>git submodule update --init --recursive</pre>
</li>
	<li>Install node modules (<em>crossweb/chat</em>)
<pre>cd crossweb/chat
npm install</pre>
</li>
	<li>Build chat project backend (<em>crossweb/chat/scripts</em>)
<pre>cd scripts
./build.sh

ถ้าไม่ผ่าน ให้ใช้คำสั่ง xcode-select --install ก่อน แล้ว ./build.sh อีกรอบ</pre>
</li>
	<li>Config chat UI path (<em>crossweb/chat/server</em>)
<pre>ไปที่ repo chat ที่ clone มา
cd public
pwd แล้ว copy path ที่ได้</pre>
<pre>ไปที่ repo crossproject
cd crossweb/chat/server
vim config-default.js
แก้บรรทัดที่ 2 ตรง webClient: '/Users/Earth/code/chat/public',
ให้เป็น webClient: 'path ที่ copy มา',
**** เก็บไว้เป็น config ของตัวเอง ไม่ต้อง push ขึ้น repo ****</pre>
</li>
</ol>

<hr />

<strong>Start Services</strong>
<ol>
	<li>start LDAP
<pre>./start-ldap.sh</pre>
</li>
	<li>start OrientDB
<pre>go to OrientDB folder
bin/server.sh</pre>
</li>
	<li>start chat service (<em>crossweb/chat/scripts</em>)
<pre>cd crossweb/chat/scripts
./start.sh</pre>
</li>
</ol>
&nbsp;

<hr />

<strong>Stop Services</strong>
<ol>
	<li>stop LDAP
<pre>./stop-ldap.sh</pre>
</li>
	<li>stop OrientDB
<pre>go to terminal that use to start OrientDB
interrupt (CTRL-C)</pre>
</li>
	<li>stop chat service (<em>crossweb/chat/scripts</em>)
<pre>cd crossweb/chat/scripts
./stop.sh</pre>
</li>
</ol>

<hr />

<strong>Useful script</strong>
<ul>
	<li>./status.sh - check the status of all service</li>
	<li>./start.sh - start all service</li>
	<li>./stop.sh - stop all service</li>
</ul>
<strong>GUI for ldap</strong>
<ul>
	<li>download <a href="https://directory.apache.org/studio/download/download-macosx.html">Apache Directory Studio</a> and Install then launch</li>
	<li>File -&gt; new -&gt; LDAP Browser -&gt; LDAP Connection</li>
	<li>Hostname: <span style="text-decoration: underline;">localhost</span> -&gt; next</li>
	<li>Bind DN or user: <span style="text-decoration: underline;">cn=admin,dc=authen</span></li>
	<li>Bind password: <span style="text-decoration: underline;">secret</span> -&gt; Finish</li>
</ul>
<strong>Force Auto AddFriend</strong>

<strong>Force Logout</strong>
<ul>
	<li>If cannot logout from chat, you need to clear cookie of this website</li>
</ul>