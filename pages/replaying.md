---
permalink: /replaying
title: Replaying
---

# Replaying

We have a really really basic [replayer](https://github.com/broadway/broadway/blob/master/src/Broadway/Replaying/Replayer.php) in Broadway.
The reason why we don't have more is because replaying is very specific to your
situation and it depends a lot on your infrastructure.

What our [replayer](https://github.com/broadway/broadway/blob/master/src/Broadway/Replaying/Replayer.php) does is basically query the event store based on given [Criteria](https://github.com/broadway/broadway/blob/master/src/Broadway/EventStore/Management/Criteria.php)
and [pass](https://github.com/broadway/broadway/blob/master/src/Broadway/EventStore/Management/EventStoreManagement.php#L20) 
the events to an [EventVisitor](https://github.com/broadway/broadway/blob/master/src/Broadway/EventStore/EventVisitor.php).

## Common pitfalls

### Changed events
If your events have changed over time old events may cause an error when replaying.
Always make sure changes to events are backwards compatible or make sure to 
upcast your old events to reflect the changes.

### Too many events
If you have a huge event stream that needs to be replayed you can run into
memory issues. Make sure your event repository uses a generator instead of
loading all events in memory.

### Time-outs
If replaying takes a long time, time-outs may occur. Try to keep your database
connection alive or make sure it reconnects. You can also add some retry 
mechanism to your replayer.

### Consistency
While you are replaying, your read models can be in an inconsistent state 
because not all events of a given aggregate have been processed. You need to 
think about how to prevent a bad user experience for your end users.

In Elasticsearch for instance you can use aliases so you can create a new index 
with replayed read models and once the replaying is complete change the alias 
from the old index to the new one.

### Bulk updates
When you replay events you need to query the read model from its repository on 
each event, update it and write it again which can be quite resource intensive.
What you could do is write all read models to an [in-memory repository](https://github.com/broadway/broadway/blob/master/src/Broadway/ReadModel/InMemory/InMemoryRepository.php)
and only at the end of replaying [transfer](https://github.com/broadway/broadway/blob/master/src/Broadway/ReadModel/Transferable.php)
all read models to the persistent repository.

## Further reading

* [Replaying event streams with Broadway](https://labs.qandidate.com/blog/2015/07/08/replaying-event-streams-with-broadway/)
* [The 3-line replayer for Broadway](https://othillo.github.io/blog/2016/03/03/3-line-replayer-for-broadway/)
* [Loading lots of Entities using Doctrine](https://www.rpkamp.com/2016/12/23/loading-lots-of-entities-using-doctrine/) by R&eacute;mon 
