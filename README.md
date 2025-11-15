
# Roku Web Remote (External Control Protocol)

This is a single-file HTML remote control interface designed to send commands to a Roku device using the External Control Protocol (ECP).

🚀 How to Use

The Roku ECP uses simple HTTP requests, making direct control from a web page feasible, provided you are on the same local network as the Roku device.

1. Find the Roku IP Address

You need to know the IP address of your Roku device. You can find this in your Roku settings:

Go to Settings > Network > About.

Note down the IP address.

2. Configure and Connect

Open the roku_remote.html file (or whatever your main file is named) in your web browser.

Enter the Roku's IP address into the input field (e.g., 192.168.1.50).

Click the Connect button.

3. Send Commands

Once configured, clicking any button will attempt to send a command via an HTTP POST request to the following endpoint on your Roku device:

http://[Roku_IP]:8060/keypress/[COMMAND]

Example: Clicking UP sends a request to http://192.168.1.50:8060/keypress/Up.

⚠️ Connectivity Note (CORS/Security)

Unlike the Fire TV, the Roku ECP is generally not blocked by the browser's CORS policy when the web remote is running locally (e.g., loaded directly from your computer via a file:// path).

However, if you host this page on a third-party domain like GitHub Pages (https://yourusername.github.io/...), modern browsers may still block the request as a cross-origin connection, especially if the Roku's response is missing certain security headers.

Workaround for Browser Hosting (Testing Only):
You can use a browser extension to temporarily disable CORS checks for testing purposes. For Chrome, the following extension can be helpful:
[CORS Unblock Extension] (https://chromewebstore.google.com/detail/lfhmikememgdcahcdlaciloancbhjino?utm_source=item-share-cb)

Best Practice: To ensure reliable functionality, run this remote on your local machine or through a proxy that supports ECP commands.
