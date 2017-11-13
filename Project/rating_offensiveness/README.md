Let's use this folder to document our progress on rating the offensiveness of songs.


## Ofcom
There is a nice survey, by the UK communications regulator "Ofcom".
They conducted a survey with 248 participants in the UK and had them rank a variety of swearwords.

The corresponding entry on their website is strangely unreachable, but I found the original paper: https://www.ofcom.org.uk/__data/assets/pdf_file/0023/91625/OfcomQRG-AOC.pdf

And a useful transcription:
http://metro.co.uk/2016/10/02/swearing-ranked-from-mild-to-strongest-6165629/#

I've converted the transcription into a JSON file that should be easy to parse with python.
I've not included "offensive gestures". And some words with a slash like "feck/effing", I've split into two entries.