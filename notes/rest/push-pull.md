
Push Vs. Pull model : Communication & Data flow models


hi there! I thought of briefing on how the well known push and pull models work, pros and cons of using them.

For communication models and data flow models in distributed architectures, the “push” and “pull” models are well known. These models depend on if the communication/data flow is data driven or demand driven. In these models, there exists an active component and a passive component, categorized based on who starts the interaction first; either sending first or demanding first.

The push model is data driven. Once the serving node identifies it has some content to be published/sent to the other node/nodes, the serving node will either send or multicast the content without any request from the receiving end. Since the sending first approach is practiced, this model identifies the sender as the active component.

The push model has its own advantages and disadvantages. Unlike in a pull-based architecture, the receiving ends do not periodically poll and ask if the serving end has something for them. Therefore, the serving node is not interrupted frequently for demands to which it cannot serve. This prevents server overload, which can occur due to flooding demand requests. This may even lead to a server crash due to unhandlably massive request/demand count. Thus it also effectively eliminates the security issue of being vulnerable for a Denial of Service attack. But still as a disadvantage, in the push communication model, the recipient may not be interested in the disseminated data up on him, and be unsatisfied.

In the pull model, the sending node passively waits until a recipient node interrupts him requesting content. Hence the receiving end becomes active component.  The serving node has to manage content without loss till the receiving end at sometime request the content. The receiving end has the freedom to decide its own interest in the content and also consider the reputation of the sender prior to demanding. Hence the recipient has control over what it receives. In the security aspect, it also has a large window of time to verify the identity of the sender, from the time elapsed between the demand request and receipt of content at the receiving end. Apart from being prone to DoS attacks, the serving node is burdened with content management complexity, having to store content till intended recipient demands, verify if the demander is the original intended recipient of content and monitor if any content is never demanded by any node causing the buffer to hold unnecessary content and get filled.

Hybrid push-pull models are used in contexts where the serving end interacts with an event channel, and the recipient picks from the event channel, as in CORBA discussed in this paper.

* http://nadeeshanihewage.blogspot.com/2012/04/push-vs-pull-model-communication-data.html
* http://ptolemy.eecs.berkeley.edu/papers/03/PushPullProcessing/PushAndPull.pdf


