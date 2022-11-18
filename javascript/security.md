- Qua security zijn er diverse dingen om op te letten:
	- **Zelf doen** (Gevoelige Informatie): Client-side JavaScript kan door iedereen via de developer tools worden uitgelezen. Gevoelige informatie moet altijd op een goed beveiligde server of in een database worden omsloten.
	- **XXS** (Cross Site Scripting): “Cross-Site Scripting (XSS) attacks are _a type of injection_, in which malicious scripts are injected into otherwise benign and trusted websites.” Oplossen met zoiets als `sanitizeHTML` bijvoorbeeld.
	- **CSRF** (Cross Site Request Forgery): “Cross-site request forgery (also known as CSRF) is a web security vulnerability that allows an attacker to induce users to perform actions that they do not intend to perform. It allows an attacker to partly circumvent the same origin policy, which is designed to prevent different websites from interfering with each other.”
	- **CORS** (Cross Site Origin Sharing): “The application server is trusting resource requests from any origin without credentials. If users within the private IP address space access the public internet then a CORS-based attack can be performed from the external site that uses the victim's browser as a proxy for accessing intranet resources.”