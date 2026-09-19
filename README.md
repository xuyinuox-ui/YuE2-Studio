# YuE2 Studio for macOS

**A local AI music workstation for Apple Silicon Macs.**
<img width="1586" height="992" alt="Intro" src="https://github.com/user-attachments/assets/c20f279e-029f-4d56-960a-b8ab85ba2133" />


YuE2 Studio brings YuE2 music generation, audio-to-ABC transcription, reference-melody workflows, model management, installation, repair, task control, playback, history, and cleanup into a single macOS application.

It is designed for people who want to use YuE2 locally on a Mac without manually building and maintaining a Python / ML environment.

> Current source package: **1.2.5**  
> Platform: **Apple Silicon macOS**  
> Recommended system: **macOS 14+ / 16 GB RAM or more**  
> For longer songs: **24 GB RAM or more recommended**

---

## Overview

YuE2 Studio provides a complete local workflow around YuE2 rather than only exposing the original command-line inference interface.

Core features include:

- **YuE2 music generation**
  - YuE2-3B
  - YuE2-Vae
  - MLX as the default Apple Silicon inference path
  - PyTorch MPS compatibility path
  - Neural Engine support for applicable workloads

- **Audio to ABC transcription**
  - SheetSage2
  - MERT-v2-FullSong
  - Vocal melody extraction
  - Instrumental main melody extraction
  - Melody and chord extraction
  - Tempo, key, and structural analysis

- **Reference melody workflow**
  - Import an existing audio file
  - Transcribe it to ABC
  - Review or edit the ABC
  - Use the resulting symbolic information during YuE2 generation

- **Integrated environment installation**
  - Independent local Python environment
  - Dependency installation
  - Model installation
  - Automatic path configuration

- **Resumable model downloads**
  - Mirror probing
  - Segmented downloads
  - Resume support
  - Existing completed shards are preserved

- **Model self-check and repair**
  - Final model files are checked directly
  - Important weights are verified separately
  - Missing components can be repaired without downloading everything again

- **Task management**
  - Stop transcription
  - Stop generation
  - Cancel queued work
  - Release associated runtime resources

- **Local-first workflow**
  - Local project history
  - Local logs
  - Local playback
  - No account required
  - No advertising
  - No analytics
  - No application telemetry

- **Clean uninstall**
  - Remove the application runtime
  - Remove local models
  - Remove cache and logs
  - Preserve generated music unless the user deletes it separately

---

## Why YuE2 Studio?

Running modern music-generation models locally on macOS usually involves more than downloading a model.

A working setup may require:

- Python version management
- virtual environments
- MLX / PyTorch dependencies
- model checkpoint downloads
- VAE setup
- Hugging Face cache management
- Apple Silicon backend configuration
- local paths
- model integrity checks
- transcription dependencies
- recovery after interrupted downloads
- process cleanup
- memory cleanup

YuE2 Studio packages these steps into one macOS workflow.

The goal is simple:

**install the app, install the models, and make music.**

---

## System Requirements

| Item | Requirement |
| --- | --- |
| Processor | Apple Silicon: M1 or newer |
| Intel Mac | Not supported |
| macOS | macOS 14.0 or later |
| Memory | 16 GB recommended |
| Longer songs | 24 GB or more recommended |
| Free storage | At least 15 GB recommended for initial installation |
| Network | Required for first installation and repair |
| Offline use | Core generation and transcription can run locally after installation |

Actual memory use and generation speed depend on model configuration, song length, quality settings, inference backend, and other applications using unified memory.

---

## Installation

### 1. Install the application

Place:

```text
YuE2 Studio.app
```

in:

```text
/Applications
```

and launch the application.

On first launch, YuE2 Studio checks the local runtime and determines which components still need to be installed.

### 2. Install the runtime and models

Click **Install** when prompted.

YuE2 Studio will prepare an independent local runtime and download the required dependencies and model files.

Keep the Mac connected to power and maintain a stable network connection during the first installation.

Large downloads are resumable.

If installation is interrupted, successfully downloaded data is preserved and reused when installation continues.

### 3. Wait for the runtime to become ready

The application verifies the required model files before declaring installation complete.

When installation reports completion and the worker becomes ready, generation and transcription are available.

---

## macOS Gatekeeper

Current community builds may be distributed without Apple Developer ID notarization.

Depending on your macOS security settings, Gatekeeper may display a warning when opening the application for the first time.

Only run software obtained from a source you trust.

If macOS blocks the first launch, use the normal macOS **Open** workflow from Finder or the Privacy & Security settings rather than disabling system-wide security protections.

Future builds may adopt Developer ID signing and Apple notarization.

---

## Local Data Locations

YuE2 Studio dynamically uses the home directory of the currently logged-in macOS user.

