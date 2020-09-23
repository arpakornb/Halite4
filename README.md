The code for my highest score bot is [here](https://github.com/arpakornb/Halite4).

First of all, I would like to thank Two Sigma and Kaggle for organizing such a fun competition. I'm also indebted to the notebook from [Yegor Biryukov](https://www.kaggle.com/yegorbiryukov/halite-swarm-intelligence) and [Alexis Cook](https://www.kaggle.com/alexisbcook/getting-started-with-halite) for getting me started.

Initially I did this only as a way to learn python and start participating in kaggle competition. My background was in C programming for networking equipment with no ML experience.

I took a direct (and you might say, naive) approach: dig, steer, deposit, with no attempt at hunting. Each ship scans its neighborhood up to four steps away from it to find the highest halite cell (with weight to prefer nearer cells) and goes there. Neighboring ships don't go to cells that have already been chosen. This seems good enough that I stick with it til the end. I augmented it (last week of competition) to improve the beginning phase (up to ~step 20) by choosing the top 9 halite cells in my quadrant (except two steps around yard) as targets for the first 9 ships. I control how much each ship digs by a maximum constant that varies based on game step and how aggressive other players are hunting.

Navigating crowded space seems very challenging. I try to solve this by assessing risk two steps around each ship at the beginning of each step. I assign varying risk values to my or enemy ship, its distance and carrying halite. I let my ships that might be attacked choose its move first followed by ships that have lower risk value (trying to make room for ships in risky position).

With all of the above, my submissions' score just would not go higher than 1100. It will do well up until around step 70-200 when not enough ships will survive the hunting onslaught. That's when I realized that I need to hunt as well so I experiment with the easiest approach. I stop collecting at around step 70 and every ship with zero halite will look for nearby enemy ships (three steps around) with the highest halite and step toward that ship. There is no coordination between ships whatsoever. This seems to raise my score into ~1200 level. I think it is not really the hunting that helps but mostly because I preserve enough ships to have a chance to collect again after step 300. I augmented this later by doing some digging if there's no enemy ship around and that helps a little bit.

I also improve the shipyard creation and placement and see a small improvement. More precision is needed there.

Other noteworthy improvements came from reacting to what other players do. rica_chan's bot taught me a lot. :) For example, its shipyard destruction near the end prompted me to tighten the ship and shipyard creation logic. I also copied mzotkiew's end game all-out deposit.

All in all, this has been good fun and a great experience. Looking forward to the next competition. I'm thankful for everyone who has shared their code. It is great learning resource. Really appreciate it!
