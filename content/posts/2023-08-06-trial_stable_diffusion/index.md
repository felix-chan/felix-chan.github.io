---
title: 初嘗 Stable Diffusion
date: 2023-08-06T11:19:00+08:00
author: HaNg~
url: /2023/08/06/trial_stable_diffusion/
categories:
  - 科技
tags:
  - AI
  - Stable Diffusion
  - Generative AI
  - photo
---

起初以為用 Stable Diffusion 可以直接打一句 prompt 就可以出到想要嘅嘢，就有如係 ChatGPT 咁問一條問題或者俾一個指示，玩左幾下發現原來要有好少少嘅圖，係要俾一個幾清晰嘅指示。好似畫一個空倉庫咁，係參考完唔同嘅網上資源之後，寫左下面正面同負面嘅 prmopt ，先至叫做可以出到令人滿意嘅圖。

**Positive prompt**

 > `High-fashion photography in an abandoned industrial warehouse, with dramatic lighting and edgy outfits,extremely detailed CG unity 8k wallpaper, detailed and intricate, original,highres,best quality`


**Negative prompt**

 > `paintings, sketches, (worst quality:2), (low quality:2), (normal quality:2), lowres, ((monochrome)), ((grayscale)), skin spots, acnes, skin blemishes, age spot, glans,extra fingers,fewer fingers,strange fingers,bad hand,signature, watermark, username, blurry, bad feet,bad leg, duplicate, extra limb, ugly, disgusting, poorly drawn hands, missing limb, floating limbs, disconnected limbs, malformed hands, blurry,mutated hands and fingers`

<!--more--> 

自己慢慢試 prompt 其實都好浪費時間，所以開始之前建議多多參考吓其他人的作品，而我都參考左 [MPost][1] 上面我覺得靚嘅作品。而我嘅行左一陣，就出左以下作品：

{{< figure src="text2img.png" alt="Stable Diffusion Text to Image" position="center" style="border-radius: 8px;" caption="Stable Diffusion Text to Image" captionPosition="center" >}}

本身自己都幾滿意呢幅圖，不過就想係上面加隻雀。如果唔想由頭叫 Stable Diffusion 產生過一系列嘅圖，其實可以用 [Inpaiting][2] 來改一改幅圖。首先選擇 **Send to img2img** ，之後再揀 **inpaint** ，之後佢會出個工具俾我油黑想改嘅部分，咁我就油咗左上角要佢改。再加埋下面嘅 prompt 去要佢加隻雀。不過個人感覺，inpainting 嘅質素係比全圖 generate 差少少。

{{< figure src="inpaint.png" alt="Stable Diffusion Image to Image" position="center" style="border-radius: 8px;" caption="Stable Diffusion Image to Image" captionPosition="center" >}}

嘗試左好幾次，佢都出唔到一隻完整嘅雀，可能因為黑色位置太細只係出到一部分，變左好似俾人斬開左隻雀。好在最後都出到一張比較滿意嘅。

{{< figure src="inpaint_result.png" alt="Stable Diffusion Final Product" position="center" style="border-radius: 8px;" caption="Stable Diffusion Final Product" captionPosition="center" >}}

如果想睇多啲人哋嘅作品，可以考慮吓上 [CIVITAI][3] 嘅網站參考其他人士嘅作品，有唔少都製作精美疑幻疑真。


[1]: https://mpost.io/best-100-stable-diffusion-prompts-the-most-beautiful-ai-text-to-image-prompts/
[2]: https://stable-diffusion-art.com/inpainting_basics/
[3]: https://civitai.com/