Runtime data is stored under:

```text
~/Library/Application Support/YuE2Studio/
```

Generated works are stored by default under:

```text
~/Music/YuE2Studio/
```

The application does not rely on paths from the development machine.

When copied to another supported Mac, runtime paths are generated for that Mac's current user.

---

# Using YuE2 Studio

## Audio to ABC

YuE2 Studio can analyze an audio file and convert musical information into ABC notation.

### Workflow

1. Drag an audio file into the **Source** area or choose a file manually.
2. Select the desired transcription mode.
3. Click **Transcribe to ABC**.
4. Wait for SheetSage2 / MERT processing to complete.
5. Review the resulting ABC.
6. Copy or edit the ABC if required.
7. Use the ABC as a reference for subsequent generation.

Available workflows include:

- **Lead Vocal + Instrumental Main Melody**
- **Lead Vocal Melody Only**
- **Melody + Chords**

During transcription, YuE2 Studio displays elapsed processing time.

After completion, the interface can also report processing speed relative to the duration of the source audio.

### Stopping transcription

Press **Stop** to interrupt transcription.

The transcription worker is terminated and associated MPS resources are released.

---

## Music Generation

To generate music:

1. Enter a style prompt.
2. Enter lyrics where applicable.
3. Configure Planning.
4. Select generation quality.
5. Select the number of songs.
6. Set the maximum length.
7. Set a random seed if reproducibility is desired.
8. Add or edit ABC when using a reference melody workflow.
9. Click **Generate**.

YuE2 Studio queues generation jobs and displays their current status.

Generation can be stopped without restarting the entire application.

---

## Inference Backends

### MLX

**MLX is the default backend on Apple Silicon.**

It is the recommended starting point for normal YuE2 Studio use on supported Macs.

### PyTorch MPS

PyTorch MPS is available as a compatibility path.

It can be useful when a workflow or dependency behaves differently under MLX.

### Neural Engine

Neural Engine acceleration is available for supported configurations and workloads.

Not every generation mode or song length is necessarily best suited to the Neural Engine path.

---

## Draft and Full Quality

Higher-quality generation requires substantially more computation than draft generation.

A first generation may also take longer because models must be loaded into memory.

For experimentation:

- start with shorter durations,
- use draft or lower-cost settings,
- refine prompts and ABC,
- then move to higher-quality generation.

This can significantly reduce iteration time.

---

# Download and Repair System

YuE2 Studio includes a dedicated installer rather than relying on a manually prepared development environment.

## Mirror selection

The installer can probe available package and model sources and select usable download paths based on availability and measured performance.

External mirrors are independent services.

Their availability and performance cannot be guaranteed.

When a mirror is unavailable, YuE2 Studio may use another available source or fall back to the corresponding upstream source.

---

## Resumable downloads

Large model downloads are divided into resumable segments.

Interrupted temporary data is retained when useful.

A partially downloaded shard is not treated as a complete model.

---

## Model verification

YuE2 Studio verifies important model components individually.

For example, YuE2-3B and YuE2-Vae are checked separately.

Installation is not considered complete merely because a model directory exists.

The installer checks the expected final files and validates expected file sizes where applicable.

This prevents incomplete or interrupted downloads from being mistaken for usable models.

---

## Partial repair

If the main YuE2 model is complete but the VAE is missing, YuE2 Studio can repair the missing VAE without downloading the complete main model again.

The same principle is used where possible for other runtime components.

---

## Local model resolution

Installed models are passed to the inference engine using local paths.

The generation workflow is therefore not dependent on resolving the model revision online every time a generation starts.

---

# Privacy

YuE2 Studio is designed as a local application.

### Local processing

The following are processed locally during normal use:

- imported audio,
- lyrics,
- ABC notation,
- transcription,
- YuE2 inference,
- generated audio,
- project history,
- application logs.

The application interface communicates with its local worker through the loopback interface:

```text
127.0.0.1
```

### No account

YuE2 Studio does not require a YuE2 Studio user account.

### No advertising

No advertising system is integrated.

### No analytics

No usage analytics system is integrated.

### No application telemetry

The runtime disables Hugging Face telemetry where configured by the application.

### Network access

Network access is required during installation and repair to obtain items such as:

- Python/runtime components,
- Python packages,
- model weights,
- dependency files,
- mirror metadata or availability checks.

External download providers can necessarily observe network requests made to their services, including normal network information such as the connecting IP address.

---

# Clean Uninstall

Use:

```text
Clean Uninstall…
```

from the YuE2 Studio application menu.

The cleanup workflow can remove:

- YuE2 Studio application runtime data,
- the local Python environment,
- downloaded models,
- caches,
- imported temporary files,
- application logs.

Generated works stored in the music output directory are intentionally preserved.

