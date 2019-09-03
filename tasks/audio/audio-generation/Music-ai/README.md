# MUSIC GENERATING AI

This is a music generation model. It's trained on classical music files which were in the MIDI format,but it can be trained on any kind
of music. I downloaded the dataset from [https://magenta.tensorflow.org/datasets/maestro] . I would suggest downloading the MIDI only file for this project. 

The MIDI files you want to train on go inside the 'input_music' folder. 

### HOW IT WORKS
The libraries required for this code to run are all listed in the requirements.txt file. The most exciting library for this project for me to use was the music21 library, the details of which you can find here: https://web.mit.edu/music21/

You can install the library by running :
```sh
$ pip install --upgrade music21
```

The code in 'training.py' extracts notes and chords from the MIDI files with the help of the music21 library, and then stores the notes in a pickle file, which is later loaded by the prepare_sequnces function in the same file. That function prepares the data to be input into the LSTM model. 

It's well known that RNN's are really good at modelling sequences. In that sense, music can be thought of as sequences of notes and chords.
Notes  become data objects containing octave, offset and pitch information, while chords become data container objects containing information
for the combination of notes played at one time.

To run this project, clone the project to your local machine, and then navigate to the Music-ai folder. 
To start training, just run "python training.py" from the terminal after navigating to the directory. Here, you can choose to use your own music files or the ones I linked above. 

### The Model Architecture

I used 4 distinctive types of layers in the model architecture:
* LSTM: A type of RNN layer.
* Dropout: A technique for regularization. This helps prevent the model from overfitting by randomly dropping some nodes.
* Dense: This is a fully connected layer where every input node is connected to every output node.
* Activation: This determines the activation function that's going to be used to produce the node's output.

The generative model architecture I designed has three LSTM layers, three Dropout layers, two Dense layers, and one Activation layer.
The loss used here is categorical_crossentropy, and the optimizer used is AdamOptimizer. In training, I decided on 200 epochs, each with 25 batches.
The training starts, and the plot.py file plots the performance for the model. 

![Performance_Img](https://github.com/AccomplishedCode/ai-platform/blob/master/tasks/audio/audio-generation/Music-ai/performance_plot.png)

### Generating new music!
After the training is finished, just run "python predict.py" to generate new music! The details of the kind of music you want to create are also in the file, so feel free to tinker arround with the values in the code to see what works!
The generated music will be stored in a new folder on your local disk. 
My generated music is in the folder 'generated_music'.

