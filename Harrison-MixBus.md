## Notes

* Analog workflow- fewer plug-ins, fixed busses
    * You can stack sounds in a single track, like layers in an image editor
    * Every region fades and cross-fades automatically
    * Fewer mouse modes, more keyboard shortcuts
    * CPU is pre-allocated, turning a processor on or off doesn't affect anything
* Session snapshot == version
* You can archive a session to do a compressed, lossless backup
* Can combine audio and video files

## Performance

* You can modify the buffer size in the audio settings
* You can how aggressively the playback or recording buffer is being consumed in the top status bar

## Selection

* Has a red border around it
* `esc` to clear

## Signal Routing

* All handled inside the software, no matrix mixer

## Mixer

* Audio busses are for things like external FX and headphones, not mixing
* Double-click control to reset it
* Adjust with mouse, fine with `ctrl`, super-fine with `shift+ctrl`
* `Ctrl+Shift Click`: Apply to all channels
* `Middle`: Non-latching mute/solo
* Top of each channel opens up I/O options
    * Also includes monitor (disk vs. input) options
* Meter is aligned to fader
* Bottom VU meters measure amount of tape saturation applied
* Top VU meter shows K/14 RMS value
* Phase alignment meter shows `Out of phase - In Phase - Mono`
* Gain staging:
    * Trim - Normalizes signal
    * Fader - Artistic choice
    * Makeup - From the compressor
* VCAs automate fader moves without bussing
* Bottom of channel strip has automation, group assignment, and metering
* "Spill" shows just channels that are on that bus
* Master channel has a hard limiter
* Redirects (plug-ins):
    * Any order, either before or after the fader
    * One green pip for mono, two for stereo, red for MIDI
* Busses just have "tone" EQs
* Channel hotkeys:
    * Arrows for faders
    * `r` to record arm
    * `s` to solo
    * `m` to mute
* Compressor:
    * Leveler- Low ratio, volume balancing or transient shaping
    * Compressor- Fixed attack/release, in-your-face
    * Limiter- Smash peaks
* Side-chaining
    * Uses a global side-chain channel
    * Small red arrow next to the output routing
    * Bus compressors can be set to listen to side-chain
* Groups can assign which attributes are shared
    * You can group channels by dragging on the black strip above the mixer
* Automation
    * Manual - No automation
    * Play - Play automation, no direct control
    * Write - Whatever current values are is written
    * Touch - Play, until you change something

## Editor

* You can show the channel for the current track with `E`
* `z` to zoom to selection, zooms out when nothing is selected
* `Ctrl+Wheel`: Zooms the timeline
* `Shift+Wheel`: Moves the timeline left/right
* `Shift+Right Click`: Deletes
* Navigate between tracks with `Alt+up/down`
* Uses playlists like Pro Tools
* Has editing modes like Pro Tools:
    * Slide - Normal
    * Ripple - Like Shuffle, closes the gap
    * Lock - Regions can be edited, but can be moved
* Editing tools:
    * Object - Normal
        * Smart - Object on top half, Range on bottom half
    * `r` Range - Selection
    * Time - Stretch
    * Speaker - Audition/Scrub
    * Pencil - Add automation and MIDI points, and write region automation
    * Contents - Edits automation and MIDI
* Editing commands - Hover over a region, and:
    * `s` to split
    * `j` to trim from beginning
    * `k` to trim from end
* Control automation in the `A` menu
* Create PT-style edit groups in the `G` menu
* You can audition and drag/drop clips S1-style from the Editor List
* Each track has a horizontal fader on its label also
* The range tool has a beat-detective tool called Rhythm Ferrett
* You can automatically align the polarity of channels with the range tool

## Transport

* Scrubbing tool right below controls
* `Shift+Left/Right` does this too

## Key Commands

* `Alt+M`: Toggles between editor and mixer
