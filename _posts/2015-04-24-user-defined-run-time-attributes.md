---
title: "User defined run time attributes"
date: 2015-04-24
author: "Ramaraj T"
tags: [Apple, Intermediate, iOS, Key Value Coding, KVC, User Defined run time attributes, Xib]
---

User defined run time attributes are one of the hidden(likely) gems of the XCode which helps you to customise/configure your UI object in the interface builder itself, without having to write code.

The "User defined run time attributes" uses the Obejctive-C's already existed concept called Key Value Coding. With the Xcode 6, this is a game changer, see here IBInspectable and IBDesignable

*Key value coding is a mechanism which helps us to access the properties of an object indirectly by name (or key, which is a string) rather than directly using the accessor method.*

That means, say for example you have the property `text` for the `UILabel`, you can use the user defined runtime attributes for changing its value.

<br/>
<p align="center">
<img src="{{site.baseUrl}}/assets/1.png" width="500">
</p>
<br/>
<br/>

Wait, who would do that? The `UILabel` control already have the IB properties for giving the text.
But, think of some other properties that the IB doesn't have. You can do that in the u.d.r.a (ah.,, user defined run time attributes, I am tired of typing this).

For example, here I have a custom class called `CustomLabel` which is a subclass of `UILabel` which have a property called `fontName`. When I give string here, my `CustomLabel` will use this string and updates it font. I can assign the value to this `fontName` in the Xib itself like this.

<br/>
<p align="center">
<img src="/assets/2.png" width="500">
</p>
<br/>
<br/>

The fun part is you can give not only key but also the key paths. (For those who doesn't know the difference between the key and the keypath, `text` is a key for the `UILabel` whereas `layer.cornerRadius` is a keypath for its corner radius)

For example, if you want to change the corner radios of a `UIView`, you can add a u.d.r.a  with the keypath `layer.cornerRadius`.

<br/>
<p align="center">
<img src="/assets/3.png" width="500">
</p>
<br/>
<br/>

Don't try to give the `layer.borderColor` in this way, because `borderColor` needs a `CGColor` object but you can only give `UIColor` with the u.d.r.a. If you want to achieve this, you can add a category for the `CALayer` with a `UIColor` property and you can write your own logic to change its borderColor.

Note:
  If you give a u.d.r.a to a UI object, that doesn't have a property with that name, you will get a warning from the debugger like this. In the previous Xcode, it will raise a invalid argument exception and crash.

<br/>
<p align="center">
<img src="/assets/4.png" width="500">
</p>
<br/>
<br/>


Here is a list of attribute types that you can use in the u.d.r.a.

<br/>
<p align="center">
<img src="/assets/5.png">
</p>
<br/>
<br/>


For the sake of clarity, I am adding the screenshot of my `CustomLabel` class here.
<br/>
<p align="center">
<img src="/assets/6.png" width="500">
</p>
<br/>
<br/>
<p align="center">
<img src="/assets/7.png" width="500">
</p>
<br/>
<br/>

[Here is the link for the Apple Docs in this topic.](https://developer.apple.com/library/prerelease/ios/recipes/xcode_help-interface_builder/Chapters/AddUserDefinedRuntimeAttributes.html)
