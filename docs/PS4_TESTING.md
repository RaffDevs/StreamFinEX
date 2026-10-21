# PS4 smoke test

Run this checklist on a jailbroken PS4 after each new PKG build. Record the console model, firmware and
jailbreak/GoldHEN version with any failure.

## Install and first boot

- Install the generated PKG and confirm it appears as **StreamFinEX** with the StreamFinEX icon/background.
- Confirm it can coexist with the original Switchfin package (StreamFinEX uses Title ID `SFEX00001`).
- Launch it twice: first with no saved data, then again after configuration has been persisted.
- Confirm the native PS4 keyboard opens and accepts a complete HTTPS addon URL.
- Alternatively upload `/data/streamfin-addon.txt`, relaunch, and confirm the URL is imported.

## Browse and network

- Load Home, Search, Anime and Library screens and verify posters render.
- Open several movie and series details, including a multi-season show.
- Confirm a failed or offline addon request shows an error instead of hanging indefinitely.
- Test once on Wi-Fi and once on Ethernet when both are available.

## Playback

- Play a known H.264/AAC stream at 720p and 1080p for at least ten minutes each.
- Verify pause/resume, shoulder-button seek, Share stream info and Options settings.
- Switch embedded audio and subtitle tracks when available.
- Load one external subtitle from the configured subtitle addon.
- Exit playback and confirm the app returns to the stream picker with resume progress saved.
- Treat HEVC, AV1, PGS and complex ASS subtitles as separate compatibility tests; PS4 decoding is currently
  software-based.

## Lifecycle and recovery

- Put the console into rest mode during browsing and during paused playback, then resume.
- Disconnect and reconnect the controller.
- Exit to the PS4 home screen and relaunch the app.
- If the app crashes, keep the matching `StreamFin.oelf` artifact. The crash handler writes an `addr2line`
  command to the kernel log that can be resolved against that exact binary.