This reduces the risk of accidentally deleting completed music when uninstalling the runtime.

---

# Troubleshooting

## Installation says the model is incomplete

This usually means the self-check found that one or more required final files are missing or incomplete.

Continue or restart installation.

Existing valid download data will be reused where possible.

---

## `model.safetensors` is missing

The corresponding model weights have not completed installation or final assembly.

Run the installation / repair process again.

YuE2 Studio should preserve already completed model components rather than redownloading everything.

---

## The first generation is slower

The first generation also includes model loading and runtime initialization.

Later generations may start faster while the relevant model state remains loaded.

---

## Memory pressure is high

YuE2 is a large local music model.

If macOS begins using heavy swap or other applications become unresponsive:

- close memory-intensive applications,
- reduce generation length,
- reduce simultaneous work,
- use a lighter generation configuration,
- restart the worker if necessary.

Macs with more unified memory generally provide more headroom for long generations.

---

## Copy and paste

YuE2 Studio provides the normal macOS editing shortcuts, including:

```text
⌘C   Copy
⌘V   Paste
⌘X   Cut
⌘A   Select All
⌘Z   Undo
⇧⌘Z  Redo
```

---

## Stopping a task

Both transcription and generation support interruption.

Use **Stop** instead of force-quitting the entire application whenever possible.

---

# Source Code

The repository includes the full source package for YuE2 Studio.

Current package:

```text
YuE2StudioMac-1.2.5-FullSourceCode.zip
```

The source is provided for inspection, learning, modification, reproducibility, and continued community development subject to the licenses applicable to the respective code and model components.

---

# Upstream Projects and Attribution

YuE2 Studio exists because of the work of multiple open-source and research projects.

## YuE Studio

Parts of YuE2 Studio are **based on, derived from, or adapted from YuE Studio by tonywestonuk**.

Upstream project:

```text
GitHub: tonywestonuk/YuE-Studio
```

YuE Studio is distributed under the **Apache License 2.0**.

YuE2 Studio contains modifications and additional application-level work, including areas such as:

- the macOS application workflow,
- installation and repair behavior,
- download and verification handling,
- model-path management,
- transcription integration,
- task controls,
- local data handling,
- user-interface behavior,
- packaging and distribution changes.

YuE Studio and its maintainer are not affiliated with, and do not endorse, YuE2 Studio.

The YuE Studio name is used only to identify the origin of upstream-derived work.

---

## YuE2

YuE2 Studio uses and adapts components from the YuE2 project by Multimodal Art Projection and contributors.

Upstream project:

```text
GitHub: multimodal-art-projection/YuE
```

YuE2 first-party source code is distributed under the applicable upstream open-source license.

YuE2 model checkpoint weights are licensed separately from the source code.

---

## YuE2-3B and YuE2-Vae

Model repositories include:

```text
Hugging Face: m-a-p/YuE2-3B
Hugging Face: m-a-p/YuE2-Vae
```

The YuE2-3B, YuE2-Vae, and YuE2-Vae-legacy checkpoint weights are licensed under:

**Creative Commons Attribution-NonCommercial 4.0 International  
(CC BY-NC 4.0)**

The model weights are not relicensed by YuE2 Studio.

---

## SheetSage2

YuE2 Studio uses SheetSage2 as part of the audio transcription workflow.

Model repository:

```text
Hugging Face: m-a-p/SheetSage2
```

Applicable released model weights are subject to the upstream licensing terms, including **CC BY-NC 4.0** where specified by the upstream repository.

---

## MERT-v2-FullSong

YuE2 Studio uses MERT-v2-FullSong as an audio representation / encoder component in the transcription workflow.

Model repository:

```text
Hugging Face: m-a-p/MERT-v2-FullSong
```

The released model weights are licensed under:

**CC BY-NC 4.0**

---

## Oobleck / stable-audio-tools

Parts of the upstream VAE implementation contain code derived from the Oobleck implementation in stable-audio-tools.

The applicable upstream code is distributed under the MIT License.

Relevant copyright and license notices must be retained.

---

## SnakeBeta / BigVGAN

Parts of the upstream VAE implementation use or derive from SnakeBeta / BigVGAN code.

The applicable upstream implementation is distributed under the MIT License.

Relevant NVIDIA copyright and license notices must be retained.

---

## uv

YuE2 Studio may use `uv` as part of local Python environment installation.

The applicable upstream release is distributed under its upstream Apache-2.0 / MIT licensing terms.

---

# Licensing

The repository should be distributed together with:

```text
LICENSE
NOTICE
THIRD_PARTY_NOTICES.md
```

and the applicable bundled third-party license texts.

Third-party software and model components retain their own licenses.

Nothing in YuE2 Studio relicenses third-party code or model weights beyond the permissions granted by their respective rights holders.

