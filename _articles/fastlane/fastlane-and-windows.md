---
title: Fastlane and Windows
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Fastlane and Windows

Unfortunately Fastlane doesn't work on Windows yet. 

Some of its internal dependencies, specifically the way it starts and handles processes, only work on Mac OS and Linux systems. There are workarounds and alternatives for the specific libraries Fatlane uses, but implementing them would mean a major refactoring of Fastlane. Because of this its maintainers are rightfully hesitant to tackle this problem.

As a Windows user myself I really want to change that and use Fastlane on Windows as well.

Theoretically it could be possible to a) develop a small CLI that can be installed on Windows and enables usage of `fastlane` by executing the actual Fastlane on Mac machines in the cloud. Or b) some of the functionality that doesn't require actual Mac software (like Xcode) could maybe be ported in a way that also works on Microsoft Windows.

Are you interested? Please submit your email address to this special mailing list so I can contact you:

{::nomarkdown}
<!-- Begin MailChimp Signup Form -->
<link href="//cdn-images.mailchimp.com/embedcode/slim-10_7.css" rel="stylesheet" type="text/css">
<style type="text/css">
	#mc_embed_signup{background:#fff; clear:left; font:14px Helvetica,Arial,sans-serif; }
	/* Add your own MailChimp form style overrides in your site stylesheet or in this style block.
	   We recommend moving this block and the preceding CSS link to the HEAD of your HTML file. */
</style>
<div id="mc_embed_signup">
<form action="//zone.us16.list-manage.com/subscribe/post?u=343ee35d12246a68f6310af0c&amp;id=be09b8c886" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
    <div id="mc_embed_signup_scroll">
	
	<input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="email address" required>
    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_343ee35d12246a68f6310af0c_be09b8c886" tabindex="-1" value=""></div>
    <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>
    </div>
</form>
</div>
<!--End mc_embed_signup-->
{:/nomarkdown}

Are you **really** interested and want to discuss this _now_ with me? Email me at ionicdotzone@gmail.com with the subject "Fastlane and Windows".