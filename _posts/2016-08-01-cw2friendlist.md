---
ID: 5437
post_title: CW2Friendlist
author: theerapat.pr
post_date: 2016-08-01 13:43:36
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5437
published: true
---
Git Repo : cw2

Required  :
- Database ( LDAP, OrientDB )
- TransportLayer Units ( Router, Shadow )
- Friendserver
- FriendClient ( service using friend API )

Message format : <a href="https://docs.google.com/document/d/1ivQFuZMCV-6--Ug2JDAl9ouU551rjXWxRMBZOR2U2qk/edit">Google doc</a>

<img class="alignnone size-full wp-image-5438" src="http://192.168.178.12/wp-content/uploads/2016/08/CWFriend.png" alt="CWFriend" width="411" height="250" />

Build step:
- Go to directory <strong>cw2/CWFriendlist</strong>
- Create build folder ( <strong>#</strong> <strong>mkdir build</strong> )
- <strong>cmake ..</strong> or <strong>cmake .. -DUSE_AUTHEN=on</strong> for using cw2 authentication with LDAP. (add <strong>-DUSE_CASSANDRA=on</strong> for using transport with Cassandra)

Launch step:
- Start OrientDB / LDAP / Cassandra(if used)
- Go to directory <strong>cw2/CWFriendlist/build/transport
</strong>- Start router ( <strong># printf "1\nconfig/router0.conf" | ./router_client </strong>)
- Start shadow ( <strong># ./shadow </strong>)
- Go to directory <strong>cw2/CWFriendlist/build
</strong>- Start friendserver ( <strong># ./friendserver config/service0.conf </strong>)

&nbsp;