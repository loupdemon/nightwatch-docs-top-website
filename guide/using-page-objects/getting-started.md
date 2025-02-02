---
title: Getting Started with Page Objects
description: Learn how to get started and use page objects in Nightwatch.
---

<div class="page-header"><h1>Getting Started with Page Objects</h1></div>

### Overview

To create a page object simply create an object with properties that describe the page. Each page object should be located in a separate file.

### Configure page objects location

Nightwatch reads the page objects from the folder (or folders) specified in the `page_objects_path` configuration property, e.g.:

<div class="sample-test">
<i>nightwatch.json</i><pre class="line-numbers"><code class="language-javascript">{
  "page_objects_path": ["nightwatch/pages"]
}
</code></pre></div>

The `page_objects_path` property can also be an array of folders, allowing you thus to logically split the page objects into smaller groups.


### Set the .url property

You can optionally add a `url` property that designates the page's URL. To navigate to the page, you can call the `navigate` method on the page object.

The URL will usually be defined as a string:

<div class="sample-test"><i>nightwatch/pages/examplePage.js</i>
<pre class="line-numbers" data-language="javascript"><code class="language-javascript">module.exports = {
  url: 'https://google.com',
  elements: {}
};
</code></pre>
</div>

It can also be a function in case the URL is dynamic. One use case for this is to support different test environments. You can create a function that gets called in the context of the page, thus allowing you to do:

<div class="sample-test"><i>nightwatch/pages/examplePage.js</i>
<pre class="line-numbers" data-language="javascript"><code class="language-javascript">module.exports = {
  url: function() { 
    return this.api.launchUrl + '/login'; 
  },
  elements: {}
};
</code></pre>
</div>

### Recommended content
- [Define page elements](/guide/using-page-objects/defining-elements.html)
- [Define sections](/guide/using-page-objects/defining-sections.html)
- [Add page-specific commands](/guide/using-page-objects/writing-page-specific-commands.html)
- [Concepts > Page object model](/guide/concepts/page-object-model.html)