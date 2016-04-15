# Broadway, the road to 1.0

Little over 1.5 years ago we [open sourced][oss] [broadway], bringing CQRS and Event Sourcing to PHP. At the time not many engineers known to us in the PHP community were deploying CQRS\ES applications in production and we decided to open up our lessons learned to others. Today we are humbled to know that broadway is used in production in many places other than [Qandidate.com]. With that in mind we want to share our current plan to reach v1.0.0.

Our high level goals are:

- show the world that the broadway codebase is stable (it is!)
- become more open for other community members to step in

With the uptake of broadway being used in production, other companies have invested in their own related implementations and tooling. Some of those projects have shown interest in becoming "official" broadway components. As the broadway project matures we want to provide the ability for those projects to continue under the broadway umbrella.

We hope the above gives context for the following changes:

- **Moving broadway to the broadway GitHub organisation** Over time the composition of the broadway core team never changed, but not everyone works at the company where it all started anymore. In the past year the project has been a community driven project more than anything and in that light we are going to move broadway to the [broadway GitHub organisation][gh]. It will also make it easier to adopt related projects under the broadway umbrella.
- **Splitting out the Symfony bundle** The Symfony bundle currently lives in the main broadway repository. We are going to make it a standalone project and encourage other framework integrations (Zend, Laravel, ...) to be published under the broadway umbrella if maintainers wish to do so.
- **Splitting out implementations** Down the line the core of broadway will be leaner, providing the base interfaces, testing helpers and storage agnostic business logic. The DBAL event store component will move to its own repository.

We are planning to move the project and split the bundle before the end of this month. After all implementations are split out as well we think broadway is ready for v1.0.0! If you have any feedback or questions, please reach out to us in #qandidate on freenode.

Let's write some history!

[Willem-Jan], [Sander] and [Alexander]


[oss]: http://labs.qandidate.com/blog/2014/08/26/broadway-our-cqrs-es-framework-open-sourced/
[broadway]: https://github.com/qandidate-labs/broadway
[Qandidate.com]: http://qandidate.com/
[gh]: https://github.com/broadway
[Willem-Jan]: https://github.com/wjzijderveld
[Sander]: https://github.com/othillo
[Alexander]: https://github.com/asm89
