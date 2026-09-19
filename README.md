# YuE2 Studio for macOS

**A local AI music workstation for Apple Silicon Macs.**

<img width="1586" height="992" alt="YuE2 Studio" src="https://github.com/user-attachments/assets/c20f279e-029f-4d56-960a-b8ab85ba2133" />

YuE2 Studio brings YuE2 music generation, audio-to-ABC transcription, reference-melody workflows, model management, installation, repair, task control, playback, history, and cleanup into a single macOS application.

It is designed for people who want to run YuE2 locally on a Mac without manually building and maintaining a Python / ML environment.

> Current source package: **1.2.5**  
> Platform: **Apple Silicon macOS**  
> Recommended system: **macOS 14+ / 16 GB unified memory or more**  
> For longer songs: **24 GB or more recommended**

---

## Features

### YuE2 Music Generation

- YuE2-3B
- YuE2-Vae
- MLX as the default Apple Silicon inference path
- PyTorch MPS compatibility path
- Neural Engine support for applicable configurations
- Style prompts
- Lyrics
- ABC reference input
- Planning controls
- Quality controls
- Duration controls
- Seed control
- Multiple-song generation
- Interruptible generation

### Audio to ABC

YuE2 Studio integrates SheetSage2 and MERT-v2-FullSong for local music analysis and transcription.

Available workflows include:

- Lead Vocal + Instrumental Main Melody
- Lead Vocal Melody Only
- Melody + Chords
- Tempo analysis
- Key analysis
- Structural analysis
- ABC extraction and editing

An existing song can be imported, analyzed, converted to ABC, reviewed or edited, and then used as a symbolic reference for YuE2 generation.

### Integrated Local Runtime

YuE2 Studio manages its own local environment, including:

- Python runtime
- Python dependencies
- YuE2 models
- transcription models
- local model paths
- Apple Silicon inference configuration

### Resumable Downloads

Large model downloads support:

- mirror probing,
- segmented downloads,
- resuming interrupted downloads,
- preservation of completed shards,
- fallback to upstream sources where applicable.

### Model Verification and Repair

YuE2 Studio checks important model files individually instead of considering a directory complete merely because it exists.

YuE2-3B and YuE2-Vae are verified separately.

If one component is missing, the installer can repair the missing component without unnecessarily downloading complete models again.

### Task Control

Both transcription and generation can be interrupted.

The application attempts to terminate associated workers and release runtime resources when work is stopped.

### Local-First Workflow

YuE2 Studio includes:

- local project history,
- local logs,
- local playback,
- local inference,
- no YuE2 Studio account requirement,
- no advertising,
- no application analytics,
- no application telemetry.

### Clean Uninstall

The application can remove:

- its local runtime,
- downloaded models,
- cache,
- logs,
- temporary imports.

Generated music is preserved unless the user chooses to remove it separately.

---

## Why YuE2 Studio?

Running a modern music-generation model locally on macOS involves more than downloading a checkpoint.

A working setup may require:

- Python version management,
- virtual environments,
- MLX or PyTorch dependencies,
- model downloads,
- VAE configuration,
- Hugging Face cache management,
- Apple Silicon backend configuration,
- local paths,
- model integrity checks,
- transcription dependencies,
- interrupted-download recovery,
- process cleanup,
- memory cleanup.

YuE2 Studio integrates these steps into one macOS workflow.

The goal is simple:

**Install the app, install the models, and make music.**

---

# System Requirements

| Item | Requirement |
| --- | --- |
| Processor | Apple Silicon, M1 or newer |
| Intel Mac | Not supported |
| macOS | macOS 14.0 or later |
| Memory | 16 GB recommended |
| Longer songs | 24 GB or more recommended |
| Storage | At least 15 GB of free space recommended for initial installation |
| Network | Required for initial installation and repair |
| Offline use | Core generation and transcription can run locally after installation |

Actual memory use and generation speed depend on model configuration, song length, quality settings, inference backend, and other applications using unified memory.

---

# Installation

## 1. Install the application

Place:

```text
YuE2 Studio.app
```

in:

```text
/Applications
```

and launch it.

On first launch, YuE2 Studio checks the local runtime and determines which components still need to be installed.

## 2. Install the runtime and models

Click **Install** when prompted.

YuE2 Studio prepares an independent local runtime and downloads the required dependencies and models.

Keep the Mac connected to power and maintain a stable network connection during the first installation.

Large downloads are resumable.

If installation is interrupted, successfully downloaded data is preserved and reused when installation continues.

## 3. Wait for the worker to become ready

The application verifies required model files before declaring installation complete.

When installation completes and the local worker reports ready, generation and transcription become available.

