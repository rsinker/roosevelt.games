---
title: Home
layout: home
tags: page
modified: 2022-01-09 00:00:00
order: 1
---
<div class = "">
<div class = ""><img class="rounded-2xl border border-gray-400 border-2 mb-12 md:w-1/2 mx-auto" src = "/images/rooseveltcover.jpg"></div>
<h1 class="title mb-12 text-center sm:text-left">
Hey there, I'm Roosevelt!
</h1>
<div class="text-xl md:text-2xl">
	<p class = "mb-8">I am a programmer, game designer, and tools engineer with a passion for creating innovative gameplay experiences. I believe in gameplay-first design and building teams that bring together diverse skillsets to make exceptional games.</p>
	<a href = "mailto:hey@roosevelt.games" class = "highlight underline"> Let's build something better, together</a>
</div>

<h1 class = "title text-center sm:text-left"> Featured Project </h1>
{% for project in collections.projects %}
{% if project.data.featured %}
<a href = "/projects/{{project.data.title | slugify}}">
<div class = "p-4 hover:bg-stone-100 rounded-xl mb-12">
<div class = "bg-slate-50 rounded-2xl border border-gray-400 border-2 grid grid-cols-1 grid-rows-2 md:grid-rows-1 md:grid-cols-2 overflow-hidden">
	<div class = "bg-no-repeat bg-center bg-cover" style = "background-image: url('/images/{{project.data.image}}');">
	</div>
	<div class = "bg-amber-400">
		<div class = "m-3 md:m-8 testspace">
			<h2 class = "text-4xl font-bold text-slate-800 text-center">{{project.data.title}} </h2>
			<p class = "highlight font-bold text-center text-2xl md:mb-8"> {{project.data.role}} </p>
			<p class = "text-slate-800"> {{project.data.summary}} </p>
			<p>  </p>
		</div>
	</div>
</div>
</div>
</a>
{% endif %}
{% endfor %}

<h1 class = "title text-center sm:text-left mx-6 mt-24">Featured Work Experience </h1>
<div class = "my-4 bg-slate-50 rounded-2xl border border-gray-400 border-2 md:pb-8 py-4 md:py-2">
<h2 class = "hidden md:block title text-4xl mx-6"> <a href = "https://rawthrills.com" class = "highlight underline" target="_blank">Raw Thrills</a> | Programming & Design Intern</h2>
<h2 class = "md:hidden text-center title !text-4xl mx-6 !my-2"><a href = "https://rawthrills.com" class = "highlight underline" target="_blank">Raw Thrills</a></h2>
<h2 class = "md:hidden text-center title !text-2xl mx-2 !my-2">Programming & Design Intern</h2>
<p class = "text-center sm:text-left text-xl mt-0 mb-2  mx-6 font-style: italic">Summer 2025</p>
<p class = "text-center sm:text-left text-lg mb-4 mx-6">Led design on an original multiplayer arcade game from a concept provided by my mentor, award-winning game designer Eugene Jarvis (Robotron 2084, Defender, Crusin' USA).
</p>
<ul class = "list-disc mx-8 mb-4">
    <li><span class="highlight">Game Design</span>: Designed core gameplay loop, objectives, hazards, and other major gameplay elements.</li>
    <li><span class="highlight">AI Players</span>: Created a complex utility-based AI that allows for human-players to be replaced with an AI while keeping teams balanced. AI is able to perform strategic team-based moves with both humans and other AIs.</li>
    <li><span class="highlight">Arcade Inputs</span>: Programmed a custom multiplayer input system, allowing for a large, yet variable, number of players to join/leave the game and have their inputs persist across multiple games.</li>
	<li><span class="highlight">QA and Usability</span>: Ran playtests and adjusted the game's design to balance feedback and client needs.</li>
	<li><span class="highlight">Feedback</span>: Gave weekly presentations to Eugene Jarvis, taking his feedback on how I was executing his original vision and making necessary adjustments to the game.</li>
</ul>
</div>
<a href = "https://linkedin.com/in/sinker" class = "highlight underline text-xl md:text-2xl">For my full resume, visit my LinkedIn</a>

{# 
<h1 class = "title text-center sm:text-left"> Lastest Blog Post </h1>

{% set latest_posts = collections.posts | reverse %} {% for post in latest_posts.slice(0,1) %}

<a href = "{{post.url}}">
<div class = "p-4 hover:bg-stone-100 rounded-xl">
<div class = "bg-slate-50 rounded-2xl border border-gray-400 border-2 grid grid-cols-1 grid-rows-2 md:grid-rows-1 md:grid-cols-2 overflow-hidden">
	<div class = "bg-amber-400 row-start-2 md:row-start-1">
		<div class = "m-3 md:m-8 testspace">
			<h2 class = "text-4xl font-bold text-slate-800 text-center">{{post.data.title}} </h2>
			<p class = "text-slate-800 mt-4"> {{post.data.summary}} </p>
			<p>  </p>
		</div>
	</div>
	<div class = "bg-no-repeat bg-center bg-cover" style = "background-image: url('/images/blog/{{post.data.image}}');">
	</div>
</div>
</div>
</a>
{% endfor %}
#}
</div>