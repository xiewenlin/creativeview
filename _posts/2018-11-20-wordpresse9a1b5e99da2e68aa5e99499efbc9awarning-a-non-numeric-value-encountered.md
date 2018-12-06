---
ID: 743
post_title: '如何解决WordPress页面报错：Warning: A non-numeric value encountered'
author: WelonMusk
post_excerpt: ""
layout: post
permalink: 'http://creativeview.cn/2018/11/20/wordpress%e9%a1%b5%e9%9d%a2%e6%8a%a5%e9%94%99%ef%bc%9awarning-a-non-numeric-value-encountered/'
published: true
post_date: 2018-11-20 16:04:30
---
<h4>痛点描述：WordPress更新到最新版本4.9.8–zh_CN后页面总是报：Warning: A non-numeric value encountered</h4>

原因分析：查看PHP7.1官方文档，对这种错误的解释：

<pre><code class="language-bash ">New E_WARNING and E_NOTICE errors have been introduced when invalid strings are coerced using operators expecting numbers (+ - * / ** % &lt;&lt; &gt;&gt; | &amp; ^) or their assignment equivalents. An E_NOTICE is emitted when the string begins with a numeric value but contains trailing non-numeric characters, and an E_WARNING is emitted when the string does not contain a numeric value.
</code></pre>

<!--more-->
报错截图如下：
<img src="https://www.wailian.work/images/2018/11/20/44a38c88b822f90e.png" alt="44a38c88b822f90e.png" border="0" />
解决问题之后的截图如下：
<img src="https://www.wailian.work/images/2018/11/21/image.png" alt="image.png" border="0" />

<h3>解决方法</h3>

1.找到服务器安装根目录下的wp-config.php：/var/www/html/wp-includes/wp-config.php
2.在文件最上方添加如下代码：

<pre><code class="language-php ">ini_set('display_errors','Off');
ini_set('error_reporting', E_ALL );
define('WP_DEBUG', false);
define('WP_DEBUG_DISPLAY', false);
</code></pre>

3.修改后的wp-config.php内容如下：

<pre><code class="language-php ">&lt;?php

/**

 * The base configuration for WordPress

 *

 * The wp-config.php creation script uses this file during the

 * installation. You don't have to use the web site, you can

 * copy this file to "wp-config.php" and fill in the values.

 *

 * This file contains the following configurations:

 *

 * * MySQL settings

 * * Secret keys

 * * Database table prefix

 * * ABSPATH

 *

 * @link https://codex.wordpress.org/Editing_wp-config.php

 *

 * @package WordPress

 */



// ** MySQL settings - You can get this info from your web host ** //

/** The name of the database for WordPress */
ini_set('display_errors','Off');
ini_set('error_reporting', E_ALL );
define('WP_DEBUG', false);
define('WP_DEBUG_DISPLAY', false);

define('DB_NAME', 'wordpress');



/** MySQL database username */

define('DB_USER', 'JackLeon');



/** MySQL database password */

define('DB_PASSWORD', 'Spark?2018');



/** MySQL hostname */

define('DB_HOST', '101.132.180.115:3306');



/** Database Charset to use in creating database tables. */

define('DB_CHARSET', 'utf8');



/** The Database Collate type. Don't change this if in doubt. */

define('DB_COLLATE', '');



/**#@+

 * Authentication Unique Keys and Salts.

 *

 * Change these to different unique phrases!

 * You can generate these using the {@link https://api.wordpress.org/secret-key/1.1/salt/ WordPress.org secret-key service}

 * You can change these at any point in time to invalidate all existing cookies. This will force all users to have to log in again.

 *

 * @since 2.6.0

 */

define('AUTH_KEY',         '383cfc0bc1d0e10900a035f278e325e42cd0895a');

define('SECURE_AUTH_KEY',  'dacde55c90786f44ca82fb6311060e123c9a06bf');

define('LOGGED_IN_KEY',    '5e63f1725f7141f7b63985b5480d6386a20b583c');

define('NONCE_KEY',        'd84a30ba571c8830ea39e2de06ec827962b5d582');

define('AUTH_SALT',        'bc4a24b794af0abd067c1f39ae5c5dea33ee0a78');

define('SECURE_AUTH_SALT', '61009b770daa67af801ecd5f7a325604cbb5b822');

define('LOGGED_IN_SALT',   '3a82934197a2f0715344fded778ff1134e93d375');

define('NONCE_SALT',       'a6a763419f24defb4d6d9973cce5a184cbcae793');



/**#@-*/



/**

 * WordPress Database Table prefix.

 *

 * You can have multiple installations in one database if you give each

 * a unique prefix. Only numbers, letters, and underscores please!

 */

$table_prefix  = 'wp_';



/**

 * For developers: WordPress debugging mode.

 *

 * Change this to true to enable the display of notices during development.

 * It is strongly recommended that plugin and theme developers use WP_DEBUG

 * in their development environments.

 *

 * For information on other constants that can be used for debugging,

 * visit the Codex.

 *

 * @link https://codex.wordpress.org/Debugging_in_WordPress

 */

define('WP_DEBUG', false);



// If we're behind a proxy server and using HTTPS, we need to alert Wordpress of that fact
// see also http://codex.wordpress.org/Administration_Over_SSL#Using_a_Reverse_Proxy
if (isset($_SERVER['HTTP_X_FORWARDED_PROTO']) &amp;&amp; $_SERVER['HTTP_X_FORWARDED_PROTO'] === 'https') {
    $_SERVER['HTTPS'] = 'on';
}

/* That's all, stop editing! Happy blogging. */



/** Absolute path to the WordPress directory. */

if ( !defined('ABSPATH') )

    define('ABSPATH', dirname(__FILE__) . '/');



/** Sets up WordPress vars and included files. */

require_once(ABSPATH . 'wp-settings.php');


</code></pre>