# Multiband Sound Design & Sampling (MSDS) Template for Cubase Pro 10.5

 ![Overview](/img/header.png?raw=true)

## TL:DR

All channels will have text notes in to help you.

1) Set up your audio in line with the Marker Tracks.
2) Set up your VSTi's with  the correct Send routing.
3) Choose which level of sample creation you want by Activating the relevant Marker Track.
4) File > Export > Audio Mixdown...
5) In the Export Range section ensure Cycle Markers is set.
6) Select all the marker in the list and check the boxes.
7) In the File Location give your sounds a Name and choose a folder to export to. If you are going to be making samples across different velocity layers I would put each layer in a separate folder.
8) At the end of the field click the cog for the Naming Scheme.
9) Drag whatever Attributes you want in to the Result field, but **CycleMrkrNm MUST BE THERE!** I choose to have "Name" and **CycleMrkrNm** with the separator set as " - " which would result in **SoundA - C#1.wav** for example.
10) Set your formats, then Export!

A quick way to adjust sample length is to increase or decrease the Tempo.

## Introduction

This template was designed to help with the creation of complex sounds, apply multiband processing to them, and then to export individual named audio files so that they can be reused in sampling scenarios. Each file will have the correct corresponding note name as long as you follow the guide.

## Version 2 & Compatibility

v2 is a major reworking over v1, and as such the way you can use it has changed as well. It has been simplified in some areas and expanded in others. Render In Place has flaws in my opinion, and is no longer the preferred rendering method.

There is no longer a "Multiband" and a "Simple" template, there is just one master template that has multiband processing baked in, you can bypass it if you want, or use it in tandem with regular processing, but it's there and up to you how you use it.

Unfortunately, because of some of the feature requirements, this will only work on 10.5 Pro. Only Pro allows more than 1 Marker Track (and limited to 10.) Pro also allows more FX channels to be used.

If you wanted to port this to other versions the principal is the same and it can be done - I might rework this to work in lower versions if I get time, or maybe split the template into individual instances but that doesn't seem as flexible to me, supporting Pro is my priority right now. You can always fork it on GitHub and make your own :)

Audio Sends are used instead of Direct Routing as they are a little more flexible when it comes to panning, levels and pre / post assignment.

## Installation

