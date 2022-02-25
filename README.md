# Backend SWE interview questions

This repo contains technical questions (and answers) on several topics you might want to prepare for an interview for BE position.

Most of the questions comes from [vietnakid](HTTPS://github.com/vietnakid/learning-material/blob/master/computer-science/cs_questions.md). I wrote down the brief answers and add some new questions/topics.

The answers to those questions bases on my humble knowledge. If you find some things want to improve or fix, please fire a PR, I would be more than happy.

## TOPICS

- [NETWORKING](#networking)
- [OPERATING SYSTEM](#operating-system)
- [DATABASE](#database)
- [SECURITY](#security)

## NETWORKING

1. Read the concept of TCP in [this wiki page](HTTPS://en.wikipedia.org/wiki/Transmission_Control_Protocol) and try to understand all the concepts of it (deeply):
    - [How TCP open a connection? What does it need to open a connection?](/answers/networking.md#How-TCP-open-a-connection?-What-does-it-need-to-open-a-connection?)
        + [Why there are 3 way handshakes but not 2 way?](/answers/networking.md#Why-there-are-3-way-handshakes-but-not-2-way?)
        + [What is syn, ack mean?](/answers/networking.md#What-is-syn,-ack-mean?)
        + [Why they have to send 2 "random" sequence numbers? The purpose of this sequence number?](/answers/networking.md#Why-they-have-to-send-2-"random"-sequence-numbers?-The-purpose-of-this-sequence-number?)
        + [What if the 3rd handshake fail? How the server can detect it and what does it do in this case?](/answers/networking.md#What-if-the-3rd-handshake-fail?-How-the-server-can-detect-it-and-what-does-it-do-in-this-case?)
    - [How TCP handles the connection?](/answers/networking.md#How-TCP-handles-the-connection?)
        + [What happens if some bits are wrong due to connection errors? How to detect them and fix them?](/answers/networking.md#What-happens-if-some-bits-are-wrong-due-to-connection-errors?-How-to-detect-them-and-fix-them?)
        + [How the timeout is handled? what if the timeout is expired?](/answers/networking.md#How-the-timeout-is-handled?-what-if-the-timeout-is-expired?)
        + [What will happen if some "packet" is missing on the way?](/answers/networking.md#What-will-happen-if-some-"packet"-is-missing-on-the-way?)
        + [How to detect the appropriate number of packets to send (speed of sending packet)?](/answers/networking.md#How-to-detect-the-appropriate-number-of-packets-to-send-(speed-of-sending-packet)?)
    - [How TCP close the connection?](/answers/networking.md#How-TCP-close-the-connection?)
        + [What if the internet is dropped in the middle of the connection? Or in case one peer is crash?](/answers/networking.md#What-if-the-internet-is-dropped-in-the-middle-of-the-connection?-Or-in-case-one-peer-is-crash?)
    - [How long you can keep a TCP connection alive?](/answers/networking.md#How-long-you-can-keep-a-TCP-connection-alive?)
2. [What are the differences between TCP and UDP? And in which case we use which?](/answers/networking.md#What-are-the-differences-between-TCP-and-UDP?-And-in-which-case-we-use-which?)

3. [How Ping command works? What is TTL? How does TTL will be changed?](/answers/networking.md#How-Ping-command-works?-What-is-TTL??-How-does-TTL-will-be-changed?)

4. [How HTTP works?](/answers/networking.md#How-HTTP-works?)
    - [Why did people say that HTTP is stateless? The reason they make it stateless?](/answers/networking.md#Why-did-people-say-that-HTTP-is-stateless?-The-reason-they-make-it-stateless?)
    - [Can we make a persistent HTTP connection? pros and cons of this way?](/answers/networking.md#Can-we-make-a-persistent-HTTP-connection?-pros-and-cons-of-this-way?)
    - [Why HTTP require cookie each time we send the request?](/answers/networking.md#Why-HTTP-require-cookie-each-time-we-send-the-request?)
    - [Can someone use your cookie and log in your Facebook account? How to migrate this?](/answers/networking.md#Can-someone-use-your-cookie-and-log-in-your-Facebook-account?-How-to-migrate-this?)
    - [What is HTTP session? How does authentication work in HTTP? What is JWT?](/answers/networking.md#What-is-HTTP-session?-How-does-authentication-work-in-HTTP?-What-is-JWT?)
    - [Which type of "data" HTTP can help us to get or push? (binary file? image? text file? video file? music file?)](/answers/networking.md#Which-type-of-"data"-HTTP-can-help-us-to-get-or-push?-(binary-file?-image?-text-file?-video-file?-music-file?))
    - [REST/RESTful?](/answers/networking.md#REST/RESTful?)
    - [AJAX technique?](/answers/networking.md#AJAX-technique?)
    - [How HTTPS work?](/answers/networking.md#How-HTTPS-work?)
    - [Learn about some useful headers](/answers/networking.md#Learn-about-some-useful-headers)

5. [When you type "google.com" into your browser, that will happen when you type enter till everything is displayed on your screen?](/answers/networking.md#When-you-type-"google.com"-into-your-browser,-that-will-happen-when-you-type-enter-till-everything-is-displayed-on-your-screen?)
    - [DNS lookup (in case you already access google.com before and also in case you do not know the IP of google.com)](/answers/networking.md#DNS-lookup-(in-case-you-already-access-google.com-before-and-also-in-case-you-do-not-know-the-IP-of-google.com))
        + [Which protocol DNS use and why?](/answers/networking.md#Which-protocol-DNS-use-and-why?)
        + [The other of place to look up DNS.](/answers/networking.md#The-other-of-place-to-look-up-DNS.)
    - [TCP or UDP will be used in this case? why?](/answers/networking.md#TCP-or-UDP-will-be-used-in-this-case?-why?)
    - [How to know "google.com" require HTTP or HTTPS? how browser can know and redirect from HTTP to HTTPS?](/answers/networking.md#How-to-know-"google.com"-require-HTTP-or-HTTPS?-how-browser-can-know-and-redirect-from-HTTP-to-HTTPS?)
    - [After you get the `HTML content` for "google.com" how to get the `*.js` and `image` files?](/answers/networking.md#After-you-get-the-HTML-content-for-"google.com"-how-to-get-the-*.js-and-image-files?)
    - [When getting `*.js` or `image` files do why use another `TCP connection` or use the same one as in the get `HTML content`? How DNS lookup work in this case?](/answers/networking.md#When-getting-*.js-or-image-files-do-why-use-another-TCP-connection-or-use-the-same-one-as-in-the-get-HTML-content?-How-DNS-lookup-work-in-this-case?)
    - [After your browser display "google.com" fully, is there any connection open?](/answers/networking.md#After-your-browser-display-"google.com"-fully,-is-there-any-connection-open?)
    - [Caching can apply to which steps? How caching applied?](/answers/networking.md#Caching-can-apply-to-which-steps?-How-caching-applied?)

6. [What is the connection pool? It's advantages and disadvantages? How to implement connection pool in your programing language?](/answers/networking.md#What-is-the-connection-pool?-It's-advantages-and-disadvantages?-How-to-implement-connection-pool-in-your-programing-language?)

7. [What is socket?](/answers/networking.md#What-is-socket?)
    - [Why do we need socket? Why socket is a "file" in linux?](/answers/networking.md#Why-do-we-need-socket?-Why-socket-is-a-"file"-in-linux?)
    - [What is `src port` when you create a connection to a "server"?](/answers/networking.md#What-is-src-port-when-you-create-a-connection-to-a-"server"?)
    - [How one server can handle multiple connections to the same port?](/answers/networking.md#How-one-server-can-handle-multiple-connections-to-the-same-port?) [Good answers here but read all answers](https://stackoverflow.com/questions/3329641/how-do-multiple-clients-connect-simultaneously-to-one-port-say-80-on-a-server)
    - [What is the maximum number of connections a server can handle? (if it has unlimited resource) (in case of the same client and in case of multiple clients)](/answers/networking.md#What-is-the-maximum-number-of-connections-a-server-can-handle?-(if-it-has-unlimited-resource)-(in-case-of-the-same-client-and-in-case-of-multiple-clients))
    - [When you open multiple tabs on your chrome, how OS knows which packet (both sending and receiving) correspond to which tab? (how about in case you open many tabs to the same page "for eg: google.com")](/answers/networking.md#When-you-open-multiple-tabs-on-your-chrome,-how-OS-knows-which-packet-(both-sending-and-receiving)-correspond-to-which-tab?-(how-about-in-se-you-open-many-tabs-to-the-same-page-"for-eg:-google.com"))
    - [What are the maximum numbers of connection your machine can connect to "google.com" (if you have unlimited resource)](/answers/networking.md#What-are-the-maximum-numbers-of-connection-your-machine-can-connect-to-"google.com"-(if-you-have-unlimited-resource))
    - [Can two processes listen to the same port on your machine? Why? How?](/answers/networking.md#Can-two-processes-listen-to-the-same-port-on-your-machine?-Why?-How?)
    - [What is `buffer`? why we always need buffer when working with "file"?](/answers/networking.md#What-is-buffer?-why-we-always-need-buffer-when-working-with-"file"?)
    - [What is `unix socket`? When to use it?](/answers/networking.md#What-is-unix-socket?-When-to-use-it?)

8. [What is `TCP proxy`? `reverse proxy`? and `VPN`?](/answers/networking.md#What-is-TCP-proxy?-reverse-proxy?-and-VPN?)
    - [How your router at your home works?](/answers/networking.md#How-your-router-at-your-home-works?)
        + [Inside LAN network, it uses IP or MAC address? Why?](/answers/networking.md#Inside-LAN-network,-it-uses-IP-or-MAC-address?-Why?)
        + [How does it know which packet comes from (or arrive at) which machine?](/answers/networking.md#How-does-it-know-which-packet-comes-from-(or-arrive-at)-which-machine?)
        + [What is the difference between Hub and Switch inside LAN?](/answers/networking.md#What-is-the-difference-between-Hub-and-Switch-inside-LAN?)
        + [How src IP/PORT and dst IP/PORT change on the way to the server?](/answers/networking.md#How-src-IP/PORT-and-dst-IP/PORT-change-on-the-way-to-the-server?)
    - [How `load-balancer` works?](/answers/networking.md#How-load-balancer-works?)
        + [When we send a packet to a `load-balancer` how does it forward to the desired server? (Does it keep any data on its memory?)](/answers/networking.md#When-we-send-a-packet-to-a-load-balancer-how-does-it-forward-to-the-desired-server?-(Does-it-keep-any-data-on-its-memory?))
        + [When the server wants to send data back to the client, does the connection need to go through the `load-balancer`?](/answers/networking.md#When-the-server-wants-to-send-data-back-to-the-client,-does-the-connection-need-to-go-through-the-load-balancer?)
        + [What is different between `reverse proxy` and `load-balancer`?](/answers/networking.md#What-is-different-between-reverse-proxy-and-load-balancer?)
        + [Can `load-balancer` be a bottleneck? (Because it is the end-point of too many requests) (bottleneck about RAM or CPU or Network?)](/answers/networking.md#Can-load-balancer-be-a-bottleneck?-(Because-it-is-the-end-point-of-too-many-requests)-(bottleneck-about-RAM-or-CPU-or-Network?))
        + [Try to understand everything in [this page](https://softwareengineering.stackexchange.com/questions/312956/what-does-a-load-balancer-return) (all the answers)