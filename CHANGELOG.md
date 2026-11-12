# Changelog

User-facing changes, newest first. Every `feat:` or `fix:` that a user would
notice adds a plain-language line under **Unreleased** in the same commit.
At release, rename **Unreleased** to the version and date and start a new
**Unreleased** section above it. The About box's Version tab shows the newest
section, so keep each section short.

- Fixed grid lines in the piano roll and track rows going missing as the playhead passes over them (#67).
## Unreleased
- Level 4 - Arrangement has a new Harmony category: parts a semitone apart, close intervals below C3, chords with no third and where the key moves, plus a Lead that keeps leaping an octave (#78).
- Right-click a drum row in the LOTRO Preview to change the LOTRO sound that MIDI drum plays; a * marks a changed map, and Update / Create map from part saves it.
- The built-in drum map is redone by sound on all 37 LOTRO drums, and the LOTRO Preview names each MIDI drum's LOTRO sound.
- A note with no note-off is now kept (given a maximum length or ended at the next note of its pitch) or skipped, as Preferences ▸ Import ▸ **Note with no note-off** says, and Level 1 reports it.
- Level 1 also checks channels, program changes and stray note-offs, and reports the song's key, key changes and each part's notes outside it (#77).
- CLI: `--unmatched-note` and `--unmatched-max-seconds` do the same; the CLI now keeps such notes by default.
- Preferences ▸ Import sets the off-grid check's grid, tolerance and share.
- Section suggestions are gone: add song sections by hand or from MIDI markers.
- **Game Preview** (`song-smith-game-preview`): plays an ABC file through your own LOTRO install's sounds, for a final check.
- ABC player: Playback ▸ Sound ▸ Game files plays the song through your LOTRO install's own sounds, as Game Preview does.
- ABC player Game files: a broken file no longer leaves the old song playing, choosing the SoundFont mid-load leaves playback alone, greyed Export and Tempo say why (#73), and "Ignore LOTRO errors" applies.
- Drumsmith: LOTRO Drums has By number / By type tabs; Save / Revert / Close at bottom right; Test LOTRO over the pads; selected drum in the accent colour.
- Removed the gap above Output device in Playback preferences (#72).
- The transport strip shows playhead time and song length at the right, e.g. `0:00 | 4:39` (#70).
- MIDI editor: **Edit ▸ Move to New Track** / **Copy to New Track** (also on right-click) put the selected notes on a new track below with the same instrument and channel (#71).
- Loudness Timeline fills in by itself in LOTRO mode: the song is silently played through the LOTRO bank and each part's loudness drawn, re-measured after edits (Preferences ▸ Playback ▸ **Measure the Loudness Timeline automatically** turns it off).
- **Volume Shaping** panel: a master band and one per instrument with fades and a smooth line of points, saved on the song and used in the ABC. A **master MIDI fade** on the Conductor row fades all tracks.
- The instrument card's **Volume** is now a horizontal slider with the percent drawn over it (drag, or double-click for 0) instead of a number box with arrows.
- Part cards show the title on its own line, so long instrument names fit.
- Index Seed ▸ **Reseed when instrument changes** re-picks a part's number when its instrument changes. Index Seed changes apply at once.
- **Parts panel:** drag a card (or right-click ▸ Move Left / Right) to reorder. The ABC still lists parts by X: index; Preferences ▸ ABC Output ▸ Write parts in card order changes that.
- **Song ▸ Arrangement…** opens the Arrangement panel: a lane per section with a density strip per part. Drag a part to another lane (Ctrl-drag copies); right-click for more; click the name to save or switch.
- **Song sections** show as a band under the MIDI source ruler (always) and the panel's top: drag an edge, double-click to rename, right-click to add, delete, Sections from Markers or clear. MIDI import names them from its markers.
- **Level 4** has eight more tips: a part transposed off the octave, an abrupt ending, an ending off the home key, all parts resting a bar, no beat-one Bass or Rhythm note, a part above the Lead, a part shadowing it in fifths or octaves, a Lead with no rest.
- **Song ▸ Diagnostics ▸ Level 4 - Arrangement** advises on register, bass, a buried Lead, doubled rhythms, crowded or empty sections, unplaced parts and a flat ending.
- Double-clicking a Level 2-4 row naming a part and bar opens its first track there.
- Drum rows are named in the gutter: General MIDI names in the MIDI editor, LOTRO pad names in the LOTRO Preview.
- The Render dialog no longer shows the ABC text.
- **Diagnostics** is now a dock panel (View ▸ Diagnostics list, or any Song ▸ Diagnostics run). It scores each level out of 100 with a Pass / Review / Error status per category; click a category, then a spot for the rows. **Run All Levels** runs all four.
- Right-click a diagnostics row to **Ignore** it (saved with the song, undoable, no longer scored or counted by Block Render on Errors); right-click empty space for Show Info / Ignored rows.
- Level 1 - MIDI also reports notes with no length or over 8 s, restruck notes, chords over six notes, flat velocity, tracks off the 1/16 grid or duplicated, and odd tempos.
- Fixed Arrangement bars drifting when a MIDI repeats a time-signature change.
- Fixed LOTRO mode playing slow and drifting on songs with tempo changes.
- Preferences ▸ Playback ▸ **Output device** picks the sound device. With logging on, a **playback log** records every Play, Stop, seek and device open; a device that cannot start playback says so.
- Preferences ▸ Diagnostics ▸ **Write a log file** saves a .log of every diagnostics run, import report and ABC render to the **Log Folder** (Preferences ▸ Folders). **Log detail** Terse writes the report and settings; Verbose adds each note decision.
- Diagnostics also report chord-keep thinning, dropped or shortened notes, notes over 8 s cut, the Q: tempo and drums with no map slot.
- `forge` gets `--log PATH` and `--log-detail terse|verbose`.
- New Preferences ▸ **ABC Behavior** page for the converter's optional decisions: the checkboxes and tie-break moved from ABC Output, plus choices (all defaulting to the old behavior) for overlaps, over-limit chords, velocity to ppp–fff, a first-note dynamic and the header's M: and Q:.
- Preferences ▸ Appearance ▸ **Contrast** slider (-100 to 100) pushes a theme's text and surfaces further apart or closer together, in Songsmith and the ABC player. Applies at once; double-click to reset to 0.
- Preferences ▸ Appearance has two text-size sliders: **Font size** (80–150 %) for buttons, menus, drop-downs and labels, and **Small text** (80–200 %) for small drawn text. Each applies at once; the piano roll and ruler are not scaled yet.
- ABC player: double-clicking an error in the status bar or the red strip under the text also shows a toast pointing at the exact place in the text, saying what is wrong.
- The ABC player now refuses a tune LOTRO's own reader would refuse (lengths, chords over 6 notes, range, over 10000 notes, restruck notes, bad headers and repeats) and says why, with line and column. Preferences ▸ **Ignore LOTRO errors (play anyway)** plays it regardless.
- Lyrics toast: an Aa button on each track head turns on lyrics for that track. While the song plays, each lyric appears as a toast under the MIDI editor's ruler. Works for any MIDI file with lyric events (and Karaoke `@K` files).
- Switching song versions closes an open Note Maps window (kit or grid) tied to a part, asking first if it has unsaved edits.
- Loudness Timeline fixes: no gaps at fast playback rates, deleting or adding a part keeps the other lines, a part's reading no longer mixes 100 ms blocks from different channels, and recording resumes 0.2 s (was 0.5 s) after a seek or loop wrap.
- The Loudness Timeline follows the latest 100 ms of sound, so a line drops about 100 ms after a note stops (was up to 400 ms), and breaks where a part falls below -50 dB instead of running along the bottom edge.
- Preferences ▸ Diagnostics ▸ Run Level 1 After an Import now covers ABC, Guitar Pro and MusicXML imports too.
- Render (ABC) also runs the Level 3 text checks on the finished ABC and stops, asks or goes ahead on their errors as it does for Level 1; Ignore Short Note Errors drops the too-short ones from both.
- Song ▸ Diagnostics ▸ Level 3 - ABC also reads the finished ABC and reports, as errors with the game's line and column, any note or rest of 60 ms or less or over 8 s, and any chord of more than 6 notes (its z-pulse counts as one).
- Each release puts the changelog on the public Song Smith page.
- Preferences ▸ ABC Output ▸ BODY FORMAT has "Make Instruments Unique": parts sharing an instrument get 1, 2, 3 added to its name in the title (Lute of Ages 1, Lute of Ages 2); a lone instrument keeps its plain name.
- Preferences ▸ ABC Output has BODY FORMAT (the five comment checkboxes) and BEHAVIOUR (mute/solo, stretch, collapse and tie options, the dynamic tie-break) headings.
- Song ▸ Default parts from tracks has shortcut F4.
- A MIDI track name that is not valid UTF-8 (for example GBK) is written into the ABC title with "?" for the bad bytes, so ABC Player no longer fails on the next line.
- Preferences ▸ ABC Output has "Stretch Short Notes and Rests When Building the ABC" (off by default): notes and rests under 60 ms are lengthened in the ABC so LOTRO loads it; no note start moves. Level 1 shows those rows as warnings.
- Preferences ▸ ABC Output has "Collapse Near-Simultaneous Starts When Building the ABC" (off by default): a note starting under 60 ms after the previous start is moved onto it and keeps its end, and a first note under 60 ms in moves to the start, so LOTRO loads the file.
- Stretch Short Notes and Rests now also closes the short rest left after a chord whose shortest note ended just before the next start while another still sounded, and ends a note at the next start of the same pitch, not a tick short.
- A note over 8 s (the most LOTRO loads) is now cut into pieces in the ABC, on an existing note start where possible. Preferences ▸ ABC Output ▸ "Tie Long Notes" (off, experimental) ties a piece to its continuation only when that is the very next note.
- Fixed "Too many notes in a chord": LOTRO counts the z-pulse of a held chord as a member, so a chord that needs one now holds at most 5 notes (the quietest of a sixth is left out).
- Fixed a long note cut into pieces making the ABC fall out of time: the pieces were listed out of order, so the part ran late. About a fifth of a 3545-file archive was affected; the notes are now kept in start order.
- Fixed a long note's last piece being cut just before another note's start (a rest or pulse under 60 ms) and a piece cut onto a six-note chord making seven: the cut keeps clear of other starts and the chord cap runs after the split.
- A note left out of a chord because LOTRO counts its z-pulse is now a warning in the render diagnostics, on its part and bar.
- Fixed "Rest's duration is too long": a silence that began less than 60 ms before a bar line was written as one rest however long it ran (47 s in one file). A rest or chord pulse is now cut at the next bar line and never runs over 8 s.
- Fixed ABC files LOTRO refused with "Rest's duration is too short": a bar line less than 60 ms into a note advance or rest cut it into a piece too short to load. Such an advance is now written whole, so the `% bar N` label may sit a few ticks late.
- Render has a "Selection only" checkbox: with a loop range set, a render in any format (also per track / part) covers just that range. ABC and MIDI keep the tempo and meter there; audio ends with a short fade-out.
- Render has a "Separate file per track" (MIDI source) / "per part" (ABC source) checkbox: tick the ones you want and each is written to its own file, `<name> - <track>.<ext>`, in any format. Quick Render (F6) repeats it within the session.
- ABC player: a Maestro part named "Basic Drum 1" (no `%%song-part`, no instrument in the title) now loads as Drums, not an unknown instrument playing as Lute of Ages. Any part name with Drum or Drums is Drums when no other instrument is named.
- Preferences has a new Diagnostics page: Run Level 1 - MIDI After a MIDI Import, Block Render on Errors, Ask Before Rendering with Errors and Ignore Short Note Errors. An ABC render runs Level 1 first and, with errors, stops, asks or goes ahead.
- Song ▸ Diagnostics ▸ Level 1 - MIDI now reports as errors notes, gaps between note starts and silences shorter than 60 ms, which the game refuses to load; nothing is changed, so quantize the file first.
- Level 1 - MIDI lists each too-short note, gap and rest on its own row with its bar and beat (up to 50 of each kind per track, then "+N more"). Double-click a row to open the MIDI editor on that track with the marker, view and selection on the notes involved.
- Guitar Pro import now reads the older `.gp3`, `.gp4` and `.gp5` files as well as `.gp`: File ▸ Import ▸ Guitar Pro… and dropping a file accept them, and the import dialog names the version it read.
- A master volume dial in the transport bar, left of the buttons: it sets the same level as the Mixer's Master fader (0–100, double-click returns to 100).
- MusicXML and Guitar Pro import: three or more alternate endings that each close the repeat play in order (A B A C A D), not repeating the second.
- MusicXML and Guitar Pro import: absurdly deep XML nesting is refused instead of crashing; a non-UTF-8 MusicXML file says so; a duplicate part id is refused; an unreadable MIDI program number is warned about.
- ABC import and the ABC player now name a part from its `%%part-name` line when it has one, and from the `T:` line otherwise.
- A song with a pickup or irregular measure (from a MusicXML import) now exports the meter covering most of the song as the ABC's single `M:` line, not the pickup's (`M:1/4`).
- The Event Grid's Data column can be edited (not notes, tempo or time signatures): double-click a value, type, Enter (Esc cancels). Each edit is one undo step.
- The Event Grid now reads text, tempo and time-signature events correctly (a 120 BPM tempo showed as 5.68).
- The floating MIDI editor reopens at the size and position you left it.
- View > Event Grid lists every MIDI event in the song (notes as Note On and Note Off) with the bar position, type, channel and data; filter by track or event type and click a heading to sort.
- Edit > Time Stretch… in the MIDI editor rescales a track's timing by a ratio or from one tempo to another (160 to 80 doubles lengths), for the selected notes or the whole track.
- About box now has Credits, EULA and Version tabs; Version shows this changelog.
- New copper anvil icon for song-smith and the ABC player, in the file, title bar and taskbar.
- Drag a section anywhere: sideways to move it in time, onto another track to move it there, Ctrl to copy, Esc to cancel. Preferences > Editing chooses merge or overwrite on landing. The Alt-drag merge is gone.
- MIDI versions: Song > MIDI Versions keeps named copies of the song's MIDI.
- Diagnostics levels 1 to 3 report on the MIDI, the LOTRO parts and the rendered ABC.
- Import MusicXML and Guitar Pro files; import ABC files.
- Standalone ABC player with a dynamics timeline you can edit.

## 0.2.0 - 2026-11-02
- The LOTRO editor: render to ABC, WAV, FLAC, Ogg, MP3 or MIDI, note maps, the Chordsmith, song versions, themes and LOTRO playback with level and loudness meters.

## 0.1.0 - 2026-10-19
- First release: the MIDI to LOTRO ABC converter and the Songsmith MIDI editor.