For the exact terms applicable to individual components, always refer to the license files distributed with this project and the corresponding upstream project.

---

# Important Model License Notice

Several model checkpoints used by YuE2 Studio are distributed under **CC BY-NC 4.0**.

This includes core weights used for YuE2 generation and transcription.

As a result, users planning commercial deployment should carefully review the applicable upstream model licenses and obtain any additional permissions that may be required.

Examples of potentially commercial contexts can include:

- selling access to a hosted generation service,
- embedding restricted model weights in a paid commercial product,
- redistributing restricted weights as part of a commercial package,
- other uses primarily directed toward commercial advantage or monetary compensation.

This README is provided for project information and does not constitute legal advice.

The applicability of a license to a particular use case may depend on the exact material used, method of distribution, jurisdiction, contractual arrangements, and other circumstances.

---

# Generated Music and User-Supplied Material

YuE2 Studio does not grant rights to source material supplied by the user.

Users are responsible for ensuring they have the necessary rights or permissions for material they process, including:

- sound recordings,
- songs,
- lyrics,
- compositions,
- melodies,
- performances,
- samples,
- reference tracks,
- voices or other protected material.

Transcription does not remove rights that exist in the original work.

Likewise, generation or transformation does not automatically resolve copyright, neighboring-rights, publicity-rights, contractual, platform, or other legal issues.

Public release of covers, adaptations, or substantially similar material may require additional permissions.

Users should review generated output before publication or distribution.

---

# No Warranty

YuE2 Studio, its upstream components, AI models, and related dependencies are provided subject to their respective licenses and warranty disclaimers.

AI-generated output can:

- contain errors,
- fail to follow prompts,
- produce unusable audio,
- resemble existing material,
- contain artifacts,
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

Community builds may currently use ad-hoc code signing and may not yet carry an Apple Developer ID notarization ticket.

This affects how macOS Gatekeeper presents the application; it does not change the licensing status of the source code or model weights.

A future distribution may add:

- Developer ID Application signing,
- Hardened Runtime,
- Apple notarization,
- stapled notarization tickets,
- signed release archives,
- published checksums.

---

# Development Notes

YuE2 Studio is developed and maintained as an independent community project.

Development has included substantial AI-assisted implementation and documentation work using **GPT-5.6 Sol**, under the direction and review of the project maintainer.

AI assistance does not replace or modify the licenses of upstream projects.

---

# Reporting Problems

When reporting an issue, please include:

- YuE2 Studio version,
- macOS version,
- Mac model,
- Apple chip model,
- unified memory capacity,
- selected inference backend,
- selected generation settings,
- whether the problem occurs during installation, transcription, or generation,
- relevant application logs.

For installation problems, include the complete log beginning from the earliest relevant:

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

The current source package includes work covering:

- local Apple Silicon execution,
- MLX generation path,
- MPS compatibility path,
- Neural Engine integration for applicable configurations,
- SheetSage2 / MERT audio transcription,
- audio-to-ABC workflow,
- reference ABC workflow,
- resumable downloads,
- model integrity checks,
- separate YuE2-3B / VAE verification,
- partial model repair,
- dynamic per-user paths,
- local model resolution,
- interruptible transcription,
- interruptible generation,
- persistent local history,
- playback,
- standard macOS editing shortcuts,
- native window dragging behavior,
- installation logs,
- clean uninstall,
- removal of development-machine-specific paths from distributed runtime configuration.

---

# Project Status

YuE2 Studio is usable as a local Apple Silicon music-generation and transcription workstation and is being actively refined.

The project currently focuses on:

1. making YuE2 practical to install on macOS,
2. improving Apple Silicon local inference,
3. integrating music transcription with generation,
4. making interrupted installations recoverable,
5. reducing manual environment configuration,
6. building a more complete local AI music workflow around open models.

Bug reports, reproducible compatibility findings, and constructive technical feedback are welcome.

---

# Acknowledgements

YuE2 Studio would not exist without the work of the upstream open-source and research communities.

Special acknowledgement goes to:

- **tonywestonuk** — YuE Studio
- **Multimodal Art Projection and contributors** — YuE / YuE2
- **SheetSage2 contributors**
- **MERT contributors**
- **Stability AI / stable-audio-tools contributors**
- **NVIDIA / BigVGAN contributors**
- **MLX contributors**
- **PyTorch contributors**
- the maintainers of the Python and macOS ecosystem components used by the application

YuE2 Studio is an independent project.

Upstream project names are used for identification and attribution only and do not imply sponsorship, affiliation, or endorsement.

---

## Legal Note

This README summarizes project behavior and licensing information for convenience.

It is not a substitute for the full license texts.

If any summary in this README conflicts with an applicable license, the applicable license text controls.
