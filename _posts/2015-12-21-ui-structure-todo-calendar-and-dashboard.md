---
ID: 5286
post_title: >
  UI Structure (Todo, Calendar and
  Dashboard)
author: chutima
post_date: 2015-12-21 18:05:19
post_excerpt: ""
layout: post
permalink: http://192.168.178.12/?p=5286
published: true
---
<div><b>Todo</b></div>
<ul>
	<li><b>Left</b>
<ul>
	<li>Trigger
<ul>
	<li>Add category</li>
	<li>Category edit batch</li>
</ul>
</li>
	<li><b>CategoryList</b>
<ul>
	<li>Hide/show</li>
</ul>
</li>
</ul>
</li>
	<li><b>Center</b>
<ul>
	<li>Quick add task</li>
	<li>Search</li>
	<li>Sort</li>
	<li>Mark as read</li>
	<li>Trigger
<ul>
	<li>Add task/state</li>
	<li>Task edit batch</li>
	<li>Edit category detail</li>
</ul>
</li>
</ul>
</li>
	<li><b>Tasklist</b>
<ul>
	<li>Pagination rendering</li>
	<li><b>StateSection</b>
<ul>
	<li>Render state and tasks in state</li>
	<li>Render only filtered task
<ul>
	<li><b>TaskItem</b>
<ul>
	<li>Add subtask to this task</li>
	<li>Follow/unfollow</li>
	<li>Trigger
<ul>
	<li>Edit task detail</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
	<li>Modal</li>
</ul>
<div></div>

<hr />

<div></div>
<div><b>Calendar</b></div>
<ul>
	<li><b>Left</b>
<ul>
	<li>Render calendar list
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
	<li><b>CalendarList</b>
<ul>
	<li>Toggle hide/show</li>
	<li>Trigger
<ul>
	<li>Add calendar/category</li>
	<li>Import calendar</li>
	<li>Calendar/category edit batch</li>
</ul>
</li>
	<li><b>CalendarItem</b>
<ul>
	<li>Hide/show</li>
	<li>Leave</li>
	<li>Copy</li>
	<li>Export</li>
	<li>Delete</li>
	<li>Trigger
<ul>
	<li>Add task/event</li>
	<li>Show detail</li>
	<li>Share</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
	<li><b>Center</b>
<ul>
	<li>View rendering
<ul>
	<li>Render all calendar view</li>
	<li>Height/width</li>
	<li>onEventRender
<ul>
	<li>Modify ui after rendering</li>
</ul>
</li>
</ul>
</li>
	<li>Next/prev duration</li>
	<li>Goto date</li>
	<li>Drag and drop</li>
	<li>Resize task/event</li>
	<li>Change view</li>
	<li>Trigger
<ul>
	<li>Add task/event</li>
	<li>Edit task/event</li>
	<li>Hide/show view more</li>
</ul>
</li>
</ul>
</li>
	<li><b>EventList</b>
<ul>
	<li>Control event rendering
<ul>
	<li>Re-render relating event</li>
</ul>
</li>
	<li><b>Calendar</b>
<ul>
	<li>Week and day view</li>
</ul>
</li>
	<li><b>CalendarMonth</b>
<ul>
	<li>Extend calendar.js</li>
	<li>Month view</li>
</ul>
</li>
	<li><b>Agenda</b>
<ul>
	<li>Agenda view</li>
	<li>EventItemGroup</li>
</ul>
</li>
</ul>
</li>
</ul>
<div></div>
<div></div>
<div>

<hr />

</div>
<div></div>
<div><b>Dashboard</b></div>
<ul>
	<li><b>Layout</b>
<ul>
	<li>Render column and module
<ul>
	<li><b>Feed-module</b></li>
	<li><b>Discussion</b>
<ul>
	<li>Extend feed-module</li>
</ul>
</li>
	<li><b>Follow</b>
<ul>
	<li>Extend feed-module</li>
	<li>Fetch feed and model
<ul>
	<li>Generate fake item for rendering</li>
</ul>
</li>
</ul>
</li>
	<li><b>Mail</b></li>
	<li><b>My-task</b></li>
	<li><b>Upcoming</b></li>
</ul>
</li>
</ul>
</li>
	<li><b>Basic module</b>
<ul>
	<li>Basic view
<ul>
	<li>Height</li>
</ul>
</li>
	<li>FilterDisplayItem</li>
	<li>Update item</li>
</ul>
</li>
	<li><b>Basic item</b></li>
</ul>