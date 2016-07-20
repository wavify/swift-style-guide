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
	<li>Nodejs version 5.0.0  (<a href="https://nodejs.org/en/">https://nodejs.org/en/</a>)</li>
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
	<li>Download orient-db (download from here <a href="http://orientdb.com/download.php?email=unknown@unknown.com&amp;file=orientdb-community-2.1.6.tar.gz&amp;os=mac">Orient-db</a>)</li>
</ol>
ถ้า brew Permissions Denied  แก้ตามนี้
<pre>~ $ sudo chown -R `whoami` /usr/local
Password:
~$ brew link --overwrite node
Linking /usr/local/Cellar/node/0.10.4... 5 symlinks created</pre>
&nbsp;

<strong>Installation (for first time only or after pull from git repo)</strong>
<ol>
	<li>Clone project from http://192.168.178.10/git/chat
*If you use git command line, you need to use
<pre>git submodule update --init --recursive</pre>
</li>
	<li>Switch branch to 'web-0.1.0-dev' (backend only) or 'web-react' (with UI)</li>
	<li>Build chat project in /chat
<pre>cd script
./rebuild.sh</pre>
</li>
	<li>run orient-db
<pre>go to orient-db folder
bin/server.sh</pre>
</li>
	<li>start authentication ldap
<pre>cd script
./start-authen.sh</pre>
</li>
	<li>add user to database (optional): use at first time or want to reset database
<pre>cd script
./adduser.sh</pre>
</li>
</ol>
<strong>Run Chat after install</strong>
<ol>
	<li>start chat service
<pre>cd script
./start-all.sh</pre>
</li>
</ol>
<strong>Run Chat after turn on computer</strong>
<ol>
	<li>run orient-db
<pre>go to orient-db folder
bin/server.sh</pre>
</li>
	<li>start authentication ldap
<pre>cd script
./start-authen.sh</pre>
</li>
	<li>start chat service
<pre>cd script
./start-all.sh</pre>
</li>
</ol>

<hr />

&nbsp;

<strong>Reset Chat</strong>
<ol>
	<li>reset server database
<pre>cd script
./reset-all.sh</pre>
</li>
	<li>clear cookie in browser</li>
	<li>login again</li>
</ol>
<strong>Clean and Adduser Authentication</strong>
<ol>
	<li>stop authen
<pre>cd script
./stop-authen.sh</pre>
</li>
	<li>remove database
<pre>cd script
./removeuser.sh</pre>
</li>
	<li>start authen
<pre>cd script
./start-authen.sh</pre>
</li>
	<li>add user to database
<pre>cd script
./adduser.sh</pre>
</li>
</ol>
<strong>Useful script</strong>
<ul>
	<li>./status.sh - check the status of all service</li>
	<li>./start-all.sh - start all service</li>
	<li>./stop-all.sh - stop all service</li>
	<li>./reset-all.sh - reset all service, clear database and start service again</li>
</ul>
<strong>How to access log</strong>
<ul>
	<li>friend service log &gt;&gt; /tmp/chat_log/friendservice.log</li>
	<li>friend-node log &gt;&gt; /tmp/chat_log/friendNode.log</li>
	<li>router log &gt;&gt; /tmp/chat_log/router.log</li>
	<li>hwserver log &gt;&gt;/tmp/chat_log/hwserver.log</li>
	<li>chat-node log &gt;&gt;/tmp/chat_log/chat-node.log</li>
</ul>
<strong>GUI for ldap</strong>
<ul>
	<li>download <a href="https://directory.apache.org/apacheds/download/download-macosx.html">Apache Directory Studio</a> and Install then launch</li>
	<li>File -&gt; new -&gt; LDAP Browser -&gt; LDAP Connection</li>
	<li>Hostname: <span style="text-decoration: underline;">localhost</span> -&gt; next</li>
	<li>Bind DN or user: <span style="text-decoration: underline;">cn=admin,dc=authen</span></li>
	<li>Bind password: <span style="text-decoration: underline;">secret</span> -&gt; Finish</li>
</ul>