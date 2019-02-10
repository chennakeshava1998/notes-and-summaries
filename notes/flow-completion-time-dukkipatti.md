## ![Why Flow-Completion Time is the Right Metric for Congestion Control](http://yuba.stanford.edu/rcp/flowCompTime-dukkipati.pdf)

Provides a comparison of TCP, XCP(Explicit Congestion Protocol) and RCP(Rate Control Protocol - new and proposed alternative) wrt Flow completion time.

### Key Points:
1. It is intractable to provably minimize FCT. So try heuristics.
2. FCT in TCP: log2(L + 1/2) * RTT + L/C[transmission delay], L = flow size, doesn't include the queueing delay
3. XCP(Explicit Congestion Protocol) stretches any flow to multiple RTTs to prevent over-subscription to a bottleneck link.
4. In a general setting, XCP is more conservative in granting bandwidth to any flow than TCP.
5. XCP and TCP work well with long-lived flows only. The shorter flows complete before they reach the fair share rate.



### To Explore:
1. Relationship between FCT and SRPT(Shortest Remaining Processing Time) and PS(Processor Sharing).
2. ** if several infinitely long TCP flows with the same round-trip time share a bottleneck, TCP will eventually converge on a fair-share allocation ** ---> Why should the round trip times of the flows be equal? Otherwise, does it cause lockout?
3. Importance of probability distributions in simulations: Poisson flow arrivals and paretto distributed flow sizes.
4. Is FCT used as a metric in evaluation of AQM?

### Interesting References:
1. J. Du, J. Y. Leung, G. H. Young, ”Minimizing mean flow time with release time constraint,” In Theoretical Computer Science archive, Volume 75, Issue 3, October 1990. : Prove that it is not possible to provably minimise the FCT even if the arrival time and durations of the flows is known beforehand.
2. N. Dukkipati, M. Kobayashi, R. Zhang-Shen, N.McKeown, “Processor Sharing Flows in the Internet,” In Thirteenth International Workshop on Quality of Service (IWQoS), Passau, Germany, June 2005. ===> A new protocol that simulates processor sharing on every router. This is a stronger version of ECN and appears to be more useful.