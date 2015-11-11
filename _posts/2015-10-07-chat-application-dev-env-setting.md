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
	<li>pkg-config, cmake, hiredis (install by home-brew (<a href="http://brew.sh">http://brew.sh</a>))</li>
	<li>ZMQ version &gt; 4.1.3 (<a href="http://zeromq.org">http://zeromq.org</a> or install by home-brew)</li>
	<li>openldap and berkeley-db (installation guide in <a href="http://192.168.178.12/?p=4869">http://192.168.178.12/?p=4869</a>)</li>
</ol>
<strong>Installation</strong>
<ol>
	<li>Clone project from http://192.168.178.10/git/chat
*If you use git command line, you need to use
<pre>git submodule update --init --recursive</pre>
</li>
	<li>Switch branch to 'web-0.1.0-dev'</li>
	<li>Build chat project in /chat
<pre>npm install

./build.sh</pre>
</li>
</ol>
<strong>Run Chat</strong>
<ol>
	<li>Start router
<pre>cd chat/datamodel/transportlayer

start router
    ./transport.sh router 0 start
stop router
    ./transport.sh router 0 start</pre>
</li>
	<li>Start node &amp; hwserver
<pre>cd chat
start server
    ./web-server.sh start 0
stop server
    ./web-server.sh stop 0</pre>
</li>
</ol>
<strong>How to access log</strong>
<ul>
	<li>router log &gt;&gt; chat/datamodel/transportlayer/build/log/router.log</li>
	<li>hwserver log &gt;&gt; chat/webserver/log/server.log</li>
	<li>node log &gt;&gt; chat/webserver/log/node.log</li>
</ul>
&nbsp;