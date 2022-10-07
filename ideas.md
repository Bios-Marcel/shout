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

## Moderation

The aim of the moderation system is to mainly operate without human intervention.
Severe violations will still require human intervention though.

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

Anything that happens on the platform should be visible to the users, even the "bad" ones.
Meaning you'll always be able to have insights regarding upvotes, downvotes and reports.
This way you can see how your own behaviour affects your karma and therefore your freedom
and capabilities on the platform.

This also goes for decisions made by the automated punishment system. You'll be informed of
punishments and be able to see why a punishment has gone into effect.

