---
ID: 774
post_title: >
  WordPress如何统计文章阅读次数？
author: WelonMusk
post_excerpt: ""
layout: post
permalink: 'http://creativeview.cn/2018/12/05/wordpress%e5%a6%82%e4%bd%95%e7%bb%9f%e8%ae%a1%e6%96%87%e7%ab%a0%e9%98%85%e8%af%bb%e6%ac%a1%e6%95%b0%ef%bc%9f/'
published: true
post_date: 2018-12-05 15:07:03
---
<h4>痛点描述：WordPress文章浏览次数统计功能是必不可少的，不少主题已经集成该功能，如果你的主题没有集成，你可以使用本教程5分钟即可轻松实现，本教程中有详尽的图文教程和修改后的代码，可谓满满的干货。</h4>

本解决方案基于主题Hypermarket,版本：1.5.6
<!--more-->

<h3>步骤一：添加插件，<span data-type="color" style="color:rgb(34, 34, 34)"><span data-type="background" style="background-color:rgb(255, 255, 255)">搜索输入：</span></span>wp-postviews</h3>

<img src="https://cdn.nlark.com/yuque/0/2018/png/195205/1543992244777-f279bee3-a558-49d3-83fb-e57bfe3fb729.png" alt="image.png | left | 747x256" title="" />

<h3>步骤二：配置插件，Settings->postviews,按照下图配置后，点击最下面的保存按钮</h3>

1.<i class="fa fa-eye"></i>%VIEW&#95;COUNT%次浏览    
2.<li><a href="%POST\_URL%"  title="%POST\_TITLE%">%POST&#95;TITLE%</a> - %VIEW&#95;COUNT% 次浏览</li>

<img src="https://cdn.nlark.com/yuque/0/2018/png/195205/1543992516202-d4995be9-7f7f-4787-8fba-8aac74161368.png" alt="image.png | left | 747x391" title="" />

<h3>步骤三、修改主题文件，外观-->编辑</h3>

<span data-type="color" style="color:rgb(35, 40, 45)"><span data-type="background" style="background-color:rgb(255, 255, 255)">Usage</span></span>

<ol>
<li>Open wp-content/themes/<YOUR THEME NAME>/index.php</li>
<li>You may place it in archive.php, single.php, post.php or page.php also.</li>
<li>Find: <?php while (have\_posts()) : the\_post(); ?></li>
<li>Add Anywhere Below It (The Place You Want The Views To Show): <?php if(function\_exists('the\_views')) { the\_views(); } ?></li>
<li>Or you can use the shortcode [views] or [views id="1"] (where 1 is the post ID) in a post</li>
<li>Go to WP-Admin -> Settings -> PostViews to configure the plugin.
在下面的三个文件下添加如下代码：</li>
</ol>

<pre><code class="language-php ">&lt;span&gt;&lt;?php if(function_exists('the_views')) { the_views(); } ?&gt;&lt;/span&gt;
</code></pre>

修改如下文件：
<span data-type="color" style="color:rgb(35, 40, 45)"><span data-type="background" style="background-color:rgb(245, 245, 245)">Hypermarket: content-archive.php (loop-templates/content-archive.php)，修改后的文件内容如下：</span></span>

<pre><code class="language-php ">&lt;?php
/**
 * The template for displaying archive pages.
 *
 * @see             http://codex.wordpress.org/Template_Hierarchy
 * @author          Mahdi Yazdani
 * @package         Hypermarket
 * @since           1.0.3
 */
/**
 * Functions hooked into "hypermarket_before_loop_posts" action
 *
 * @hooked hypermarket_loop_posts_header_image             - 10
 * @since 1.0
 */