Download the [Multiband Sound Design & Sampling (MSDS).cpr](https://github.com/smadgerano/MSDS/blob/master/Multiband%20Sound%20Design%20%26%20Sampling%20(MSDS).cpr) file from GitHub, and save it to the relevant folder on your machine.

On Windows this is here...

`C:\Users\yourusername\AppData\Roaming\Steinberg\Cubase 10.5_64\Project Templates`

On Mac it's this folder here...

`/Users/yourusername/Library/Preferences/Cubase 10.5/Project Templates`

More details on these can be found [here](https://helpcenter.steinberg.de/hc/en-us/articles/360000327730-Location-file-paths-of-presets-in-Cubase-and-Nuendo-) if needed

You can create subfolders in this directory, or rename the template CPR files as you need, Cubase will still recognize them during the new project dialogue.

You could GIT clone this repo directly into your template folder, but I wouldn't recommend that as it will fill your personal folder up with files you don't need, and backing it up more of a pain.

## Loading the Template

After loading Cubase, select File then New Project to open the New Project dialogue. The MSDS template will be in the **More** section. Then choose your project location as usual.

![New Project Dialogue](/img/new-dialogue.png?raw=true)

## Multiband Routing Explained

The routing in this template is flexible but does need to be setup a certain way, and depending on how many instruments, audio tracks and effects you add, it will use more resources, but that's OK because the whole point of this is to export the samples anyway!

The Output routing for every sound source is routed to the **MB PROCESSING BYPASSED** channel, so that's all Audio and VSTi channels. On each of these channels the Effects Sends are also enabled, and routed to each of the multiband processing Buses.

![Channel Routing](/img/channel-setup.png?raw=true)

Each of the Multiband processing Buses are then routed through to the **MB PROCESSING ACTIVE** channel.

![Bus Overview](/img/routing-overview.png?raw=true)

To listen to just the basic stereo signal from your sound sources, **mute** the MB PROCESSING ACTIVE channel, and **unmute** MB PROCESSING BYPASSED.

![MB Bypassed](/img/mb-bypassed.png?raw=true)

To listen to just the multiband processed signal from your sound sources, **unmute** the MB PROCESSING ACTIVE channel, and **mute** MB PROCESSING BYPASSED.

![MB Active](/img/mb-active.png?raw=true)

Of course you can have both channels on for some extra crazy effects, but things soon get a bit "wobbly" if you do this and I hold no responsibility for broken speaker cones :)

#### The Multiband Frequencies

Band / Bus Name | Frequency Range
------------ | -------------
SUB | 0 Hz – 60 Hz 
LO | 60 Hz – 200 Hz
MID | 200 Hz – 550 Hz
HI | 550 Hz – 16 KHz
PRES | 16 KHz – 20 KHz

## Using the Multiband Sends

Because the template uses Effect Sends on each signal source to route the frequencies, we have complete flexibility of stereo placement and volume. By default all signals with be passed through at 0db, but this can be changed in the Mixer.

![MB Send Levels](/img/mb-send-levels.png?raw=true)

## Expanding & Altering Bands

Whilst it is possible to use this same technique of routing signals to multiple FX channels up to 16 using Sends and Direct Routing, each extra band will increase the demands on the system, 5 seems to be the sweet spot in terms of manageability, speed, flexibility and resource usage for me.

If you wish to alter the crossover frequencies of each of the bands, open the Channel Strip and change each of the High Pass and Low Pass Filter frequencies, so that each channel has a unique frequency band. You can change the Filters from 48 db/oct to other values, but I find the frequency buildup at those points becomes too noticeable.

![Frequency Bands on the MB MID Bus](/img/mid-bus-band.png?raw=true)

If you wanted to be more precise with the filtering you could load the bundled Frequency EQ plugin into Insert Slot 1 on each of the MB Bus Channels, setting the relevant frequencies, types, and MS settings, and then disable the filters on the Channel Strip. This can yield great results, but again at the cost of resource usage.

![Alternative Band Filtering](/img/alternative-band-filtering.png?raw=true)

It is absolutely possible to create a "hybrid" filtering system using Frequency for the SUB and LO Bus for absolute precision, and then use the Channel Strip Filters for the remaining Buses. This approach can be useful if you need to filter the channel signal after a certain effect, for example some effects will introduce aliasing into the chain, having the filter after teh effect can reduce "frequency spill" and create a cleaner overall signal.

## Using Multiband Effects

Insert effects can be added on sound sources as usual, and depending on Send levels will be routed through all multiband buses.

If you wanted to make a multiband effect out of a non-multiband effect, for example the Bitcrusher, it would have to be on each of the Multiband Buses insert Effect Slots.

![MB Bitcrusher](/img/mb-bitcrusher.png?raw=true)

At this point it's entirely up to you how you link these effects together or not to create the sound you need. Or you could only have the effect on a specific band.

## Adding Sound Sources

A sound source is a VSTi, an Audio track, a Sampler Track, Group Channel, or further Effects Channels. In order to use the multiband processing, they should all have their Output and Send Routing as the tracks already in the template.

![Channel Routing](/img/channel-setup.png?raw=true)

There are a number of ways to route the existing MIDI data, the most basic involves duplicating the parts to the new track, but I prefer to keep things as they unless I really need to separate out the data, so I use the MIDI Sends to duplicate the outputs to multiple sources. But this is of course up to you.

![MIDI Sends](/img/midi-sends.png?raw=true)

If you want a specif audio sample to trigger for each note, the easiest way to do this is to import it as a Sampler TRack and route the existing MIDI to it. Otherwise you will need to duplicate the audio segment for each note you want to export.

## Altering Sample Capture Lengths

To quickly adjust the size of the resultant samples or the length of the MIDI notes, increase or decrease the Tempo. The faster the Tempo the shorter the note and region that's captured for each sample.

If you need to change the length of the notes, unlock the layer, select all parts, open the Editor in the bottom panel, then select all the notes and change them accordingly.

## Controller Data

To apply specific controller automation for each note, the best way is to use a new layer, create an even that has the same length as a note event, then repeat it for the entire arrangement.

![CC Data](/img/note-cc.png?raw=true)
![Repeat the Event](/img/cc-repeat.png?raw=true)

This also allows you to Ramp data across the key range for more realistic samples.

![Apply Gradients](/img/cc-gradient.png?raw=true)

## Capture Levels

##### WARNING

Using higher capture rates will massively increase file size for diminishing sonic quality, only use them if you need to. For most situations, SMALL or lower will be absolutely fine. MICRO, NANO and PICO are in the sweet spot of audio quality vs storage space  and resource usage. And if you are targeting multiple velocity layers you can be very good results with less samples by staggering the velocity layers and using roundrobins.

You can obviously create your own capture levels but these are the ones in the template.

Capture Level | Number of Notes Captured
--------------|----------------
EPIC | 128
MAJOR | 84
FULL | 64
MEDIUM | 42
SMALL | 37
MICRO | 29
NANO | 26
PICO | 22
DIRTY | 13
DRAFT | 6

## Velocity Layers

The notes on the MIDI Note layer all set to a velocity level of 1. The quickest and easiest way to change this is using the MIDI Modifiers. The Vel.Shift default value in the template is +126, making the resulting MIDI Note Velocity values 127.

![Velocity Levels](/img/velocity.png?raw=true)

If you intend to create multiple velocity layers for your final samples, the easiest way is to change the value and rerun the export process. Make sure to set a new folder for each otherwise the renders from the previous velocity level will be overwritten.

It is absolutely possible to duplicate the entire arrangement content in series for as many layers as you need, but then that gets a bit too crazy, and you'd also need to go through renaming all the Markers to coincide with them - given how long it took me to get these done, you're welcome to do that yourself :)

