---
layout: default
title: Chess Battle Advanced
permalink: easter-eggs/cba
---

<a id="infinite-cba" href="https://www.youtube.com/channel/UC_xZVsCKBk9xT-fpPs5Q6mQ">CHESS BATTLE ADVANCED</a>

<script>
	(function() {
		var link = document.getElementById('infinite-cba');
		var text = "<br>CHESS BATTLE ADVANCED";
		// Create a larger chunk for efficiency
		var chunk = text.repeat(50);

		function fillPage() {
			// Get the scroll height of the document
			var scrollHeight = document.documentElement.scrollHeight;
			var scrollTop = window.pageYOffset || document.documentElement.scrollTop;
			var clientHeight = document.documentElement.clientHeight;

			// If we are within 2000px of the bottom, add more content
			if (scrollHeight - scrollTop - clientHeight < 2000) {
				link.insertAdjacentHTML('beforeend', chunk);

				// Check again immediately via RAF to ensure we fill enough
				requestAnimationFrame(fillPage);
			}
		}

		window.addEventListener('scroll', fillPage);
		window.addEventListener('resize', fillPage);

		// Initial fill
		fillPage();
	})();
</script>
