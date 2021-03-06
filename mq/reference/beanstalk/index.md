---
title: Beanstalk Interface
layout: default
section: mq
breadcrumbs:
  - ['Reference', '/reference']
  - ['Beanstalk Interface', '/beanstalk']
---

You can use any of the [Beanstalkd clients](https://github.com/kr/beanstalkd/wiki/client-libraries) with IronMQ. The list of supported languages is extensive and so there is sure to one for your language of choice. 

<section id="toc">
  <h3>Table of Contents</h3>
  <ul>
    <li><a href="#beanstalk_libraries">Beanstalk Libraries</a></li>
    <li><a href="#host_information">Host Information</a></li>
    <li><a href="#authentication">Authentication</a></li>
    <li><a href="#tubes_vs_queues">Tubes vs Queues</a></li>
    <li><a href="#notes">Notes</a></li>
  </ul>  
</section>

<h2 id="beanstalk_libraries">Beanstalk Libraries</h2>

Here's a sample list of languages available (with multiple clients libs to choose from for many languages):

<table style="border: 0px; width: 100%;">
  <tr>
    <td style="width: 25%;">
      <ul>
        <li>C</li>
        <li>C++</li>
        <li>Clojure</li>
        <li>Django</li>
        <li>Common Lisp</li>
      </ul>
    </td>
    <td style="width: 25%">
      <ul>
        <li>Erlang</li>
        <li>Go</li>
        <li>Haskell</li>
        <li>Io</li>
        <li>Java</li>
      </ul>
    </td>
    <td style="width: 25%">
      <ul>
        <li>Node.js</li>
        <li>OCaml</li>
        <li>Perl</li>
        <li>PHP</li>
        <li>Python</li>
      </ul>
    </td>
    <td style="width: 25%" valign="top">
      <ul>
        <li>Rails</li>
        <li>Ruby</li>
        <li>Scheme (Chicken)</li>
        <li>.NET/C#</li>
      </ul>
    </td>
  </tr>
</table>


Check out list of client libraries [on GitHub](https://github.com/kr/beanstalkd/wiki/client-libraries)

<h2 id="host_information">Host Information</h2>

To connect to IronMQ using Beanstalkd, use one of the [hosts on our Clouds page](/mq/reference/clouds). 

**NOTE**: Beanstalkd is currently not supported on Rackspace. Please use one of our 
[HTTP clients](/mq/libraries) if you are on Rackspace. 

<h2 id="authentication">Authentication</h2>
Because IronMQ requires authentication, the first command you send must put a message onto the queue with the contents:

oauth <span class="variable token">{TOKEN}</span> <span class="variable project_id">{PROJECT_ID}</span>

The DRAINING response will be returned if authentication fails or if any other command is sent before authentication.

<h2 id="tubes_vs_queues">Tubes vs Queues</h2>
Note that a Beanstalkd _tube_ is synonymous with an IronMQ <span class="queue_name variable">{Queue Name}</span> within the REST/HTTP API.

If a tube/queue name is not specified, then the queue name `default` will be used within IronMQ.

<h2 id="notes">Notes</h2>
* The ID you receive when using the Beanstalkd interface will *not* be the same as the HTTP interface so you *cannot* use them interchangeably.

* At the moment, there are some commands that IronMQ does not implement. These include:
  * bury
  * peek, peek-delayed, peek-buried
  * kick
  * list-tubes
  * stats, stats-job, stats-tube
  * pause-tube
  * quit
