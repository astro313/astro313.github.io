---
layout: post
title: "Markov Bot"
date: 2018-10-23
---

A while ago (2016-04-28), I audited the physicst, [Paul Ginsparg](https://en.wikipedia.org/wiki/Paul_Ginsparg)'s class on information science. First, I have say, I was extremely amazed by the way Paul thinks, even very basic mathematics -- definitely reminds me of how I was trainned to think in the Mathematics Olympiad classes back in the days.

When he was talking about Hidden Markov model, he mentioned trigram. We wrote a short code, MarkovBot, as an example. The idea is to train on some text given in a file, and then the code picks on the next word based on current bigram. 

This is the output from training on Sherlock:
> They laid me on a point. Of course, that is in a railway accident near
Crewe. Dr. Roylott had gone to live happily together in a pitiable
state of excitement, who insists upon seeing me. She is the last train
from Waterloo." "It is for the grace and kindliness with which he had
taken place, and that he is in your position of unofficial adviser and
helper in many ways unique, and its solution is its own sake,"
remarked Sherlock Holmes, laughing. "You really are very often
connected not with the right side." "The right side? You're mad! Here
is the less you must not interfere, come what may.

From training on the Declaration of Independence:
> He has obstructed the Administration of Justice by refusing his Assent
to their Acts of pretended Legislation: For quartering large bodies of
armed troops among us: For protecting them, by a mock Trial from
punishment for any Murders which they should commit on the protection
of Divine Providence, we mutually pledge to each other our Lives, our
Fortunes and our sacred Honor. When in the Legislature, a right
inestimable to them shall seem most likely to effect their Safety and
Happiness. Prudence, indeed, will dictate that Governments long
established should not be changed for light and transient causes; and
accordingly all experience hath shewn that mankind are more disposed
to suffer, while evils are sufferable than to right themselves by
their Creator with certain unalienable Rights, that among these are
Life, Liberty and the pursuit of Happiness.

From training on Shakespeare:
> I prithee, boy, run to the Maskers. Cap. Welcome, gentlemen! Ladies
that have abridged His time is come after it. Pedro. Wilt thou love
hawking? Thou hast sworn to stay with me to peruse, As I have sworn
thee fair: more perjured I, To swear against you? Such things as you!
Enter a SOLDIER as a traitorous innovator, A foe to sweat; And
travelling along this coast, I bere am come to this? COSTARD. Sir, I
did not bid for you must expect of me at court, Then not in confidence
Of author's pen or actor's voice, but suited In like conditions as
this dire night To meet Mark Antony.
We must, therefore, acquiesce in the great Lion, of which they are all
set free, and are wondering how we shall sometime come to me tomorrow
and you will have the castle of the Wicked Witch was so angry when she
bade me good-bye and sent him tumbling, over and cried, "Oh, my!" just
as they looked down and break myself." "But could you not a vain man
he did not care for it, saying it was made of tin. "I thought Oz was
alive he never lets anyone come into his straw stuffing would let him,
before this beautiful creature, she looked down and seized Quelala,
carried him up so that no harm was intended, so they will worry about
me.

Quite amusing, I find...
