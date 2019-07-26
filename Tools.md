<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tools</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><h1 id="小工具收集">小工具收集</h1>
<h2 id="network">Network</h2>
<h3 id="mtr">mtr</h3>
<p>結合 ping 與 tracerote 的小工具, 方便找出反應慢的 hop<br>
Install</p>
<pre class=" language-bash"><code class="prism  language-bash">$  brew <span class="token function">install</span> <span class="token function">mtr</span>
</code></pre>
<p>Output</p>
<pre class=" language-bash"><code class="prism  language-bash">Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                                                                                                                                                   Packets               Pings
 Host                                                                                                                                                            Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. router.asus.com                                                                                                                                               0.0%    14    1.1   1.1   0.9   1.5   0.2
 2. h254.s98.ts.hinet.net                                                                                                                                         0.0%    13   11.5  10.9  10.1  11.5   0.5
 3. shmz-3302.hinet.net                                                                                                                                           0.0%    13   10.2  14.6   9.8  49.7  11.0
 4. pcpd-3212.hinet.net                                                                                                                                           0.0%    13   12.0  13.2  10.7  23.4   3.2
 5. pcpd-3211.hinet.net                                                                                                                                           0.0%    13   11.4  13.4  10.1  22.5   4.0
 6. 72.14.202.34                                                                                                                                                  0.0%    13   11.4  12.9  11.4  19.9   2.3
 7. 108.170.244.77                                                                                                                                                0.0%    13   13.3  25.2  11.5 171.2  43.9
 8. 108.170.236.253                                                                                                                                               0.0%    13   20.2  15.3  14.2  20.2   1.6
 9. 74.125.37.92                                                                                                                                                  0.0%    13   20.3  16.3  14.3  22.3   2.6
10. 209.85.245.48                                                                                                                                                 0.0%    13   21.9  28.3  19.6  58.6  12.1
11. 74.125.253.83                                                                                                                                                 0.0%    13   19.3  19.3  18.1  21.2   0.9
12. ???
13. ???
14. ???
15. ???
16. ???
17. ???
18. ???
19. ???
20. ???
21. tk-in-f103.1e100.net                                                                                                                                          0.0%    13   17.5  17.3  16.7  18.5   0.6
</code></pre>
<h3 id="httpstat">httpstat</h3>
<p>詳細列出 http/https request 到 response 開銷時間<br>
Install</p>
<pre class=" language-bash"><code class="prism  language-bash">$ brew <span class="token function">install</span> httpstat
</code></pre>
<p>Output</p>
<pre class=" language-bash"><code class="prism  language-bash">httpstat www.google.com.tw
Connected to 127.0.0.1:1110 from 127.0.0.1:55067

HTTP/1.1 200 OK
Date: Fri, 25 Jan 2019 16:04:23 GMT
Expires: -1
Cache-Control: private, max-age<span class="token operator">=</span>0
Content-Type: text/html<span class="token punctuation">;</span> charset<span class="token operator">=</span>Big5
P3P: CP<span class="token operator">=</span><span class="token string">"This is not a P3P policy! See g.co/p3phelp for more info."</span>
Server: gws
X-XSS-Protection: 1<span class="token punctuation">;</span> mode<span class="token operator">=</span>block
X-Frame-Options: SAMEORIGIN
Set-Cookie: 1P_JAR<span class="token operator">=</span>2019-01-25-16<span class="token punctuation">;</span> expires<span class="token operator">=</span>Sun, 24-Feb-2019 16:04:23 GMT<span class="token punctuation">;</span> path<span class="token operator">=</span>/<span class="token punctuation">;</span> domain<span class="token operator">=</span>.google.com.tw
Set-Cookie: NID<span class="token operator">=</span>156<span class="token operator">=</span>hUgETya1jJEzmAuTaWjNhs_VL1Lt80l-LWliaHLg1ZvcZKc_KG1TP5UPGv-jBUDt7vDn-jy2mY0edKfObYXhgRw5iO9ydf22slC60__ULVANsy5E1XN6pZbEf708-slm4RLNcaXksIKuayz9o6FS9EN3Ip_-NUCBoKOaBj4CB-M<span class="token punctuation">;</span> expires<span class="token operator">=</span>Sat, 27-Jul-2019 16:04:23 GMT<span class="token punctuation">;</span> path<span class="token operator">=</span>/<span class="token punctuation">;</span> domain<span class="token operator">=</span>.google.com.tw<span class="token punctuation">;</span> HttpOnly
Accept-Ranges: none
Vary: Accept-Encoding
Transfer-Encoding: chunked


  DNS Lookup   TCP Connection   Server Processing   Content Transfer
<span class="token punctuation">[</span>    31ms    <span class="token operator">|</span>      15ms      <span class="token operator">|</span>       100ms       <span class="token operator">|</span>        0ms       <span class="token punctuation">]</span>
             <span class="token operator">|</span>                <span class="token operator">|</span>                   <span class="token operator">|</span>                  <span class="token operator">|</span>
    namelookup:31ms           <span class="token operator">|</span>                   <span class="token operator">|</span>                  <span class="token operator">|</span>
                        connect:46ms              <span class="token operator">|</span>                  <span class="token operator">|</span>
                                      starttransfer:146ms            <span class="token operator">|</span>
                                                                 total:146ms

speed_download: 74.2 KiB/s, speed_upload: 0.0 KiB/s
</code></pre>
<p>可以關閉 save  body 減少垃圾</p>
<pre class=" language-txrt"><code class="prism  language-txrt"># httpstat
export HTTPSTAT_SAVE_BODY=false 
</code></pre>
</div>
</body>

</html>
