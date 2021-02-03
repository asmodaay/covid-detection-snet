# Covid detection service


## Welcome

The service receives an audio file and uses it as an input for a pre-trained model.

## What’s the point?

The service performs COVID-19 detection using machine learning techniques.
The service receives the audio file in binary format and outputs the text string resulting from detection. 

##  Model details:

The service receives an WAV audio file and uses it as an input to the VGG model, based on a deep convolutional neural network and outputs the embedding of input samle, then embedding used as input for machine learning classifier. The input audio file size is limited to 4Mb, in practice the optimal duration of the processed audio track should be no more than 10 seconds for 320 kbps audio.

## How does it work?

The user must provide the following inputs in order to start the service and get a response:

Inputs:

 -   `endpoint`: node1.naint.tech:14393.
 -   `method`: s2t.
 -   `input_path`: Path to '\*.txt' file containing JSON representation of input argument 'file@data' and its value - path to '\*.wav' input audio file.

Example of input file content:

```
{"file@data": "samples/sample.wav"}
```

You can call the service from SingularityNET CLI (`snet`).

Assuming that you have an open channel (`id: 0`) to this service:

```
$ snet client call 0 0.1 node1.naint.tech:14393 s2t samples/sample.txt

Read call params from the file: samples/sample.txt

text: "healthy"
```

## What to expect from this service?

Input audio:
samples/sample.wav

Response:
`text: "healthy/positive_asymp/positive_mild/positive_moderate"`
