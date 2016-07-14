# ember-edge

An edge server for your ember application. Today, hosting and serving of your
ember app is a fairly ad-hoc experience. We see many great but bespoke
solutions in our community, lighting deploys, multi-version deploys,
authentication, versioned releases, fastboot, prefetch etc. All great
solutions, but can be difficult to integrate, share and collaborate on. That is
where ember-edge comes in. It can be thought of as the production server
sibling to ember-cli.

Where ember-cli is the development harness, ember-edge will be the production
platform. Where ember-cli provided addons for both code-sharing, build time,
and deployment time sharing. Ember-edge aims to provide safe and secure addons
for production concerns, fastboot, prefetch, authentication, proxying, server
side actions and hopefully the foundation for a whole new class of
optimizations and sharable solutions.

This is obviously an ambitious experiment, but we feel the need is real, worth
the investment. The success of ember-cli and the ember addon ecosystem
gives us confidence that this will not only provide value but given our strong
community a success.


Alright, enough with the pie in the sky thought leadering. Give me some diagrams!

At a highe level, the edge server with be:

* the source of requests hitting the origin, this includes
	* serving the index.html (which points to the version of assets that should be displayed)
	* serving same origin API requests (via proxying, or a backend)
	* deciding which index.html and which backend

```
                        +--------+
                        | Config | (by version of the app)
                        +--------+
                             ^
+---------+                  |
| client  |<-----+           |
+---------+      |           v
+---------+      |      +---------+        +----------+
| client  |<-----+----->|  edge   |<------>|Backend(s)|
+---------+      |      +---------+        +----------+
+---------+      |
| client  |<-----+
+---------+
```


Currently ember-deploy offers some of this via
https://github.com/ember-cli-deploy/ember-cli-deploy-lightning-pack/ and as a
server
https://github.com/stonecircle/express-lightning-deploy/blob/master/server/index.js
the goal though, is to continue to mature the hosting server, so it can be
configurable/pluggble and sharable by the larger community, but still a deploy
target for ember-deploy. For example, it should coordinate other processes such
as fastboot/prefetch or proxies, or server side ations etc. so the ember
version remains correctly synchronized for a given user sesssion. For now
though, the above should be a
great starting place.

related:

-  https://www.youtube.com/watch?v=QZVYP3cPcWQ
