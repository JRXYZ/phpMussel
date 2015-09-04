## phpMussel 自述文件写在中文（简体）。

### 内容
- 1. [前言](#SECTION1)
- 2A. [如何安装（对于WEB服务器）](#SECTION2A)
- 2B. [如何安装（对于CLI）](#SECTION2B)
- 3A. [如何使用（对于WEB服务器）](#SECTION3A)
- 3B. [如何使用（对于CLI）](#SECTION3B)
- 4A. [浏览器命令](#SECTION4A)
- 4B. [CLI（命令行界面）](#SECTION4B)
- 5. [文件在包](#SECTION5)
- 6. [配置选项](#SECTION6)
- 7. [签名格式](#SECTION7)
- 8. [已知的兼容问题](#SECTION8)

---


###1. <a name="SECTION1"></a>前言

谢谢对于使用phpMussel，PHP编程旨在检测木马，病毒，恶意软件，和其他威胁内的文件上传到您的系统随地编程是连接，根据ClamAV的签名和其他签名。

PHPMUSSEL版权2013和此后GNU/GPLv.2通过Caleb M （Maikuolan）。

这个脚本是免费软件;您可以重新分配它和/或修改它按照条款GNU通用公共许可证发表由自由软件基金会;或第2版本的许可证，或（根据您的选择）任何新版本。这个脚本是提供在希望将是有用，但不提供任何担保和不提供任何隐含担保的适销或适用于某一特定用途。见GNU通用公共许可证的更多细节，坐落于`LICENSE`文件于`_docs`文件夹的相关包和知识库的此文件和也可从：
- <http://www.gnu.org/licenses/>。
- <http://opensource.org/licenses/>。

谢谢[ClamAV](http://www.clamav.net/)为计划灵感和为签名这个脚本利用，没有它，这个脚本很可能不会存在，或充其量，将有非常有限的价值。

谢谢Sourceforge和GitHub为主办的计划文件，[Spambot Security](http://www.spambotsecurity.com/forum/viewforum.php?f=55)为主办的phpMussel讨论论坛，和其他来源的签名利用由phpMussel：[SecuriteInfo.com](http://www.securiteinfo.com/)，[PhishTank](http://www.phishtank.com/)，[NLNetLabs](http://nlnetlabs.nl/)和他人，和特别谢谢大家为支持的计划，和任何人我忘了提，和您，为您的运用的脚本。

这个文件和其关联包可以下载免费从：
- [Sourceforge](http://phpmussel.sourceforge.net/）。
- [GitHub](https://github.com/Maikuolan/phpMussel/）。

---


###2A. <a name="SECTION2A"></a>如何安装（对于WEB服务器）

我希望能够简化这过程通过创建的安装程序在某一点在近未来，但直到那个时候，遵循这些说明以经营phpMussel在多数系统和CMS：

1） 通过您的阅读这，我假设您已经下载一个存档的副本的脚本，已解压缩其内容和有它地方的某处上您的机器。从这里，您要决定在哪里在您的服务器您想放这些内容。一个文件夹例如`/public_html/phpmussel/`或类似（无论您选择，不要紧，只要它的安全和您是满意）会是足够了。*之前您开始上传，继续阅读。。*

2） 自选（强烈推荐为高级用户，但不推荐为业余用户或为没有经验用户），打开`phpmussel.ini`（位于内`vault`） - 这个文件包含所有指令可用的为phpMussel。以上的每指令应该有一个简评以说明它做什么和它的功能。调整这些指令您认为合适的，按照随您是适合为您的特定的设置。保存文件，关闭。

3） 上传内容（phpMussel和它的文件）至文件夹您决定在早期（不需要包括`*.txt`/`*.md`文件，但大多，您应该上传的一切）。

4） CMHOD的`vault`文件夹为“755”。主文件夹存储的内容（一个您先前选择），平时，可以单独留，但CHMOD状态应检查如果您有权限问题以往上您的系统（由标准，应该是这样的"755"）。

5） 接下来，您需要｢钩子｣phpMussel为您的系统或CMS。有几种不同的方式在其中您可以｢钩子｣脚本例如phpMussel为您的系统或CMS，但最简单的是简单地包括的脚本在开头的核心文件为您的系统或CMS（这是一个是通常一直加载的当有人访问的任何页面在您的网站）使用`require()`或`include()`命令。平时，这将是存储的在文件夹例如`/includes`，`/assets`或`/functions`，和将经常被命名的某物例如`init.php`，`common_functions.php`，`functions.php`或类似。您需要确定哪些文件这是为您的情况；如果您遇到困难关于确定这为您自己，访问phpMussel支持论坛和让我们知道；这是可能的我自己或其他用户可有经验的该CMS您正在使用（您需要让我们知道其中CMS您正在使用），和从而，可能能够提供援助关于这。为了使用`require()`或`include()`，插入下面的代码行到最开始的该核心文件，更换里面的数据引号以确切的地址的`phpmussel.php`文件（本地地址，不HTTP地址；它会类似于vault地址前面提到的）。

`<?php require '/user_name/public_html/phpmussel/phpmussel.php'；?>`

保存文件，关闭，重新上传。

-- 或交替 --

如果您使用Apache网络服务器和如果您可以访问`php.ini`，您可以使用该`auto_prepend_file`指令为附上的phpMussel每当任何PHP请求是创建。就像是：

`auto_prepend_file = "/user_name/public_html/phpmussel/phpmussel.php"`

或在该`.htaccess`文件：

`php_value auto_prepend_file "/user_name/public_html/phpmussel/phpmussel.php"`

6） 从这里，您完成了！然，您应该测试它以确保它的正常运行。为了测试文件上传保护，尝试上传测试文件包括在包内`_testfiles`至您的网站通过您常用的基于浏览器的上传方法。如果一切正常，信息应该出现从phpMussel以确认上载已成功阻止了。如果出现什么，什么是不正常工作。如果您使用的任何先进的功能或如果您使用的其它类型的扫描可能的，我建议尝试它跟他们以确保其工作正常，也。

---


###2B. <a name="SECTION2B"></a>如何安装（对于CLI）

我希望能够简化这过程通过创建的安装程序在某一点在近未来，但直到那个时候，遵循这些说明为预备phpMussel于操作使用CLI模式（请注意，在这个时候，CLI支持仅适用于基于Windows系统；Linux和其他系统即将推出到更高版本的phpMussel）：

1） 通过您的阅读这，我假设您已经下载一个存档的副本的脚本，已解压缩其内容和有它地方的某处上您的机器。当您决定您满意​​​​与选择的位置为phpMussel，继续。

2） phpMussel需要PHP安装在主机以经营。如果您没有PHP安装上您的机器，请安装PHP上您的机器，和跟随任何指令提供由PHP的安装程序。

3） 自选（强烈推荐为高级用户，但不推荐为业余用户或为没有经验用户），打开`phpmussel.ini`（位于内`vault`） - 这个文件包含所有指令可用的为phpMussel。以上的每指令应该有一个简评以说明它做什么和它的功能。调整这些指令您认为合适的，按照随您是适合为您的特定的设置。保存文件，关闭。

4） 自选，使用的phpMussel在CLI模式可能是更容易为您如果您创建一个批处理文件为自动加载的PHP和phpMussel。要做到这一点，打开一个纯文本编辑器例如Notepad或Notepad++，键入完整路径为`php.exe`文件在文件夹的您的PHP安装，其次是一个空格，然后完整路径为`phpmussel.php`文件在文件夹的您的phpMussel安装，最后，保存此文件使用一个".bat"扩展名在一个地方您会容易发现它；从这里，双击的文件以经营phpMussel在未来。

5） 从这里，您完成了！然，您应该测试它以确保它的正常运行。以测试phpMussel，经营phpMussel和尝试扫描`_testfiles`文件夹提供有包。

---


###3A. <a name="SECTION3A"></a>如何使用（对于WEB服务器）

phpMussel的目的是作为一个脚本这将将满意地和正确地执行｢从开箱｣有最小的要求为您完成：如果正确地安装的，简而言之，它应该正确地功能。

扫描的文件上传是自动和活性由标准，所以，有没有任何需要为您关于这特殊的功能。

然而，另外，您能指示phpMussel至扫描文件，文件夹或存档该您指示以做。要做到这一点，首先，您需要确保适当配置是确定在`phpmussel.ini`文件（cleanup｢清理｣必须关闭），和在做完，在任何一个PHP文件是钩子至phpMussel，使用下列功能在您的代码：

`phpMussel($what_to_scan，$output_type，$output_flatness);`

- `$what_to_scan`可以是字符串，数组，或多维数组，和表明什么文件，收集的文件，文件夹和／或文件夹至扫描。
- `$output_type`是布尔，和表明什么格式以回报扫描结果作为。False｢假／负｣指示关于功能以回报扫描结果作为整数（结果回报的-3表明问题是遇到关于phpMussel签名文件或签名MAP｢地图｣文件和表明他们可能是失踪或损坏，-2表明损坏数据是检测中扫描和因此扫描失败完成，-1表明扩展或插件需要通过PHP以经营扫描是失踪和因此扫描失败完成，0表明扫描目标不存在和因此没有什么至扫描，1表明扫描目标是成功扫描和没有问题是检测，和2表明扫描目标是成功扫描和问至少一些题是检测）。True｢真／正｣指示关于功能以回报扫描结果作为人类可读文本。此外，在任一情况下，结果可以访问通过全局变量后扫描是完成。变量是自选，确定作为False｢假／负｣由标准。
- `$output_flatness`是布尔，表明如果回报扫描结果（如果有多扫描目标）作为数组或字符串。False｢假／负｣指示回报结果作为数组。True｢真／正｣负｣指示回报结果作为字符串。变量是自选，确定作为False｢假／负｣由标准。

例子：

```
 $results=phpMussel('/user_name/public_html/my_file.html'，true，true);
 echo $results;
```

回报这样的事情或类似（作为字符串）：

```
 Wed, 16 Sep 2013 02:49:46 +0000 开始.
 > 检查 '/user_name/public_html/my_file.html'：
 -> 没有问题发现。
 Wed, 16 Sep 2013 02:49:47 +0000 完了.
```

For a full break-down of what sort of签名phpMussel uses during its scans和how it handles these signatures，refer to the Signature Format section of this README file。

If you encounter any false positives，if you encounter something new that you think should be blocked，or为anything else regarding signatures，please contact me about it so that I may make the necessary changes，which，if you do not contact me，I may not necessarily be aware of。

To disable签名included with phpMussel (such as if you're experiencing a false positive specific to your purposes that shouldn't normally be removed from streamline)，refer to the Greylisting notes within the Browser Commands section of this README file。

In addition to the default文件upload scanning和the optional scanning of other文件和／或 directories specified via the above function，included in phpMussel是a function intended为scanning the body of email messages. This function behaves similarly to the standard phpMussel() function，but focuses solely on matching against the ClamAV email-based signatures. I have not tied these签名into the standard phpMussel() function，because it是highly unlikely that you'd ever find the body of an incoming email message in need of scanning within a文件upload targeted to a page where phpMussel是hooked，和thus，to tie these签名into the phpMussel() function would be redundant. However，that said，having a separate function to match against these签名could prove to be extremely useful为some，especially为those whose CMS or webfront system是somehow tied into their email system和for those parsing their emails via a php脚本that they could potentially hook into phpMussel。Configuration为this function，like all others，是controlled via the `phpmussel.ini` file. To use this function (you'll need to do your own implementation)，in a php文件that是hooked to phpMussel，use 下列 function在您的code：

`phpMussel_mail($body);`

Where $body是body of the email message you wish to scan (additionally，you could try scanning new forum posts，inbound messages from your online contact form or similar). If any error occurs preventing the function from completing its scan，a value of -1 will be returned. If the function completes its scan和doesn't match anything，a value of 0 will be returned (meaning clean). If，however，the function does match something，a string will be returned containing a message declaring what it has matched。

In addition to the above，if you look at the source code，you may notice the function phpMusselD()和phpMusselR(). These functions are sub-functions of phpMussel()，和shouldn't be called directly outside of that parent function (not because of adverse effects，but rather，simply because it'd serve no purpose，和most probably won't actually work correctly anyhow）。

There are many other controls和functions available within phpMussel为your use，too.为any such controls和functions which，by the end of this section of the README，have not yet been documented，please continue reading和refer to the Browser Commands section of this README file。

---


###3B. <a name="SECTION3B"></a>如何使用（对于CLI）

Please refer to the "如何安装（对于CLI）" section of this readme file。

Be aware that，虽说 future versions of phpMussel should support other systems，at this time，phpMussel CLI mode support是only optimized为use on Windows-based system (you can，of course，try it on other systems，but I can't guarantee it'll work as intended）。

Also be aware that phpMussel是not the functional equivalent of a complete 杀毒 suite，和unlike conventional 杀毒 suites，doesn't monitor active memory or detect viruses on-the-fly! It'll only detect viruses contained by those specific文件that you explicitly tell it to scan。

---


###4A. <a name="SECTION4A"></a>浏览器命令

Once phpMussel has been installed和is correctly functioning on your system，if you've set the script_password和logs_password variables在您的配置文件，you will be able to perform some limited number of administrative functions和input some number of commands to phpMussel via your browser. The reason these passwords need to be set in order to enable these browser-side controls是both to ensure proper security，proper protection of these browser-side controls和to ensure that there exists a way为these browser-side controls to be entirely disabled if they are not desired by you 和／或 other webmasters/administrators using phpMussel。So，in other words，to enable these controls，set a pasword，和to disable these controls，set no password. Alternatively，if you choose to enable these controls和then choose to disable these controls at a later date，there是a command to do this (such can be useful if you perform some actions that you feel could potentially compromise the delegated passwords和need to quickly disable these controls without modifying your 配置文件）。

A couple of reasons why you _**SHOULD**_ enable these controls：
- Provides a way to greylist签名on-the-fly in instances例如when you discover a signature that是producing a false-positive while uploading文件to your system和you don't have time to manually edit和重新上传 your greylist file。
- Provides a way为you to allow someone other than yourself to control your copy of phpMussel without the implicit need to grant them access to FTP。
- Provides a way to provide controlled access to your log files。
- Provides an easy way to update phpMussel when updates are available。
- Provides a way为you to monitor phpMussel when FTP access or other conventional access points为monitoring phpMussel are not available。

A couple of reasons why you should _**NOT**_ enable these controls：
- Provides a vector为potential attackers和undesirables to determine whether you're using phpMussel or not (虽说，this could be both a reason for和a reason against，depending on perspective) by way of blindly sending commands to servers as a means to probe. On one hand，this could discourage attackers from targeting your system if they learn that you're using phpMussel，assuming that they are probing because their attack method是rendered ineffective as a result of using phpMussel。However，on the other hand，if some unforeseen和currently unknown exploit within phpMussel or a future version thereof comes to light，和if it could potentially provide an attack vector，a positive result from such probing could actually encourage attackers to target your system。
- If your delegated passwords were ever compromised，unless changed，could provide a way为an attacker to bypass whatever签名may be otherwise normally preventing their attacks from succeeding，or even potentially disable phpMussel altogether，thus providing a way to render the effectiveness of phpMussel moot。

Either way，regardless of what you choose，the choice是ultimately yours. By default，these controls will be disabled，but have a think about it，和if you decide you want them，this section explains both how to enable them和how to use them。

A list of available browser-side commands：

scan_log
- Password required: logs_password
- Other requirements: scan_log must be set。
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?logspword=[logs_password]&phpmussel=scan_log`
- What it does: Prints the contents of your scan_log文件to the screen。

scan_kills
- Password required: logs_password
- Other requirements: scan_kills must be set。
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?logspword=[logs_password]&phpmussel=scan_kills`
- What it does: Prints the contents of your scan_kills文件to the screen。

controls_lockout
- Password required: logs_password OR script_password
- Other requirements: (none)
- Required parameters: (none)
- Optional parameters: (none)
- Example 1: `?logspword=[logs_password]&phpmussel=controls_lockout`
- Example 2: `?pword=[script_password]&phpmussel=controls_lockout`
- What it does: Disables ("locks out") all browser-side controls. This should be used if you suspect that either of your passwords have been compromised (this can happen if you're using these controls from a computer that's not secured 和／或 not trusted). controls_lockout works by creating a file，`controls.lck`，在您的vault，that phpMussel will check为before performing any commands of any kind. Once this happens，to reenable controls，you'll need to manually delete the `controls.lck`文件via FTP or similar. Can be called using either password。

disable
- Password required: script_password
- Other requirements: (none)
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=disable`
- What it does: Disables phpMussel。This should be used if you're performing any updates or changes to your system or if you're installing any new 软件 or modules to your system that either does or potentially could trigger false positives. This should also be used if you're having any problems with phpMussel but don't wish to remove it from your system. Once this happens，to reenable phpMussel，use "enable"。

enable
- Password required: script_password
- Other requirements: (none)
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=enable`
- What it does: Enables phpMussel。This should be used if you've previously disabled phpMussel using "disable"和want to reenable it。

update
- Password required: script_password
- Other requirements: `update.dat`和`update.inc` must exist。
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=update`
- What it does: Checks为updates to both phpMussel和its signatures. If update checks succeed和updates are found，will attempt to download和install these updates. If update checks fail，update will abort. Results of the entire process are printed to the screen. I recommend checking at least once per month to ensure that your signatures和your copy of phpMussel are kept up to-date (unless，of course，you're checking为updates和installing them manually，which，I'd still recommend doing at least once per month). Checking more than twice per month是probably pointless，considering I'm (at the time of writing this) working on this 计划 by myself和I'm very unlikely to be able to produce updates of any kind more frequently than that (nor do I particularly want to为the most part）。

greylist
- Password required: script_password
- Other requirements: (none)
- Required parameters: [Name of signature to be greylisted]
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=greylist&musselvar=[Signature]`
- What it does: Add a signature to the greylist。

greylist_clear
- Password required: script_password
- Other requirements: (none)
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=greylist_clear`
- What it does: Clears the entire greylist。

greylist_show
- Password required: script_password
- Other requirements: (none)
- Required parameters: (none)
- Optional parameters: (none)
- Example: `?pword=[script_password]&phpmussel=greylist_show`
- What it does: Prints the contents of the greylist to the screen。

---


###4B. <a name="SECTION4B"></a>CLI（命令行界面）

phpMussel can be run as an interactive文件scanner in CLI mode under Windows-based systems. Refer to the "如何安装（对于CLI）" section of this readme file为more details。

For a list of available CLI commands，at the CLI prompt，type 'c'，和press Enter。

---


###5. <a name="SECTION5"></a>文件在包

下面是一个列表的所有的文件该应该是存在在您的存档在下载时间，任何文件该可能创建作为结果的您的使用这个脚本，包括一个简短说明的他们的目的。

文件                                       | 说明
-------------------------------------------|--------------------------------------
/phpmussel.php                             | 加载文件。它加载主脚本，更新文件，和等等。这个是文件您应该｢钩子｣（必不可少）!
/web.config                                | 一个ASP.NET配置文件（在这种情况，以保护`/vault`文件夹从被访问由非授权来源在事件的脚本是安装在服务器根据ASP.NET技术）。
/_docs/                                    | 笔记文件夹（包含若干文件）。
/_docs/change_log.txt                      | 记录的变化做出至脚本间不同版本（不需要为正确经营脚本）。
/_docs/readme.de.md                        | 自述文件：DEUTSCH
/_docs/readme.de.txt                       | 自述文件：DEUTSCH
/_docs/readme.en.md                        | 自述文件：ENGLISH
/_docs/readme.en.txt                       | 自述文件：ENGLISH
/_docs/readme.es.md                        | 自述文件：ESPAÑOL
/_docs/readme.es.txt                       | 自述文件：ESPAÑOL
/_docs/readme.fr.md                        | 自述文件：FRANÇAIS
/_docs/readme.fr.txt                       | 自述文件：FRANÇAIS
/_docs/readme.id.md                        | 自述文件：BAHASA INDONESIA
/_docs/readme.id.txt                       | 自述文件：BAHASA INDONESIA
/_docs/readme.it.md                        | 自述文件：ITALIANO
/_docs/readme.it.txt                       | 自述文件：ITALIANO
/_docs/readme.nl.md                        | 自述文件：NEDERLANDSE
/_docs/readme.nl.txt                       | 自述文件：NEDERLANDSE
/_docs/readme.pt.md                        | 自述文件：PORTUGUÊS
/_docs/readme.pt.txt                       | 自述文件：PORTUGUÊS
/_docs/readme.ru.md                        | 自述文件：РУССКИЙ
/_docs/readme.ru.txt                       | 自述文件：РУССКИЙ
/_docs/signatures_tally.txt                | 文件为数量追踪的为包含的签名（不需要为正确经营脚本）。
/_testfiles/                               | 测试文件文件夹（包含若干文件）。所有包含文件是测试文件为测试如果phpMussel是正确地安装上您的系统，和您不需要上传这个文件夹或任何其文件除为上传测试。
/_testfiles/ascii_standard_testfile.txt    | 测试文件以测试phpMussel标准化ASCII签名。
/_testfiles/coex_testfile.rtf              | 测试文件以测试phpMussel复杂扩展签名。
/_testfiles/exe_standard_testfile.exe      | 测试文件以测试phpMussel移植可执行｢PE｣签名。
/_testfiles/general_standard_testfile.txt  | 测试文件以测试phpMussel通用签名。
/_testfiles/graphics_standard_testfile.gif | 测试文件以测试phpMussel图像签名。
/_testfiles/html_standard_testfile.txt     | 测试文件以测试phpMussel标准化HTML签名。
/_testfiles/md5_testfile.txt               | 测试文件以测试phpMussel MD5签名。
/_testfiles/metadata_testfile.tar          | 测试文件以测试phpMussel元数据签名和以测试TAR文件支持在您的系统。
/_testfiles/metadata_testfile.txt.gz       | 测试文件以测试phpMussel元数据签名和以测试GZ文件支持在您的系统。
/_testfiles/metadata_testfile.zip          | 测试文件以测试phpMussel元数据签名和以测试ZIP文件支持在您的系统。
/_testfiles/ole_testfile.ole               | 测试文件以测试phpMussel OLE签名。
/_testfiles/pdf_standard_testfile.pdf      | 测试文件以测试phpMussel PDF签名。
/_testfiles/pe_sectional_testfile.exe      | 测试文件以测试phpMussel移植可执行｢PE｣部分签名。
/_testfiles/swf_standard_testfile.swf      | 测试文件以测试phpMussel SWF签名。
/_testfiles/xdp_standard_testfile.xdp      | 测试文件以测试phpMussel XML／XDP块签名。
/vault/                                    | 安全／保险库｢Vault｣文件夹（包含若干文件）。
/vault/cache/                              | 缓存｢Cache｣文件夹（为临时数据）。
/vault/cache/.htaccess                     | 超文本访问文件（在这种情况，以保护敏感文件属于脚本从被访问由非授权来源）。
/vault/lang/                               | 包含phpMussel语言数据。
/vault/lang/.htaccess                      | 超文本访问文件（在这种情况，以保护敏感文件属于脚本从被访问由非授权来源）。
/vault/lang/lang.de.inc                    | 语言数据：DEUTSCH
/vault/lang/lang.en.inc                    | 语言数据：ENGLISH
/vault/lang/lang.es.inc                    | 语言数据：ESPAÑOL
/vault/lang/lang.fr.inc                    | 语言数据：FRANÇAIS
/vault/lang/lang.id.inc                    | 语言数据：BAHASA INDONESIA
/vault/lang/lang.it.inc                    | 语言数据：ITALIANO
/vault/lang/lang.ja.inc                    | 语言数据：日本語
/vault/lang/lang.nl.inc                    | 语言数据：NEDERLANDSE
/vault/lang/lang.pt.inc                    | 语言数据：PORTUGUÊS
/vault/lang/lang.ru.inc                    | 语言数据：РУССКИЙ
/vault/lang/lang.vi.inc                    | 语言数据：TIẾNG VIỆT
/vault/lang/lang.zh.inc                    | 语言数据：中文（简体）
/vault/lang/lang.zh-TW.inc                 | 语言数据：中文（傳統）
/vault/quarantine/                         | 隔离文件夹（包含隔离文件）。
/vault/quarantine/.htaccess                | 超文本访问文件（在这种情况，以保护敏感文件属于脚本从被访问由非授权来源）。
/vault/.htaccess                           | 超文本访问文件（在这种情况，以保护敏感文件属于脚本从被访问由非授权来源）。
/vault/ascii_clamav_regex.cvd              | 标准化ASCII签名文件。
/vault/ascii_clamav_regex.map              | 标准化ASCII签名文件。
/vault/ascii_clamav_standard.cvd           | 标准化ASCII签名文件。
/vault/ascii_clamav_standard.map           | 标准化ASCII签名文件。
/vault/ascii_custom_regex.cvd              | 标准化ASCII签名文件。
/vault/ascii_custom_standard.cvd           | 标准化ASCII签名文件。
/vault/ascii_mussel_regex.cvd              | 标准化ASCII签名文件。
/vault/ascii_mussel_standard.cvd           | 标准化ASCII签名文件。
/vault/coex_clamav.cvd                     | 复杂扩展签名文件。
/vault/coex_custom.cvd                     | 复杂扩展签名文件。
/vault/coex_mussel.cvd                     | 复杂扩展签名文件。
/vault/elf_clamav_regex.cvd                | ELF签名文件。
/vault/elf_clamav_regex.map                | ELF签名文件。
/vault/elf_clamav_standard.cvd             | ELF签名文件。
/vault/elf_clamav_standard.map             | ELF签名文件。
/vault/elf_custom_regex.cvd                | ELF签名文件。
/vault/elf_custom_standard.cvd             | ELF签名文件。
/vault/elf_mussel_regex.cvd                | ELF签名文件。
/vault/elf_mussel_standard.cvd             | ELF签名文件。
/vault/exe_clamav_regex.cvd                | 移植可执行｢PE｣签名文件。
/vault/exe_clamav_regex.map                | 移植可执行｢PE｣签名文件。
/vault/exe_clamav_standard.cvd             | 移植可执行｢PE｣签名文件。
/vault/exe_clamav_standard.map             | 移植可执行｢PE｣签名文件。
/vault/exe_custom_regex.cvd                | 移植可执行｢PE｣签名文件。
/vault/exe_custom_standard.cvd             | 移植可执行｢PE｣签名文件。
/vault/exe_mussel_regex.cvd                | 移植可执行｢PE｣签名文件。
/vault/exe_mussel_standard.cvd             | 移植可执行｢PE｣签名文件。
/vault/filenames_clamav.cvd                | 文件名签名文件。
/vault/filenames_custom.cvd                | 文件名签名文件。
/vault/filenames_mussel.cvd                | 文件名签名文件。
/vault/general_clamav_regex.cvd            | 通用签名文件。
/vault/general_clamav_regex.map            | 通用签名文件。
/vault/general_clamav_standard.cvd         | 通用签名文件。
/vault/general_clamav_standard.map         | 通用签名文件。
/vault/general_custom_regex.cvd            | 通用签名文件。
/vault/general_custom_standard.cvd         | 通用签名文件。
/vault/general_mussel_regex.cvd            | 通用签名文件。
/vault/general_mussel_standard.cvd         | 通用签名文件。
/vault/graphics_clamav_regex.cvd           | 图像签名文件。
/vault/graphics_clamav_regex.map           | 图像签名文件。
/vault/graphics_clamav_standard.cvd        | 图像签名文件。
/vault/graphics_clamav_standard.map        | 图像签名文件。
/vault/graphics_custom_regex.cvd           | 图像签名文件。
/vault/graphics_custom_standard.cvd        | 图像签名文件。
/vault/graphics_mussel_regex.cvd           | 图像签名文件。
/vault/graphics_mussel_standard.cvd        | 图像签名文件。
/vault/greylist.csv                        | 灰名单签名CSV（逗号分隔变量）文件说明为phpMussel什么签名它应该忽略（文件自动重新创建如果删除）。
/vault/hex_general_commands.csv            | 十六进制编码的CSV（逗号分隔变量）为通用命令检测，使用可选通过phpMussel。
/vault/html_clamav_regex.cvd               | 标准化HTML签名文件。
/vault/html_clamav_regex.map               | 标准化HTML签名文件。
/vault/html_clamav_standard.cvd            | 标准化HTML签名文件。
/vault/html_clamav_standard.map            | 标准化HTML签名文件。
/vault/html_custom_regex.cvd               | 标准化HTML签名文件。
/vault/html_custom_standard.cvd            | 标准化HTML签名文件。
/vault/html_mussel_regex.cvd               | 标准化HTML签名文件。
/vault/html_mussel_standard.cvd            | 标准化HTML签名文件。
/vault/lang.inc                            | 语言数据。
/vault/macho_clamav_regex.cvd              | Mach-O签名文件。
/vault/macho_clamav_regex.map              | Mach-O签名文件。
/vault/macho_clamav_standard.cvd           | Mach-O签名文件。
/vault/macho_clamav_standard.map           | Mach-O签名文件。
/vault/macho_custom_regex.cvd              | Mach-O签名文件。
/vault/macho_custom_standard.cvd           | Mach-O签名文件。
/vault/macho_mussel_regex.cvd              | Mach-O签名文件。
/vault/macho_mussel_standard.cvd           | Mach-O签名文件。
/vault/mail_clamav_regex.cvd               | 电子邮件签名文件。
/vault/mail_clamav_regex.map               | 电子邮件签名文件。
/vault/mail_clamav_standard.cvd            | 电子邮件签名文件。
/vault/mail_clamav_standard.map            | 电子邮件签名文件。
/vault/mail_custom_regex.cvd               | 电子邮件签名文件。
/vault/mail_custom_standard.cvd            | 电子邮件签名文件。
/vault/mail_mussel_regex.cvd               | 电子邮件签名文件。
/vault/mail_mussel_standard.cvd            | 电子邮件签名文件。
/vault/mail_mussel_standard.map            | 电子邮件签名文件。
/vault/md5_clamav.cvd                      | 基于MD5签名文件。
/vault/md5_custom.cvd                      | 基于MD5签名文件。
/vault/md5_mussel.cvd                      | 基于MD5签名文件。
/vault/metadata_clamav.cvd                 | 存档元数据签名文件。
/vault/metadata_custom.cvd                 | 存档元数据签名文件。
/vault/metadata_mussel.cvd                 | 存档元数据签名文件。
/vault/ole_clamav_regex.cvd                | OLE签名文件。
/vault/ole_clamav_regex.map                | OLE签名文件。
/vault/ole_clamav_standard.cvd             | OLE签名文件。
/vault/ole_clamav_standard.map             | OLE签名文件。
/vault/ole_custom_regex.cvd                | OLE签名文件。
/vault/ole_custom_standard.cvd             | OLE签名文件。
/vault/ole_mussel_regex.cvd                | OLE签名文件。
/vault/ole_mussel_standard.cvd             | OLE签名文件。
/vault/pdf_clamav_regex.cvd                | PDF签名文件。
/vault/pdf_clamav_regex.map                | PDF签名文件。
/vault/pdf_clamav_standard.cvd             | PDF签名文件。
/vault/pdf_clamav_standard.map             | PDF签名文件。
/vault/pdf_custom_regex.cvd                | PDF签名文件。
/vault/pdf_custom_standard.cvd             | PDF签名文件。
/vault/pdf_mussel_regex.cvd                | PDF签名文件。
/vault/pdf_mussel_standard.cvd             | PDF签名文件。
/vault/pe_clamav.cvd                       | 移植可执行｢PE｣部分签名文件。
/vault/pe_custom.cvd                       | 移植可执行｢PE｣部分签名文件。
/vault/pe_mussel.cvd                       | 移植可执行｢PE｣部分签名文件。
/vault/pex_custom.cvd                      | 移植可执行｢PE｣扩展签名文件。
/vault/pex_mussel.cvd                      | 移植可执行｢PE｣扩展签名文件。
/vault/phpmussel.inc                       | 主脚本；主体和机制的phpMussel（必不可少）！
/vault/phpmussel.ini                       | 配置文件;包含所有配置指令为phpMussel，告诉它什么做和怎么正确地经营（必不可少）!
※ /vault/scan_log.txt                     | 记录的一切phpMussel扫描。
※ /vault/scan_kills.txt                   | 记录的所有上传文件phpMussel受阻／杀。
/vault/swf_clamav_regex.cvd                | Shockwave签名文件。
/vault/swf_clamav_regex.map                | Shockwave签名文件。
/vault/swf_clamav_standard.cvd             | Shockwave签名文件。
/vault/swf_clamav_standard.map             | Shockwave签名文件。
/vault/swf_custom_regex.cvd                | Shockwave签名文件。
/vault/swf_custom_standard.cvd             | Shockwave签名文件。
/vault/swf_mussel_regex.cvd                | Shockwave签名文件。
/vault/swf_mussel_standard.cvd             | Shockwave签名文件。
/vault/switch.dat                          | 控制和确定某些变量。
/vault/template.html                       | 模板文件；模板为HTML产量产生通过phpMussel为它的受阻文件上传信息（信息可见向上传者）。
/vault/template_custom.html                | 模板文件；模板为HTML产量产生通过phpMussel为它的受阻文件上传信息（信息可见向上传者）。
/vault/update.dat                          | 文件包含版本信息为phpMussel的脚本和phpMussel的签名。如果您随时需要自动更新phpMussel或需要更新phpMussel通过您的浏览器，这个文件是必不可少。
/vault/update.inc                          | 更新脚本；需要为自动更新和为更新phpMussel通过您的浏览器，但不否则需要。
/vault/whitelist_clamav.cvd                | 文件具体白名单。
/vault/whitelist_custom.cvd                | 文件具体白名单。
/vault/whitelist_mussel.cvd                | 文件具体白名单。
/vault/xmlxdp_clamav_regex.cvd             | XML／XDP块签名文件。
/vault/xmlxdp_clamav_regex.map             | XML／XDP块签名文件。
/vault/xmlxdp_clamav_standard.cvd          | XML／XDP块签名文件。
/vault/xmlxdp_clamav_standard.map          | XML／XDP块签名文件。
/vault/xmlxdp_custom_regex.cvd             | XML／XDP块签名文件。
/vault/xmlxdp_custom_standard.cvd          | XML／XDP块签名文件。
/vault/xmlxdp_mussel_regex.cvd             | XML／XDP块签名文件。
/vault/xmlxdp_mussel_standard.cvd          | XML／XDP块签名文件。

※ Filename may differ based on configuration stipulations (in `phpmussel.ini`）。

####*REGARDING SIGNATURE FILES*
CVD是an acronym为"ClamAV Virus Definitions"，in reference both to how ClamAV refers to its own signatures和to the use of those签名for phpMussel;文件ending with "CVD" contain签名。

Files ending with "MAP"，quite literally，map which签名phpMussel should和shouldn't use为individual scans；Not all签名are necessarily required为every single scan，so，phpMussel uses maps of the signature文件to speed up the scanning process (a process that would otherwise be extremely slow和tedious）。

Signature文件marked with "_regex" contain签名that utilise regular expression pattern checking (regex）。

Signature文件marked with "_standard" contain签名that specifically don't utilise any form of pattern checking。

Signature文件marked with neither "_regex" nor "_standard" will be as one or the other，but not both (refer to the Signature Format section of this README file为documentation和specific details）。

Signature文件marked with "_clamav" contain签名that are sourced entirely from the ClamAV database (GNU/GPL）。

Signature文件marked with "_custom"，by default，don't contain any签名at all；These such文件exist to give you somewhere to place your own custom signatures，if you come up with any of your own。

Signature文件marked with "_mussel" contain签名that specifically are not sourced from ClamAV，签名which，generally，I've either come up with myself 和／或 based on information gathered from various 来源。


---


###6. <a name="SECTION6"></a>配置选项
下列是a list of variables found在`phpmussel.ini` 配置文件 of phpMussel，along with a description of their purpose和function。

####"general" (Category)
General phpMussel configuration。

"script_password"
- As a convenience，phpMussel will allow certain functions (including the ability to update phpMussel on-the-fly) to be manually triggered via POST，GET和QUERY. However，as a security precaution，要做到这一点，phpMussel will expect a password to be included with the command，as to ensure that it's you，和not someone else，attempting to manually trigger these functions. Set script_password to whatever password you would like to use. If no password是set，manual triggering will be disabled by default. Use something you will remember but which是hard为others to guess。
- Has no influence in CLI mode。

"logs_password"
- The same as script_password，but为viewing the contents of scan_log和scan_kills. Having separate passwords can be useful if you want to give someone else access to one set of functions but not the other。
- Has no influence in CLI mode。

"cleanup"
- Unset脚本variables和cache after execution. If you're not using the脚本beyond the initial scanning of uploads，should set to yes，to minimize memory usage. If you're using the脚本for purposes beyond the initial scanning of uploads，should set to no，to avoid unnecessarily reloading duplicate data into memory. In general practise，it should probably be set to yes，but，if you do this，you won't be able to use the脚本for anything other than scanning文件uploads。
- Has no influence in CLI mode。

"scan_log"
- Filename of文件to log all scanning results to. Specify a filename，or leave blank to disable。

"scan_kills"
- Filename of文件to log all records of blocked or killed uploads to. Specify a filename，or leave blank to disable。

"ipaddr"
- Where to find IP address of connecting request? (Useful为services例如Cloudflare和the likes) Default = REMOTE_ADDR. WARNING: Don't change this unless you know what you're doing!

"forbid_on_block"
- Should phpMussel send 403 headers with the文件upload blocked message，or stick with the usual 200 OK? 0 = No (200) [Default]，1 = Yes (403）。

"delete_on_sight"
- Enabling this directive will instruct the脚本to attempt to immediately delete any scanned attempted文件upload matching any detection criteria，whether via签名or otherwise.文件determined to be "clean" won't be touched.在case of archives，the entire archive will be deleted，regardless of 不论是否 the offending file是only one of several文件contained within the archive.为the case of文件upload scanning，usually，it isn't necessary to enable this directive，because usually，php will automatically purge the contents of its cache when execution has finished，meaning it'll usually delete any文件uploaded through it to the server unless they've been moved，copied or deleted already. This directive是added here as an extra measure of security为those whose copies of php mightn't always behave在manner expected. 0 - After scanning，leave the文件alone [Default]，1 - After scanning，if not clean，delete immediately。

"lang"
- Specify the default language为phpMussel。

"lang_override"
- Specify if phpMussel should，when possible，override the language specification with the language preference declared by inbound requests (HTTP_ACCEPT_LANGUAGE). 0 - No [Default]，1 - Yes。

"lang_acceptable"
- The `lang_acceptable` directive tells phpMussel which languages may be accepted by the脚本from `lang` or from `HTTP_ACCEPT_LANGUAGE`. This directive should **ONLY** be modified if you're adding your own customised language文件or forcibly removing language files. The directive是a comma delimited string of the codes used by those languages accepted by the script。

"quarantine_key"
- phpMussel是able to quarantine flagged attempted文件uploads in isolation within the phpMussel vault，if this是something you want it to do. Casual users of phpMussel that simply wish to protect their websites or hosting environment without having any interest in deeply analysing any flagged attempted文件uploads should leave this functionality disabled，but any users interested in further analysis of flagged attempted文件uploads为malware research or为similar such things should enable this functionality. Quarantining of flagged attempted文件uploads can sometimes also assist in debugging false-positives，if this是something that frequently occurs为you. To disable quarantine functionality，simply leave the `quarantine_key` directive empty，or erase the contents of that directive if it isn't already empty. To enable quarantine functionality，enter some value into the directive. The `quarantine_key`是an important security feature of the quarantine functionality required as a means of preventing the quarantine functionality from being exploited by potential attackers和as a means of preventing any potential execution of data stored within the quarantine. The `quarantine_key` should be treated在same manner as your passwords: The longer the better，和guard it tightly.为best effect，use in conjunction with `delete_on_sight`。

"quarantine_max_filesize"
- The maximum allowable filesize of文件to be quarantined.文件larger than the value specified will NOT be quarantined. This directive是important as a means of making it more difficult为any potential attackers to flood your quarantine with unwanted data potentially causing run-away data usage on your hosting service. Value是in KB. Default =2048 =2048KB =2MB。

"quarantine_max_usage"
- The maximum memory usage allowed为the quarantine. If the total memory used by the quarantine reaches this value，the oldest quarantined文件will be deleted until the total memory used no longer reaches this value. This directive是important as a means of making it more difficult为any potential attackers to flood your quarantine with unwanted data potentially causing run-away data usage on your hosting service. Value是in KB. Default =65536 =65536KB =64MB。

"honeypot_mode"
- When honeypot mode是enabled，phpMussel will attempt to quarantine every single文件upload that it encounters，regardless of 不论是否 the文件being uploaded matches any included signatures，和no actual scanning or analysis of those attempted文件uploads will actually occur. This functionality should be useful为those that wish to use phpMussel为the purposes of virus/malware research，but it's neither recommended to enable this functionality if the intended use of phpMussel by the user is为actual文件upload scanning，nor recommended to use the honeypot functionality为purposes other than honeypotting. By default，this option是disabled. 0 = Disabled [Default]，1 = Enabled。

"scan_cache_expiry"
-为how long should phpMussel cache the results of scanning? Value是the number of seconds to cache the results of scanning for. Default是21600 seconds (6 hours)；A value of 0 will disable caching the results of scanning。

"disable_cli"
- Disable CLI mode? CLI mode是enabled by default，but can sometimes interfere with certain testing tools (such as PHPUnit，为example)和other CLI-based applications. If you don't need to disable CLI mode，you should ignore this directive. 0 = Enable CLI mode [Default]，1 = Disable CLI mode。

####"signatures" (Category)
Signatures configuration。
- %%%_clamav = ClamAV签名(both mains和daily）。
- %%%_custom = Your custom签名(if you've written any）。
- %%%_mussel = phpMussel签名included在您的current签名set that aren't from ClamAV。

Check against MD5签名when scanning? 0 = No，1 = Yes [Default]。
- "md5_clamav"
- "md5_custom"
- "md5_mussel"

Check against 通用签名when scanning? 0 = No，1 = Yes [Default]。
- "general_clamav"
- "general_custom"
- "general_mussel"

Check against 标准化ASCII签名when scanning? 0 = No，1 = Yes [Default]。
- "ascii_clamav"
- "ascii_custom"
- "ascii_mussel"

Check against 标准化HTML签名when scanning? 0 = No，1 = Yes [Default]。
- "html_clamav"
- "html_custom"
- "html_mussel"

Check移植可执行｢PE｣文件(EXE，DLL，etc) against移植可执行｢PE｣Sectional签名when scanning? 0 = No，1 = Yes [Default]。
- "pe_clamav"
- "pe_custom"
- "pe_mussel"

Check移植可执行｢PE｣文件(EXE，DLL，etc) against移植可执行｢PE｣extended签名when scanning? 0 = No，1 = Yes [Default]。
- "pex_custom"
- "pex_mussel"

Check移植可执行｢PE｣文件(EXE，DLL，etc) against 移植可执行｢PE｣签名when scanning? 0 = No，1 = Yes [Default]。
- "exe_clamav"
- "exe_custom"
- "exe_mussel"

Check ELF文件against ELF签名when scanning? 0 = No，1 = Yes [Default]。
- "elf_clamav"
- "elf_custom"
- "elf_mussel"

Check Mach-O文件(OSX，etc) against Mach-O签名when scanning? 0 = No，1 = Yes [Default]。
- "macho_clamav"
- "macho_custom"
- "macho_mussel"

Check graphics文件against graphics based签名when scanning? 0 = No，1 = Yes [Default]。
- "graphics_clamav"
- "graphics_custom"
- "graphics_mussel"

Check archive contents against archive metadata签名when scanning? 0 = No，1 = Yes [Default]。
- "metadata_clamav"
- "metadata_custom"
- "metadata_mussel"

Check OLE objects against OLE签名when scanning? 0 = No，1 = Yes [Default]。
- "ole_clamav"
- "ole_custom"
- "ole_mussel"

Check filenames against filename based签名when scanning? 0 = No，1 = Yes [Default]。
- "filenames_clamav"
- "filenames_custom"
- "filenames_mussel"

Allow scanning with phpMussel_mail()? 0 = No，1 = Yes [Default]。
- "mail_clamav"
- "mail_custom"
- "mail_mussel"

Enable文件specific whitelist? 0 = No，1 = Yes [Default]。
- "whitelist_clamav"
- "whitelist_custom"
- "whitelist_mussel"

Check XML／XDP chunks against XML／XDP块签名when scanning? 0 = No，1 = Yes [Default]。
- "xmlxdp_clamav"
- "xmlxdp_custom"
- "xmlxdp_mussel"

Check against 复杂扩展签名when scanning? 0 = No，1 = Yes [Default]。
- "coex_clamav"
- "coex_custom"
- "coex_mussel"

Check against PDF签名when scanning? 0 = No，1 = Yes [Default]。
- "pdf_clamav"
- "pdf_custom"
- "pdf_mussel"

Check against Shockwave签名when scanning? 0 = No，1 = Yes [Default]。
- "swf_clamav"
- "swf_custom"
- "swf_mussel"

Signature matching length limiting options. Only change these if you know what you're doing. SD = Standard signatures. RX = PCRE (Perl Compatible Regular Expressions，or "Regex") signatures. FN = Filename signatures. If you notice php crashing when phpMussel attempts to scan，try lowering these "max" values. If possible和convenient，let me know when this happens和the results of whatever you try。
- "fn_siglen_min"
- "fn_siglen_max"
- "rx_siglen_min"
- "rx_siglen_max"
- "sd_siglen_min"
- "sd_siglen_max"

"fail_silently"
- Should phpMussel report when签名files are missing or corrupted? If fail_silently是disabled，missing和corrupted文件will be reported on scanning，和if fail_silently是enabled，missing和corrupted文件will be ignored，with scanning reporting为those文件that there aren't any problems. This should generally be left alone unless you're experiencing crashes或类似problems. 0 = Disabled，1 = Enabled [Default]。

"fail_extensions_silently"
- Should phpMussel report when extensions are missing? If fail_extensions_silently是disabled，missing extensions will be reported on scanning，和if fail_extensions_silently是enabled，missing extensions will be ignored，with scanning reporting为those文件that there aren't any problems. Disabling this directive may potentially increase your security，but may also lead to an increase of false positives. 0 = Disabled，1 = Enabled [Default]。

"detect_adware"
- Should phpMussel parse签名for detecting adware? 0 = No，1 = Yes [Default]。

"detect_joke_hoax"
- Should phpMussel parse签名for detecting joke/hoax malware/viruses? 0 = No，1 = Yes [Default]。

"detect_pua_pup"
- Should phpMussel parse签名for detecting PUAs/PUPs? 0 = No，1 = Yes [Default]。

"detect_packer_packed"
- Should phpMussel parse签名for detecting packers和packed data? 0 = No，1 = Yes [Default]。

"detect_shell"
- Should phpMussel parse签名for detecting shell scripts? 0 = No，1 = Yes [Default]。

"detect_deface"
- Should phpMussel parse签名for detecting defacements和defacers? 0 = No，1 = Yes [Default]。

####"files" (Category)
File handling configuration。

"max_uploads"
- Maximum allowable number of文件to scan during文件upload scan before aborting the scan和informing the user they are uploading too much at once! Provides protection against a theoretical attack whereby an attacker attempts to DDoS your system or CMS by overloading phpMussel to slow down the php process to a grinding halt. Recommended: 10. You may wish to raise or lower this number depending on the speed of your hardware. Note that this number doesn't account为or include the contents of archives。

"filesize_limit"
- Filesize limit in KB. 65536 = 64MB [Default]，0 = No limit (always greylisted)，any (positive) numeric value accepted. This can be useful when your php configuration limits the amount of memory a process can hold or if your php configuration limits filesize of uploads。

"filesize_response"
- What to do with文件that exceed the filesize limit (if one exists). 0 - Whitelist，1 - Blacklist [Default]。

"filetype_whitelist"，"filetype_blacklist"，"filetype_greylist"
- If your system only allows specific types of文件to be uploaded，or if your system explicitly denies certain types of files，specifying those filetypes in whitelists，blacklists和greylists can increase the speed at which scanning是performed by allowing the脚本to skip over certain filetypes. Format是CSV (comma separated values). If you want to scan everything，rather than whitelist，blacklist or greylist，leave the variable(/s) blank；Doing so will disable whitelist/blacklist/greylist。
- Logical order of processing is：
  - If the filetype是whitelisted，don't scan和don't block the file，和don't check the文件against the blacklist or the greylist。
  - If the filetype是blacklisted，don't scan the文件but block it anyway，和don't check the文件against the greylist。
  - If the greylist是empty or if the greylist是not empty和the filetype是greylisted，scan the文件as per normal和determine whether to block it based on the results of the scan，but if the greylist是not empty和the filetype是not greylisted，treat the文件as blacklisted，therefore not scanning it but blocking it anyway。

"check_archives"
- Attempt to check the contents of archives? 0 - No (do not check)，1 - Yes (check) [Default]。
- Currently，only checking of BZ，GZ，LZF和ZIP文件is supported (checking of RAR，CAB，7z和etcetera not currently supported）。
- This是not foolproof! While I highly recommend keeping this turned on，I can't guarantee it'll always find everything。
- Also be aware that archive checking currently是not recursive为ZIPs。

"filesize_archives"
- Carry over filesize blacklisting/whitelisting to the contents of archives? 0 - No (just greylist everything)，1 - Yes [Default]。

"filetype_archives"
- Carry over filetype blacklisting/whitelisting to the contents of archives? 0 - No (just greylist everything) [Default]，1 - Yes。

"max_recursion"
- Maximum recursion depth limit为archives. Default = 10。

"block_encrypted_archives"
- Detect和block encrypted archives? Because phpMussel isn't able to scan the contents of encrypted archives，it's possible that archive encryption may be employed by an attacker as a means of attempting to bypass phpMussel，杀毒 scanners和other such protections. Instructing phpMussel to block any archives that it discovers to be encrypted could potentially help reduce any risk associated with these such possibilities. 0 - No，1 - Yes [Default]。

####"attack_specific" (Category)
Attack-specific directives。

Chameleon attack detection: 0 = Off，1 = On。

"chameleon_from_php"
- Search为php header in文件that are neither php文件nor recognised archives。

"chameleon_from_exe"
- Search为executable headers in文件that are neither executables nor recognised archives和for executables whose headers are incorrect。

"chameleon_to_archive"
- Search为archives whose headers are incorrect (Supported: BZ，GZ，RAR，ZIP，RAR，GZ）。

"chameleon_to_doc"
- Search为office documents whose headers are incorrect (Supported: DOC，DOT，PPS，PPT，XLA，XLS，WIZ）。

"chameleon_to_img"
- Search为images whose headers are incorrect (Supported: BMP，DIB，PNG，GIF，JPEG，JPG，XCF，PSD，PDD，WEBP）。

"chameleon_to_pdf"
- Search为PDF文件whose headers are incorrect。

"archive_file_extensions"和"archive_file_extensions_wc"
- Recognised archive文件extensions (format是CSV；should only add or remove when problems occur；unnecessarily removing may cause false-positives to appear为archive files，whereas unnecessarily adding will essentially whitelist what you're adding from attack specific detection；modify with caution；also note that this has no effect on what archives can和can't be analysed at content-level). The list，as是at default，lists those formats used most commonly across the majority of systems和CMS，but intentionally isn't necessarily comprehensive。

"general_commands"
- Search content of files为general commands例如`eval()`，`exec()`和`include()`? 0 - No (do not check) [Default]，1 - Yes (check). Disable this option if you intend to upload any of 下列 to your system or CMS via your browser: PHP，JavaScript，HTML，python，perl files和etcetera. Enable this option if you don't have any additional protections on your system和do not intend to upload such files. If you use additional security in conjunction with phpMussel例如ZB Block，there是no need to turn this option on，because most of what phpMussel will look为(in the context of this option) are duplications of protections that are already provided。

"block_control_characters"
- Block any文件containing any control characters (other than newlines)? (`[\x00-\x08\x0b\x0c\x0e\x1f\x7f]`) If you're _**ONLY**_ uploading plain-text，then you can turn this option on to provide some additional protection to your system. However，if you upload anything other than plain-text，turning this on may result in false positives. 0 - Don't block [Default]，1 - Block。

"corrupted_exe"
- Corrupted files和parse errors. 0 = Ignore，1 = Block [Default]. Detect和block potentially corrupted移植可执行｢PE｣ files? Often (but not always)，when certain aspects of a移植可执行｢PE｣file are corrupted or can't be parsed correctly，it can be indicative of a viral infection. The processes used by most 杀毒 programs to detect viruses in PE文件require parsing those文件in certain ways，which，if the programmer of a virus是aware of，will specifically try to prevent，in order to allow their virus to remain undetected。

"decode_threshold"
- Optional limitation or threshold to the length of raw data within which decode commands should be detected (in case there are any noticeable performance issues whilst scanning). Value是an integer representing filesize in KB. Default = 512 (512KB). Zero or null value disables the threshold (removing any such limitation based on filesize）。

"scannable_threshold"
- Optional limitation or threshold to the length of raw data that phpMussel是permitted to read和scan (in case there are any noticeable performance issues whilst scanning). Value是an integer representing filesize in KB. Default = 32768 (32MB). Zero or null value disables the threshold. Generally，this value shouldn't be less than the average filesize of文件uploads that you want和expect to receive to your server or website，shouldn't be more than the filesize_limit directive，和shouldn't be more than roughly one fifth of the total allowable memory allocation granted to php via the php.ini 配置文件. This directive exists to try to prevent phpMussel from using up too much memory (that'd prevent it from being able to successfully scan文件above a certain filesize）。

####"compatibility" (Category)
Compatibility directives为phpMussel。

"ignore_upload_errors"
- This directive should generally be disabled unless it's required为correct functionality of phpMussel on your specific system. Normally，when disabled，when phpMussel detects the presence of elements在`$_FILES` array()，it'll attempt to initiate a scan of the文件that those elements represent，and，if those elements are blank or empty，phpMussel will return an error message. This是proper behaviour为phpMussel。However，为some CMS，empty elements in `$_FILES` can occur as a result of the natural behaviour of those CMS，or errors may be reported when there aren't any，in which case，the normal behaviour为phpMussel will be interfering with the normal behaviour of those CMS. If such a situation occurs为you，enabling this option will instruct phpMussel to not attempt to initiate scans为such empty elements，ignore them when found和to not return any related error messages，thus allowing continuation of the page request. 0 - OFF，1 - ON。

"only_allow_images"
- If you only expect or only intend to allow images to be uploaded to your system or CMS，和if you absolutely don't require any文件other than images to be uploaded to your system or CMS，this directive should be enabled，but should otherwise be disabled. If this directive是enabled，it'll instruct phpMussel to indiscriminately block any uploads identified as non-image files，without scanning them. This may reduce processing time和memory usage为attempted uploads of non-image files. 0 - OFF，1 - ON。

####"heuristic" (Category)
Heuristic directives。

"threshold"
- There are certain签名of phpMussel that are intended to identify suspicious和potentially malicious qualities of文件being uploaded without in themselves identifying those文件being uploaded specifically as being malicious. This "threshold" value tells phpMussel what the maximum total weight of suspicious和potentially malicious qualities of文件being uploaded that's allowable是before those文件are to be flagged as malicious. The definition of weight in this context是the total number of suspicious和potentially malicious qualities identified. By default，this value will be set to 3. A lower value generally will result in a higher occurrence of false positives but a higher number of malicious文件being flagged，whereas a higher value generally will result in a lower occurrence of false positives but a lower number of malicious文件being flagged. It's generally best to leave this value at its default unless you're experiencing problems related to it。

####"virustotal" (Category)
VirusTotal.com directives。

"vt_public_api_key"
- Optionally，phpMussel是able to scan文件using the Virus Total API as a way to provide a greatly enhanced level of protection against viruses，trojans，malware和other threats. By default，scanning文件using the Virus Total API是disabled. To enable it，an API key from Virus Total是required. Due to the significant benefit that this could provide to you，it's something that I highly recommend enabling. Please be aware，however，that to use the Virus Total API，you _**MUST**_ agree to their Terms of Service和you _**MUST**_ adhere to all guidelines as per described by the Virus Total documentation! You are NOT permitted to use this integration feature UNLESS：
  - You have read和agree to the Terms of Service of Virus Total和its API. The Terms of Service of Virus Total和its API can be found [Here](https://www.virustotal.com/en/about/terms-of-service/）。
  - You have read和you understand，at a minimum，the preamble of the Virus Total Public API documentation (everything after "VirusTotal Public API v2.0" but before "Contents"). The Virus Total Public API documentation can be found [Here](https://www.virustotal.com/en/documentation/public-api/）。

Note: If scanning文件using the Virus Total API是disabled，you won't need to review any of the directives in this category (`virustotal`)，because none of them will do anything if this是disabled. To acquire a Virus Total API key，from anywhere on their website，click the "Join our Community" link located towards the top-right of the page，enter在information requested，和click "Sign up" 在做完. Follow all instructions supplied，和when you've got your public API key，copy/paste that public API key to the `vt_public_api_key` directive of the `phpmussel.ini` 配置文件。

"vt_suspicion_level"
- By default，phpMussel will restrict which文件it scans using the Virus Total API to those文件that it considers "suspicious". You can optionally adjust this restriction by changing the value of the `vt_suspicion_level` directive。
- `0`:文件are only considered suspicious if，upon being scanned by phpMussel using its own signatures，they are deemed to carry a heuristic weight. This would effectively mean that use of the Virus Total API would be为a second opinion为when phpMussel suspects that a文件may potentially be malicious，but can't entirely rule out that it may also potentially be benign (non-malicious)和therefore would otherwise normally not block it or flag it as being malicious。
- `1`:文件are considered suspicious if，upon being scanned by phpMussel using its own signatures，they are deemed to carry a heuristic weight，if they're known to be executable (PE files，Mach-O files，ELF/Linux files，etc)，or if they're known to be of a format that could potentially contain executable data (such as executable macros，DOC/DOCX files，archive文件such as RARs，ZIPS和etc). This是the default和recommended suspicion level to apply，effectively meaning that use of the Virus Total API would be为a second opinion为when phpMussel doesn't initially find anything malicious or wrong with a文件that it considers to be suspicious和therefore would otherwise normally not block it or flag it as being malicious。
- `2`: All文件are considered suspicious和should be scanned using the Virus Total API. I don't generally recommend applying this suspicion level，due to the risk of reaching your API quota much quicker than would otherwise be the case，but there are certain circumstances (such as when the webmaster or hostmaster has very little faith or trust whatsoever in any of the uploaded content of their users) where this suspicion level could be appropriate. With this suspicion level，all文件not normally blocked or flagged as being malicious would be scanned using the Virus Total API. Note，however，that phpMussel will cease using the Virus Total API when your API quota has been reached (regardless of suspicion level)，和that your quota will likely be reached much faster when using this suspicion level。

Note: Regardless of suspicion level，any文件that are either blacklisted or whitelisted by phpMussel won't be scanned using the Virus Total API，because those such文件would've already been declared as either malicious or benign by phpMussel by the time that they would've otherwise been scanned by the Virus Total API，和therefore，additional scanning wouldn't be required. The ability of phpMussel to scan文件using the Virus Total API是intended to build further confidence为whether a file是malicious or benign in those circumstances where phpMussel itself isn't entirely certain as to whether a file是malicious or benign。

"vt_weighting"
- Should phpMussel apply the results of scanning using the Virus Total API as detections or as detection weighting? This directive exists，because，虽说 scanning a文件using multiple engines (as Virus Total does) should result in an increased detection rate (and therefore in a higher number of malicious文件being caught)，it can also result in a higher number of false positives，和therefore，in some circumstances，the results of scanning may be better utilised as a confidence score rather than as a definitive conclusion. If a value of 0是used，the results of scanning using the Virus Total API will be applied as detections，和therefore，if any engine used by Virus Total flags the文件being scanned as being malicious，phpMussel will consider the文件to be malicious. If any other value是used，the results of scanning using the Virus Total API will be applied as detection weighting，和therefore，the number of engines used by Virus Total that flag the文件being scanned as being malicious will serve as a confidence score (or detection weighting)为不论是否 the文件being scanned should be considered malicious by phpMussel (the value used will represent the minimum confidence score or weight required in order to be considered malicious). A value of 0是used by default。

"vt_quota_rate"和"vt_quota_time"
- According to the Virus Total API documentation，"it是limited to at most 4 requests of any nature in any given 1 minute time frame. If you run a honeyclient，honeypot or any other automation that是going to provide re来源 to VirusTotal和not only retrieve reports you are entitled to a higher request rate quota". By default，phpMussel will strictly adhere to these limitations，but due to the possibility of these rate quotas being increased，these two directives are provided as a means为you to instruct phpMussel as to what limit it should adhere to. Unless you've been instructed to do so，it's不推荐为you to increase these values，but，if you've encountered problems relating to reaching your rate quota，decreasing these values _**MAY**_ sometimes help you in dealing with these problems. Your rate limit是determined as `vt_quota_rate` requests of any nature in any given `vt_quota_time` minute time frame。

####"template_data" (Category)
Directives/Variables为templates和themes。

Template data relates to the HTML output used to generate the "Upload Denied" message displayed to users upon a文件upload being blocked. If you're using custom themes为phpMussel，HTML output是sourced from the `template_custom.html` file，和otherwise，HTML output是sourced from the `template.html` file. Variables written to this section of the 配置文件 are parsed to the HTML output by way of replacing any variable names circumfixed by curly brackets found within the HTML output with the corresponding variable data.为example，where `foo="bar"`，any instance of `<p>{foo}</p>` found within the HTML output will become `<p>bar</p>`。

"css_url"
- The 模板文件为custom themes utilises external CSS properties，whereas the 模板文件为the default theme utilises internal CSS properties. To instruct phpMussel to use the 模板文件为custom themes，specify the public HTTP address of your custom theme's CSS文件using the `css_url` variable. If you leave this variable blank，phpMussel will use the 模板文件为the default theme。

---


###7. <a name="SECTION7"></a>签名格式

####*FILENAME SIGNATURES*
All filename签名follow the format：

`NAME:FNRX`

Where NAME是the name to cite为that signature和FNRX是the regex pattern to match filenames (unencoded) against。

####*MD5 SIGNATURES*
All MD5签名follow the format：

`HASH:FILESIZE:NAME`

Where HASH是the MD5 hash of an entire file，FILESIZE是the total size of that file和NAME是the name to cite为that signature。

####*ARCHIVE 元数据签名*
All archive metadata签名follow the format：

`NAME:FILESIZE:CRC32`

Where NAME是the name to cite为that signature，FILESIZE是the total size (uncompressed) of a文件contained within the archive和CRC32是the CRC32 checksum of that contained file。

####*PE SECTIONAL SIGNATURES*
All移植可执行｢PE｣Sectional签名follow the format：

`SIZE:HASH:NAME`

Where HASH是the MD5 hash of a section of a移植可执行｢PE｣file，SIZE是the total size of that section和NAME是the name to cite为that signature。

####*PE EXTENDED SIGNATURES*
All移植可执行｢PE｣extended签名follow the format：

`$VAR:HASH:SIZE:NAME`

Where $VAR是the name of the移植可执行｢PE｣variable to match against，HASH是the MD5 hash of that variable，SIZE是the total size of that variable和NAME是the name to cite为that signature。

####*WHITELIST SIGNATURES*
All Whitelist签名follow the format：

`HASH:FILESIZE:TYPE`

Where HASH是the MD5 hash of an entire file，FILESIZE是the total size of that file和TYPE是the type of签名the whitelisted file是to be immune against。

####*复杂扩展 SIGNATURES*
复杂扩展签名are rather different to the other types of签名possible with phpMussel，in that what they are matching against是specified by the签名themselves和they can match against multiple criteria. The match criterias are delimited by ";"和the match type和match data of each match criteria是delimited by ":" as so that format为these签名tends to look a bit like：

`$variable1:SOMEDATA;$variable2:SOMEDATA;SignatureName`

####*EVERYTHING ELSE*
All other签名follow the format：

`NAME:HEX:FROM:TO`

Where NAME是the name to cite为that signature和HEX是a hexadecimal-encoded segment of the文件intended to be matched by the given signature. FROM和TO are optional parameters，indicting from which和to which positions在source data to check against (not supported by the mail function）。

####*REGEX*
Any form of regex understood和correctly processed by php should also be correctly understood和processed by phpMussel和its signatures. However，I'd suggest taking extreme caution when writing new regex based signatures，because，if you're not entirely sure what you're doing，there can be highly irregular 和／或 unexpected results. Take a look at the phpMussel source-code if you're not entirely sure about the context in which regex statements are parsed. Also，remember that all patterns (with exception to filename，archive metadata和MD5 patterns) must be hexadecimally encoded (foregoing pattern syntax，of course)!

####*WHERE TO PUT CUSTOM SIGNATURES?*
Only put custom签名in those文件intended为custom signatures. Those文件should contain "_custom" in their filenames. You should also avoid editing the default signature files，unless you know exactly what you're doing，because，aside from being good practise in general和aside from helping you distinguish between your own signatures和the default签名included with phpMussel，it's good to stick to editing only the文件intended为editing，because tampering with the default signature文件can cause them to stop working correctly，due to the "maps" files: The maps文件tell phpMussel where在signature文件to look for签名required by phpMussel as per when required，和these maps can become out-of-sync with their associated signature文件if those signature文件are tampered with. You can put pretty much whatever you want into your custom signatures，so long as you follow the correct syntax. However，be careful to test new签名for false-positives beforehand if you intend to share them or use them in a live environment。

####*SIGNATURE BREAKDOWN*
下列是a breakdown of the types of签名used by phpMussel：
- "Normalised ASCII Signatures" (ascii_*). Checked against the contents of every non-whitelisted文件targeted为scanning。
- "复杂扩展 Signatures" (coex_*). Mixed signature type matching。
- "ELF Signatures" (elf_*). Checked against the contents of every non-whitelisted文件targeted为scanning和matched to the ELF format。
- "Portable Executable Signatures" (exe_*). Checked against the contents of every non-whitelisted targeted为scanning和matched to the移植可执行｢PE｣format。
- "Filename Signatures" (filenames_*). Checked against the filenames of文件targeted为scanning。
- "General Signatures" (general_*). Checked against the contents of every non-whitelisted文件targeted为scanning。
- "Graphics Signatures" (graphics_*). Checked against the contents of every non-whitelisted文件targeted为scanning和matched to a known graphical文件format。
- "General Commands" (hex_general_commands.csv). Checked against the contents of every non-whitelisted文件targeted为scanning。
- "Normalised HTML Signatures" (html_*). Checked against the contents of every non-whitelisted HTML文件targeted为scanning。
- "Mach-O Signatures" (macho_*). Checked against the contents of every non-whitelisted文件targeted为scanning和matched to the Mach-O format。
- "Email Signatures" (mail_*). Checked against the $body variable parsed to the phpMussel_mail() function，which是intended to be the body of email messages或类似entities (potentially forum posts和etcetera）。
- "MD5 Signatures" (md5_*). Checked against the MD5 hash of the contents和the filesize of every non-whitelisted文件targeted为scanning。
- "Archive 元数据签名" (metadata_*). Checked against the CRC32 hash和filesize of the initial文件contained inside of any non-whitelisted archive targeted为scanning。
- "OLE Signatures" (ole_*). Checked against the contents of every non-whitelisted OLE object targeted为scanning。
- "PDF Signatures" (pdf_*). Checked against the contents of every non-whitelisted PDF文件targeted为scanning。
- "Portable Executable Sectional Signatures" (pe_*). Checked against the MD5 hash和the size of each移植可执行｢PE｣section of every non-whitelisted文件targeted为scanning和matched to the移植可执行｢PE｣format。
- "Portable Executable Extended Signatures" (pex_*). Checked against the MD5 hash和the size of variables within every non-whitelisted文件targeted为scanning和matched to the移植可执行｢PE｣format。
- "SWF Signatures" (swf_*). Checked against the contents of every non-whitelisted Shockwave文件targeted为scanning。
- "Whitelist Signatures" (whitelist_*). Checked against the MD5 hash of the contents和the filesize of every文件targeted为scanning. Matched文件will be immune to being matched by the type of signature mentioned in their whitelist entry。
- "XML／XDP块 Signatures" (xmlxdp_*). Checked against any XML／XDP chunks found within any non-whitelisted文件targeted为scanning。
(Note that any of these签名may be easily disabled via `phpmussel.ini`）。

---


###8. <a name="SECTION8"></a>已知的兼容问题

####PHP和PCRE
- phpMussel requires PHP和PCRE to execute和function correctly. Without PHP，or without the PCRE extension of PHP，phpMussel won't execute or function correctly. Should make sure your system has both PHP和PCRE installed和available prior to downloading和installing phpMussel。

####杀毒软件兼容性

在大多数情况下，phpMussel应该相当兼容性与大多数杀毒软件。然，冲突已经报道由多个用户以往。下面这些信息是从VirusTotal.com，和它描述了一个数的假阳性报告的各种杀毒软件针对phpMussel。虽说信息是不绝对的保证的不论是否您会遇到兼容性问题间phpMussel和您的杀毒软件，如果您的杀毒软件是 noted as flagging against phpMussel，you should either consider disabling it prior to working with phpMussel or should consider alternative options to either 您的杀毒软件 or phpMussel。

This information was last updated 28th May 2015和is current为all phpMussel releases of the two most recent minor versions (v0.5-v0.6i) at the time of writing this。

| 扫描器               |  结果                                 |
|----------------------|--------------------------------------|
| Ad-Aware             |  没有已知的问题                       |
| Agnitum              |  没有已知的问题                       |
| AhnLab-V3            |  没有已知的问题                       |
| AntiVir              |  没有已知的问题                       |
| Antiy-AVL            |  没有已知的问题                       |
| Avast                |  报告 "JS:ScriptSH-inf [Trj]"        |
| AVG                  |  没有已知的问题                       |
| Baidu-International  |  没有已知的问题                       |
| BitDefender          |  没有已知的问题                       |
| Bkav                 |  报告 "VEXDAD2.Webshell"             |
| ByteHero             |  没有已知的问题                       |
| CAT-QuickHeal        |  没有已知的问题                       |
| ClamAV               |  没有已知的问题                       |
| CMC                  |  没有已知的问题                       |
| Commtouch            |  没有已知的问题                       |
| Comodo               |  没有已知的问题                       |
| DrWeb                |  没有已知的问题                       |
| Emsisoft             |  没有已知的问题                       |
| ESET-NOD32           |  没有已知的问题                       |
| F-Prot               |  没有已知的问题                       |
| F-Secure             |  没有已知的问题                       |
| Fortinet             |  没有已知的问题                       |
| GData                |  没有已知的问题                       |
| Ikarus               |  没有已知的问题                       |
| Jiangmin             |  没有已知的问题                       |
| K7AntiVirus          |  没有已知的问题                       |
| K7GW                 |  没有已知的问题                       |
| Kaspersky            |  没有已知的问题                       |
| Kingsoft             |  没有已知的问题                       |
| Malwarebytes         |  没有已知的问题                       |
| McAfee               |  报告 "New Script.c"                 |
| McAfee-GW-Edition    |  报告 "New Script.c"                 |
| Microsoft            |  没有已知的问题                       |
| MicroWorld-eScan     |  没有已知的问题                       |
| NANO-Antivirus       |  没有已知的问题                       |
| Norman               |  没有已知的问题                       |
| nProtect             |  没有已知的问题                       |
| Panda                |  没有已知的问题                       |
| Qihoo-360            |  没有已知的问题                       |
| Rising               |  没有已知的问题                       |
| Sophos               |  没有已知的问题                       |
| SUPERAntiSpyware     |  没有已知的问题                       |
| Symantec             |  报告 "WS.Reputation.1"              |
| TheHacker            |  没有已知的问题                       |
| TotalDefense         |  没有已知的问题                       |
| TrendMicro           |  没有已知的问题                       |
| TrendMicro-HouseCall |  没有已知的问题                       |
| VBA32                |  没有已知的问题                       |
| VIPRE                |  没有已知的问题                       |
| ViRobot              |  没有已知的问题                       |


---


最近更新时间： 2015.09.03。