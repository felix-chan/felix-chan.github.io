---
title: 安裝 Stable Diffusion
date: 2023-07-17T17:45:00+08:00
author: HaNg~
url: /2023/07/17/install_stable_diffusion/
categories:
  - 科技
tags:
  - AI
  - Stable Diffusion
  - Generative AI
  - photo
---

近年人工智能技術急速發展，而自從 2022 年出現了 [DALL·E 2][1] 同 [ChatGPT 3.5][2] 之後， [Generative AI][3] 就成為左人工智能界嘅熱門話題。

可惜嘅係，香港自從由亂入治之後，好多新嘅高科技嘢香港都冇得用，而 [OpenAI 嘅 service 都唔例外][4]，所以 Dall-E 呢個由交字生成圖片嘅 AI 香港就未必用到啦。不過唔緊要，市場上仲有 [Stable Diffusion][5] 呢個 opensource framework 可以用，而我就決定下用 Stable Diffusion 去生產圖片。

<!--more--> 

如果自己要由 **0** 開始去設定 Stable Diffusion，真係唔太容易。好在網絡社群已經有唔少有心人整好左唔同嘅 [Stable Diffusion WebUI][6]，方便新手或者我呢類嘅懶人。呢條 link https://github.com/camenduru/stable-diffusion-webui-colab 就好好咁整合左唔同 Google Colab 嘅 [Jupyter Notebook][7]，方便大家一 click 就可以係 Google Service 到開嚟用 Stable Diffusion WebUI。

Google Colab 用就真係好方便，可惜有[資源限制][8]，話咁快就會用晒。我自己都有 GPU ，所以最後決定係自己部機到安裝，唔駛俾 Google 加左咁多限制。我見上網話其實係 Windows 上面都裝到，不過為左方便起見我想用番 Notebook 上面嘅 command ，所以我決定係 [Ubuntu 18.04 LTS][9] 上面用。而安裝指令就要作出一定嘅更改。

首先進入 https://github.com/camenduru/stable-diffusion-webui-colab ，而我選擇左 `neverending_dream_ned_webui_colab` 作為我第一個 model 。

{{< figure src="github.png" alt="Stable Diffusion WebUI Colab" position="center" style="border-radius: 8px;" caption="Stable Diffusion WebUI Colab" captionPosition="center" >}}

入左去之後會開左個 [Google Colab Notebook][10] ，因為部機已經 set 好晒，所以 apt install 個部分我就冇做，直接由第一個 pip 開始。我部機本身有個舊版嘅 CUDA ，而佢又要用 **CUDA 11.8** 去行 [PyTorch 2.0][11] ，呢到我都搞左好一段時間。記住搞好先開始 pip install。

{{< figure src="colab.png" alt="Google Colab 畫面" position="center" style="border-radius: 8px;" caption="Google Colab 畫面" captionPosition="center" >}}

基本上大部分嘅 command 都可以直接用，不過有啲地方行之前要修改一下：

 1. 預設嘅檔案位置係放晒係 `/content` ，有需要嘅話自己改番你想要嘅 path
 2. 如果行唔到 `aria2c` ，可能要安裝番 **aria2**
     - `sudo apt install -y aria2`
 3. 如果你嘅檔案唔係放係 `/content` ，咁你 `sed` 個兩行都要改改佢。我自己就唔熟 `sed` 所以我都係人手開番個 file 改

裝好晒就行以下 command 去開 Stable Diffusion WebUI 。你見我冇左 `--multiple` 同多左 
`--port 8800` ，因為自己機行到就得唔駛開個臨時 URL 去連，而我又想指定用 Port `8800` 。

```sh
python launch.py --listen --xformers --enable-insecure-extension-access --theme dark --gradio-queue --port 8800
```

開完之後係 browser 打番條 link `http://localhost:8800` 就會上到 WebUI。圖片生產旅程正式開始。

{{< figure src="webui.png" alt="WebUI 畫面" position="center" style="border-radius: 8px;" caption="WebUI 畫面" captionPosition="center" >}}

[1]: https://openai.com/dall-e-2
[2]: https://openai.com/blog/chatgpt
[3]: https://www.nvidia.com/en-us/glossary/data-science/generative-ai/
[4]: https://www.cnbc.com/2023/06/12/google-openai-limit-chatbots-in-hong-kong-amid-china-tensions-report.html
[5]: https://stability.ai/
[6]: https://github.com/AUTOMATIC1111/stable-diffusion-webui
[7]: https://jupyter.org/
[8]: https://linux-blog.anracom.com/2023/05/04/google-colab-ram-vram-and-gpu-usage-limits-i-no-clear-conditions-over-multiple-sessions/
[9]: https://releases.ubuntu.com/18.04/
[10]: https://colab.research.google.com/github/camenduru/stable-diffusion-webui-colab/blob/main/stable/neverending_dream_webui_colab.ipynb
[11]: https://pytorch.org/get-started/pytorch-2.0/
