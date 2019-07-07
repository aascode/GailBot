# Gailbot 0.3.0

GAILBOT will (G)enerate (A)n (I)nitiaL (B)allpark (O)rthographic (T)ranscript

## About Gailbot

Gailbot is named after [Gail Jefferson](https://en.wikipedia.org/wiki/Gail_Jefferson), inventor of the transcription system used for [Conversation Analysis](https://en.wikipedia.org/wiki/Conversation_analysis). It can generate a first pass at a transcript that can then be improved manually.

Gailbot was developed at the [Tufts Human Interaction Lab](https://sites.tufts.edu/hilab/people/) in collaboration with [Dr. Saul Albert](https://www.lboro.ac.uk/subjects/communication-media/staff/saul-albert/) at Loughborough university, UK.

## How Gailbot works

Gailbot either takes in a recorded dialogue or records a new dialogue and uses an internal Speech to Text API to generate a transcript in the [CHAT transcription format](https://talkbank.org/manuals/CHAT.html). It then applies multiple post-processing modules to detect conversation speech rate, analyze laughter, and transcribe conversation features (pauses, gaps, overlaps etc.)

## Status
Gailbot has been tested on MAC OSX.
The current version is an alpha version. Feel free to provide feedback at: hilab-dev@elist.tufts.edu

Gailbot 0.3.0 includes major updates to the original Gailbot version and is intended to be used as a standalone tool.


## Before using gailbot

In order to use Gailbot, you should have some familiarity with using the terminal to install and run software.
You should also be aware that Gailbot uses [IBM Watson's STT API](https://cloud.ibm.com/apidocs/speech-to-text) that includes transcription charges.

## Installation

1. Install [python 3.7](https://www.python.org/downloads/release/python-373/)

2. Install the [homebrew](https://brew.sh/) using the command:
* mkdir homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew

3. Run 'brew install python3' to ensure that the pip3 package installer is installed.

4. Download and install the CLAN editor and CAfont from TalkBank:
* https://talkbank.org/software/

5. Navigate to the Gailbot directory and use the 'requirements.txt' file to install all required libraries:
* pip3 install -r requirements.txt

6. Create an account with IBM so you can use Watson's speech-to-text service:
* You can sign up for a trial account [here](console.bluemix.net/catalog/services/speech-to-text)
* **Note**: Your IBM Bluemix username and password is required to establish a connection with Watson's Speech to Text service. Once you have registered you can find your credentials here: https://console.us-east.bluemix.net/developer/watson/existing-services
* For transcription pricing details see https://www.ibm.com/cloud/watson-speech-to-text/pricing

## Usage 

Use the following command to run Gailbot:

* python3 gailbot-3.py -username [Bluemix Username] -password [Bluemix Password]
* Follow Gailbot's prompts to generate a transcript.

When adding files to be transcribed:
* -pair [file-1] [file-2] --> Allows a pair of files corresponding to the same conversation to be added.
* -dir [Directory Name] --> Allows transcription of all files in a directory as separate files. Results are inside the given directory.
* Individual files can be added without any additional flag.

## Compatible media file types

Gailbot currently supports a wide variety of audio and video file formats:

* Video file formats: mxf, mp4, mov, wmv, flv, avi, swf, m4v

* Audio file formats: alaw, basic, flac, g729, pcm, mp3, mpeg, ulaw, opus, wav, webm

## Gailbot menus

Gailbot has multiple internal menus that offer a complete and clear interface.

### Main-menu
1. This menu offers three options: 
* Transcribe an existing audio/videop file.
* Record and transcribe a new conversation.
* Apply post-processing to existing Gailbot output.

**NOTE: The last option is intended to allow users to run different post-processing using different settings without having to re-transcribe the entire conversation.**

### Post-processing interface
* This interface allows the user to select their desired combination of post-processing modules to be applied to the transcript.
* It provides a clear status indication for the modules that will be applied.

### CHAT generation module interface
* This interface allows the user to set CHAT file parameters.
* It allows user to change CHAT file headers and modify features including corpus name, speaker roles, speaker identities etc.
* It allows user to modify functional parameters and thresholds for conversation features including pauses, gaps etc. Additionally, allows user to use beat-timing or absolute-timing mode.

### Pre-request menu
* Provides the user with multiple details regarding custom language and acoustic models, some IBM features, and details regarding files to be trascribed.
**NOTE: Use the custom language model to select a base model if needed.**

### Post-processing file selection interface.
* Allows user to add existing Gailbot data and apply post-processing only.
* For a pair of files corresponding to the same conversation, the user has to manually add both files separately with the desired speaker names.
**NOTE: The interface asks for the combined as well as the individual audio files. These may be the same for a single file and different for a pair of files.**


### Audio Recording Settings interface
* Allows user to select different parameters for the audio to be recorded including bit-rate, length etc.
* The minimum length that can be recorded is 30 seconds.


##

##  Custom and Acoustic Language Models:
Gailbot's Custom language model is meant to expand on Watson's existing word dictionary to transcribe specialized contexts. 
Users can add individual words, multiple words, or a corpus text file to the custom model. 
For more details: https://console.bluemix.net/docs/services/speech-to-text/language-resource.html#corporaWords

Gailbot's Acoustic language model is meant to train the service to recognize particular sound environments to improve the accuracy of the transcripts.
Currently, Gailbot allows a '.wav' file to train the custom acoustic model.
* The file must be less than 100 MB
* The file length must be greater than 10 minutes and less than 50 hours
* Must be a '.wav' file.

## Contribute

Please send feedback, bugs & requests to:
* hilab-dev@elist.tufts.edu

## Collaborators and Acknowledgments

The [HiLab](https://sites.tufts.edu/hilab/people/), including

* [Muhammad Umair](http://sites.tufts.edu/hilab/people)
* [Saul Albert](http://twitter.com/saul)
* [Jan P. Deruiter](http://twitter.com/jpderuiter)
* [Julia Mertens](https://twitter.com/therealjmertens)
* [Lena Warnke](https://twitter.com/LenaWrnk)
