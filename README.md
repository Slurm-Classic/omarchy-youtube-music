![YouTube Music popup](preview.png)

# Omarchy YouTube Music

A YouTube Music controller for the Omarchy Quickshell bar.

The plugin reads the browser's live MPRIS player. It shows the current track,
album art, artist, album, progress, and playback controls in a popup panel.

## Requirements

- Omarchy Quattro with Quickshell
- YouTube Music open in Brave, Google Chrome, Chromium, Firefox, or Zen
- A browser that exposes the current media tab through MPRIS

The plugin does not start a background service, use browser automation, or
store account data. It activates when MPRIS identifies a YouTube player,
reports a YouTube URL (`music.youtube.com`, `youtube.com`, `youtu.be`,
`youtube-nocookie.com`), or -- for Brave, Chrome, and Chromium, which publish
no page URL at all -- when such a browser player is playing. MPRIS cannot tell
which site a Chromium-family player is playing, so any playing media in those
browsers is shown; Firefox and Zen are scoped to YouTube URLs instead. A
non-empty `xesam:album` keeps a paused YouTube Music player selected.

## Install

```sh
omarchy plugin add https://github.com/levyvix/omarchy-youtube-music.git --enable
```

Place it in the bar if needed:

```sh
omarchy bar move levi.youtube-music --section left
```

## Controls

- Left click the music icon to open or close the panel.
- Middle click toggles play/pause.
- Right click plays the next track.
- `Space` toggles play/pause.
- `n` or Right arrow plays the next track.
- `p` or Left arrow plays the previous track.
- Drag the progress bar to seek.
- `Escape` closes the panel.

The panel keeps the last detected browser player while it remains connected
*and* still reports YouTube Music, so pausing a track does not make the panel
appear idle, while switching that tab to a regular video clears it. Long track
labels are truncated in the bar and remain available in the tooltip and panel.

## Validate locally

```sh
omarchy plugin validate .
qmllint -I "$OMARCHY_PATH/shell" Panel.qml
```

## Remove

```sh
omarchy plugin remove levi.youtube-music
```

## License

MIT. See [LICENSE](LICENSE).