---

# macOS Gatekeeper

Community builds may currently be distributed without Apple Developer ID notarization.

Depending on macOS security settings, Gatekeeper may display a warning when opening the application for the first time.

Only run software obtained from a source you trust.

If macOS blocks the first launch, use the normal macOS **Open** workflow through Finder or **Privacy & Security** rather than disabling system-wide security protections.

Future builds may adopt Developer ID signing and Apple notarization.

---

# Local Data

YuE2 Studio dynamically uses the home directory of the current macOS user.

Runtime data is stored under:

```text
~/Library/Application Support/YuE2Studio/
```

Generated works are stored by default under:

```text
~/Music/YuE2Studio/
```

The distributed application does not depend on development-machine-specific user paths.

---

# Using YuE2 Studio

## Audio to ABC

1. Drag an audio file into the **Source** area or choose a file.
2. Select the desired transcription mode.
3. Click **Transcribe to ABC**.
4. Wait for SheetSage2 / MERT processing.
5. Review the resulting ABC.
6. Copy or edit the ABC as required.
7. Use the ABC as a symbolic reference for subsequent generation.

During transcription, YuE2 Studio displays elapsed processing time.

Press **Stop** to interrupt transcription.

---

## Music Generation

1. Enter a style prompt.
2. Enter lyrics where applicable.
3. Configure Planning.
4. Select generation quality.
5. Select the number of songs.
6. Set maximum length.
7. Set a random seed if reproducibility is desired.
8. Add or edit ABC when using a reference-melody workflow.
9. Click **Generate**.

Generation jobs are queued and their status is displayed in the application.

Generation can be stopped without restarting the entire application.

---

# Inference Backends

## MLX

**MLX is the default inference path for supported Apple Silicon Macs.**

It is the recommended starting point for normal YuE2 Studio use.

## PyTorch MPS

PyTorch MPS is available as a compatibility path.

## Neural Engine

Neural Engine acceleration is available for supported workloads and configurations.

Not every generation mode or song length is necessarily best suited to the Neural Engine path.

---

# Draft and Full Quality

Higher-quality generation requires substantially more computation than draft generation.

The first generation may also take longer because models must be loaded and initialized.

For experimentation:

- start with shorter durations,
- use draft or lower-cost settings,
- refine prompts and ABC,
- then move to higher-quality generation.

---

# Download and Repair

## Resumable Downloads

Large model downloads can be resumed after interruption.

Partial temporary data is not treated as a completed model.

## Model Verification

Important model components are checked individually.

YuE2-3B and YuE2-Vae are verified separately.

Installation is not considered complete merely because a model directory exists.

## Partial Repair

If the main model is complete but another required component is missing, YuE2 Studio can download or repair the missing component without downloading everything again where supported.

## Local Model Resolution

Installed models are passed to the inference engine through local paths.

Normal local generation therefore does not depend on resolving model revisions online for every generation.

---

# Privacy

YuE2 Studio is designed as a local application.

During normal operation, the following are processed locally:

- imported audio,
- lyrics,
- ABC notation,
- transcription,
- YuE2 inference,
- generated audio,
- history,
- logs.

The user interface communicates with its local worker through the loopback interface:

```text
127.0.0.1
```

YuE2 Studio itself does not require an account and does not integrate advertising or application analytics.

Network access is required during installation and repair to obtain components such as:

- Python/runtime files,
- Python packages,
- model weights,
- dependency files,
- mirror availability information.

External download providers necessarily receive ordinary network requests, including the connecting IP address.

---

# Clean Uninstall

Choose:

```text
Clean Uninstall…
```

from the YuE2 Studio application menu.

The cleanup workflow can remove:

- application runtime data,
- local Python environment,
- downloaded models,
- caches,
- imported temporary files,
- logs.

Generated works stored in the music output directory are intentionally preserved.

---

# Troubleshooting

## Installation reports an incomplete model

The self-check has determined that one or more required final files are missing or incomplete.

Run installation or repair again.

Existing valid download data will be reused where possible.

## `model.safetensors` is missing

The corresponding weights have not completed installation or final assembly.

Run installation / repair again.

## First generation is slower

The first generation includes model loading and runtime initialization.

Later generations may begin more quickly while relevant model state remains loaded.

## High memory pressure

YuE2 is a large local music model.

If macOS begins using heavy swap:

- close memory-intensive applications,
- reduce generation length,
- reduce simultaneous work,
- use a lighter generation configuration,
- restart the worker when appropriate.

## Standard editing shortcuts

YuE2 Studio supports normal macOS editing shortcuts:

