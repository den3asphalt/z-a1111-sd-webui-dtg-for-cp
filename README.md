## A1111-SD-WebUI-DTGのconfig-presets用改変版

### 変更点
私がよく使うモデルの[BAXLv3](https://civitai.com/models/212253/baxl-or-blue-archive-flat-celluloid-style-fine-tune-or-kohaku-d-and-animagine-xl-v3)の推奨設定ではdtgが使われており、設定を保存していつでも呼び出せるようにしたかった。

[config-presets](https://github.com/Zyin055/Config-Presets)では、Gradioのelem_idが存在する設定を保存してくれるため、これを付与した。

初心者だから何か間違えていたらごめんなさい。

# English translation

## Modified version of A1111-SD-WebUI-DTG for config-presets

### Changes.
The recommended settings for [BAXLv3](https://civitai.com/models/212253/baxl-or-blue-archive-flat-celluloid-style-fine-tune-or-kohaku-d-and-animagine-xl-v3), the model I use most often, use dtg and I wanted to be able to save the settings and recall them at any time.

The [config-presets](https://github.com/Zyin055/Config-Presets) will save the settings where Gradio's elem_id is present, so I gave it to them.

I'm a newbie, so sorry if I'm doing something wrong.

# Original text below

# A1111-SD-WebUI-DTG

A sd-webui extension for utilizing DanTagGen to "upsample prompts".

It can generate the detail tags/core tags about the character you put in the prompts. It can also add some extra elements into your prompt.

**an extra z is added to repo name to ensure this extension will run `process()` after other extensions**

## What is DanTagGen

DanTagGen(Danbooru Tag Generator) is a LLM model designed for generating Danboou Tags with provided informations.
It aims to provide user a more convinient way to make prompts for Text2Image model which is trained on Danbooru datasets.

More information about model arch and training data can be found in the HuggingFace Model card:

[KBlueLeaf/DanTagGen-beta · Hugging Face](https://huggingface.co/KBlueLeaf/DanTagGen-beta)

## How to use it

After install it into the sd-webui or sd-webui-forge. Just enable it in the acordion. It will automatically read the content of your prompt and generate more tags based on your prompt.

### Options

* tag length:
  * very short: around 10 tags
  * short: around 20 tags
  * long: around 40 tags
  * very long: around 60 tags
  * ***short or long is recommended***
* Ban tags: The black list of tags you don't want to see in final prompt. Regex supported.
* Prompt Format: The format of final prompt. Default value is the recommended format of [Kohaku XL Delta](https://civitai.com/models/332076/kohaku-xl-delta)
* Seed: the seed of prompt generator. Since we use temperature/top k/top p sampling, so it is not deterministic unless you use same seed. -1 for random seed.
* Upsampling timing:
  * After: after other prompt processings, for example: after dynamic prompts/wildcard.
  * Before: Before other prompt processings.
* Temperature: Higher = more dynamic result, Lower = better coherence between tags.

## Example

![image](https://github.com/KohakuBlueleaf/z-a1111-sd-webui-dtg/assets/59680068/e45995c6-561f-4068-b78c-eeffaf4f9e5f)

## Faster inference

You can now select models in Generation config accordion. The script will automatically download the selected models if it is not existed. (Include gguf model.)

If you want to download the gguf model by yourself, you need to rename it to `<Model Name>_<GGUF Name>` for example: `DanTagGen-gamma_ggml-model-Q6_K.gguf`
