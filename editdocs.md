---
layout: docwithnav
---

<p>&nbsp;</p>
<script language="JavaScript">
var forwarding=window.location.hash.replace("#","");
$( document ).ready(function() {
    if(forwarding) {
    	$("#generalInstructions").hide();
    	$("#continueEdit").show();
    	$("#continueEditButton").text("Edit " + forwarding);
    	$("#continueEditButton").attr("href", "https://github.com/gertisdemo/gertisdemo.github.io/edit/master/" + forwarding)
    } else {
        $("#generalInstructions").show();
    	$("#continueEdit").hide();
    }
});
</script>
<div id="continueEdit">

<h2>Continue your editing</h2>

<p>Click the link below to edit the page you were just on. When you are done, click **Commit Changes** at the bottom of the screen. This will create a copy of the CLC documentation web site on your GitHub account called a "fork." You can make other changes in your fork after it is created, if you want. When you are ready to send us all your changes, go to the index page of your forked repository on GitHub, and select **New Pull Request** to let us know about it.</p>

<p><a id="continueEditButton" class="button"></a></p>

</div>
<div id="generalInstructions">

<h2>Edit the CLC documentation site in the cloud</h2>

<p>Click the button below to visit our repository. You can then click the "Fork" button in the upper-right area of the screen to create a copy of our site on your GitHub account called a "fork." Make any changes you want in your fork, and when you are ready to send those changes to us, go to the index page of your forked repository on GitHub, and select **New Pull Request** to let us know about it.</p>

<p><a class="button" href="https://github.com/gertisdemo/gertisdemo.github.io/">Browse this site's source code</a></p>

</div>

{% include_relative README.md %}
