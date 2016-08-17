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

<h2>Continue your Editing</h2>

<p>Click the link below to edit the page you were just on. This will send you to the CLC documentation web site where you can create a copy of the site called a "fork". Make your changes, and when you are done, enter a title and a short description of you changes, and click **Propose file change** at the bottom of the screen. You can either instantly create a pull request for your changes, or continue with making other changes in your fork. When you are ready to send us all your changes, go to the index page of your forked repository on GitHub, and select **New Pull Request** to let us know about it.</p>

<p><a id="continueEditButton" class="button"></a></p>

</div>
<div id="generalInstructions">

<h2>Edit the CLC Documentation in the Cloud</h2>

<p>Click the link below to visit the CLC documentation repository on GitHub where you can view the source code of this site.</p>

<p><a class="button" href="https://github.com/gertisdemo/gertisdemo.github.io/">CLC documentation repository</a></p>

</div>

{% include_relative README.md %}
