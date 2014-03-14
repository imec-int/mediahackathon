mediahackathon
==============

Start project to connect to the stream of MIDI data that will be provided.

MIDI carries event messages that specify notation, pitch (~note) and velocity (~ attack of the note/volume), control signals for parameters such as volume, vibrato, audio panning, cues, and clock signals that set and synchronize tempo between multiple devices. <br/>
Most MIDI messages are three bytes long.

Some more information on MIDI can be found on http://www.mixxx.org/wiki/doku.php/midi_controller_mapping_file_format (search for <strong>MIDI Crash Course</strong>).

This project allows you to listen (via web sockets) to MIDI events. You can simply listen to `onNoteOn` and `onNoteOff`, and then you get the corresponding pitch, velocity and channel. (There are multiple channels so you can route different signals to different destinations). A mapping for the pitch number to real notes can be found in `api.js`.<br/>
You can also listen to all MIDI data through `onData`. Then you will also get program changes etc. (Different programs correspond to different instruments. There was an attempt to standardize these instruments/programs; General MIDI, mapping also in `api.js`, although it's probably not very useful for this hackathon).<br/>
There is also a function `parseData` provided that maps the raw MIDI data to a human-readable form; e.g. `channel: 1, type: 'Note on', note: 'F 4', velocity: 103` instead of `145 65 103`. (F 4 is an F in the fourth octave; a formula to calculate the actual frequency can be found in `index.js`).

In the example, the Web Audio API and its oscillators are used to play back the incoming notes. It's quite compatible to MIDI in the sense that you also have noteOn and noteOff functions. On iOS, playback won't work right away, since you first need a button press.

Happy coding!





