# Azure Cognitive Service for Speech to Text

Today was an experiment with Azure cognitive tool kit!
Its always interesting to see how use of cloud computing goes from the most remote city in the world.
Still the network speeds aren't terrible in 2021, even with the extra NETFLIX and Streaming traffic due to COVID-19

ADD WEBSITE HERE

REASON:
I wanted to try out Azure voice to text and see how well it would work.
My intention for this is to take the work out of minute notes and indexing of video recordings.
My ideal would be meeting minutes produced for me without effort at the end of a recording.
They would then be in a format that allows search to be rapid and improved over manual.
This is mainly for accountability and understanding purposes of the recorded material.


SOFTWARE:
First thing, I'm doing this using python and as of this post python is up to 3.9.1.
As Python is a particularly forgiving language for starting out/rapid prototyping.
This version DOES NOT work with Azure cognitive tools so you will need 3.7.6 for compatibility.

ADD WEBSITE HERE

So, I'm not sure how you like to arrange things but I like to put versions of python into folders with the packages
and run virtualenv [folder address and name], install cmd prompt: virtualenv path/to/folder/VenvNAME.
This allows executables with py2exe to only use the packages necessary once you have worked out the nuts and bolts.

This installs the python version on PATH environmental variable into the package which is handy for isolatation and versioning.

With this installed, I was then able to install jupyter and run all the other installs from magics within a notebook (e.g. !pip install pandas)

PIP INSTALL JUPYTER

SETUP OF CHAIN:
Once all set up, the following are required:
1. A suitable video or voice recording
2. To download FFMPEG source code or a binary depending on your OS and install in a location and add to PATH.
3. convert the video or audio via FFMPEG into a .wav format, which is necessary for the Azure API.
4. Install the azure cognitive Software Development Kit
5. Optionally, install the spx CLI, which doesn't require knowing Python, C++ or C# etc (No Code).
6. Sign up for a free (for 12 months) Azure account.
7. Subscribe to the Speech service
8. find API key and Region code for input in python

I also noticed whilst going through the documentation that there is a video indexer API/Service that spits out JSON files for a similar purpose.

1: Finding a recording shouldn't be too hard with youtube etc available.
2: FFMPEG website - https://ffmpeg.org/
These guys are awesome, as I'm working on a windows platform I used a binary from Gyan (tip him a coffee if you do!)
The executable can be placed in a folder and added to path, I decided (unwisely) to drop it in system32 folder to save hassle.
3: Use of FFMPEG is pretty easy.

I also found that you can use the convert function in VLC using the GUI but this is quite slow and clunky in the long term.
Top tip for VLC is to use more options and select convert explicitedly.

ADD SCREENSHOT FFMPEG line to modify

4: The cognitive services are pretty easy to install via jupyter with a magic and pip.

ADD PIP screenshot from notebook

5: SPX is a "no code" command line tool, which still requires understanding the cmdline etc. So is at best a convienent way if python/jupyter is not
an option.

6: Use an existing microsoft account or create one and pass them your credit card details.
7: Once in the Azure console, the Speech API needs to be added as a service and the key and region found.

ADD SPEECH API

8: Finding the API KEY (there are two, that can be individually regenerated) and REGION

ADD KEY and REGION screens
ADD input into example code.

EXPERIENCE USING AZURE COGNITIVE SERVICE - SPEECH TO TEXT (standard models):
The whole experience is pretty good.
As with all things Machine Learning, the models are a good starting point but need some context.
This would be no different to a human.


First go:
1 shot recognition using the example code on the Azure GitHub.
It works well but is limited, it will wait 15s or end with a silence after a recognition has triggered.
This means that it can't deal with anything more than a sound bite.
This is the reason that the website example that you can upload a file into has a lot of recognition started type notifications.
I found that I preferred the second method of continuous recognition, which is a bit heavier but works out better.

Second go:
Continuous recognition works on an event handler basis.
This means that it has to be explicitly told to stop.
This can be by EOF for the recording or via an event.
The output from the example shows the recognising working its way from a silence and a phrase.
This worked reasonably well.
It struggles with multiple language based accents and pronouncation and specific domain wording.
This is to be expected, and there is an option for this: custom modelling.

Speaker Recognition:
There is also an addition API that can be given 20s clips of an individual and tries to then pick them out in the conversation.
I found that this is heavily affected by background noise.

Video indexer:
At the next opportunity I'm going to explore this option and report back seperately in its own post.
Unfortunately there isn't a python API (as of this blog).
I therefore will likely have to use C#.

Using SPX on CMD:
I found that redirection to file was the easiest way to complete a first run.
It can take some time, depending on your recording to go through the whole thing and print to file.

