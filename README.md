# cloudflare-lab-assignment
Section A:

Web Server Implementation and SSL Setup (Technical Requirements 1,2 and 3)

a) "ssl_setup" folder contains the cerificate file and private key.Also it contains the SSL settings files to limit the SSL connection to TLS1.2 and above with ECC based ciphers on the origin server.
b) "web_server_config" folder contains the Virtual Host configuration on Apache for host "www1.asinglalabs.com" which is listening on port 443 with SSL certificate,php and html pages deployed.
c) index.php inside "web_server_config" folder is the php page on the web server that contains the logic to returns all HTTP request
headers in the body of the HTTP response.
d) login.html page is the login page inside "secure" directory of the Document Root where the Access with One time passowrd has been implemnted.
e) Edge certificate on the Cloudflare SSL settings to deploy a generic wildcard certicate with TLS1.2 and above protocols allowed with ECC based ciphers

Section B: (Technical Requirement 4)

Argo Tunnels Implementation:

a) Cloudflared deamon was installed on the webserver (ubuntu).
b) Setup authentication using token for tunnels to map to my account ID.
c) created and configured tunnels.
d) running the  tunnel and routing the traffic using CName entry for www1.asinglalabs.com poiniting to tunnel subdomain - "7bfc8ab4-eef5-42ff-b2c1-00241a2d3962.cfargotunnel.com"

"argotunnels_setup" folder contains all the files for ArgoTunnels implementation.

Please refer the file config.yaml file which have all the details defined for the fine-grained control over how an instance of cloudflared will operate.

Section C: (Technical Requirement 5)

Cloudflare Workers implementation related files:
The worker script implementation was done in javascript.

wrangler.toml:

Template file which contains all the details about Worker run time environment,deployment and other details.

index.js:

Actual logic to cover the technical requirement 5.

a) Perform a redirect to "https://developers.cloudflare.com/workers/about/" whenever the
request is made using cURL.The route for cloudflare logic is confined to "https///www1.asinglalabs.com/test/*"

b) The Logic bypasses this redirect if the client
request includes a special cookie+value pair (cookie name: "cf-noredir", cookie value: "true") and returns a custom html page from the edge as the response.





