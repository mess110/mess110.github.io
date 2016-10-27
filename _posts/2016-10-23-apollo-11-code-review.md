---
layout: post
title: Apollo 11 - Code Review
---

Stardate 23018.1 or 21st of July 1969, mankind takes its first steps on the Moon.

<center>
  <video width="320" height="240" controls>
    <source src="/blog/videos/apollo/Apollo_11_Landing_-_first_steps_on_the_moon.ogv" type="video/ogg">
  </video>
</center>

Meet Margaret Hamilton, the woman who in 1965 lead the Software Engineering Division at MIT Instrumentation Laboratory.
In the picture below, she is standing next to the printed source code of the flight software for the Apollo Guidance Computer.
Over 400 people worked on Apollo's software which helped people safetly land on the moon.

<center>
  <img src="/blog/images/apollo/Margaret_Hamilton.gif" />
</center>

You can bet your sweet ass they followed good software development practices. As a bare minimum, we know the software was
tested, reviewed and approved. It was written in a special version of the assembly language.
The code can be found on [GitHub](https://github.com/chrislgarry/Apollo-11), so lets take a look.

#### Readability is important

All the source code for [Luminary099](https://github.com/chrislgarry/Apollo-11/tree/master/Luminary099) has 64.992 lines. There are 40.202 lines of code.
There are no files without comments, 31.443 of the lines contain a comment and there are 5900 blank lines used.

#### The software was submitted by 1 person and approved by 6 other people.

<center>
  <a href="https://github.com/chrislgarry/Apollo-11/blob/master/Comanche055/CONTRACT_AND_APPROVALS.agc"><img src="/blog/images/apollo/submitted.png" /></a>
</center>

#### Temporary does not exist in programming. It is a myth! Hope is not a strategy.

<center>
  <a href="https://github.com/chrislgarry/Apollo-11/blob/master/Luminary099/LUNAR_LANDING_GUIDANCE_EQUATIONS.agc#L179"><img src="/blog/images/apollo/temporary.png" /></a>
</center>

#### Respect your users, but don't trust them.

<center>
  <a href="https://github.com/chrislgarry/Apollo-11/blob/9e0ef60171e359d5eb7056ca2cfbce0422b26761/Luminary099/THE_LUNAR_LANDING.agc#L245-L249"><img src="/blog/images/apollo/users.png" /></a>
</center>

#### Humor is essential for landing people on the moon.

* [Trashy little subroutines](https://github.com/chrislgarry/Apollo-11/blob/master/Luminary099/LUNAR_LANDING_GUIDANCE_EQUATIONS.agc#L1375)
* [Numero mysterioso](https://github.com/chrislgarry/Apollo-11/blob/master/Luminary099/LUNAR_LANDING_GUIDANCE_EQUATIONS.agc#L666)
* [Burn baby burn](https://github.com/chrislgarry/Apollo-11/blob/master/Luminary099/BURN_BABY_BURN--MASTER_IGNITION_ROUTINE.agc#L66)
* [Shakespeare quote](https://github.com/chrislgarry/Apollo-11/blob/e73b2973b06fd12ddbeb2049a203f031f4261511/Luminary099/PINBALL_GAME_BUTTONS_AND_LIGHTS.agc#L216-L225)
* [Hello there. Goodbye. Come again soon.](https://github.com/chrislgarry/Apollo-11/blob/e73b2973b06fd12ddbeb2049a203f031f4261511/Luminary099/BURN_BABY_BURN--MASTER_IGNITION_ROUTINE.agc#L904-L925)

#### Errors will happen. Write software with that in mind.

*"Due to an error in the checklist manual, the rendezvous radar switch was placed in the wrong position. This caused it to send erroneous signals to the computer. The result was that the computer was being asked to perform all of its normal functions for landing while receiving an extra load of spurious data which used up 15% of its time. The computer (or rather the software in it) was smart enough to recognize that it was being asked to perform more tasks than it should be performing. It then sent out an alarm, which meant to the astronaut, I'm overloaded with more tasks than I should be doing at this time and I'm going to keep only the more important tasks; i.e., the ones needed for landing ... Actually, the computer was programmed to do more than recognize error conditions. A complete set of recovery programs was incorporated into the software. The software's action, in this case, was to eliminate lower priority tasks and re-establish the more important ones ... If the computer hadn't recognized this problem and taken recovery action, I doubt if Apollo 11 would have been the successful moon landing it was."*
— Margaret Hamilton, Director of Apollo Flight Computer Programming MIT Draper Laboratory, Cambridge, Massachusetts, "Computer Got Loaded", Letter to Datamation, March 1, 1971

#### Bonus: SLOCCount output for Luminary099

* Total Physical Source Lines of Code (SLOC)                = 40,202
* Development Effort Estimate, Person-Years (Person-Months) = 9.67 (116.06)
   (Basic COCOMO model, Person-Months = 2.4 * (KSLOC**1.05))
* Schedule Estimate, Years (Months)                         = 1.27 (15.22)
   (Basic COCOMO model, Months = 2.5 * (person-months**0.38))
* Estimated Average Number of Developers (Effort/Schedule)  = 7.62
* Total Estimated Cost to Develop                           = $ 1,306,477
   (average salary = $56,286/year, overhead = 2.40).

#### References

* [https://en.wikipedia.org/wiki/Apollo_11](https://en.wikipedia.org/wiki/Apollo_11)
* [http://www.htius.com/Articles/r12ham.pdf](http://www.htius.com/Articles/r12ham.pdf)
* [https://www.youtube.com/watch?v=hyhI85Rd1kI](https://www.youtube.com/watch?v=hyhI85Rd1kI)
* [/r/ProgrammerHumor](https://www.reddit.com/r/ProgrammerHumor/comments/4ro9v9/apollo_11_guidance_computer_source_code_now_on/)
* [https://en.wikipedia.org/wiki/File:Margaret_Hamilton.gif](https://en.wikipedia.org/wiki/File:Margaret_Hamilton.gif)
* [https://en.wikiquote.org/wiki/Neil_Armstrong](https://en.wikiquote.org/wiki/Neil_Armstrong)
* [http://www.amazingwomeninhistory.com/](http://www.amazingwomeninhistory.com/margaret-hamilton-the-woman-behind-the-moon-landing/)
