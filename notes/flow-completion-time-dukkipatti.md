![Why Flow-Completion Time is the Right Metric for Congestion Control](http://yuba.stanford.edu/rcp/flowCompTime-dukkipati.pdf)

### Key Points:
1. It is intractable to provably minimize FCT. So try heuristics.


### To Explore:
1. Relationship between FCT and SRPT(Shortest Remaining Processing Time) and PS(Processor Sharing).
2. ** if several infinitely long TCP flows with the same
round-trip time share a bottleneck, TCP will eventually converge on a fair-share allocation ** ---> Why should the round trip times of the flows be equal? Otherwise, does it cause lockout?
3. Importance of probability distributions in simulations: Poisson flow arrivals and paretto distributed flow sizes.
4. Bandwidth Delay product and it's effect on FCT.

### Interesting References:
1. J. Du, J. Y. Leung, G. H. Young, ”Minimizing mean flow time with release time constraint,” In Theoretical Computer Science archive, Volume 75, Issue 3, October 1990. : Prove that it is not possible to provably minimise the FCT even if the arrival time and durations of the flows is known beforehand.