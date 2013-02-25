<div class="legible-width">
  <p><a href="http://socketo.me/">Ratchet</a> is a websocket server written in php. It's a platform that enables the server and the client to communicate freely. Unlike with regular http, which relies on the client asking for information and the server replying, ws (the websocket protocol) allows the server to start a two-way conversation. The best example is a chat server:</p>
	<ol>
		<li>Jack & Jill visit your chat page from seperate computers</li>
		<li>Jack enters "hello" in to a form and clicks the submit button</li>
		<li>The server receives the request, and notifies Jill's computer</li>
		<li>Jill's computer receives Jack's salutation from the server, and a fairy tale begins...</li>
	</ol>
	<p>Websockets take care of the third part of that interaction; something we haven't been able to do in regular web programming before.</p>
	<p><i>It's hard to overstate how important websockets are. They will revolutionise the way we write web apps.</i></p>

	<p>This tutorial is in three parts, and is intended to get you up and hacking. It's by no means a 'best-practice' guide - I have a week's experience with websockets, so treat this as a leg-up from someone who's gone before, rather than good advice =].</p>

	<p>This, the first part, is an introduction. It will give you a brief overview of what we'll be making. The <a title="Coming real soon!">second part</a> is a step-by-step tutorial to guide you through setting up the necessary components, and the <a title="Watch this space">third</a> part covers writing a websocket app.</p>

	<p>I'm going to be installing ratchet on a linux server. I'm told it's possible on Windows, but I tried and gave up pretty quickly. I'll be using Ubuntu, because I am a linux noob, but the instructions should be exactly the same for any debian-based distro. If you find any errors then please either let me know in the comments, or <a href="https://gist.github.com/MauMaGau/5034237">fork</a> this document and submit a pull request.</p>

	<p>Ok, pull your work boots on, it's time to get down to business</p>

	<p>Ratchet is made up of several components, together they fulfill the following roles:</p>
	<dl class="dl-horizontal">
		<dt>Websocket server</dt>
		<dd>Y'know Apache? It listens for a request and replies with data. A websocket server listens for a request from a client, and then opens a connection. From then on, the client and the server can send each other data without the client having to requesting it first.</dd>
		<dt>Client code</dt>
		<dd>We need some code on the client's computer to talk to our server.</dd>
		<dt>Server code</dt>
		<dd>And we need code on the server to.. y'know, do stuff! Save stuff to a database, get stuff from a database, find a cute picture of a kitten. All the wonderful things we developers do.</dd>
	</dl>

	<p>Now, there are two ways build a web socket app:</p>
	<dl class="dl-horizontal">
		<dt>Natively</dt>
		<dd>Everything uses websockets to communicate</dd>
		<dt>With Apache</dt>
		<dd>We still use our regular web server for most things, but harness websockets for live events. (you can use another web server like IIS if you want, I won't tell anyone).</dd>
	</dl>

	<p>For this tutorial, and I expect for the foreseeable future of my development career, we're going to go with the second option.</p>
	<p>Firstly, it would be a huge upheaval to start writing web apps purely using websockets. The current system of request>reply is ingrained in so much of what we do (our frameworks, our libraries, our mindsets) that we'd be starting almost from zero.</p>
	<p>Secondly, websockets isn't supported by every browser yet. And by every browser, I mean older browsers. Modern <a href="http://caniuse.com/websockets">browser support</a> is actually fantastic - IE10 supports websockets, as do most mobile browsers (and of course Chrome, Firefox, Safari, Opera). So for mainstream web apps, websockets are gonna be a nice-to-have, but shouldn't be required (just like JavaScript used to be).</p>

	<p>So, our new web app is going to be running off two servers - the regular Apache server, and the brand-spanking new websockets server. But don't worry, we're not going to need any extra hardware (until our app starts trending on HN at least). A websocket server will quite happily live in the same house as Apache. In fact, the two of them will become best buds and talk to each other regularly. Together with the client, they'll form a three-way partnership -</p>
	<dl class="dl-horizontal">
		<dt>Client to Apache</dt>
		<dd>Apache serves up the regular web page</dd>
		<dt>Client to websocket server</dt>
		<dd>Websocket server starts a two-way conversation with the client</dd>
		<dt>Apache to websocket server</dt>
		<dd>We can send a notification our from our regular web app to the websocket server, and in turn, the client</dd>
	</dl>

	<p>And thus, the holy triad is born. The power of our standard LAMP stack, the interactivety of client JavaScript, and the realtime awesomness of websockets.</p>

	<p><i>If you have anything to add, please leave a comment or 
</div>
