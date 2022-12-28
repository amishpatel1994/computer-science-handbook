## How does a web page get rendered when you enter "example.com" on web browser?

1. You open your web browser and type a URL into the address bar. The URL consists of a protocol (such as "http" or "https"), a domain name (such as "example.com"), and possibly a path to a specific resource on the server (such as "/about").

2. Your computer looks up the IP address for the domain name specified in the URL using the Domain Name System (DNS). DNS is a distributed database that maps domain names to IP addresses, allowing computers to access websites and other online resources using familiar, easy-to-remember names. Here's a detailed explanation of the DNS resolution process:

    - Your computer sends a request to a DNS resolver. A DNS resolver is a program that is responsible for translating domain names into IP addresses.
    
    - The DNS resolver first checks its local cache to see if it already has the IP address for the requested domain name. If it does, it returns the IP address to the computer, and the process is complete.
    
    - If the DNS resolver does not have the IP address in its cache, it sends a request to a local DNS server. A DNS server is a program that is responsible for storing and managing DNS records, which contain information about domain names and their corresponding IP addresses.
    
    - The local DNS server checks its own cache and, if it has the IP address for the requested domain name, it returns it to the DNS resolver. If it does not have the IP address in its cache, it sends a request to a root DNS server.
    
    - A root DNS server is a server that is responsible for directing DNS requests to the appropriate top-level domain (TLD) server. A TLD is the last part of a domain name (such as ".com" or ".net"). There are 13 root DNS servers in total, and they are distributed around the world to ensure fast and reliable DNS resolution.
    
    - The root DNS server receives the request and looks up the IP address of the appropriate TLD server based on the domain name's TLD. It then sends a request to the TLD server.
    
    - The TLD server receives the request and looks up the IP address of the domain's name server based on the domain name. It then sends a request to the name server.
    
    - The name server receives the request and looks up the IP address of the domain based on the domain name. It then sends the IP address back to the TLD server.
    
    - The TLD server sends the IP address back to the root DNS server.
    
    - The root DNS server sends the IP address back to the local DNS server.
    
    - The local DNS server sends the IP address back to the DNS resolver.

    - The DNS resolver sends the IP address back to the computer.

This process may involve multiple DNS servers and multiple requests before the final IP address is returned to the computer. However, the process is typically very fast, as DNS servers use caching to store frequently-requested domain names and their corresponding IP addresses, allowing subsequent requests to be resolved more quickly.

3. Your computer sends a request for the specified resource to your router, which is responsible for connecting your computer to the internet.

4. The router receives the request and uses its routing table to determine the most efficient path for the request to take.

5. The router sends the request to your internet service provider (ISP), which is responsible for connecting you to the internet.

6. The ISP receives the request and uses its own routing table to determine the most efficient path for the request to take.

7. The ISP sends the request to the appropriate server on the internet using the IP address that was resolved in step 2.

8. The server receives the request and processes it using the appropriate communication protocol (such as HTTP).

9. The server retrieves the requested resource from its database or file system and prepares it for transmission.

10. The server sends the requested resource back to your computer via the ISP and router.

11. Your web browser receives the requested resource and renders it for you to view.

This process occurs in a matter of milliseconds, allowing you to access the requested resource almost instantly.

### DNS Resolvers

Internet service providers (ISPs): Many ISPs provide DNS resolution services to their customers as part of their internet service package. For example, Comcast, AT&T, and Verizon all offer DNS resolution services to their customers.

Public DNS resolvers: There are also many public DNS resolvers that can be used by anyone, regardless of their ISP. Some examples include Google Public DNS, Cloudflare DNS, and OpenDNS. These DNS resolvers are usually free to use and are often faster and more secure than the DNS resolution services provided by ISPs.

Corporate DNS resolvers: Large corporations often operate their own DNS resolvers for use by their employees. This can be more efficient and secure than relying on a public DNS resolver, as it allows the corporation to control the DNS resolution process and customize it to meet their specific needs.

It's worth noting that you can choose which DNS resolver you use on your computer or device. Many operating systems allow you to specify a preferred DNS resolver in the network settings. Alternatively, you can use a third-party DNS resolver such as those listed above by changing the DNS settings on your router.
