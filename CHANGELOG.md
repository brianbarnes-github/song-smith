# Changelog

User-facing changes, newest first. Every `feat:` or `fix:` that a user would
notice adds a plain-language line under **Unreleased** in the same commit.
At release, rename **Unreleased** to the version and date and start a new
**Unreleased** section above it. The About box's Version tab shows the newest
section, so keep each section short.

- Fixed grid lines in the piano roll and track rows going missing as the playhead passes over them (#67).
## Unreleased
- **Parts panel:** drag a part card left or right (or right-click ▸ Move Left / Move Right) to reorder. The ABC still lists parts by X: index; Preferences ▸ ABC Output ▸ Write parts in card order changes that.
- **Song ▸ Arrangement…** (or View ▸ Arrangement) opens the Arrangement panel: your parts as a band, a lane per section (Lead, Counter-melody, Harmony, Texture, Accent, Bass, Rhythm) with a density strip per part. Songsmith suggests the lanes from what each part plays and saves nothing until you edit. Drag a part to another lane (Ctrl-drag copies), right-click strips and lane labels to move parts or rename, add, remove and move sections, and click the arrangement name to save, switch, rename, delete or reset. It also lists tips and each part's register, velocity, notes per bar and estimated heard dB.
- **Song sections** (Intro, Verse, Chorus…) show as a band under the MIDI source ruler (always) and the panel's top: drag an edge, double-click to rename, right-click to add, delete, Suggest Song Sections, Sections from Markers or clear. A MIDI import names them from the file's markers (Preferences ▸ Import).
- **Song ▸ Diagnostics ▸ Level 4 - Arrangement** (also run by Run All Levels) advises on shared register, a bass sitting high or missing, a buried Lead, parts that double each other's rhythm, one section holding most of the 64 voices, empty sections, unplaced parts, a flat ending, and song sections that sound alike or never change. Shown as a fourth Diagnostics card and the panel's tips; right-click a tip to ignore it.
- Double-clicking a Level 2, 3 or 4 row naming a part and a bar (no track) opens the part's first track at that bar.
- Drum rows are named in the gutter: a channel-10 track in the MIDI editor shows General MIDI names; a mapped Drums part in the LOTRO Preview shows LOTRO pad names.
- The Render dialog no longer shows the ABC text after an ABC render; diagnostics and histogram remain.
- **Diagnostics** is now a dock panel (View ▸ Diagnostics list, or any Song ▸ Diagnostics run). The front page scores each level out of 100 (suggestions never lower the MIDI score) with error / warning / suggestion counts and a Pass / Review / Error status per category; click a category for its trouble spots by track and bar, then a spot for the rows. **Run All Levels** runs all four in order.
- Right-click a diagnostics row to **Ignore** it (saved with the song, undoable, no longer scored or counted by Block Render on Errors); right-click a page's empty area for Show Info / Ignored rows.
- Level 1 - MIDI also reports, as warnings and suggestions, notes with no length or over 8 s, a note restruck while it still sounds, notes starting together, chords over six notes, flat velocity, tracks off the 1/16 grid or duplicating another, and odd tempos.
- Fixed Suggest Song Sections doing nothing, and the Arrangement panel's bars drifting by one, on songs whose MIDI repeats a time-signature change at the same tick.
- Fixed LOTRO mode playing slow, and its playhead drifting, on songs with tempo changes.
- Preferences ▸ Playback ▸ **Output device** picks the sound device. With logging on, a **playback log** records every Play, Stop, seek and device open with the output level; a device that cannot start playback now says so.
- Preferences ▸ Diagnostics ▸ **Write a log file for each diagnostics run and ABC render** saves a .log of every Level 1/2/3 run, import report and ABC render to the new **Log Folder** (Preferences ▸ Folders; else a Logs folder beside the ABC folder or song). **Log detail** Terse writes the report and settings; Verbose adds a line for each decision on a note.
- Diagnostics also report chord-keep thinning, zero-length notes dropped, same-pitch notes shortened, notes over 8 s cut, the tempo chosen for Q:, and drum notes with no drum-map slot.
- `forge` gets `--log PATH` and `--log-detail terse|verbose`.
- New Preferences ▸ **ABC Behavior** page for the converter's optional decisions: the checkboxes and tie-break moved from ABC Output, plus choices (all defaulting to the old behavior) for same-pitch overlaps, over-limit chord notes, velocity to ppp–fff (ABC import too), a first-note dynamic, and which M: and Q: the header names.
- Preferences ▸ Appearance ▸ **Contrast** slider (-100 to 100) pushes a theme's text and surfaces further apart or closer together, in Songsmith and the ABC player. Applies at once; double-click to reset to 0.
- Preferences ▸ Appearance has two text-size sliders: **Font size** (80–150 %) for buttons, menus, drop-downs and labels, and **Small text** (80–200 %) for the small drawn text on track heads, the instrument card and chips. Each applies at once in Songsmith and the ABC player; the piano roll and ruler are not scaled yet.
- ABC player: double-clicking an error in the status bar or the red strip under the text also shows a toast with an arrow at the exact place in the text, saying what is wrong.
- The ABC player now refuses to play a tune that LOTRO's own ABC reader would refuse, and says why in the status line and at the place in the text, naming the line and column the game would report. It checks note and rest lengths (60 ms to 8 s), chords over 6 notes, notes outside C, to c', a part over 10000 notes, a note restruck at another volume, malformed `X:` / `K:` / `M:` / `Q:` / `L:` / `+:` lines, inline fields, odd repeats, decorations and stray characters. Preferences ▸ **Ignore LOTRO errors (play anyway)** plays such a tune regardless; the warning stays.
- Lyrics toast: an Aa button on each track head (right of the pitch bend button) turns on lyrics for that track. While the song plays, each MIDI lyric appears as a toast just ahead of the playhead in a strip under the MIDI editor's ruler. Works for any MIDI file with lyric events (and Karaoke `@K` files); greyed out with fewer than two.
- Switching song versions closes an open Note Maps window (kit or grid) tied to a part, asking first if it has unsaved edits.
- Loudness Timeline fixes: no gaps at fast playback rates, deleting or adding a part keeps the other lines, a part's reading no longer mixes 100 ms blocks from different channels, and recording resumes 0.2 s (was 0.5 s) after a seek or loop wrap.
- The Loudness Timeline follows the latest 100 ms of sound, so a line drops about 100 ms after a note stops (was up to 400 ms), and breaks where a part falls below -50 dB instead of running along the bottom edge.
- Preferences ▸ Diagnostics ▸ Run Level 1 After an Import now covers ABC, Guitar Pro and MusicXML imports too.
- Render (ABC) also runs the Level 3 text checks on the finished ABC and stops, asks or goes ahead on their errors as it does for Level 1; Ignore Short Note Errors drops the too-short ones from both.
- Song ▸ Diagnostics ▸ Level 3 - ABC also reads the finished ABC and reports, as errors with the game's line and column, any note or rest of 60 ms or less or over 8 s, and any chord of more than 6 notes (its z-pulse counts as one).
- Each release puts the changelog on the public Song Smith page.
- Preferences ▸ ABC Output ▸ BODY FORMAT has "Make Instruments Unique" (off by default): parts that share an instrument get 1, 2, 3 added to its name wherever the title format has it (Lute of Ages 1, Lute of Ages 2). An instrument used once keeps its plain name; a format without the instrument name label is unchanged.
- Preferences ▸ ABC Output has BODY FORMAT (the five comment checkboxes) and BEHAVIOUR (mute/solo, stretch, collapse and tie options, the dynamic tie-break) headings.
- Song ▸ Default parts from tracks has shortcut F4.
- A MIDI track name that is not valid UTF-8 (for example GBK) is written into the ABC title with "?" for the bad bytes, so ABC Player no longer fails on the next line.
- Preferences ▸ ABC Output has "Stretch Short Notes and Rests When Building the ABC" (off by default): notes and rests under 60 ms are lengthened in the ABC so LOTRO loads it; no note start is moved. Level 1 then shows those rows as warnings and Render no longer stops for them. Starts closer than 60 ms still need fixing by hand.
- Preferences ▸ ABC Output has "Collapse Near-Simultaneous Starts When Building the ABC" (off by default): a note that starts less than 60 ms after the previous start (for example 4.9 ms late in a live-played chord) is moved onto that start and keeps its end, and a first note under 60 ms after the song start moves to the start, so LOTRO loads the file. It is the only option that moves a start. The same pitch struck again within 60 ms is merged into the earlier note with a warning; Level 1 shows start-gap rows as warnings.
- Stretch Short Notes and Rests now also closes the short rest left after a chord whose shortest note ended just before the next start while another still sounded, and ends a note at the next start of the same pitch, not a tick short.
- A note over 8 s (the most LOTRO loads) is now cut into pieces in the ABC, on an existing note start where possible and never within 60 ms of another start. Preferences ▸ ABC Output ▸ "Tie Long Notes" (off by default, experimental) ties a piece to its continuation only when that is the very next note.
- Fixed "Too many notes in a chord": LOTRO counts the z-pulse of a held chord as a member, so a chord that needs one now holds at most 5 notes (the quietest of a sixth is left out).
- Fixed a long note cut into pieces making the ABC fall out of time: the pieces were listed out of order, so the part ran late. About a fifth of a 3545-file archive was affected; the notes are now kept in start order.
- Fixed a long note's last piece being cut just before another note's start (a rest or pulse under 60 ms) and a piece cut onto a six-note chord making seven: the cut keeps clear of other starts and the chord cap runs after the split.
- A note left out of a chord because LOTRO counts its z-pulse is now a warning in the render diagnostics, on its part and bar.
- Fixed "Rest's duration is too long": a silence that began less than 60 ms before a bar line was written as one rest however long it ran (47 s in one file). A rest or chord pulse is now cut at the next bar line and never runs over 8 s.
- Fixed ABC files LOTRO refused with "Rest's duration is too short": a bar line less than 60 ms into a note advance or rest cut it into a piece too short to load. Such an advance is now written whole, so the `% bar N` label may sit a few ticks late.
- Render has a "Selection only" checkbox: with a loop range set, a render in any format (ABC, MIDI Format 0 or 1, WAV, FLAC, Ogg, MP3, also per track / part) covers just that range, from its first beat. ABC and MIDI keep the tempo and meter in effect there and clip notes at the loop edges; audio ends with a short fade-out. Greyed out without a loop.
- Render has a "Separate file per track" (MIDI source) / "per part" (ABC source) checkbox: tick the ones you want and each is written to its own file, `<name> - <track>.<ext>`, in any format. Quick Render (F6) repeats it within the session.
- ABC player: a Maestro part named "Basic Drum 1" (no `%%song-part`, no instrument in the title) now loads as Drums, not an unknown instrument playing as Lute of Ages. Any part name with Drum or Drums is Drums when no other instrument is named.
- Preferences has a new Diagnostics page: Run Level 1 - MIDI After a MIDI Import (opens the report on every import), and, for diagnostic errors, Block Render on Errors, Ask Before Rendering with Errors (used when blocking is off) and Ignore Short Note Errors. An ABC render runs Level 1 - MIDI first and, with errors, stops, asks, or goes ahead. Other formats are never held up.
- Song ▸ Diagnostics ▸ Level 1 - MIDI now reports as errors notes, gaps between note starts and silences shorter than 60 ms, which the game refuses to load; nothing is changed, so quantize the file first.
- Level 1 - MIDI lists each too-short note, gap and rest on its own row with its bar and beat (up to 50 of each kind per track, then "+N more"). Double-click a row to open the MIDI editor on that track with the marker, view and selection on the notes involved.
- Guitar Pro import now reads the older `.gp3`, `.gp4` and `.gp5` files as well as `.gp`: File ▸ Import ▸ Guitar Pro… and dropping a file accept them, and the import dialog names the version it read.
- A master volume dial in the transport bar, left of the buttons: it sets the same level as the Mixer's Master fader (0–100, double-click returns to 100).
- MusicXML and Guitar Pro import: three or more alternate endings that each close the repeat play in order (A B A C A D), not repeating the second.
- MusicXML and Guitar Pro import: absurdly deep XML nesting is refused with an error instead of crashing; a MusicXML file that isn't UTF-8 (for example ISO-8859-1) says so and how to fix it; a duplicate part id is refused; an unreadable MIDI program number in the part list is warned about.
- ABC import and the ABC player now name a part from its `%%part-name` line when it has one, and from the `T:` line otherwise.
- A song with a pickup or irregular measure (from a MusicXML import) now exports its real time signature as the ABC's single `M:` line, not the pickup's (it wrote `M:1/4`): the meter covering most of the song.
- The Event Grid's Data column can be edited: double-click a controller, program change, pitch bend, pressure, text, key signature or channel prefix value, type the new value and press Enter (Esc cancels). Out-of-range entries are refused; each edit is one undo step. Notes, tempo and time-signature rows stay read-only.
- The Event Grid now reads text, tempo and time-signature events correctly (a track name lost its first letter and a 120 BPM tempo showed as 5.68 BPM).
- The floating MIDI editor reopens at the size and position you left it, not too big and misplaced (screens at different scale factors).
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
