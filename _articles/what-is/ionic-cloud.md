Ionic Cloud was an early cloud offering of Ionic. 

It was available under [apps.ionic.io](https://apps.ionic.io) and its documentation on [docs.ionic.io](http://docs.ionic.io/). Ionic Cloud contained the services:

* _Ionic View_ app
* _Ionic Deploy_: Live Updates
* _Ionic Package_: Native Builds
* _Ionic Auth_
* _Ionic Push_
* Organization support in the dashboard 
* and an HTTP API. 

Via the Ionic CLI command `ionic upload` developers could upload there apps' code to the online service that then offered to deploy it as updates (via Deploy) or build native apps with it (via Package).

During its lifetime Ionic Cloud also temporarily contained the _Ionic Analytics_ and _Ionic DB_ services, which were both shut down after shorter testing or beta periods.

In June 2017 Ionic announced they were replacing Ionic Cloud with a new service called _Ionic Pro_ and Ionic Cloud would no longer be available to existing Cloud users as of January 31st, 2018: [Ionic Blog post "Where we’re going with “Cloud”"](http://blog.ionicframework.com/where-were-going-with-cloud/). Ionic Package and the `ionic upload` command were replaced by a similarly named, but differently working service based on `git`.

Ionic Pro adopted most of the previously available services (and of course added new ones), but Ionic Cloud Push and Ionic Cloud Auth were sunset and not made available on the new service as announced in August 2017: [Ionic Blog post "Sunsetting Ionic Cloud Push and Auth"](http://blog.ionicframework.com/sunsetting-ionic-cloud-push-and-auth/). The reason was that it was hard to compete with the other great options out there and was not really a viable business that Ionic wanted to and could focus on.

