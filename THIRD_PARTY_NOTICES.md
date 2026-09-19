# Third-Party Notices

YuE2 Studio incorporates, adapts, downloads, or interoperates with software and model components developed by third parties.

These components remain subject to their respective licenses. Nothing in the YuE2 Studio license replaces or overrides those licenses.

## 1. YuE Studio

YuE2 Studio is based in part on and contains modifications derived from:

**YuE Studio**  
Author / maintainer: tonywestonuk  
Source: https://github.com/tonywestonuk/YuE-Studio  
License: Apache License 2.0

YuE2 Studio includes substantial modifications and additional application-level functionality.

YuE Studio and its author are not affiliated with and do not endorse YuE2 Studio.

## 2. YuE2

**YuE2**  
Developer: Multimodal Art Projection and contributors  
Source: https://github.com/multimodal-art-projection/YuE  
License for first-party source code: Apache License 2.0

YuE2 Studio uses and/or adapts YuE2 inference functionality for local operation on Apple Silicon.

The Apache License applying to YuE2 source code does not apply to the YuE2 model weights.

## 3. YuE2 Model Weights

The following model checkpoint weights are distributed or downloaded separately under Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0):

- YuE2-3B
- YuE2-Vae
- YuE2-Vae-legacy, where applicable

Sources:

https://huggingface.co/m-a-p/YuE2-3B  
https://huggingface.co/m-a-p/YuE2-Vae

License:

https://creativecommons.org/licenses/by-nc/4.0/

These model weights are not relicensed by YuE2 Studio.

Users are responsible for complying with the applicable model license, including its non-commercial restrictions.

## 4. SheetSage2

**SheetSage2**  
Developer: Multimodal Art Projection and contributors  
Source: https://huggingface.co/m-a-p/SheetSage2  
License: CC BY-NC 4.0 for the released model materials as specified by the upstream repository.

SheetSage2 is used by YuE2 Studio for music transcription and symbolic music extraction.

License:

https://creativecommons.org/licenses/by-nc/4.0/

## 5. MERT2 / MERT-v2-FullSong

**MERT-v2-FullSong**  
Developer: Multimodal Art Projection and contributors  
Source: https://huggingface.co/m-a-p/MERT-v2-FullSong  
Model-weight license: CC BY-NC 4.0

MERT2 is used as an audio representation / encoder component in the transcription workflow.

License:

https://creativecommons.org/licenses/by-nc/4.0/

## 6. Oobleck / stable-audio-tools

Portions of the VAE inference implementation used by upstream YuE2 are derived from stable-audio-tools.

**stable-audio-tools / Oobleck**  
Copyright © 2023 Stability AI  
License: MIT

The original license text should be retained with the distributed application or source package.

## 7. SnakeBeta / BigVGAN

Portions of the upstream VAE implementation use or derive from the SnakeBeta implementation associated with BigVGAN.

**SnakeBeta / BigVGAN**  
Copyright © 2022 NVIDIA CORPORATION  
License: MIT

The original license text should be retained with the distributed application or source package.

## 8. uv

YuE2 Studio may distribute or invoke `uv` as part of its local Python environment installation workflow.

Source:

https://github.com/astral-sh/uv

License: Apache License 2.0 and/or MIT License, as specified by the applicable upstream release.

The corresponding upstream license texts should be retained when redistributing the executable.

## 9. Other Python and Runtime Dependencies

YuE2 Studio installs or uses additional Python packages, frameworks, codecs, runtime libraries, and other dependencies.

Each dependency remains subject to its own upstream license.

Where license texts are required for redistribution, copies should be included in the application's bundled license directory.

## Model Downloads

YuE2 Studio may download model weights during first-run installation or repair rather than embedding all model weights directly in the application package.

Downloading a model through YuE2 Studio does not change that model's license.

Users should review and comply with the current upstream terms before use.

## No Endorsement

Names of upstream projects and contributors are used solely to identify the origin of incorporated or interoperable components.

YuE2 Studio is an independent community project and is not sponsored by, affiliated with, or endorsed by the upstream authors unless expressly stated otherwise.