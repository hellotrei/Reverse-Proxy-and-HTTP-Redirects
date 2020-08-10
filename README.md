<!--
*** Thanks for checking out this README Template. If you have a suggestion that would
*** make this better, please fork the repo and create a pull request or simply open
*** an issue with the tag "enhancement".
*** Thanks again! Now go create something AMAZING! :D
-->





<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">Reverse-Proxy-and-HTTP-Redirects</h3>

  <p align="center">
    An awesome README template to jumpstart your projects!
    <br />
    <a href="https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git">View Demo</a>
    ·
    <a href="https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git/issues">Report Bug</a>
    ·
    <a href="https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git/issues">Request Feature</a>
  </p>
</p>



<!-- TABLE OF CONTENTS -->
## Table of Contents

* [About the Project](#about-the-project)
  * [Reverse Proxy Solutions](#Reverse-Proxy-Solutions)
* [Getting Started HTTP Reverse Proxy](#Getting-Started-HTTP-Reverse-Proxy)
  * [Creating Mapping](#Creating-Mapping-Rules-for-HTTP-Requests)
  * [Enabling HTTP Reverse Proxy](#Enabling-HTTP-Reverse-Proxy)
  * [Setting Optional](#Setting-Optional-HTTP-Reverse-Proxy-Options)
  * [Redirecting](#Redirecting-HTTP-Requests)
  * [Example](#Example)

* [License](#license)
* [Contact](#contact)
* [Acknowledgements](#acknowledgements)



<!-- ABOUT THE PROJECT -->
## About The Project

[![Product Name Screen Shot][product-screenshot]](https://docs.trafficserver.apache.org/en/latest/_images/revproxy.jpg)

As a reverse proxy cache, Traffic Server serves requests on behalf of origin servers. Traffic Server is configured in such a way that it appears to clients like a normal origin server.

Here's why:

With forward proxy caching, Traffic Server handles web requests to origin servers on behalf of the clients requesting the content. Reverse proxy caching (also known as server acceleration) is different because Traffic Server acts as a proxy cache on behalf of the origin servers that store the content. Traffic Server is configured to behave outwardly as origin server which the client is trying to connect to. In a typical scenario the advertised hostname of the origin server resolves to Traffic Server, which serves client requests directly, fetching content from the true origin server when necessary.


### Reverse Proxy Solutions
There are many ways to use Traffic Server as a reverse proxy. Below are a few example scenarios.

* Offload heavily-used origin servers.

* Deliver content efficiently in geographically distant areas.

* Provide security for origin servers that contain sensitive information.



<!-- GETTING STARTED -->
## Getting Started HTTP Reverse Proxy

In reverse proxy mode, Traffic Server serves HTTP requests on behalf of a web server. The figure below illustrates how Traffic Server in reverse proxy mode serves an HTTP request from a client browser.

[![Product Name Screen Shot][product-screenshot2]](https://docs.trafficserver.apache.org/en/latest/_images/httprvs.jpg)

The figure above demonstrates the following steps:

* A client browser sends an HTTP request addressed to a host called www.host.com on port 80. Traffic Server receives the request because it is acting as the origin server (the origin server’s advertised hostname resolves to Traffic Server).

* Traffic Server locates a map rule in the remap.config file and remaps the request to the specified origin server [realhost.com](realhost.com).

* If the request cannot be served from cache, Traffic Server opens a connection to the origin server (or more likely, uses an existing connection it has pre-established), retrieves the content, and optionally caches it for future use.

* If the request was a cache hit and the content is still fresh in the cache, or the content is now available through Traffic Server because of step 3, Traffic Server sends the requested object to the client from the cache directly.




### Creating Mapping Rules for HTTP Requests

1. Enter the map and reverse-map rules into (`remap.config.`) 
2. Run the command  (`traffic_ctl config reload`) to apply the configuration changes.


### Enabling HTTP Reverse Proxy

To enable HTTP reverse proxy:

1. Edit  (`proxy.config.reverse_proxy.enabled`) in  

```sh
CONFIG proxy.config.reverse_proxy.enabled INT 1
```

2. Run the command  (`traffic_ctl config reload`) to apply the configuration changes.

### Setting Optional HTTP Reverse Proxy Options

Traffic Server provides several reverse proxy configuration options in (`records.config.`)  that enable you to:

* Configure Traffic Server to retain the client host header information in a request during translation. See 
`proxy.config.url_remap.pristine_host_hdr.`

* Configure Traffic Server to serve requests only to the origin servers listed in the mapping rules. As a result,
  requests to origin servers not listed in the mapping rules are not served. See
`proxy.config.url_remap.remap_required.`

* Specify an alternate URL to which incoming requests from older clients ,such as ones that do not provide (`Host`)
headers, are directed. See 
`proxy.config.header.parse.no_host_url_redirect.`

### Redirecting HTTP Requests

You can configure Traffic Server to redirect HTTP requests without having to contact any origin servers. For 
example, if you redirect all requests for (`http://www.ultraseek.com`) to (`http://www.server1.com/products/portal/search/`), 
then all HTTP requests for (`www.ultraseek.com`) go directly to (`www.server1.com/products/portal/search.`)


## Example

The following permanently redirects all HTTP requests for `www.server1.com` to `www.server2.com` :

```sh
redirect http://www.server1.com http://www.server2.com
```



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.



<!-- CONTACT -->
## Contact


Project Link: [https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git](https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git)


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=flat-square
[contributors-url]: https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=flat-square
[forks-url]: https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=flat-square
[stars-url]: https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=flat-square
[issues-url]: https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=flat-square
[license-url]: https://github.com/treidoristivan/Reverse-Proxy-and-HTTP-Redirects.git/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
[product-screenshot]: images/img1.jpg
[product-screenshot2]: images/img2.jpg
