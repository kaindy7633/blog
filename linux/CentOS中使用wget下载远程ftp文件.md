<!-- wp:paragraph -->
<p>在MAC中使用ssh连接远程服务器:</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>打开终端，输入：</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code -->
<pre class="wp-block-syntaxhighlighter-code">ssh -p 9011 username@192.168.0.110</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>回车后输入密码，提示登录成功....</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>切换到需要存放文件的目录，在命令行下输入：</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code -->
<pre class="wp-block-syntaxhighlighter-code">prompt off  (回车)   /* 不用每次都输入Y来确认是否下载 */</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>接下来输入：</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code -->
<pre class="wp-block-syntaxhighlighter-code">wget ftp://ip:port/子目录/* --ftp-user=你的用户名 --ftp-password=你的FTP密码 -r</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>示例：</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code -->
<pre class="wp-block-syntaxhighlighter-code">wget ftp://192.168.20.249:8081/htdocs/* --ftp-user=lzadmin --ftp-password=123456 -r</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>注意：-r 的意思是下载所有文件包括文件夹</p>
<!-- /wp:paragraph -->
