****
10/3/2024

Cross Site Request Forgery (CSRF)
- user logs in
- visits another site containing the attack
- sends user auth cookie with request $\rightarrow$ transaction will be fulfilled 
$\rightarrow$ cookie auth is insufficient when side effects occur

Solution
- Secret Token Validation
- Referer Validation
- Custom HTTP header

XSS
- Reflected XSS
	- attacker script is reflected back to the user as part of a page from the victim site
- Stored XSS
	- the attacker stores the malicious code in a resource
- Others

scripts do not have to be in only $<script>$
****
10/10/2024

We want to isolate code from different sources

Same Origin Policy (SOP)

Content Security Policy (CSP)
- prevent and limit damage of XSS
- inland and eval are blocked by default
- but can enable it
HTML5 Sandbox
Idea: restrict frame actions
Directive sandbox 
- ensures iframe has unique origin and cannot execute Javascript
- ensures iframe has unique origin
Sandbox: remove all permissions and then allow JavaScript, popups, form submission, and twitter.com cookies

inland script: javascript embedded in the attack

Cross-Origin Resource Sharing (CORS)
- amazon.com can whitelist aws.com so aws.com makes requests

