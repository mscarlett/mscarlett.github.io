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
		<p>This past year, I have been experimenting with Java/Android game development by working on a skydiving game. The game uses <a href="http://libgdx.badlogicgames.com/" target="_blank">Libgdx</a>, which provides a unified API that runs on many platforms and abstracts away the low-level graphics implementation to allow for rapid prototyping. The library uses the JNI to provide access to native C code for OpenGL graphics rendering and accelerated math operations. Libgdx also features an API designed to avoid JVM garbage collection by using a custom implementation for loading and deletion game resources. This post will explore the Libgdx framework in depth and provide more details regarding the game that I am planning to release.</p>
        <p>
            <ul>
                <li><a href="http://libgdx.badlogicgames.com/documentation.html" target="_blank">Libgdx Getting Started</a></li>
                <li><a href="http://www.github.com/libgdx/libgdx" target="_blank">GitHub Libgdx Repo</a></li>
                <li><a href="http://libgdx.badlogicgames.com/gallery.html" target="_blank">Gallery of Libgdx Games</a></li>
            </ul>
        </p>
		<h2>How it Works</h2>
		<figure>
		    <img src="https://raw.githubusercontent.com/wiki/libgdx/libgdx/images/modules-overview.png" width="420">
		    <figcaption>Diagram of Libgdx modules from <a href="https://github.com/libgdx/libgdx/wiki/Modules-overview" target="_blank">wiki page</a></figcaption>
		</figure>
		<p>Libgdx comprises several modules for input, graphics, files, audio, networking, game logic, and math/physics. It enables you to write code once and deploy it to multiple platforms without modification. High-level APIs simplify the rendering of 2D and 3D graphics, however Libgdx gives the option of working with OpenGL directly using Java interfaces.</p>
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