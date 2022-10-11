# Architechture

The main goal of the architechture should be to allow hosting geographically close to the areas in which the service is used, but still allowing things such as users and chats to be shared between instances.
Therefore, a microservice architechture will be handy. Services will be split into rough categories, such as users, chat and content.
While users will be critical to overall fumctionallity, chat will work without content and vice-versa.
Additionally, this allows us to share Resonance and other user statistics between instance, while still allowing partial outages.
While there shouldn't be instances per city, it is thinkable to have one instance per county (there are 16 in germany).
These instances should optimally be spread across different datacenters and be geographically close to their area of use.

As for data-storage, we'll attempt to go for a database-less approach that supports lazy-loading and caching.
This is where Oracles microstream comes into play. Paired with Helidon SE (for now), we can build a simple and lightweight codebase that doesn't make use of too many "magical" features.

The cherry on top would be the usage of GraalVM, which according to their propaganda leads to a minimum of 1,04x performance improvements compared to traditional JVMs and has significantly faster startup time and reduce memory usage.
While it us unclear how well using microstream with Graal should work, due to its usage of reflection, it is still worth an investigation.

In the end, this architechture, paired with proper backups and redundancy of core services, will probably allow us sufficient scalability and reliability for the type of service that this project is gonna be.
Backups will be rather simple to do, considering we use a simple file based approach and the fact that Microstream can handle partially written data.
