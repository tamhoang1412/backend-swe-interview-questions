# Backend SWE interview questions

This repo contains technical questions (and answers) on several topics you might want to prepare for an interview for BE position.

Inspired by [vietakid](https://github.com/vietnakid), most of the questions comes from [his repo](https://github.com/vietnakid/learning-material/blob/master/computer-science/cs_questions.md). I wrote down the brief answers and add some new questions/topics.

The answers to those questions bases on my humble knowledge. If you find some things want to improve or fix, please fire a PR, I would be more than happy.

## TOPICS

- [NETWORKING](#networking)
- [OPERATING SYSTEM](#operating-system)
- [DATABASE](#database)
- [SECURITY](#security)

## NETWORKING

1. Read the concept of TCP in [this wiki page](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) and try to understand all the concepts of it (deeply):
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
