---
ID: 5278
post_title: Basic Web (Todo, Calendar and Dashboard)
author: chutima
post_date: 2015-12-21 17:56:31
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5278
published: true
---
<div>
<div><b>JS pattern</b></div>
</div>
<ul>
	<li>Define
<ul>
	<li>Order!/text!</li>
	<li>Path</li>
</ul>
</li>
	<li>Class
<ul>
	<li>el</li>
	<li>Class variable &amp; const</li>
	<li>Event</li>
	<li>Initialise
<ul>
	<li>Binding</li>
</ul>
</li>
	<li>Render
<ul>
	<li>addAll</li>
	<li>addOne</li>
</ul>
</li>
	<li>Event handler (onXXX)</li>
	<li>onClose</li>
	<li>Util</li>
</ul>
</li>
	<li>Return class</li>
</ul>
<div>
<div></div>

<hr />

<div><b>App ui structure</b></div>
</div>
<ul>
	<li>Header</li>
	<li>Content</li>
	<li>Detail
<ul>
	<li>Header (detail view)
<ul>
	<li>Priority</li>
	<li>Id</li>
	<li>Action
<ul>
	<li>Follow/unfollow</li>
	<li>Next/prev</li>
	<li>Share
<ul>
	<li>Get reference link</li>
	<li>Leave</li>
	<li>Delete</li>
</ul>
</li>
	<li>Save</li>
	<li>Close</li>
</ul>
</li>
</ul>
</li>
	<li>Name</li>
	<li>Metadata</li>
	<li>Description</li>
	<li>Calendar setting
<ul>
	<li>Color</li>
	<li>Private/public calendar</li>
</ul>
</li>
	<li>Mail detail</li>
	<li>Subtask list</li>
	<li>State list</li>
	<li>Attachment</li>
	<li>Activity</li>
	<li>Time
<ul>
	<li>Timeline</li>
	<li>Reminder</li>
	<li>Start and due date</li>
	<li>Recurrence</li>
</ul>
</li>
	<li>People
<ul>
	<li>Assignee</li>
	<li>Share list</li>
</ul>
</li>
	<li>Category/state, calendar</li>
	<li>Location</li>
	<li>Chat (Comment)</li>
</ul>
</li>
</ul>
<div>

<hr />

<div><b>Todo</b></div>
<ul>
	<li>Category list
<ul>
	<li>Default category (custom query)</li>
	<li>Following</li>
	<li>Category
<ul>
	<li>Hidden</li>
</ul>
</li>
</ul>
</li>
	<li>Task list
<ul>
	<li>Search bar + quick add task</li>
	<li>State</li>
	<li>Task
<ul>
	<li>Subtask</li>
</ul>
</li>
</ul>
</li>
	<li>Modal
<ul>
	<li>Add item
<ul>
	<li>Task</li>
	<li>Category, state</li>
</ul>
</li>
	<li>Edit item
<ul>
	<li>Task, event</li>
	<li>Category, state, calendar</li>
</ul>
</li>
	<li>Edit batch
<ul>
	<li>Task, category</li>
</ul>
</li>
	<li>Manage category and state</li>
	<li>Share item</li>
	<li>Set permission</li>
</ul>
</li>
</ul>

<hr />

<div><b>Calendar</b></div>
<ul>
	<li>Calendar list
<ul>
	<li>Following</li>
	<li>Calendar
<ul>
	<li>Hidden</li>
</ul>
</li>
	<li>Category
<ul>
	<li>Hidden</li>
</ul>
</li>
	<li>Subscribed
<ul>
	<li>Hidden</li>
</ul>
</li>
</ul>
</li>
	<li>Calendar view
<ul>
	<li>Month</li>
	<li>Week/day</li>
	<li>Agenda</li>
</ul>
</li>
	<li>Modal
<ul>
	<li>Add item
<ul>
	<li>Task, event</li>
	<li>Category, state, calendar</li>
</ul>
</li>
	<li>Import</li>
	<li>Edit item
<ul>
	<li>Task, event</li>
	<li>Category, state, calendar</li>
</ul>
</li>
	<li>Edit batch
<ul>
	<li>Category. calendar</li>
</ul>
</li>
	<li>Manage category and state/ calendar</li>
	<li>Share item</li>
	<li>Set permission</li>
</ul>
</li>
</ul>

<hr />

<div><b>Dashboard</b></div>
<ul>
	<li>Chat
<ul>
	<li>Last updated chats</li>
	<li>Fetch from discussion feed</li>
	<li>Go to chat</li>
</ul>
</li>
	<li>Mail
<ul>
	<li>Last unread emails in Inbox</li>
	<li>Go to email</li>
</ul>
</li>
	<li>My task
<ul>
	<li>All tasks and subtasks assigned to me</li>
	<li>Go to task or subtask</li>
</ul>
</li>
	<li>Upcoming
<ul>
	<li>Following tasks, subtasks and events that will happen in 3 days</li>
	<li>Go to task, subtask or event</li>
</ul>
</li>
	<li>Following
<ul>
	<li>Last history of all following items</li>
	<li>Fetch data
<ul>
	<li>All following items</li>
	<li>Last history of them</li>
</ul>
</li>
	<li>Go to item</li>
</ul>
</li>
</ul>
</div>