```text
⌘C   Copy
⌘V   Paste
⌘X   Cut
⌘A   Select All
⌘Z   Undo
⇧⌘Z  Redo
```

---

# Source Code

The repository includes the full source package for YuE2 Studio.

Current package:

```text
YuE2StudioMac-1.2.5-FullSourceCode.zip
```

Source code is provided subject to the licenses applicable to YuE2 Studio and its incorporated third-party components.

---

# Licensing

## YuE2 Studio Source Code

Except for separately identified third-party components, YuE2 Studio source code and project modifications are distributed under the:

**Apache License, Version 2.0**

See:

```text
LICENSE
```

Parts of YuE2 Studio are based on, derived from, or adapted from **YuE Studio by tonywestonuk**, which is also distributed under Apache License 2.0.

Upstream:

https://github.com/tonywestonuk/YuE-Studio

YuE2 Studio contains substantial modifications and additional application-level work, including installation, repair, model management, transcription integration, task control, local-data handling, packaging, user-interface behavior, and Apple Silicon workflows.

YuE Studio and its maintainer are not affiliated with and do not endorse YuE2 Studio.

---

## YuE2 Source Code

YuE2 Studio uses and adapts components from the YuE2 project by Multimodal Art Projection and contributors.

Upstream:

https://github.com/multimodal-art-projection/YuE

YuE2 first-party source code is distributed under Apache License 2.0.

Model weights are licensed separately from source code.

---

# YuE2 Model Weights

YuE2-3B, YuE2-Vae and YuE2-Vae-legacy checkpoint weights are distributed under **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)** together with additional permissions published by the YuE2 licensors.

Sources:

https://huggingface.co/m-a-p/YuE2-3B

https://huggingface.co/m-a-p/YuE2-Vae

Current model license:

https://github.com/multimodal-art-projection/YuE/blob/main/MODEL_LICENSE

## Individual Creator Permission

As of the YuE2 model license update dated **2026-09-16**, the YuE2 licensors grant personal users, content creators, and musicians acting in an individual capacity additional permission to use the YuE2 model weights to generate outputs and to publish, distribute, sell, license, or otherwise monetize those outputs, subject to the responsible-use conditions in the upstream model license.

Under that additional permission, an individual creator does not need a separate commercial license from the YuE2 model licensors merely to monetize YuE2-generated outputs.

The upstream license also states that generated outputs are not subject to the YuE2 model weights' NonCommercial restriction solely because they were generated with YuE2.

This additional permission:

- concerns generation and use of outputs,
- does not authorize commercial redistribution or sale of the YuE2 model weights,
- does not authorize commercial use of the YuE2 weights by companies,
- is subject to the responsible-use conditions in the upstream license,
- does not grant rights in third-party material contained in inputs or outputs.

Companies wishing to use YuE2 model weights commercially should follow the commercial licensing instructions provided by the YuE2 project.

The current upstream model license controls if its terms change or differ from this summary.

---

# SheetSage2

YuE2 Studio uses SheetSage2 in its audio-transcription workflow.

Source:

https://huggingface.co/m-a-p/SheetSage2

The released repository/model materials are identified upstream under **CC BY-NC 4.0**.

The additional individual-creator permission published specifically for YuE2 model weights should not be assumed to apply to SheetSage2.

Users planning commercial use involving SheetSage2 should review the current SheetSage2 upstream license.

---

# MERT-v2-FullSong

YuE2 Studio uses MERT-v2-FullSong as an audio representation / encoder component in the transcription workflow.

Source:

https://huggingface.co/m-a-p/MERT-v2-FullSong

The released MERT model weights are distributed under **CC BY-NC 4.0**.

The additional individual-creator permission published specifically for YuE2 model weights should not be assumed to apply to MERT model weights.

Users planning commercial use involving MERT should review the current upstream license.

---

# Other Third-Party Components

YuE2 / YuE Studio upstream code also contains or derives from third-party implementations including:

- Oobleck / stable-audio-tools — MIT
- SnakeBeta / BigVGAN — MIT
- uv — Apache-2.0 / MIT, according to the applicable upstream release
- other Python and runtime dependencies under their respective licenses

See:

```text
THIRD_PARTY_NOTICES.md
```

and the bundled third-party license files for details.

---

# Important Commercial-Use Distinction

The licensing situation is not accurately summarized by saying either:

> "Everything is commercial"

or:

> "Everything is non-commercial."

Different components have different terms.

### YuE2 code

Apache License 2.0.

### YuE2 model weights

CC BY-NC 4.0 plus the YuE2 licensors' additional individual-creator permission.

That additional permission expressly permits qualifying individual creators to monetize YuE2-generated outputs under its stated conditions.

