---
layout: page
---
<div>	
<button class="btn btn-default pull-right" onclick="loadResume();">Resume</button>
<button class="btn btn-default pull-right" onclick="loadImage();">WordCloud</button>
</div>
<img id="testimage" src="https://sdasara95.github.io/assets/wordcloud.png" width="706px" height="449px" />
<iframe id="testiframe" src="https://sdasara95.github.io/Satya_Dasara_Resume_DS.pdf" width=”100%” height=”100%” />

<input type="button" value="Load" onclick="loadPage();"/>
<iframe id="testiframe" width="400" height="300" src="">
<script>
function loadResume() {
     document.getElementById('testiframe');
}
function loadImage() {
	document.getElementById('testimage');
}
</script>