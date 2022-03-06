---
title: "Don't just say 'Hi' or 'Hello' in chat!!!"
date: 2020-03-05
author: "Ramaraj T"
tags: [Apple, Custom Keyboard in iOS, iOS, iOS extension, iOS8]
---

I was recently working on a custom keyboard application. I was trying few things (which of course the client asked to do) for many hours, then later I came to know that they are not really possible. I thought I could share them here, so that it may be helpful to someone.

So before developing a custom keyboard extension for iOS, one should consider these things too.

1. No transparent background for the keyboard.
      You can't have a transparent background for your custom keyboard. By default the iOS provide a view which has the default keyboard's background. It may be in light/dark depending on the keyboard appearance (light/dark). You can, of course set any colour to your container view of the keyboard, but not the clearColor.

2. Your keyboard can't be a stand alone. You must have a Main app also. My focus was only on the keyboard, literally the Main app is useless in my case. So I added the About Us and Support screen where I provided some information about my client and instructions about how to enable/use my keyboard.

3. You can't share any information directly from your Main app with your keyboard and vice versa. You have to use App Groups for that. Since Keyboard extension is more like a separate app, both the keyboard and the main app could share the same app group. You can also store the data you don't want to share directly in the default.
   For e.g in my keyboard I stored the last used keyboard, last used theme... information like that directly in the user default. But I also had in app purchases and the user can purchase them only for the Main app, so I stored the purchases details with the app group defaults, which both the apps can share.

4. You can't draw key popups outside your keyboards bounds. So I inserted one more row (with some special characters which will be used more often) in the top of the keyboard, which don't have any popups. And the popups for the second row can be shown now without any problem

5.  Even you don't care about the decimal and special characters, all the keyboard apps must provide the decimal and special characters keyboard in order to pass the app review process.

6. Auto correction, text selection, cut/copy/paste - not possible.

7. Had some problems while deleting characters when using my custom keyboard in Safari address bar, which is normal

8. Use the current selected keyboard type and return key type from the textDocumentroxy and change your keyboard appearance and the return key title accordingly.

9. You have to provide the primary language for your custom keyboard in the info.plist file. Since my keyboard supports multiple language I can't use en/fr/it something like that, but there is a special option just for this. I used the key 'mul' in the primary language of the plist which means 'Multiple Languages'.