### SheetSage2 and MERT model weights

Their separately applicable upstream model licenses remain relevant.

Do not assume that YuE2's additional individual-creator permission automatically extends to these separately licensed model weights.

### YuE2 Studio application code

Except for separately identified third-party components, this project is distributed under Apache License 2.0.

Users planning company deployment, commercial model hosting, model-weight redistribution, paid inference services, or other commercial use involving restricted model weights should review the current upstream licenses and obtain additional permission where required.

This README is informational and does not constitute legal advice.

---

# User-Supplied Material and Generated Music

YuE2 Studio does not grant rights to material supplied by users.

Users are responsible for obtaining any necessary rights or permissions for:

- sound recordings,
- songs,
- lyrics,
- compositions,
- melodies,
- performances,
- samples,
- reference tracks,
- voices,
- other protected material.

Transcription does not remove rights that exist in the original work.

Generation or transformation does not automatically resolve copyright, neighboring-rights, publicity-rights, contractual, platform, or other legal issues.

Users should review outputs before publication or distribution.

---

# No Warranty

YuE2 Studio, upstream software, AI models, and related dependencies are provided subject to their respective licenses and warranty disclaimers.

AI-generated output can:

- contain errors,
- fail to follow prompts,
- contain audio artifacts,
- resemble existing material,
- require editing,
- be unsuitable for publication.

Users are responsible for reviewing outputs and deciding whether and how they should be used.

---

# Distribution and Signing

YuE2 Studio currently targets:

```text
arm64 / Apple Silicon
```

Intel Macs are not supported.

Community builds may use ad-hoc code signing and may not carry an Apple Developer ID notarization ticket.

This affects macOS Gatekeeper behavior but does not change the licenses applicable to source code or model weights.

Future releases may add:

- Developer ID Application signing,
- Hardened Runtime,
- Apple notarization,
- stapled notarization tickets,
- release checksums.

---

# Required License Files

Source and application distributions should retain the applicable license and attribution information.

Repository root:

```text
LICENSE
NOTICE
THIRD_PARTY_NOTICES.md
```

Relevant third-party license texts should also remain bundled where required.

Nothing in YuE2 Studio relicenses third-party code or model weights beyond permissions granted by their respective rights holders.

---

# Reporting Problems

When reporting an issue, please include:

- YuE2 Studio version,
- macOS version,
- Mac model,
- Apple chip,
- unified memory capacity,
- selected inference backend,
- generation settings,
- whether the problem occurred during installation, transcription, or generation,
- relevant logs.

For installation issues, include the log beginning from the earliest relevant:

```text
[installer]
```

entry where possible.

Contact:

```text
xuyinuox@163.com
```

---

# Current 1.2.5 Highlights

- Apple Silicon local execution
- MLX generation path
- MPS compatibility path
- Neural Engine integration for applicable configurations
- SheetSage2 / MERT audio transcription
- audio-to-ABC workflow
- reference ABC workflow
- resumable downloads
- model integrity checks
- separate YuE2-3B / VAE verification
- partial model repair
- dynamic per-user paths
- local model resolution
- interruptible transcription
- interruptible generation
- persistent local history
- playback
- macOS editing shortcuts
- installation logs
- clean uninstall
- removal of development-machine-specific paths from distributed runtime configuration

---

# Project Status

YuE2 Studio is a usable local Apple Silicon music-generation and transcription workstation and continues to be actively refined.

The project focuses on:

1. making YuE2 practical to install on macOS,
2. improving Apple Silicon local inference,
3. integrating music transcription with generation,
4. making interrupted installations recoverable,
5. reducing manual environment configuration,
6. building a complete local AI music workflow around open models.

Bug reports, reproducible compatibility findings, and constructive technical feedback are welcome.

---

# Acknowledgements

YuE2 Studio would not exist without the work of its upstream open-source and research communities.

Special acknowledgement goes to:

- **tonywestonuk** — YuE Studio
- **Multimodal Art Projection and contributors** — YuE / YuE2
- **SheetSage2 contributors**
- **MERT contributors**
- **Stability AI / stable-audio-tools contributors**
- **NVIDIA / BigVGAN contributors**
- **MLX contributors**
- **PyTorch contributors**
- maintainers of the Python and macOS ecosystem components used by the application

YuE2 Studio is an independent community project.

Upstream project names are used for identification and attribution only and do not imply sponsorship, affiliation, or endorsement.

---

## Legal Note

This README summarizes project behavior and licensing information for convenience.

It is not a substitute for the full applicable license texts.

If a summary in this README conflicts with an applicable license, the applicable license text controls.
