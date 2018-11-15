# DadaSlicer1.0
Giving your samples a second life.

## Why DadaSlicer?

I am a big believer in randomness and happy accidents. Being inspired by almost century long tradition of Dada movement and earlier Surrealist tradition - Surrealist automatism -  whereby as a method of art-making artist would suppresses conscious control over the making process, allowing the unconscious mind to have great sway. In our case it is not the mind wondering, but the roll of automated dices which govern the process. 

## Installation

Us the devtools package to install the app:
```r
# install.packages("devtools")
devtools::install_github("myownelixir/DadaSlicer1.0")
```

## Features
* Filters out samples that are below 10 sec
* Extracts and normalises 1 sec samples from randomly 10 time points
* Saves new samples to the output folder creating automatically new Sample Pack
* Can save samples into smaller Sample Packs by randomly distributing 15 1 sec files into newly created subfolder based on output value folder via ```
dada_folders(output) ```

## Setup
Make sure you have installed dependencies:
```r
install.packages("tuneR")
install.packages("seewave")
install.packages("dplyr")
```
Point to the path where you keep the sample that you want to process:

```r
input <- "C:/some_folder/audiofiles/"
```
Make sure that the samples are Wave files, they are 44.1K, stereo and 16 bit. If your samples are in different format use GoldWave batch conversion function to convert them into desired format. 

Define output folder like below. If the output folder does not exist it will be created. 

```r
output <- "C:/some_folder/my_outout_folder"
```
## Usage

Core function is the ``` dada_slicer()``` which takes as arguments ```(input, output)``` values like so:
```r 
dada_slicer(input, output)
```
Once the the process is completed we can check the output folder to see if new samples were created:
```r 
>list.files(output)
[1] "sample_1.wav" "sample_2.wav" "sample_3.wav" sample_4.wav"
```
An additional function is an ``` dada_folders()``` which as an argument takes  earlier defined ```(output)``` folder. It takes the newly generated files randomly selects 15 and puts this new selection into a new subfolder. The process is repeated until all the files are redistributed. WARNING (!) Be careful when using this function as when the process is finished it deletes all the original files from the ```(output)``` folder.
The output of this function are new folders in the ```(output)``` folder containing your 1 sec samples.

## Application of the package

When I was creating it, the main use case I was thinking about was to help me to go quickly through 100s or 1000s of samples, session recordings, foley recordings etc, and rather then manually select the most interesting bits I would leave it to chance, and let the faith decide and pick 10 1 sec audio clips from each of my samples. I use it to generate a my personal sample packs and reuse newly generated samples in music production, sound design, TidalCycles projects etc.  
I have noticed that always there will be some very interesting clips among those samples that otherwise I might have missed. 

* Go through 1000s of audio files and instantly generate interesting sample packs
* Reuse your old samples and chope them in new fashion to breath new live into your older work
* Use it to chop your long foley recording sessions into nicely digestible audio clips
* Get inspired, start recording random sounds from various inputs and turn them into sound packs. I routinely use my iPhone, my synth sessions, my portable recorder sounds to generate something new and inspiring.
