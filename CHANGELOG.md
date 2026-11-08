# Changelog

User-facing changes, newest first. Every `feat:` or `fix:` that a user would
notice adds a plain-language line under **Unreleased** in the same commit.
At release, rename **Unreleased** to the version and date and start a new
**Unreleased** section above it. The About box's Version tab shows the newest
section, so keep each section short.

## Unreleased
- Loudness Timeline fixes: at fast playback rates the line no longer has gaps, deleting or adding a part keeps the other parts' lines, a part's reading no longer mixes 100 ms blocks from different channels, and recording resumes 0.2 s after a seek or loop wrap instead of 0.5 s.
- The Loudness Timeline now follows the latest 100 ms of sound, so a line drops about 100 ms after a note stops instead of trailing it for up to 400 ms, and it breaks where a part falls below the -50 dB scale instead of running along the bottom edge.
- Preferences ▸ Diagnostics ▸ Run Level 1 After an Import now covers ABC, Guitar Pro and MusicXML imports as well as MIDI.
- Render (ABC) now also runs the Level 3 text checks on the finished ABC and stops, asks or goes ahead on their errors exactly as it does for Level 1 (Preferences ▸ Diagnostics); Ignore Short Note Errors drops the too-short ones from both.
- The ABC player now warns, without stopping the tune, about any note or rest LOTRO would refuse (60 ms or less, over 8 s, or a chord of more than 6 notes), naming the line and column the game would report.
- Song ▸ Diagnostics ▸ Level 3 - ABC also reads the finished ABC and reports, as errors with the game's line and column, any note or rest of 60 ms or less, any over 8 s, and any chord of more than 6 notes (its z-pulse counts as one).
- Each release now also puts the changelog on the public Song Smith page as CHANGELOG.md.
- Preferences ▸ ABC Output ▸ BODY FORMAT has "Make Instruments Unique" (off by default): parts that share an instrument get 1, 2, 3 added to the instrument name wherever the title format has it (Lute of Ages 1, Lute of Ages 2), so a band can say which one to take. An instrument used once keeps its plain name; a format without the instrument name label is not changed.
- Preferences ▸ ABC Output has BODY FORMAT and BEHAVIOUR headings: the five comment checkboxes sit under the first, the mute/solo, stretch, collapse and tie options and the dynamic tie-break under the second.
- Song ▸ Default parts from tracks has the shortcut F4.
- A MIDI track name that is not valid UTF-8 (for example a GBK name) is written into the ABC title with "?" in place of the bad bytes, so ABC Player no longer fails on the line after it.
- Preferences ▸ ABC Output has "Stretch Short Notes and Rests When Building the ABC" (off by default): notes and rests under 60 ms are lengthened in the ABC so LOTRO loads it, and no note start is ever moved. With it on, Level 1 shows those rows as warnings and Render no longer stops for them. Starts closer than 60 ms still need fixing by hand.
- Preferences ▸ ABC Output has "Collapse Near-Simultaneous Starts When Building the ABC" (off by default): a note that starts less than 60 ms after the previous start (for example 4.9 ms late in a live-played chord) is moved onto that start and keeps its end, and a first note under 60 ms after the start of the song moves to the start, so LOTRO loads the file. It is the only option that moves a start. The same pitch struck again within 60 ms, which LOTRO cannot play, is merged into the earlier note (its start unchanged, running on to the later end) and reported as a warning. With it on, Level 1 shows the start-gap rows as warnings.
- Stretch Short Notes and Rests now also closes the short rest the ABC writer put after a chord when its shortest note ended just before the next start while another note was still sounding, and ends a note exactly at the next start of the same pitch instead of one tick short (which left a rest too short to load).
- A note longer than LOTRO will load (ABC Player: "Note's duration is too long"; measured: 8.0 s loads, 8.5 s does not, so the limit is 8 s) is now cut into pieces in the ABC, on an existing note start where possible and never within 60 ms of another start. Preferences ▸ ABC Output ▸ "Tie Long Notes" (off by default, experimental) ties a piece to its continuation only when that is the very next note written.
- Fixed "Too many notes in a chord": LOTRO counts the z-pulse of a held chord as a member, so a chord that needs one now holds at most 5 notes (the quietest of a sixth is left out, as the 6-note cap does).
- Fixed a long note cut into pieces making the ABC fall out of time: the pieces were listed out of order, so the writer wrote the chord they belonged to as one note after another and the rest of the part ran late. Affected about a fifth of a 3545-file MIDI archive; the notes are now kept in start order and the writer no longer depends on it.
- Fixed a long note's last piece being cut just before another note's start (a rest or pulse under 60 ms, "Rest's duration is too short"), and a piece cut onto a full six-note chord making a seven-note chord: the cut keeps clear of other starts and the chord cap runs again after the split.
- A note left out of a chord because LOTRO counts its z-pulse is now reported as a warning in the render diagnostics, on the part and bar it happened.
- Fixed "Rest's duration is too long": a silence that began less than 60 ms before a bar line was written as one rest however long it ran (47 s in one file). A rest or chord pulse is now cut at the following bar line instead, and never runs over 8 s even where a bar is longer than that.
- Fixed ABC files LOTRO refused with "Rest's duration is too short": when a bar line fell less than 60 ms into a note advance or rest, the ABC was cut there into a piece too short to load. Such an advance is now written whole, so the `% bar N` label may sit a few ticks late.
- Render has a "Selection only" checkbox: with a loop range set, a render in any format (ABC, MIDI Format 0 or 1, WAV, FLAC, Ogg, MP3, also per track / part) covers just that range, starting at its first beat. ABC and MIDI keep the tempo and meter in effect there and clip notes that cross the loop edges; audio ends with a short fade-out and still lets a note held across the start sound. Greyed out without a loop.
- Render has a "Separate file per track" (MIDI source) / "per part" (ABC source) checkbox: tick the tracks or parts you want and each is written to its own file, named `<name> - <track>.<ext>`, in any format (ABC, WAV, FLAC, Ogg, MP3, MIDI). Quick Render (F6) repeats it within the same session.
- ABC player: a Maestro part named "Basic Drum 1" (no `%%song-part`, no instrument name in the title) now loads as Drums instead of reporting an unknown instrument and playing as Lute of Ages. Any part name with the word Drum or Drums is treated as Drums when no other instrument is named.
- Preferences has a new Diagnostics page with four choices: Run Level 1 - MIDI After a MIDI Import (opens the report on every MIDI import), and, for diagnostic errors, Block Render on Errors, Ask Before Rendering with Errors (used when blocking is off) and Ignore Short Note Errors. Render now follows the three error choices: an ABC render runs the Level 1 - MIDI check first and, with errors, stops (and shows the report), asks, or goes ahead. Other formats are never held up.
- Song ▸ Diagnostics ▸ Level 1 - MIDI now reports as errors (red) notes, gaps between note starts and silences shorter than 60 ms. The game refuses to load an ABC with any of them ("Note's duration is too short"); nothing is changed, so quantize the file first.
- Level 1 - MIDI lists each too-short note, gap and rest on its own row, with its bar and beat (up to 50 of each kind per track, then a "+N more" row). Double-click a row to open the MIDI editor on that track with the marker, the view and the selection on the note or notes involved.
- Guitar Pro import now reads the older `.gp3`, `.gp4` and `.gp5` files as well as `.gp`: File ▸ Import ▸ Guitar Pro… and dropping a file accept them, and the import dialog names the version it read.
- A master volume dial in the transport bar, left of the buttons: it sets the same level as the Mixer's Master fader (0–100, double-click returns to 100).
- MusicXML and Guitar Pro import: three or more alternate endings that each close the repeat now play in order (A B A C A D) instead of repeating the second ending.
- MusicXML and Guitar Pro import: a file with absurdly deep XML nesting is refused with an error instead of crashing the program; a MusicXML file that isn't UTF-8 (for example ISO-8859-1) says so and how to fix it; a duplicate part id is refused; and an unreadable MIDI program number in the part list is now warned about.
- ABC import and the ABC player now name a part from its `%%part-name` line when it has one, and from the `T:` line otherwise.
- A song with a pickup or irregular measure (from a MusicXML import) now exports its real time signature as the ABC's single `M:` line, not the pickup's length (it was writing `M:1/4`). The `M:` is the meter that covers the most of the song.
- The Event Grid's Data column can be edited: double-click a controller, program change, pitch bend, pressure, text, key signature or channel prefix value, type the new value and press Enter (Esc cancels). Entries outside the allowed range are refused, and each edit is one undo step. Notes, tempo and time-signature rows stay read-only.
- The Event Grid now reads text, tempo and time-signature events correctly (a track name lost its first letter and a 120 BPM tempo showed as 5.68 BPM).
- The floating MIDI editor reopens at the size and position you left it, instead of too big and in the wrong place (a fix for screens at different scale factors).
- View > Event Grid lists every MIDI event in the song (notes as Note On and Note Off) with the bar position, type, channel and data; filter by track or event type and click a heading to sort.
- Edit > Time Stretch… in the MIDI editor rescales a track's timing, by a ratio or from one tempo to another (160 to 80 makes notes twice as long), for the selected notes or the whole track.
- About box now has Credits, EULA and Version tabs; Version shows this changelog.
- New copper anvil icon for song-smith and the ABC player, in the file, title bar and taskbar.
- Drag a section anywhere: sideways to move it in time, onto another track to move it there, Ctrl to copy, Esc to cancel. Preferences > Editing chooses merge or overwrite when it lands on notes. The Alt-drag merge is gone.
- MIDI versions: Song > MIDI Versions keeps named copies of the song's MIDI.
- Diagnostics levels 1 to 3 report on the MIDI, the LOTRO parts and the rendered ABC.
- Import MusicXML and Guitar Pro files; import ABC files.
- Standalone ABC player with a dynamics timeline you can edit.

## 0.2.0 - 2026-11-02
- The LOTRO editor: render to ABC, WAV, FLAC, Ogg, MP3 or MIDI, note maps, the Chordsmith, song versions, themes and LOTRO playback with level and loudness meters.

## 0.1.0 - 2026-10-19
- First release: the MIDI to LOTRO ABC converter and the Songsmith MIDI editor.
