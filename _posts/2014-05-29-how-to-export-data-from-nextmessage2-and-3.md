---
ID: 5014
post_title: >
  How to export data from Nextmessage2 and
  3
author: Nook Api
post_date: 2014-05-29 12:04:23
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5014
published: true
---
<h2>Nextmessage 3</h2>
1. Check current version. It must be 3.7.30+
<pre>cat /usr/local/opal/release.properties
Build-Date = Jun 18, 2015 08:46 PM
Build-Commit = Nextmessage_3.7.39b2
Build-describe = tags/Nextmessage_3.7.39b2-0-g0a66d2c
Build-namerev-tag = Nextmessage_3.7.39b2
Build-namerev = remotes/origin/Nextmessage_3.7QA_t
Commit-Date = Thu Jun 18 20:41:58 2015 +0700
Build-ProductName = Nextmessage_3.7.39b2
Build-Version = 3.7.39b2
</pre>
2. Export domain user
<pre>/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportUserCmd ${domain_export_path}
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportUserCmd ${domain_export_path} ${domainName}

Ex:
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportUserCmd /data/export/domain/user
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportUserCmd /data/export/domain/user testdomain.net
</pre>
<pre>/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAdminUserCmd ${domain_export_path}
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAdminUserCmd ${domain_export_path} ${domainName}

Ex:
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAdminUserCmd /data/export/domain/admin
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAdminUserCmd /data/export/domain/admin testdomain.net
</pre>
3. Export domain addressbook
<pre>/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportDomainAddressbookCmd ${domain_export_path}
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportDomainAddressbookCmd ${domain_export_path} ${domainName}

Ex:
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportDomainAddressbookCmd /data/export/domain/contact
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportDomainAddressbookCmd /data/export/domain/contact test.net
</pre>
4. Export user addressbook
<pre>/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAddressbookCmd ${user_export_path}
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAddressbookCmd ${user_export_path} ${domainName}

Ex:
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAddressbookCmd /data/export/userdata
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAddressbookCmd /data/export/userdata test.net
</pre>
5. Export user mail filter rule
<pre>/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportSieveCmd ${user_export_path}
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportSieveCmd ${user_export_path} ${domainName}

Ex:
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportSieveCmd /data/export/userdata
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportSieveCmd /data/export/userdata test.net
</pre>
6. Export user calendar
<pre>/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportCalendarCmd ${user_export_path}
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportCalendarCmd ${user_export_path} ${domainName}

Ex:
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportCalendarCmd /data/export/userdata
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportCalendarCmd /data/export/userdata test.net
</pre>
7. scp data to crossmail and run import command from crossmail
<h2>Nextmessage 2</h2>
1. Check current version. It must be 2.2.38+
<pre>cat /usr/local/opal/release.properties
Build-Date = 05/30/2014 11:31 AM 
Build-Url = http://192.168.178.10/svn/development/modules/projects/opal/branch/nextmessage_2.2.38 
Build-Revision = 20538 
Build-ProductName = nextmessage_2.2.38 
Build-Version = 2.2.38 
</pre>
2. Export domain user
<pre>/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportUserCmd ${domain_export_path}
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportUserCmd ${domain_export_path} ${domainName}

Ex:
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportUserCmd /data/export/domain/user
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportUserCmd /data/export/domain/user test.net
</pre>
3. Export domain addressbook
<pre>/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportDomainAddressbookCmd ${domain_export_path}
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportDomainAddressbookCmd ${domain_export_path} ${domainName}

Ex:
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportDomainAddressbookCmd /data/export/domain
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportDomainAddressbookCmd /data/export/domain test.net
</pre>
4. Export user addressbook
<pre>/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAddressbookCmd ${user_export_path}
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAddressbookCmd ${user_export_path} ${domainName}

Ex:
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAddressbookCmd /data/export/userdata
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportAddressbookCmd /data/export/userdata test.net
</pre>
5. Export user mail filter rule
<pre>/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportSieveCmd ${user_export_path}
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportSieveCmd ${user_export_path} ${domainName}

Ex:
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportSieveCmd /data/export/userdata
/usr/local/opal/bin/runclass.sh etherdia.nextmessage.tools.ExportSieveCmd /data/export/userdata test.net
</pre>
6. scp data to crossmail and run import command from crossmail

&nbsp;

<hr />

&nbsp;

<strong>Crossflow</strong>

1. copy file to crossmail ex.
<pre>scp -r userdata opal@10.10.5.25:/tmp/userdata
</pre>
2. create org, then import user and create mail account

3. cd /usr/local/crossweb/migrate-script and run migrate script
<pre>node migrate.js --path=PATH_TO_USER_ADDRESS_BOOK [--level=LOG_LEVEL]
</pre>
example
<pre>node migrate.js --path=/tmp/userdata/testcf.net --level=INFO
</pre>
4. check migrate data

<hr />

&nbsp;

**Update script 13 Jan 2016**

1.create org. + add lc (ในcf)

2.vi domain.txt ใส่org.ที่ต้องการจะเอาorg.อะไรบ้าง

3.run script export file

<strong>/cli/src/script/tools/doMigrate.sh 10.10.5.235 domain.txt</strong>

4.run only this script ที่cf ทีเดียวจบ [ไฟล์domain.txt, Deployment, org.typeไหน]

<strong><span class="s1">/cli/src/script/tools/doImport.sh domain.txt local102 localhost </span></strong>