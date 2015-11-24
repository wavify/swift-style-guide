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
	<li>Nodejs version &gt; 4.0  (<a href="https://nodejs.org/en/">https://nodejs.org/en/</a>)</li>
	<li>pkg-config, cmake, hiredis, curl, sqlite (install by home-brew (<a href="http://brew.sh">http://brew.sh</a>))</li>
	<li>ZMQ version &gt; 4.1.3 (<a href="http://zeromq.org">http://zeromq.org</a> or install by home-brew)</li>
	<li>openldap and berkeley-db (installation guide in <a href="http://192.168.178.12/?p=4869">http://192.168.178.12/?p=4869</a>)</li>
	<li>Download orient-db (download from here <a href="http://orientdb.com/download.php?email=unknown@unknown.com&amp;file=orientdb-community-2.1.6.tar.gz&amp;os=mac">Orient-db</a>)</li>
</ol>
<strong>Installation</strong>
<ol>
	<li>Clone project from http://192.168.178.10/git/chat
*If you use git command line, you need to use
<pre>git submodule update --init --recursive</pre>
</li>
	<li>Switch branch to 'web-0.1.0-dev'</li>
	<li>Build chat project in /chat
<pre>npm install</pre>
</li>
</ol>
<strong>Run Chat</strong>
<ol>
	<li>run orient-db
<pre>go to orient-db folder
cd bin
./server.sh</pre>
</li>
	<li>run chat service
<pre>cd chat/script
./reset-all.sh</pre>
</li>
</ol>
<strong>How to access log</strong>
<ul>
	<li>friend log &gt;&gt; /tmp/chat_log/friendservice.log</li>
	<li>router log &gt;&gt; /tmp/chat_log/router.log</li>
	<li>hwserver log &gt;&gt;/tmp/chat_log/server.log</li>
	<li>node log &gt;&gt;/tmp/chat_log/node.log</li>
</ul>
<strong>GUI for ldap</strong>
<ul>
	<li>download <a href="https://directory.apache.org/apacheds/download/download-macosx.html">Apache Directory Studio</a> and Install then launch</li>
	<li>File -&gt; new -&gt; LDAP Browser -&gt; LDAP Connection</li>
	<li>Hostname: <span style="text-decoration: underline;">localhost</span> -&gt; next</li>
	<li>Bind DN or user: <span style="text-decoration: underline;">cn=admin,dc=authen</span></li>
	<li>Bind password: <span style="text-decoration: underline;">secret</span> -&gt; Finish</li>
</ul>