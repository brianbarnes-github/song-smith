# Changelog

User-facing changes, newest first. Every `feat:` or `fix:` that a user would
notice adds a plain-language line under **Unreleased** in the same commit.
At release, rename **Unreleased** to the version and date and start a new
**Unreleased** section above it. The About box's Version tab shows the newest
section, so keep each section short. The full line-by-line history up to
2026-11-12 is in `CHANGELOG-old.md`.

## Unreleased

New programs
- ABC player (`song-smith-abc-player`): plays one ABC file through the LOTRO sounds, with a dynamics timeline you can edit, looping, export, and the same load checks as the game (it says what is wrong and where; Preferences can play it anyway).
- Game Preview (`song-smith-game-preview`): plays an ABC file through your own LOTRO install's sounds. The ABC player can do the same from Playback ▸ Sound ▸ Game files.

Import
- Import ABC, MusicXML and Guitar Pro (`.gp`, `.gp3`, `.gp4`, `.gp5`) files, with repeats and alternate endings played out.
- A MIDI note with no note-off is kept or skipped as Preferences ▸ Import says; song sections are named from the MIDI's markers.

Diagnostics
- Diagnostics is a dock panel with four levels (MIDI, LOTRO, ABC, Arrangement), each scored out of 100. Double-click a row to jump to the note; right-click to ignore it.
- Level 1 finds what the game will refuse or play badly (notes, gaps and rests under 60 ms, notes over 8 s, big chords, stray events) and reports the song's key.
- Level 3 reads the finished ABC and reports errors with the game's line and column.
- Level 4 gives arrangement advice: register, bass, a buried Lead, crowded or empty sections, endings, harmony clashes, notes that do not suit an instrument, a sudden start and a peak that comes too early.
- Preferences ▸ Diagnostics: run Level 1 after an import, block or ask before a render with errors, and write a log file.

ABC output
- Fixed several causes of LOTRO refusing or mistiming an ABC: notes over 8 s are cut into pieces, held chords stay within the game's limit, and rests are never too short or too long.
- Optional Stretch Short Notes and Rests and Collapse Near-Simultaneous Starts make a file with sub-60 ms durations load.
- New Preferences ▸ ABC Behavior page for the converter's optional decisions; Make Instruments Unique numbers parts sharing an instrument; parts can be written in card order.
- Render: Selection only (the loop range), a separate file per track or part, and no ABC text in the dialog.

Arranging and mixing
- Song ▸ Arrangement: a lane per song section with a density strip per part, and saved named arrangements. Song sections show as a band under the ruler.
- Volume Shaping panel: fades and a smooth volume line for the whole song and each part, used in the ABC; a master MIDI fade on the Conductor row.
- Song ▸ MIDI Versions keeps named copies of the song's MIDI.
- The Loudness Timeline fills in by itself in LOTRO mode and follows the sound more closely.
- Drag part cards to reorder them; Volume on the instrument card is a slider; Index Seed can reseed when an instrument changes.

Drums
- The built-in drum map is redone by sound across all 37 LOTRO drums, and drum rows are named in the MIDI editor and the LOTRO Preview.
- Right-click a drum row in the LOTRO Preview to change its LOTRO sound; Update / Create map from part saves the result.
- Drumsmith: By number / By type tabs and a tidier layout.

Editing
- Drag a section anywhere: sideways in time, onto another track, Ctrl to copy. The Alt-drag merge is gone.
- MIDI editor: Time Stretch, Move / Copy to New Track, and a lyrics toast for tracks with lyric events.
- View ▸ Event Grid lists every MIDI event; its Data column can be edited.

Playback and appearance
- Preferences ▸ Playback picks the output device; a master volume dial and a playhead time / song length readout sit in the transport bar.
- Preferences ▸ Appearance: Contrast, Font size and Small text sliders.
- The About box has Credits, EULA and Version tabs, and there is a new copper anvil icon.

Fixes
- LOTRO mode no longer plays slow or drifts on songs with tempo changes.
- Arrangement bars no longer drift when a MIDI repeats a time-signature change.
- Grid lines no longer go missing as the playhead passes over them (#67).
- A MIDI track name that is not valid UTF-8 no longer breaks the ABC title.
- The floating MIDI editor reopens at the size and position you left it.

Command line
- `forge` gets `--log`, `--log-detail`, `--unmatched-note` and `--unmatched-max-seconds`, and now keeps notes with no note-off by default.

## 0.2.0 - 2026-11-02
- The LOTRO editor: render to ABC, WAV, FLAC, Ogg, MP3 or MIDI, note maps, the Chordsmith, song versions, themes and LOTRO playback with level and loudness meters.

## 0.1.0 - 2026-10-19
- First release: the MIDI to LOTRO ABC converter and the Songsmith MIDI editor.
