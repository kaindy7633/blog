<!-- wp:paragraph -->
<p><strong>shadowsocks</strong>，是个什么我就不多解释了，最近想把自己的vps弄一下，重装了系统，结果在跟新的时候出现问题了，更新源连接成功，但是更新不了，报了很多404，下面来看下如何解决。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>我用了很多网上的方法，都么有成功，比如说替换源地址啊等等，发现几乎国内的都有问题，后来看到一篇文章，写的还是替换成官方的地址，只是不是最新的，而是这个：<strong>old-releases.ubuntu.com</strong>，所以就有了下面的操作。</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>首先执行下面的操作：</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code -->
<pre class="wp-block-syntaxhighlighter-code">sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>请注意：我的原来的 <code>sources.list</code> 文件里的源地址是有个us开头的，也就是这个：<code>us.archive.ubuntu.com</code>，所以要根据源文件里的地址来改，所以就有了下面的操作</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code -->
<pre class="wp-block-syntaxhighlighter-code">sudo sed -i -e 's/us.archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>搞完之后，直接上：</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code -->
<pre class="wp-block-syntaxhighlighter-code">sudo apt-get update && sudo apt-get upgrade</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>最后成功更新</p>
<!-- /wp:paragraph -->
