---
ID: 5292
post_title: Share process and Policy
author: chutima
post_date: 2015-12-21 20:16:03
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5292
published: true
---
<div><b>Share step</b></div>
<ol>
	<li>Select target (friend)</li>
	<li>Set permission (read, edit, share, delete)</li>
</ol>
<div></div>
<div><b>Permission</b></div>
<ul>
	<li>Inherit permission
<ul>
	<li>Task &gt; subtask</li>
	<li>Category &gt; state</li>
	<li>Root event &gt; recurrence event</li>
</ul>
</li>
	<li>Bit string</li>
	<li>Permission
<ul>
	<li>Key: username</li>
	<li>Value: policy</li>
</ul>
</li>
	<li>Using
<ul>
	<li>Read
<ul>
	<li>0 (CLPolicyRead)</li>
</ul>
</li>
	<li>Write
<ul>
	<li>Update item data</li>
	<li>Update subitem data
<ul>
	<li>Task &gt; subtask (add/reorder/delete)</li>
	<li>Category &gt; state (add/reorder/delete)</li>
</ul>
</li>
	<li>1 (CLPolicyEditData)</li>
</ul>
</li>
	<li>Share
<ul>
	<li>Share item</li>
	<li>Edit permission</li>
	<li>3 (CLPolicyCanShare)</li>
	<li>8 (CLPolicyUnshareData)</li>
	<li>10 (CLPolicyCanShareClone)</li>
	<li>11 (CLPolicyEditPolicy)</li>
</ul>
</li>
	<li>Delete
<ul>
	<li>Delete item</li>
	<li>7 (CLPolicyDeleteData)</li>
</ul>
</li>
</ul>
</li>
	<li>Saving
<ul>
	<li>Save diff ONLY</li>
</ul>
</li>
</ul>
<div></div>