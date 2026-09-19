# Third-Party Notices

YuE2 Studio incorporates, adapts, downloads, invokes, or interoperates with software and model components developed by third parties.

These components retain their respective upstream licenses.

Nothing in YuE2 Studio's license replaces, overrides, or relicenses those third-party terms.

---

## 1. YuE Studio

**Project:** YuE Studio  
**Author / maintainer:** tonywestonuk  
**Source:** https://github.com/tonywestonuk/YuE-Studio  
**License:** Apache License 2.0

YuE2 Studio is based in part on, derived from, or adapted from YuE Studio.

YuE2 Studio contains substantial modifications and additional application-level functionality.

Where files derived from YuE Studio have been modified, those modifications should be identified in the source distribution as required by Apache License 2.0.

YuE Studio and its maintainer are not affiliated with and do not endorse YuE2 Studio.

---

## 2. YuE / YuE2 Source Code

**Project:** YuE / YuE2  
**Developer:** Multimodal Art Projection and contributors  
**Source:** https://github.com/multimodal-art-projection/YuE  
**First-party source-code license:** Apache License 2.0

YuE2 Studio uses and/or adapts YuE2 inference functionality for local Apple Silicon operation.

The Apache License applying to YuE2 first-party source code does not apply to YuE2 model checkpoint weights.

---

## 3. YuE2 Model Weights

The following YuE2 model checkpoint weights are separately licensed under Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0), together with additional permissions published by the YuE2 licensors:

- YuE2-3B
- YuE2-Vae
- YuE2-Vae-legacy, where applicable

Sources:

https://huggingface.co/m-a-p/YuE2-3B

https://huggingface.co/m-a-p/YuE2-Vae

Current upstream model license:

https://github.com/multimodal-art-projection/YuE/blob/main/MODEL_LICENSE

The model weights are not relicensed by YuE2 Studio.

### Additional Individual-Creator Permission

The upstream YuE2 model license includes an additional permission dated 2026-09-16.

Under the current upstream terms, personal users, content creators, and musicians acting in an individual capacity are granted permission to use the YuE2 model weights to generate outputs and to publish, distribute, sell, license, or otherwise monetize those outputs, subject to the responsible-use conditions stated by the YuE2 licensors.

For those qualifying individual creative activities, the YuE2 licensors waive the CC BY-NC NonCommercial restriction to the extent stated in the upstream additional permission.

The current upstream terms also state that:

- qualifying individual creators do not need a separate commercial license from the YuE2 model licensors merely to monetize YuE2-generated outputs;
- generated outputs are not subject to the model weights' NonCommercial restriction solely because they were generated with YuE2;
- the permission does not authorize commercial redistribution or sale of the model weights;
- the permission does not authorize commercial use of the model weights by companies;
- responsible use is a condition of the additional permission;
- the permission does not grant rights in third-party material present in inputs or outputs.

The full current upstream model license controls.

YuE2 Studio does not expand, narrow, or reinterpret that permission.

---

## 4. SheetSage2

**Project / model:** SheetSage2  
**Developer:** Multimodal Art Projection and contributors  
**Source:** https://huggingface.co/m-a-p/SheetSage2  
**Upstream license designation:** CC BY-NC 4.0

YuE2 Studio uses SheetSage2 as part of its music-transcription and symbolic-music extraction workflow.

SheetSage2 remains subject to its own upstream license.

The additional individual-creator permission published for YuE2 model weights should not be assumed to apply to SheetSage2.

Users considering commercial use involving SheetSage2 should consult the current upstream repository and license.

---

## 5. MERT-v2-FullSong

**Project / model:** MERT-v2-FullSong  
**Developer:** Multimodal Art Projection and contributors  
**Source:** https://huggingface.co/m-a-p/MERT-v2-FullSong  
**Model-weight license:** CC BY-NC 4.0

MERT-v2-FullSong is used as an audio representation / encoder component in the transcription workflow.

MERT model weights retain their upstream license.

The additional individual-creator permission published for YuE2 model weights should not be assumed to apply to MERT model weights.

Users considering commercial use involving MERT should consult the current upstream repository and license.

---

## 6. Oobleck / stable-audio-tools

Portions of the VAE implementation used by upstream YuE2 / YuE Studio are derived from stable-audio-tools.

**Project:** stable-audio-tools / Oobleck  
**Copyright:** Copyright (c) 2023 Stability AI  
**License:** MIT

The corresponding MIT license text should remain included with distributed source or application packages where the applicable code is present.

Recommended bundled filename:

```text
licenses/stable-audio-tools-MIT.txt
```

---

## 7. SnakeBeta / BigVGAN

Portions of the upstream VAE implementation use or derive from the SnakeBeta implementation associated with BigVGAN.

**Project:** SnakeBeta / BigVGAN  
**Copyright:** Copyright (c) 2022 NVIDIA CORPORATION  
**License:** MIT

The corresponding MIT license text should remain included with distributed source or application packages where the applicable code is present.

Recommended bundled filename:

```text
licenses/SnakeBeta-NVIDIA-MIT.txt
```

---

## 8. uv

YuE2 Studio may distribute or invoke `uv` as part of its local Python environment installation workflow.

**Project:** uv  
**Source:** https://github.com/astral-sh/uv

`uv` remains subject to the licenses applicable to the upstream release being distributed or invoked.

Where required for redistribution, the corresponding upstream license texts should be retained with the application package.

---

## 9. MLX

YuE2 Studio uses or interoperates with Apple's MLX ecosystem for Apple Silicon inference.

Source:

https://github.com/ml-explore/mlx

MLX and related packages remain subject to their respective upstream licenses.

---

## 10. PyTorch and Python Dependencies

YuE2 Studio installs or uses additional Python packages, frameworks, codecs, runtime libraries, and dependencies.

These dependencies remain subject to their own upstream licenses.

Where an upstream license requires a license or attribution notice to accompany redistribution, that notice should be retained in the distributed application or source package.

---

# Model Downloads

YuE2 Studio may download model weights during first-run installation or repair instead of embedding all model weights directly in the application package.

Downloading a model through YuE2 Studio does not change that model's license.

Model licenses are determined by the applicable upstream rights holders.

Users should review the current upstream terms for their intended use.

---

# Commercial-Use Note

Different components have different licensing terms.

In particular:

- YuE2 first-party source code is Apache-2.0;
- YuE2 model weights are CC BY-NC 4.0 together with the additional permissions published in the YuE2 MODEL_LICENSE;
- the current YuE2 additional permission allows qualifying individual creators to monetize YuE2-generated outputs under its stated conditions;
- SheetSage2 and MERT model weights remain separately licensed and are not automatically covered by YuE2's additional individual-creator permission;
- third-party software components retain their respective licenses.

YuE2 Studio does not provide additional rights to third-party code, models, input material, or output material.

---

# User-Supplied Material

YuE2 Studio does not grant copyright, neighboring rights, publicity rights, trademark rights, contractual rights, or other rights in material supplied by users.

Users are responsible for obtaining any permissions required for the audio, lyrics, compositions, voices, samples, recordings, melodies, or other material they process.

---

# No Endorsement

Names of upstream projects and contributors are used solely to identify the origin of incorporated, adapted, downloaded, or interoperable components.

YuE2 Studio is an independent community project.

It is not sponsored by, affiliated with, officially released by, or endorsed by the upstream authors unless expressly stated otherwise.

---

# License Precedence

This document is provided for attribution and informational purposes.

It does not replace the full upstream license texts.

If this summary conflicts with an applicable upstream license, the applicable license text controls.