do_action('hypermarket_before_loop_posts');
?&gt;
&lt;!-- Content --&gt;
&lt;section class="container padding-top-3x"&gt;
        &lt;div class="category-tile"&gt;
            &lt;div class="inner"&gt;
                &lt;?php
                    the_archive_title( '&lt;h1 class="mobile-center"&gt;', '&lt;/h1&gt;' );
                    the_archive_description( '&lt;p class="taxonomy-description"&gt;', '&lt;/p&gt;' );
                ?&gt;
            &lt;/div&gt;&lt;!-- .inner ?&gt; --&gt;
        &lt;/div&gt;&lt;!-- .category-tile ?&gt; --&gt;
            &lt;?php
                while (have_posts()):
                    the_post();
            ?&gt;
                &lt;!-- Post --&gt;
                &lt;article id="post-&lt;?php the_ID(); ?&gt;" &lt;?php post_class('row padding-top paddin-bottom hypermarket-post-loop'); ?&gt;&gt;
                    &lt;?php 
                        /**
                         * Functions hooked into "hypermarket_loop_posts" action
                         *
                         * @hooked hypermarket_post_meta                    - 10
                         * @hooked hypermarket_process_simple_like          - 20
                         * @hooked hypermarket_post_entry                   - 30
                         * @since 1.0
                         */
                        do_action('hypermarket_loop_posts');
                    ?&gt;
                &lt;/article&gt;&lt;!-- #post-&lt;?php the_ID(); ?&gt; --&gt;
    &lt;span&gt;&lt;?php if(function_exists('the_views')) { the_views(); } ?&gt;&lt;/span&gt;
                &lt;hr&gt;
        &lt;?php 
            endwhile; 
            /**
             * Functions hooked into "hypermarket_loop_posts_paging_navigation" action
             *
             * @hooked hypermarket_paging_navigation                       - 10
             * @since 1.0
             */
            do_action('hypermarket_loop_posts_paging_navigation');
        ?&gt;
&lt;/section&gt;&lt;!-- .container --&gt;
</code></pre>

修改如下文件：
<span data-type="color" style="color:rgb(35, 40, 45)"><span data-type="background" style="background-color:rgb(245, 245, 245)">Hypermarket: content-post.php (loop-templates/content-post.php) ，修改后的文件内容如下：</span></span>

<pre><code class="language-php ">&lt;?php
/**
 * The template used for displaying single post content in single.php
 *
 * @see             http://codex.wordpress.org/Template_Hierarchy
 * @author          Mahdi Yazdani
 * @package         Hypermarket
 * @since           1.0.9.0
 */
/**
 * Functions hooked into "hypermarket_before_single_post" action
 *
 * @hooked hypermarket_featured_image_single_post     - 10
 * @since 1.0.9.0
 */
do_action('hypermarket_before_single_post');
?&gt;
&lt;!-- Content --&gt;
&lt;section id="hypermarket-post-content" class="container&lt;?php echo (apply_filters('hypermarket_fluid_template', false)) ? '-fluid' : ''; ?&gt; padding-top-3x"&gt;
    &lt;h1 class="mobile-center"&gt;&lt;?php the_title(); ?&gt;&lt;/h1&gt;
        &lt;?php
            while (have_posts()):
                the_post();
            ?&gt;
                &lt;!-- Post --&gt;
                &lt;article id="post-&lt;?php the_ID(); ?&gt;" &lt;?php post_class('row padding-top paddin-bottom'); ?&gt;&gt;

                    &lt;div class="col-sm-12"&gt;
                        &lt;?php do_action('hypermarket_before_single_post_content'); ?&gt;
                        &lt;?php the_content(); ?&gt;
                        &lt;?php
                            /**
                             * Functions hooked into "hypermarket_end_single_post_content" action
                             *
                             * @hooked hypermarket_single_post_paging     - 10
                             * @since 1.0.4
                             */
                            do_action('hypermarket_end_single_post_content');
                        ?&gt;
                        &lt;hr&gt;

                        &lt;div class="blog-post-meta"&gt;
                            &lt;div class="column"&gt;
                                &lt;span&gt;&lt;?php esc_html_e('by', 'hypermarket'); ?&gt; &lt;/span&gt;
                                &lt;?php the_author_posts_link(); ?&gt;
                                &lt;span class="divider"&gt;&lt;/span&gt;
                                &lt;?php the_date(get_option('date_format')); ?&gt;
                                &lt;?php 
                                    $get_categories = get_the_category();
                                    if( !empty( $get_categories ) ): 
                                ?&gt;
                                    &lt;span class="divider"&gt;&lt;/span&gt;
                                    &lt;span&gt;&lt;?php esc_html_e('in', 'hypermarket'); ?&gt; &lt;/span&gt;
                                    &lt;?php the_category(', '); ?&gt;
                                &lt;?php endif; ?&gt;
                                &lt;?php 
                                    $get_tags = get_the_tags();
                                    if( !empty( $get_tags ) ): 
                                ?&gt;
                                    &lt;span class="divider"&gt;&lt;/span&gt;
                                    &lt;?php the_tags('#', ' #', ''); ?&gt;
                                &lt;?php endif; ?&gt;
                            &lt;/div&gt;&lt;!-- .column --&gt;
                            &lt;span&gt;&lt;?php if(function_exists('the_views')) { the_views(); } ?&gt;&lt;/span&gt;
                            &lt;div class="column"&gt;
                                &lt;?php
                                    $is_comment_open = comments_open($post-&gt;ID);
                                    $num_comments = intval(get_comments_number());
                                    if(($is_comment_open &amp;&amp; post_password_required() === false) || (!$is_comment_open &amp;&amp; $num_comments &gt;= 1)):
                                ?&gt;
                                        &lt;a href="#comments" class="single-comments-link scroll-to" target="_self"&gt;
                                        &lt;i class="material-icons comment"&gt;&lt;/i&gt;
                                            &lt;?php echo ($num_comments &gt;= 1) ? esc_html($num_comments) : ''; ?&gt;
                                        &lt;/a&gt;&lt;!-- .single-comments-link --&gt;
                                &lt;?php endif; ?&gt;
                            &lt;/div&gt;&lt;!-- .column --&gt;
                        &lt;/div&gt;&lt;!-- .blog-post-meta --&gt;
                        &lt;?php do_action('hypermarket_after_single_post_content'); ?&gt;
                    &lt;/div&gt;&lt;!-- .col-sm-12 --&gt;
                &lt;/article&gt;&lt;!-- #post-&lt;?php the_ID(); ?&gt; --&gt;
        &lt;?php 
            endwhile;
            // If comments are open or we have at least one comment, load up the comment template.
            if ( comments_open() || get_comments_number() ):
                comments_template();
            endif;
        ?&gt;
