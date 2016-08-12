---
---
<style>
h2, h3, h4 {
  border-bottom: 0px !important;
}
.colContainer {
  padding-top:2px;
  padding-left: 2px;
  overflow: auto;
}
#samples a {
  color: #000;
}
.col3rd {
  display: block;
  width: 250px;
  float: left;
  margin-right: 30px;
  margin-bottom: 30px;
  overflow: hidden;
}
.col3rd h3, .col2nd h3 {
  margin-bottom: 0px !important;
}
.col3rd .button, .col2nd .button {
  margin-top: 20px;
  border-radius: 2px;
}
.col3rd p, .col2nd p {
  margin-left: 2px;
}
.col2nd {
  display: block;
  width: 400px;
  float: left;
  margin-right: 30px;
  margin-bottom: 30px;
  overflow: hidden;
}
.shadowbox {
  display: inline;
  float: left;
  text-transform: none;
  font-weight: bold;
  text-align: center;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
  line-height: 24px;
  position: relative;
  display: block;
  cursor: pointer;
  box-shadow: 0 2px 2px rgba(0,0,0,.24),0 0 2px rgba(0,0,0,.12);
  border-radius: 10px;
  background: #fff;
  transition: all .3s;
  padding: 16px;
  margin: 0 16px 16px 0;
  text-decoration: none;
  letter-spacing: .01em;
}
.shadowbox img {
    min-width: 150px;
    max-width: 150px;
    max-height: 50px;
}
</style>
<div class="colContainer">
  <div class="col3rd">
    <h3>What is CLC?</h3>
    <p>Cloud Load Control (CLC) is an out-of-the-box solution for companies that are looking for a preassembled and enterprise-ready distribution of tools for provisioning and managing clusters and containers on top of OpenStack-based cloud computing platforms.</p>
    <a href="/docs/clc-overview/intro/" class="button">Read the Overview</a>
  </div>
  <div class="col3rd">
    <h3>Hello Node!</h3>
    <p>In this quickstart, a Kubernetes instance is created that stands up a simple “Hello World” application using `Node.js`. In just a few minutes you will deploy an application to a Kubernetes cluster.</p>
    <a href="/docs/hellonode/" class="button">Get Started</a>
  </div>
  <div class="col3rd">
    <h3>Guided Tutorial</h3>
    <p>If you’ve completed the quickstart, a great next step is ...</p>
    <a href="/docs/walkthrough/" class="button">Walkthrough</a>
  </div>
</div>

## Samples

<div id="samples" class="colContainer">
<!--a href="/docs/getting-started-guides/meanstack/" class="shadowbox">
  <img src="/images/docs/meanstack/image_0.png"><br/>MEAN Stack
</a-->
<a href="https://github.com/kubernetes/kubernetes/tree/{{page.githubbranch}}/examples/guestbook" target="_blank" class="shadowbox">
  <img src="/images/docs/redis.svg"><br/>Guestbook + Redis
</a>
<a href="https://github.com/kubernetes/kubernetes/tree/{{page.githubbranch}}/examples/cassandra" target="_blank" class="shadowbox">
  <img src="/images/docs/cassandra.svg"><br/>Cloud Native Cassandra
</a>
<a href="https://github.com/kubernetes/kubernetes/tree/{{page.githubbranch}}/examples/mysql-wordpress-pd/" target="_blank" class="shadowbox">
  <img src="/images/docs/wordpress.svg"><br/>WordPress + MySQL
</a>
</div>

<p>&nbsp;</p>
<p>&nbsp;</p>

<div class="colContainer">
  <div class="col2nd">
  <h3>Contribute to Our Documentation</h3>
  <p>The documentation for CLC is open-source, just like the code for CLC itself. The documentation is on GitHub Pages, so you can fork it and it will auto-stage on username.github.io, previewing your changes!</p>
  <a href="/editdocs/" class="button">Write Documentation for CLC</a>
  </div>
  
</div>
