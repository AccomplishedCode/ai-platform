MUSIC GENERATING AI

This is a music generation model. It's trained on classical music files which were in the MIDI format,but it can be trained on any kind
of music. 

It extracts notes and chords with the help of the music21 library, and then the notes are then fed into multiple layers of LSTM cells.

It's well known that RNN's are really good at modelling sequences. In that sense, music can be thought of as sequences of notes and chords.
Notes  become data objects containing octave, offset and pitch information, while chords become data container objects containing information
for the combination of notes played at one time.

The data used for training is stored in the input_data folder, which contains 93 MIDI files. The music21 library loads the MIDI files into an array,
which is then partitioned by instruments and then separated to better represent different features.

To start training, just run "python training.py" from the terminal after navigating to the directory. You can choose to use your own music files.
After the training is finished (I found 200 epochs to be the ideal setting), run "python predict.py" to generate new music!

The generated music will be stored in a new folder on your local disk. 

My generated music is in the folder 'generated_music'.

Please tinker around with the code if you like, and feel free to tell me how the music turned out!
