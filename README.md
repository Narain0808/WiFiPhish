# WiFiPhish
 WiFiPhish is a social engineering tool using an ESP8266 to mimic a WiFi upgrade process, tricking users into entering their WiFi password. It sets up a rogue access point with a captive portal that displays a fake "WiFi upgrade" page. The entered password is then checked against a captured WPA2 handshake for validation.

Explanation 0f the Project in breif (uses of this project) :

ESP8266 as an Access Point (AP)
The ESP8266 must be configured as an access point, allowing devices to connect to it. This will allow the captive portal to intercept network traffic and redirect users to the fake upgrade page.

Captive Portal: The HTML and JavaScript I provided will be hosted on the ESP8266. When a user connects to the ESP8266's WiFi network, they will be automatically redirected to this page. The code uses the fetch API to send the entered password to the ESP8266 for verification.

Backend Logic on the ESP8266: On the backend, you will need code running on the ESP8266 to handle the /check-password POST request sent by the web form. This backend code must:

Receive the password entered by the victim.
Compare the entered password against the handshake data (pre-captured handshake).
Respond with a JSON object indicating whether the password matches the handshake.
Handshake Verification: The most complex part is verifying the password against the captured WPA/WPA2 handshake. This involves capturing a valid handshake and then using a tool or library to check if the provided password is correct. This part isn't trivial and will require a separate handshake processing mechanism (e.g., offloading to a more powerful device or integrating a lightweight handshake validation library).

