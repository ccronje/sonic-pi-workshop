---
chapter: Make a song
title: Drum beat
lang: en
layout: exercise
---

Let’s look at how to create a simple drum beat, consisting of a kick drum, snare and hi-hat. You'll get to know two new things: `live_loop` and `sample`.

Start with a empty buffer and create a `live_loop` called `:drums`. It could be named anything, the names is just for quickly identifying what the loop does. `live_loop` is an endless repeating loop that can be synchronised with other live_loops (a `live_loop` has to have at least one sleep):

{% highlight ruby %}
live_loop :drums do
  sample :drum_heavy_kick
  sleep 1
end
{% endhighlight %}

Hit **Run** to hear your first `live_loop` playing a nice kick drum every beat. 

Let's do a simple backbeat with kick drum on 1 and 3, snare on 2 and 4. Instead of playing notes, you will be triggering samples. It's as simple as writing `sample :sample_name`. Here's an example drumbeat:

{% highlight ruby %}

use_bpm 100

live_loop :drums do
  sample :drum_heavy_kick
  sleep 1
  sample :drum_snare_hard
  sleep 1
  sample :drum_heavy_kick
  sleep 1
  sample :drum_snare_hard
  sleep 1
end
{% endhighlight %}

That's a steady backbeat. The `:drums` loop starts with a kick, plays snare on the two, kick on three, then a snare on the four. Then the loop starts again:

<img src="{{ "/assets/img/live_loop.png" | prepend: site.baseurl}}">

Now, try changing the tempo (the number after `use_bpm`) and play with the samples. When you start writing the sample name, you can browse different samples with the auto-complete feature. Try different samples and check out what they sound like. Notice that you don't have to hit stop to change the sound - just change the code and re-hit **Run** - the sounds will change automatically on the next loop without losing a beat!

## Add hi-hat

Now add a hi-hat. Create another live loop called `:hihat` and add your hi-hat samples. You could do for example straight 8th or 16th notes like this (this is 16th notes):

{% highlight ruby %}
live_loop :hihat do
  sample :drum_cymbal_closed
  sleep 0.25
end
{% endhighlight %}

But it doesn't have to be so square. You could also go for a bit more funky like this:

{% highlight ruby %}
live_loop :hihat do
  sample :drum_cymbal_closed
  sleep 0.25
  sample :drum_cymbal_pedal
  sleep 1
end
{% endhighlight %}

The polyrhythmic hi-hat pattern was first a "mistake". The loop is 1.25 beats long instead of the supposed 1. But it sounds cool! So remember to make a lot of mistakes to find something you weren't even looking for.

Now the song looks something like this:

{% highlight ruby %}
use_bpm 100

live_loop :drums do
  sample :drum_heavy_kick
  sleep 1
  sample :drum_snare_hard
  sleep 1
  sample :drum_heavy_kick
  sleep 1
  sample :drum_snare_hard
  sleep 1
end

live_loop :hihat do
  sample :drum_cymbal_closed
  sleep 0.25
  sample :drum_cymbal_pedal
  sleep 1
end
{% endhighlight %}

You might be wondering how the live_loops would translate to music sequences in popular music-making apps? The following video might help you to understand their relation.

<iframe width="640" height="360" src="https://www.youtube.com/embed/iFMNOb33_KM?rel=0&amp;controls=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

Now play around with different samples and rhythms. You could also add a third `live_loop` for percussions or other effects. Next you'll create a bass track for your composition.
