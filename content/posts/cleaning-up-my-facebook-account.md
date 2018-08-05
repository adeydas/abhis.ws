---
title: "Cleaning Up My Facebook Account"
date: 2018-03-25T19:18:24-07:00
draft: false
tags: [facebook, social media, security, technology]
layout: "post"
---

The Facebook and Cambridge Analytica fiasco brought up a very fundamental question: what more is required on part of the end-user to ensure that their accounts are secure. If you aren't aware of the aforementioned fiasco, a company called Cambridge Analytica retrieved a bunch of data from Facebook using Facebook apps and other means, to draw up profiles and influence voters for Brexit and the recent US Presidential election. If you want to read more about the fiasco, [here's](https://www.vox.com/policy-and-politics/2018/3/23/17151916/facebook-cambridge-analytica-trump-diagram) a nice article on it. Since the time seemed opportune, I decided to do a little spring cleaning of my FB account.

Delete dangling apps
---------------------------
I wish app permissions were deactivated automatically when not used for a certain amount of time. Realistically, we download and access several apps throughout the lifecycle of our FB account but use only a handful of them on a regular cadence. Thus, to me, it makes no sense to let app permissions be forever. However, since app permissions *are* forever today, the first thing I decided to do is remove the apps I no longer use.

Facebook apps and associated permissions are on this page: [https://www.facebook.com/settings?tab=applications](https://www.facebook.com/settings?tab=applications).

My account is about 8 years old and I had 289 apps. Out of those, I use less than 100 on a regular basis. One more thing to look at is the list of data objects the app has access to. You can get to it by clicking on the app. Here's an example of an app with access to my photos, videos, etc:

![Facebook app permissions](/images/2018-03-25_19-50-26.png)

Customize the data fed to the ads network
------------------------------------------
Facebook seems pretty transparent with the kind of ads its showing. The ads settings page is here: [https://www.facebook.com/ads/preferences/?entry_product=ad_settings_screen](https://www.facebook.com/ads/preferences/?entry_product=ad_settings_screen).

I expanded the "advertisers I've interacted with" and was surprised how many of them were matched with my contact information. Facebook can and do share contact information like phone number and email addresses with businesses and they can match and show targeted ads. The interesting bit with regards to account security here is the "Ad settings" section.

![Facebook ad settings](/images/2018-03-25_20-00-31.png)

The most interesting one here is "Ads based on use of websites and apps". To get that working Facebook and other vendors track a bunch of information to streamline ads that one may like. The DAA has a project to request opt-outs from advertisers tracking personal information. Their tool matched me to 133 websites who were tracking my data at the time of writing.

Coming back to Facebook, I set "Show online interest-based ads" to *Off*.

And now a prevention technique.

Check the permissions you are about to give
---------------------------------------------
We often, in the excitement of playing that new game forget to check what permissions we are giving to an app. Whenever a user tries to use a new app that requires a set of permissions, Facebook will explicitly ask for it. I think its a good practice to pay attention to that ask. For instance, I opened up Candy Crush (*no, I didn't end up playing it, if that's what you are wondering*) and these are the permissions it asked for.

![Facebook permissions](/images/2018-03-25_20-15-33.png)

Seems like Candy Crush wants to know both about me and my friends. Now I have never played the game so I am not sure if that's a legitimate request but intuitively it does seem quite a bit.

From a programming perspective, Facebook apps can ask [29 different kinds of permissions from the user](https://developers.facebook.com/docs/facebook-login/permissions/). If you look at the list, it seems like pretty much every category of data that Facebook stores of its users.

Conclusion
---------------
This list is by no means is exhaustive and I wish there was a better, more automated way to explain to end-users what each permission could mean and whether they should grant it. 