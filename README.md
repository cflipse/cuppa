# This is a demo and teaching tool

This repository is intended as a demonstration of using [ROM] in a Rails
application. Where possible, I'll be writing detailed commit messages; reading
the logs will _hopefully_ be instructive.

I also hope for this to be a usable application, for my own purposes.  Only
by actually using the application can you really expect to find out how well
it performs, and that will help inform whether or not some of the breakdowns
I'm planning will actually work well.

My writing and explanation on this is going to *assume familiarity* with
writing Ruby and Rails applications; I'm generally only going to talk through
the parts that deviate from usual Rails practice.

Assuming I can get my act together on the writing front, I'll also step along
with this on my blog; links when and if that happens.

[ROM]: https://rom-rb.org

## The Plan

I'm going to start with a monolithic Rails application using `rom-rails`
as it's data access solution, rather than `ActiveRecord`.  From there, I'll
look at running the application inside a docker container.

Later, I'm planning on breaking the app apart, replacing the Rails monolith
with a smaller number of services interacting in both HTTP api and in an
event-sourced paradigm.  The idea here is to demonstrate how ROM helps
decouple from data sources, and supports blending data from multiple sources.

## The application

I make coffee at home.  Not that K-Cup stuff; Real Coffee.  I grind fresh
beans on the spot, and (usually) use a Chemex pourover. Sometimes it's a french
press.

There are a lot of variables to tweak when you do this.  The fineness of the
grind, how hot the water is, water-to-bean ratio, duration of the bloom ...
heck, even the age of the beans is a factor.  I want to log these things,
and figure out how they impact the final cup.

Yes, I am an engineer, and I'm going to overanalyse the way I make coffee.
Nothing in that should be surprising.
