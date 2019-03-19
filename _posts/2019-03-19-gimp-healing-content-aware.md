---
layout: post
title: gimp healing/content aware
---

Lets start with an [example from /r/picrequests](https://www.reddit.com/r/picrequests/comments/b2nmm4/can_someone_please_edit_the_people_in_the_front/).
The request is: *"Can someone please edit the people in the front by the
water out?"* This is the picture:

<center>
  <img src="/blog/images/gimpheal/bgseaem1txm21.jpg" />
</center>

Previously I would remove things or people from images by hand using a
combination of the Clone tool and blur/sharpen/smudge. It was a tedious
task. Just found out about healing selections.

Just use the Free Select Tool to highlight the item you want removed. Hint: you
can press and hold Shift/Ctrl to add/remove from your current selection. Like
so:

<center>
  <img src="/blog/images/gimpheal/step1.jpg" />
</center>

Next go to Filters > Enhance > Heal selection. Defaults work ok, so press OK.

<center>
  <img src="/blog/images/gimpheal/step2.jpg" />
</center>

And you should be good to go. Sure, it can use some manual cleanup but the
results are impressive.

By default, Gimp does not come with this addon installed. To install it, run

{% highlight sh %}
sudo apt install gimp-plugin-registry
{% endhighlight %}

[Happy trolling](https://www.reddit.com/r/picrequests/comments/b2nmm4/can_someone_please_edit_the_people_in_the_front/eiw5brq).
