# :rocket: Web Performance Insights

TCP Slow Start
------------------------------
Keeping [TCP Slow](https://blog.std.in/http-response-sizes-and-tcp/) start in mind, it would be fair to say that, the lesser you ship payload to the user, the faster would be the load time. 

Server Side Rendering
-------------------------------
The term [Progressive Hydration](https://www.youtube.com/watch?v=k-A2VfuUROg&t=960s) was introduced by Google at Google I/O 2019 where they gave a gist of how we can split the component's hydration phase progressively instead of going all out at the page boot up phase. This is a bit tricky to implement but has substantial performance gains.

Script Streaming
--------------------------------
With [Script streaming](https://blog.chromium.org/2015/03/new-javascript-techniques-for-rapid.html), parsing async/defer scripts can be offloaded to a separate worker thread instead of the main thread. This means that parsing can complete just milliseconds after the download has finished, and results in pages loading as much as 10% faster.
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Loading scripts w/&lt;script async&gt; or &lt;script defer&gt;? V8 parses em on a separate thread once downloading begins. Improves loading by up to 10% <a href="https://t.co/PH5shfK8Mb">pic.twitter.com/PH5shfK8Mb</a></p>&mdash; Addy Osmani (@addyosmani) <a href="https://twitter.com/addyosmani/status/808713528160813056?ref_src=twsrc%5Etfw">December 13, 2016</a></blockquote>
