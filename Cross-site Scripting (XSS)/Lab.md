**DOM XSS in document.write sink using source location.search**
'vikash" onload="alert()'

<img width="889" alt="image" src="https://github.com/katvik001/PortSwigger-Academy-CheatSheets/assets/21978067/b020f623-4f38-4e33-94db-5a99d50b4526">

code:
=======================================================================================
<script>
function trackSearch(query) { document.write('<img src="/resources/images
/tracker.gif?searchTerms='+query+'">'); } var query = (new
URLSearchParams(window.location.search)).get('search'); if(query) { trackSearch(query); }
</script>

======================================================================================

Here's the vulnerability breakdown:

Unsanitized URL Parameter: The query variable is directly appended to the src attribute of an img tag. If an attacker crafts a URL with a search parameter containing JavaScript code, it could be executed.

Dangerous Sink (document.write): Using document.write to inject dynamic content is dangerous because it can execute script tags. If query includes something like "><script>malicious code here</script><img src=", it would close the img tag and open a script tag, leading to XSS.

To fix this vulnerability, you should:

Sanitize the query by escaping any HTML entities.
Use DOM manipulation methods (like createElement and setAttribute) instead of document.write.
If possible, avoid putting user input directly into the DOM. If you must, use textContent or other properties/methods that treat the input as text rather than HTML.

