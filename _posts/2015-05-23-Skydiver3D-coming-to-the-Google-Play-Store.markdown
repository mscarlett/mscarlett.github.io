---
layout: post
title: Skydiver 3D coming to the Google Play Store
category: Coding
tags: android gaming libgdx opengl
year: 2015
month: 5
day: 23
published: true
summary: This is my first attempt at a 3D video game using libgdx, an open-source Java framework for cross-platform game development. 
image: skydiver.png
---

<div class="row">	
	<div class="span9 columns">
		<iframe width="420" height="315" src="https://www.youtube.com/embed/-NmvwspVKGo" frameborder="0" allowfullscreen></iframe>
		<h2>Preface</h2>
		<p>This past year, I have been experimenting with Java/Android game development by working on a skydiving game. The game uses <a href="http://libgdx.badlogicgames.com/" target="_blank">Libgdx</a>, which provides a unified API that runs on many platforms and abstracts away the low-level graphics implementation to allow for rapid prototyping. The library uses the JNI to provide access to native C code for OpenGL graphics rendering and accelerated math operations. Libgdx also features an API designed to avoid JVM or Android garbage collection by using a custom implementation for loading and deletion game resources. This post will explore the Libgdx framework briefly and provide more details regarding the game that I am planning to release.</p>
        <p>
            <ul>
                <li><a href="http://libgdx.badlogicgames.com/documentation.html" target="_blank">Libgdx Getting Started</a></li>
                <li><a href="http://www.github.com/libgdx/libgdx" target="_blank">GitHub Libgdx Repo</a></li>
                <li><a href="http://libgdx.badlogicgames.com/gallery.html" target="_blank">Gallery of Libgdx Games</a></li>
            </ul>
        </p>
		<h2>How it Works</h2>
		<figure>
		    <img src="https://raw.githubusercontent.com/wiki/libgdx/libgdx/images/modules-overview.png">
		    <figcaption><i>Overview of Libgdx modules (<a href="https://github.com/libgdx/libgdx/wiki/Modules-overview" target="_blank">from wiki</a>)</i></figcaption>
		</figure>
		<p>Libgdx comprises several modules for input, graphics, files, audio, networking, game logic, and math/physics. It enables you to write code once and deploy it to multiple platforms without modification. High-level APIs simplify the rendering of 2D and 3D graphics, however Libgdx gives the option of working with OpenGL directly using Java interfaces. More information is available at the <a href="https://github.com/libgdx/libgdx/wiki" target="_blank">Libgdx wiki</a>.</p>
        <h2>Creating the Skydiver 3D game</h2>
		<p>The game consists of a skydiver who jumps off a plane from 14,000 feet and soars to the ground, earning points for collecting rings and stars. The player can optionally go faster by pressing a lightning bolt icon to get a bonus. Once the skydiver reaches an altitude of 3,000 feet, the player is prompted to open the parachute while an accuracy bar is displayed on the screen. Points are awarded based on the timing of the parachute opening. Once the parachute is opened, the player lands the skydiver on a target as close to the center as possible.</p>
        <p>The skydiver is represented by a 3D model which I created in <a href="https://www.blender.org/" target="_blank">Blender</a>. The model contains animations for opening the parachute and changing the pose of the skydiver to a diving position. The ring and star collectibles are represented by 2D images which are rendered using a perspective projection model, via the usage of a "Decal" class that represents a sprite in 3D space. The terrain is represented by a mesh of 3D locations and triangles. The <a href="http://en.wikipedia.org/wiki/Diamond-square_algorithm" target="_blank">diamond-square algorithm</a> is used for the procedural generation of a heightmap to create more realistic detail, and a custom OpenGL shader is used to apply a fog effect at high altitudes and allow blending of textures. Originally I had 3D models for the plane and the target, but these caused slow rendering performance in Android that caused the game to crash unexpectedly. The target is now a 2D texture that is generated procedurally. I am also working on the procedural generation of clouds using <a href="http://en.wikipedia.org/wiki/Perlin_noise" target="_blank">Perlin noise</a>, which is ideal for randomly generating natural textures when memory is limited.</p>
        <p>I implemented the model-view-controller design pattern to abstract away game logic from user input and rendering. The "model" consists of a World class which encapsulates the game objects and stores the state of the world. Libgdx is used to perform rendering and user input based on the current state of the world. A heads-up-display is used to show the current game status.</p>
		<p>Overall, the game is organized into several screens which represent the user interface for the current activity and utilize a common base class. Transitions between each user interface is managed by switching the current screen. A single screen represents the user interface displayed when skydiving, and a series of menu screens allow navigation throughout the game and the changing of settings.</p>
        <p>A single class is used to manage loading game resources such as textures, models, and sounds so that resources are centralized within the game. Helper classes are also used to manage the playing of music and sound effects, store user preferences, and generate text dynamically from a FreeType font.</p>
        <p>One of the main issues that I encountered was that the behaviour of the game on Android varied significantly from desktop performance due to differences in processor speed and memory, so I would recommend anyone planning to use Libgdx for Android to test the game regularly on a real Android device and not an emulator. Additional care must be taken to reduce memory usage.</p>
        <p>The source code of the game is available at my <a href="https://github.com/mscarlett/Skydiver-3D" target="_blank">Github repo</a> if you want to try it yourself. I also hope to release the game on the Google Play Store in a month.</p>
	</div>
</div> 

<div class="row">	
	<div class="span9 column">
			<p class="pull-right">{% if page.previous.url %} <a href="{{page.previous.url}}" title="Previous Post: {{page.previous.title}}"><i class="icon-chevron-left"></i></a> 	{% endif %}   {% if page.next.url %} 	<a href="{{page.next.url}}" title="Next Post: {{page.next.title}}"><i class="icon-chevron-right"></i></a> 	{% endif %} </p>  
	</div>
</div>

<div class="row">	
    <div class="span9 columns">    
		<h2>Comments Section</h2>
	    <p>Feel free to comment on the post but keep it clean and on topic.</p>	
		<div id="disqus_thread"></div>
		<script type="text/javascript">
			/* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
			var disqus_shortname = 'mscarlett'; // required: replace example with your forum shortname
			var disqus_identifier = '{{ page.url }}';
			var disqus_url = 'http://mscarlett.github.io{{ page.url }}';
			
			/* * * DON'T EDIT BELOW THIS LINE * * */
			(function() {
				var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
				dsq.src = 'http://' + disqus_shortname + '.disqus.com/embed.js';
				(document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
			})();
		</script>
		<noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
		<a href="http://disqus.com" class="dsq-brlink">blog comments powered by <span class="logo-disqus">Disqus</span></a>
	</div>
</div>

<!-- Twitter -->
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>

<!-- Google + -->
<script type="text/javascript">
  (function() {
    var po = document.createElement('script'); po.type = 'text/javascript'; po.async = true;
    po.src = 'https://apis.google.com/js/plusone.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(po, s);
  })();
</script>