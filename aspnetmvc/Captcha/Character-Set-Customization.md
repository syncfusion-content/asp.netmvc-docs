---
layout: post
title: Character-Set-Customization
description: character set customization
platform: ejmvc
control: Captcha
documentation: ug
---

## Character Set Customization

The Captcha characters can be customized by CharacterSet property. Depending on this value, the Captcha characters are generated. This property accepts string values.

The following code example is used to render the Captcha with customized character set.

1. Add the following code example to the corresponding CSHTML page to render Captcha with customized character set.

[CSHTML]

@Html.EJ().Captcha("captcha").CharacterSet("qwertyuiop1234") 



2. The following screenshot illustrates the Captcha with customized character set. 

{{ '![](Character-Set-Customization_images/Character-Set-Customization_img1.png)' | markdownify }}
{:.image }