## Exporting Samples

Once you have your sounds ready to export there are a few things that must be done in order for everything to work correctly.

1) Activate the Marker Track with the capture level you need.

![Marker Tracks](/img/marker-tracks.png?raw=true)

2) Go to the File Menu, then choose Export and then Audio Mixdown...

![File Export](/img/file-export.png?raw=true)

3) In the Export Range section ensure Cycle Markers is set, and make sure all the markers in the list are checked. You can use SHIFT to select the top and bottom from the list if you need.

![Cycle Markers](/img/cycle-markers.png?raw=true)

5) In the File Location give your sounds a Name and choose a folder to export to. If you are going to be making samples across different velocity layers I would put each layer in a separate folder.

6) At the end of the field click the cog for the Naming Scheme.

7) Drag whatever Attributes you want in to the Result field, but **CycleMrkrNm MUST BE THERE!** I choose to have "Name" and **CycleMrkrNm** with the separator set as " - " which would result in **SoundA - C#1.wav** for example.

![Naming Scheme](/img/naming-scheme.png?raw=true)

8) Set your formats, then Export!

![Exporting](/img/exporting.png?raw=true)

![Result](/img/result.png?raw=true)

## Tips & Tricks

Because everyone loves a tip or trick (shoutout to Greg Ondo) here's a couple to help make your way around this template.

* Adding one long audio file that contains an ambience is a great way to give character to each individual note, in order to prevent clipping and pops at the start, use a gate with a sidechain that's triggered from another channel.

* Linking Insert Effects and parameters on the MB Buses can be sped up if you select all the channels you want to work on, then hit the Quick-Link button, just remember to turn it off again when you've completed the step you wanted.

* The VCA fader is set up to control the Multiband Buses, but only for volume. If you want to link other parameters to it, hover over the title where the Panning Slider would be, click the arrow and choose Edit Link Group Settings.

![Edit Link Group Settings](/img/vca-link-settings.png?raw=true)

* If you want to create unique samples across the key range, create slow moving automation that spans the entire project, this can help to create subtle variations. Or assign one of the MIDI LFO's to a controller and set it to be random.

![Slow Modulation Rise](/img/modulation.png?raw=true)
![Random LFO](/img/auto-lfo.png?raw=true)

Hope this is helpful for some people, let me know if you think it can be improved in any way.

Andy