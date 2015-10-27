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
	<li>ZMQ (<a href="http://zeromq.org">http://zeromq.org</a> or install by home-brew)</li>
</ol>
<strong>Installation</strong>
<ol>
	<li>Clone project from <a href="http://192.168.178.10/git/chat">http://192.168.178.10/git/chat</a></li>
	<li>Switch branch to 'web'</li>
	<li>Run command under /chat
<ul>
	<li>
<pre>npm install</pre>
</li>
</ul>
</li>
	<li>Go to chat/transportlayer and run
<ul>
	<li>
<pre>mkdir build
cd build
cmake ..
make install</pre>
</li>
</ul>
</li>
	<li>Go to chat/webserver and run
<ul>
	<li>
<pre>make</pre>
</li>
</ul>
</li>
</ol>
<strong>Run Chat</strong>
<ol>
	<li>Start router</li>
</ol>
<pre>cd chat/transportlayer/build
./router_client.o

Select Router or Client 
1: Router
2: Client
3: Shadow
0: Exit
&gt; 1 

Select Router or Client 
1: Router
2: Client
3: Shadow
0: Exit
&gt; config/router0.conf
</pre>
2. Start node &amp; hwserver
<pre>cd chat</pre>
<pre>start server
 ./web-server.sh start 0</pre>
<pre>stop server
 ./web-server.sh stop 0</pre>
&nbsp;
<ul>
	<li> How to access log</li>
</ul>
<pre>cd chat/webserver/log</pre>
<ul>
	<li>node &gt;&gt; node.log</li>
	<li>hwserver &gt;&gt; server.log</li>
	<li>hwserver error &gt;&gt; error.log</li>
</ul>