
# serial MP3


MakeCode extension for Serial MP3 players with the YX5300 chip.

This package is adapted from the famous makerbitpackage. The MakerBit connects to the BBC micro:bit to provide easy connections to a wide variety of sensors, actuators and other components, for example a Serial MP3 player. https://1010technologies.com/
You can connect the makerbit to your Calliope mini with a free (in Germany) adapterboard you found here at the Makerbit-Calliope mini Project https://www.hackster.io/calliope-makerbit-team/makerbit-am-calliope-mini-4ce1e2

![mp3player](https://github.com/MKleinSB/pxt-serialmp3/raw/master/icon.png "serial mp3 player") 

## Serial MP3

This extension supports MP3 devices with the YX5300 chip, e.g. the Catalex Serial MP3 und the grove mp3-player V2.
If it does nor work, change RX- and TX-pin

The microSD card shall be formatted as FAT16 or FAT32. exFAT is not supported properly and shall be avoided.

To support all commands properly, the names of folders and files need to obey the following strict pattern:

- Directory names are two-digit numbers, e.g. `01`.
- Track names within the directories shall start with a three digit numbers such as `001.mp3` or `002.wav`

Up to 99 directories and 255 tracks per directory are supported.

```
├── 01/
│   ├── 001.mp3
│   ├── 002 second track.mp3
│   └── 003 third track.mp3
├── 02/
│   ├── 001.mp3
│   └── 002.mp3
│
…
```

The MP3 device reads files and folders in alphabetic order. It is required to create a sequence of folders like `01`, `02`, `03` and name the tracks within each folder starting at `001`. Make sure to avoid gaps in your number based naming scheme. This allows you to use folder and track names as parameters in the playback functions below.

If you experience playback problems, check for deviations to the naming convention and the file system format.

### serialmp3 connectSerialMp3

Connects to the Serial MP3 device. The first pin needs to be attached the MP3 device receiver pin (RX) and the second pin to the MP3 device transmitter pin (TX).
You have to cross Rx and Tx line. So Calliope RX has to connect to mp3player TX and Calliope TX has to connect to mp3player RX.

```sig
serialmp3.connectSerialMp3(DigitalPin.C16, DigitalPin.C17)
```

### serialmp3 playMp3TrackFromFolder

Plays a track from a folder.

```sig
serialmp3.playMp3TrackFromFolder(1, 1, Mp3Repeat.No)
```

### serialmp3 playMp3Folder

Plays all tracks in a folder.

```sig
serialmp3.playMp3Folder(1, Mp3Repeat.No)
```

### serialmp3 setMp3Volume

Sets the volume.

```sig
serialmp3.setMp3Volume(30)
```

### serialmp3 runMp3Command

Dispatches a command to the MP3 device.

```sig
serialmp3.runMp3Command(Mp3Command.PLAY_NEXT_TRACK)
```

### serialmp3 onMp3TrackStarted

Do something when a MP3 track is started.

```sig
serialmp3.onMp3TrackStarted(() => {})
```

### serialmp3 onMp3TrackCompleted

Do something when a MP3 track is completed.

```sig
serialmp3.onMp3TrackCompleted(() => {})
```

### serialmp3 mp3Folder

Returns the index of the selected MP3 folder.

```sig
serialmp3.mp3Folder()
```

### serialmp3 mp3Track

Returns the index of the last MP3 track event.

```sig
serialmp3.mp3Track()
```

### serialmp3 mp3Volume

Returns the MP3 volume.

```sig
serialmp3.mp3Volume()
```

## License

Licensed under the MIT License (MIT). See LICENSE file for more details.

## Supported targets

- for PXT/calliopemini
- for PXT/microbit
