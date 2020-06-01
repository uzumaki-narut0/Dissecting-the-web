# :rocket: Web Performance Insights

TCP Slow Start
------------------------------
![](https://www.keycdn.com/img/support/tcp-slow-start-lg.webp)

Keeping [TCP Slow](https://blog.std.in/http-response-sizes-and-tcp/) start in mind, it would be fair to say that, the lesser you ship payload to the user, the faster would be the load time. 

Server Side Rendering
-------------------------------
Server-side rendering (SSR) is the ability of a Javascript Application to render on the server rather on the client. This way, you ship the initial rendered page along with the Javascript which would take over the app once it gets fetched, parsed and executed. This improves the [First Contentful Paint](https://web.dev/first-contentful-paint/) and [First Meaningful Paint](https://web.dev/first-meaningful-paint/). Also, from SEO standpoint search engines are yet inefficient in correctly index applications that exclusively render client-side.

### Progressive Hydration
The term [Progressive Hydration](https://www.youtube.com/watch?v=k-A2VfuUROg&t=960s) was introduced by Google at Google I/O 2019 where they gave a gist of how we can split the component's hydration phase progressively instead of going all out at the page boot up phase. This is a bit tricky to implement but has substantial performance gains.

Script Streaming
--------------------------------
With [Script streaming](https://blog.chromium.org/2015/03/new-javascript-techniques-for-rapid.html), parsing async/defer scripts can be offloaded to a separate worker thread instead of the main thread. This means that parsing can complete just milliseconds after the download has finished, and results in pages loading as much as 10% faster.

![](https://pbs.twimg.com/media/Czkf6kfVIAAmQM6?format=jpg&name=large)

  Resource prioritization
  --------------------------------
  > If Everything is Important, Then Nothing Is.
