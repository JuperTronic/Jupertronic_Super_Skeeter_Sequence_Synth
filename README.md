# Jupertronic Super Skeeter Sequence Synth
Arduino synth with sequence triggering, drone glitch setting, rate, legato, phase, LP filter, sync out, MIDI in and out, and OLED display

The sound generation is based on the Mosquito Synth by AnalogSketchbook https://www.instructables.com/Arpeggiating-Synthesizer-Mosquito-I/

**Extensive changes and additions have been made.**
  - Extensively customized the sequences.
  - Adjusted the frequency shift between the 2 oscilators to a 5th to create a power chord.
  - Added a latching drone button with LED which is awesome for live jamming. You can adjust the sequence when in drone mode so that you come out on a different sequence.
  - Added MIDI in to adjust the root note of the sequence playing.
  - Added MIDI out.
  - Added toggle for MIDI out to send either the whole sequence or only the root note for layering a bass synth.
  - Changed Osc1 pot to control the root note of the MIDI out. Noon or 12 o'clock is same as Super Skeeter, clockwise goes higher up to 1 octave, counter clockwise goes lower down to -1 octave. Included a custom pot scale diagram. I suggest using 0s, 12s, or 7s for unison, octaves, or 5ths.
  - Added sync out for drum sequencer. It may be affected by the legato adjustment.
  - Root note changes via MIDI are stored when received and take effect on first note of sequence only, not in the middle, to prevent live jam timing accidents when you trigger a change.
  - Sequence changes are stored when buttons are pressed and take effect on the first note of a sequence only as explained above.
  - A second Arduino connected to the buttons runs an OLED display showing the sequence # selected so you can tell what the heck you're doing when you change sequences. 
  - Drone button LED flashes on last note of sequence. 
  - OLED screen has a blinking indicator for last note and first note of sequence for timing cues.
  - Super Skeeter outputs MIDI on channel 1.
  - Super Skeeter accepts MIDI in on all channels. Use any other channel except 1 for MIDI in for proper operation.

There may be better ways to implement this from scratch, but I have learned a ton from modifying the original Mosquito code to add the functionality that I wanted. You can play this alone or with lots of other stuff like a drum sequencer, external synths, MIDI controllers, etc. 

I'm not a coding expert or a Fritzing wiz. I've commented the code pretty heavily to explain what's going on. 

Install Jupertronic_Skeeter_Synth.ino on your first Arduino which is in charge of the sound. Use the MIDI in and MIDI out 5 pin DIN socket circuits described by NotesandVolts.com. I've included the schematics separately but not incorporated into my Fritzing. MIDI in runs into the RX pin. MIDI out runs from the TX pin. You need to install the MIDI.h library and the Mozzi library. Install a switching mechanism to disconnect the MIDI in. Otherwise you cannont update code on the board with it connected. I used a female jumper wire attached to the pin and a jumper on the MIDI socket so I can just unplug it because I didn't have any small switches at the time. A protoboard switch would be great for this. You can leave the MIDI out wiring attached when you upload code. _Be sure to switch your MIDI back on when you're done. I'm telling you, you will probably forget this._

Install Jupertronic_Skeeter_Display.ino on your second Arduino which will run the OLED display. You need to install the ss_oled.h library to run the OLED. 

**_Connect ground from both boards to a common spot._** Connect buttons to common ground and input pins for both boards by jumpering the input or connecting 2 signal leads to the buttons themselves. If you jumper you could put in diodes if you want to.

For a simpler version of this with a single Arduino, sound adjustments, drone glitch added, MIDI in (not out), sync out, and no display see Jupertronic_Simple_Skeeter_Synth. You can added the changes in the code so that the root note and sequence only change on the first note of sequence by referencing this code. 

Wish list - rate sync in that is Volca compatible.

Feel free to build your own Skeeter and to mod or share with reference to this project and Mosquito. Let me know if you make upgrades. 

Wishing wellness and wellbeing to all!

*-Janis*

Jupertronic aka Janis Wilson Hughes aka J Dub aka vitalWho aka EvolutionStoneware (youtube)
