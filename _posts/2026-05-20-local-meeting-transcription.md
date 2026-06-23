---
lang: en
title: "Building a free mymeet alternative on my laptop"
date: 2026-05-20
description: "Meeting transcription with speaker diarization, fully local on a MacBook M1 Pro: Whisper + MLX + pyannote, $0, nothing leaves the device. What worked and where the limits are."
alt: /posts/zamena-mymeet-na-noutbuke/
---

Transcription services made my work life much easier: there are a lot of meetings, details slip, and transcribing a call and writing a memo in time helps keep focus. I really like mymeet — out of the box it covers almost any audio scenario, fast. But I decided to skip the subscription and tinker with Claude Code myself.

## The setup

- Hardware — a regular MacBook M1 Pro, 16 GB, no GPU server.
- Test recording — a 63-minute meeting, Russian speech, 4 participants.
- The recordings are sensitive — sending them to the cloud isn't always OK.
- Needed: audio → text + speaker separation.

## What I did

- Dropped the task into Claude chat — it proposed a prompt to move into Code.
- Went step by step: speech recognition with the Whisper model, speaker separation with pyannote. Both open and free.
- Hit a problem: recognition ran 2.3× slower than real time — for 63 minutes, ~145 minutes just for the text. The cause: on Mac the library was computing on the CPU while the GPU sat idle.
- Switched recognition to the Mac GPU (Apple's **MLX** framework), used the fast **large-v3-turbo** model, added silence trimming, and ran recognition and diarization **in parallel**. Left speaker separation on the CPU.

## The result

A working tool that turns a recording into `.srt` / `.txt` / `.json` with speakers. An hour of audio processes in about an hour (stages run in parallel). Cost — **$0**: open models (a one-time ~1.7 GB download), everything local. Built in **3 hours** of active back-and-forth with Claude plus background waits (model downloads, slow first runs).

## The downsides

- It's not "upload and it's ready in a minute" like mymeet. Speaker separation on a laptop runs roughly at real time: an hour of audio = ~an hour of waiting.
- It's an engine, not a product. The output is text with speakers — no polished summaries, action items, or calendar/CRM integrations like mymeet has. Summaries can be bolted on via an LLM, but that's again either the cloud (goodbye, privacy) or more work.
- If you have lots of meetings to transcribe regularly, run the system overnight (when there's a free 8 hours) so it finishes in the background.

Judging by this case, product life cycles can shrink several times over: what used to be a subscription now gets built in a couple of evenings.
