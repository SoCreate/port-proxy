## port-proxy

## Installation

    npm install -g port-proxy

Note: *You need to have [Node.js](https://nodejs.org/) installed.*

## Usage
If you installed **port-proxy** as a global module:

    port-proxy localPort to proxyPort

For instance, if your application's port is 51123, run this in the Command Prompt:

    port-proxy 51123 to 3000

The program will list the external addresses you can use for testing 
your application on remote devices.

## Advanced usage (VPN, virtual hosts, etc.)
You can also use **port-proxy** to expose an server instance 
running on a **different host** accessible through VPN, like this:

    port-proxy host:port to proxyPort

For instance, let's conside this scenario:
- the application is running on 192.168.96.3:5000 and 
  **it only accepts connections from clients within a VPN**;
- your development machine has a network interface within the same VPN 
and another publicly accessible one (192.168.0.102);
- **you need to test the application from mobile devices without having to add those devices to the VPN**.

By running this in the Command Prompt:

    port-proxy 192.168.96.3:5000 to 3000

...you'll be able to access the application by pointing the mobile devices to 192.168.0.102:3000.

## Limitations

`port-proxy` doesn't work in scenarios involving integrated Windows 
authentication.

## How does it work
It's proxying the HTTP traffic on `localPort` to `proxyPort` on all the available network 
interfaces and it's also [changing the origin of the host header](https://github.com/nodejitsu/node-http-proxy/blob/master/lib/http-proxy.js#L44), 
allowing you to test web applications hosted on various remote devices 
(mobile devices, other desktops, etc.).
