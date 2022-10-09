## Architechture

The main goal of the architechture should be to allow hosting geographically close to the areas in which the service is used, but still allowing things such as users and chats to be shared between instances.
Therefore, a microservice architechture will be handy. Services will be split into rough categories, such as users, chat and content.
While users will be critical to overall fumctionallity, chat will work without content and vice-versa.
Additionally, this allows us to share karma and other user statistics between instance, while still allowing partial outages.
While there shouldn't be instances per city, it is thinkable to have one instance per county (there are 16 in germany).
These instances should optimally be spread across different datacenters and be geographically close to their area of use.

As for data-storage, we'll attempt to go for a database-less approach that supports lazy-loading and caching.
This is where Oracles microstream comes into play. Paired with Helidon SE (for now), we can build a simple and lightweight codebase that doesn't make use of too many "magical" features.

The cherry on top would be the usage of GraalVM, which according to their propaganda leads to a minimum of 1,04x performance improvements compared to traditional JVMs and has significantly faster startup time and reduce memory usage.
While it us unclear how well using microstream with Graal should work, due to its usage of reflection, it is still worth an investigation.

In the end, this architechture, paired with proper backups and redundancy of core services, will probably allow us sufficient scalability and reliability for the type of service that this project is gonna be.
Backups will be rather simple to do, considering we use a simple file based approach and the fact that Microstream can handle partially written data.

## Statistics

In Jodel, you don't really know how many active users there are or in which
regions of your city the usage is high or low.

Therefore, having the following datapoints would be interesting:

* Per city
  * Registered users
  * Active users
  * Active posting users
* Proximity
  * Active users
  * Active posting users

A problem with proximity statistics might be a high computation cost.

### Account

* Block certain telephone numbers (payphones and such)

### Moderation

The aim of the moderation system is to mainly operate without human intervention.
Severe violations will still require human intervention though.

### Location

* Locations should allow exact sharing (at least in chat)

### Posts

* Sorting
  * Good posts first
  * New posts first
  * Heated (commented) posts first
* Posts will have a character limit of 3000~ (requires more insights), but have a low preview character limit
* No pictures, audio and video for now, since its high effort
* Text is copyable
* Links
  * Blacklist
  * Whitelist for highlighting and preview

### Channel

* Global and geo-dependent channels
  > Some topics might generally be interesting and some things, such as meetups, might only be interesting locally.
* Channel discoverability
  * Add rough channel topics
    > Example:
    > The channels `tabletennis` and `gym` belong into rough channel topic `sports` .
  * Subscribe to rough topics for channel suggestions
  * Initially ask for channel interests
* A channel should only exist, after the first post has been made.

#### Pins

* Should allow categorisation

### Karma

Just like Jodel, we will have a Karma system. Karma can be earned through
upvotes, lost through downvotes and spent by reporting.

Karma will determine how the moderation system treats you.

If your karma is very low or you have lost lots of karma recently, one of
the following things might happen:

* Banned from certain types of channels (for example question posts)
* Reduced post speed (N posts or replies per M hours)
* Replies are hidden away by default
* Temporary ban from posting

In order to have any of these punishments take effect, we can either use the
overall karma or recent changes in karma balance, if any exist. An upside of
the latter would be, that users with a lot of karma also can't afford trolling
from time to time, using their karma as "troll budget".

By default, each user starts with a rather low base karma, but an amount bigger
than zero, in order to be able to use the reporting functionality.

### Karma Coupon Store

Cooperation with corperations, that allow users to reduce the cost of their product by spending karma on it.
This will potentially induce good behaviour and assign a value to karma.

### Voting

Voting is the main mechanism that changes a users karma. An upvote can be given
for free and will increase the posters karma. Downvoting will decrease the posters
karma, but also reduce the own karma, in order to prevent abuse.

### Reports

A report is kind of like a downvote, but more extreme. Attached to a report
can be a text message and a reason. Reasons might go from mild things such as
`spam` or `disrespective behaviour` to `exposing personal information` or
`violence`.

On Jodel, people tend to quickly report others if they are in disagreement.
In order to combat this, reporting should have a cost. The cost shouldn't be
too big, but also not insignificant.

Certain types of reports should be exempt from cost though, such as illegal content
regarding minors for example.

### Negative achievment badges

If a user does negative things, such as portray bad behaviour in physical meetups or
troll a lot, they can be reported for these things and earn a badge, marking them
as a "bad" person, visible to all other users, but not themselves. These badges
are indicators for potential dangers coming from a certain person in order to allow
users to reduce their risk when interaction with fellow users.

These badegs won't run out with time, but can get removed if users "commend" you, for
having improved your behaviour. A downside to this feature is, that if people do
report abuse, people might be flagged as "bad" even though they haven't really done
anything severe. However, a single report shouldn't be enough to get branded like this.

### Human moderators

Moderators aren't auto elected, like on Jodel. There's no community election process
either, as that's not really possible without users having an identity. Instead, Moderators
are platform internal people that act according to pre-defined rules.

If users wish to become moderators, they can apply through the app. As the service is
currently not intending to make any money, this will not give any payment though.

### Transparency

Anything that happens on the platform should be visible to the users.
Meaning you'll always be able to have insights regarding upvotes, downvotes and reports.
This way you can see how your own behaviour affects your karma and therefore your freedom
and capabilities on the platform.

This also goes for decisions made by the automated punishment system. You'll be informed of
punishments and be able to see why a punishment has gone into effect.

Every user should at any point in time have the option to download or delete ALL their data.
This includes all posts, replies, chats and other data related directly to the users account.

### Privacy

* Only save mandatory data
  * Reduce cooperation with authorities
  * No IP adresses
  * Telephone number used for registration isn't saved (Achieved through hashing)
  * Locations will never be exact