&lt;/section&gt;&lt;!-- .container --&gt;
</code></pre>

修改如下文件：
<span data-type="color" style="color:rgb(35, 40, 45)"><span data-type="background" style="background-color:rgb(245, 245, 245)">Hypermarket: content-loop.php (loop-templates/content-loop.php)，修改后的文件内容如下：</span></span>

<pre><code class="language-php ">&lt;?php
/**
 * The loop template file.
 * Included on pages like index.php, archive.php and search.php to display a loop of posts.
 *
 * @see             http://codex.wordpress.org/The_Loop
 * @author          Mahdi Yazdani
 * @package         Hypermarket
 * @since           1.0.6
 */
/**
 * Functions hooked into "hypermarket_before_loop_posts" action
 *
 * @hooked hypermarket_loop_posts_header_image             - 10
 * @since 1.0
 */
do_action('hypermarket_before_loop_posts');
?&gt;
&lt;!-- Content --&gt;
&lt;section class="container padding-top-3x"&gt;
        &lt;?php 
            $get_posts_page = get_option('page_for_posts', true);
            if( !empty($get_posts_page) ):
                echo '&lt;h1 class="mobile-center"&gt;' . get_the_title( get_option('page_for_posts', true) ) . '&lt;/h1&gt;'; 
            endif;
            while (have_posts()):
                the_post();
        ?&gt;
                &lt;!-- Post --&gt;
                &lt;article id="post-&lt;?php the_ID(); ?&gt;" &lt;?php post_class('row padding-top paddin-bottom hypermarket-post-loop'); ?&gt;&gt;
                    &lt;?php 
                        /**
                         * Functions hooked into "hypermarket_loop_posts" action
                         *
                         * @hooked hypermarket_post_meta                    - 10
                         * @hooked hypermarket_post_entry                   - 30
                         * @since 1.0.6
                         */
                        do_action('hypermarket_loop_posts');
                    ?&gt;
                    &lt;span&gt;&lt;?php if(function_exists('the_views')) { the_views(); } ?&gt;&lt;/span&gt;
                &lt;/article&gt;&lt;!-- #post-&lt;?php the_ID(); ?&gt; --&gt;

                &lt;hr&gt;
        &lt;?php 
            endwhile; 
            /**
             * Functions hooked into "hypermarket_loop_posts_paging_navigation" action
             *
             * @hooked hypermarket_paging_navigation                       - 10
             * @since 1.0
             */
            do_action('hypermarket_loop_posts_paging_navigation');
        ?&gt;
&lt;/section&gt;&lt;!-- .container --&gt;
</code></pre>

<h3>步骤四、测试结果</h3>

<img src="https://cdn.nlark.com/yuque/0/2018/png/195205/1543993138695-41939182-5fe9-4963-96b3-17c35f45615c.png" alt="image.png | left | 675x260" title="" />

<img src="https://cdn.nlark.com/yuque/0/2018/png/195205/1543993177906-5e5cd048-af5b-493f-9113-d9bec2a91c9f.png" alt="image.png | left | 747x328" title="" />