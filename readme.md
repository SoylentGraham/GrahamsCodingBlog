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
