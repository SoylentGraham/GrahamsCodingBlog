Thursday 5th December 2019
===========================
This afternoon I've been trying to work out why my c# mp4 decoder (PopCodecs) is failing with a fragmented mp4 created from ffmpeg (`ffmpeg -i cat_baseline.mp4 -c copy -movflags frag_keyframe+empty_moov cat_baseline_fragment.mp4`) but has been working well when streaming from hololens.
I tested my file against http://mp4parser.com/ and the file is okay, but my values in the `moof/trun` atom (fragment sample table) are off (again, working before!)

Looked up the reference docs in my source https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-sstr/6d796f37-b4f0-475f-becd-13f1c86c2d1f?redirectedfrom=MSDN and checked the flag bits... they're off.
Checked the source of mp4parser...
http://178.62.222.88/mp4parser/mp4.js

Different flag layout...
```
enum TrunFlags  //	mp4 parser
{
	DataOffsetPresent = 0,
	FirstSampleFlagsPresent = 2,
	SampleDurationPresent = 8,
	SampleSizePresent = 9,
	SampleFlagsPresent = 10,
	SampleCompositionTimeOffsetPresent = 11
}
/*
enum TrunFlags  //	ms (matching hololens stream)
{
	DataOffsetPresent = 0,
	FirstSampleFlagsPresent = 3,
	SampleDurationPresent = 9,
	SampleSizePresent = 10,
	SampleFlagsPresent = 11,
	SampleCompositionTimeOffsetPresent = 12
};*/
```

This seems like it's going to be a problem. (Both are version_byte=0)



Wednesday 4th December 2019
========================
Hololens 2 is great. Tried at VRLO.


Monday 2nd December 2019
===========================
https://twitter.com/soylentgraham/status/1201472609566810112

I got stuck today on http://adventofcode.com/ because of a weird bug that threw me for a bit.
This just crashes chrome (maybe v8?) but really I'd expect a syntax error :)
```
function Hello()
{
}

function DoTheThing()
{
	Hello();
}

async function Hello()
{
	DoTheThing();
}

Hello().then( console.log ).catch( console.error );
```

Hello Worlf
==================
I've decided I should keep a record of little bugs and annoyances and quirks whilst coding.

I'm lazy, so it's in markdown. There's no better todo list than `todo.txt`, I'm pretty sure this applies to logs too, and twitter just drowns in noise.

http://www.twitter.com/soylentgraham/
