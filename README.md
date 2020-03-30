**Due to the impact of the coronavirus, FlightAware's Tcl Bounty program is temporarily on hold until the business climate has stabilized.**

# Tcl-bounties
Bounty program for improvements to Tcl and certain Tcl packages.

FlightAware is offering a number of bounties for various enhancements, fixes, etc, for Tcl and/or Tcl extensions.

Bounties we are offering run to tens of thousands of dollars.

## ~~Upgrade the scotty extension~~

* ~~$1000 to update Scotty to modern Tcl Extension Architecture (TEA) build standards, compilling properly under FreeBSD, Debian and macOS, with stub support.~~

Status: bounty conditions met by @jorge-leon **PAID**

* ~~$1000 to fix bugs in Scotty's UDP stuff -- "configure/cget" of config vars working and configured host and port to be used if not specified in "send".~~

Status: bounty conditions met by @jorge-leon **PAID**

## ~~Support for SO_REUSEPORT on server sockets~~

* ~~This would allow multiple programs to open the same port from a server socket.~~
* ~~It would be a switch to the socket command.~~
* ~~It looks pretty easy.~~
* ~~$2500~~

Status:  Bounty conditions met by lemonboy... **PAID**

## ~~tclreadline improvements~~

* ~~$2500 to make tclreadline able to recognize iTcl and tclOO objects and do tab completion for method names, tab completion for variables if indicated by the present of cget or configure~~

Status: Bounty conditions met by dbohdan, pull request https://github.com/flightaware/tclreadline/pull/1.  **PAID**

## ~~Support for epoll()/kqueue() to replace select() in socket handling~~

* ~~This could considerably reduce the overhead for Tcl programs that have thousands of sockets open.~~
* ~~There was a Google Summer of Code project to do this that never got integrated and might not have been completed but could be a starting point.~~
* ~~$10,000~~

Status: Bounty conditions met by lalbornoz, implementation in trunk. **PAID**

## ~~Clean up of tcltls~~
* ~~support all TLS versions.~~
* ~~fix hangs in protocol negotiation.~~
* ~~fix background errors to provide an error message.~~
* ~~test and get it working with LibreSSL -- drop SSLv2, SSLv3, etc.~~
* ~~plus light maintenance for a year~~
* ~~$5,000~~

Status: Bounty conditions met by rkeene.  **PAID**

## Call-by-name syntactic sugar for proc definitions that would obviate most uses of upvar
* something like... proc find_flightplan_from_position {*flightplan *position}  {}
* ...that would replace proc find_flightplan_from_position {_flightplan position} ... upvar $flightplan flightplan $_position position, etc
* (To be implemented as a first class thing in the Tcl code, not some proc that generates a proc or something lame like that.)
* $10,000

Status: Part of http://www.tcl.tk/cgi-bin/tct/tip/457.html

## ~~Speed up clock format and clock scan~~
* 2X for $5,000
* 4X for $10,000
* 10X for $20,000

Complete by @sebres, waiting on core team to pick up. **PARTIALLY PAID**

## ~~Revive the Tcl Pro debugger~~
~~There was a Tcl Pro package from Scriptics many years ago that was open sourced.  Included was a source-level debugger.~~
* ~~Get the source-level debugger working again with Tcl 8.6 and accepted into the Tcl core~~
* ~~$20,000~~

Status: Completed by blacksqrl, **PAID**

## Make TclX's signal trap handlers safe to use with threaded Tcl
* currently they are prone to deadlock as the signal can be delivered to the select thread and this will self-deadlock if it happens at the wrong time
* this will need Tcl core changes to support it
* $5,000

~~## Make TclX's profiler work properly with Tcl 8.6~~
* ~~currently it crashes Tcl~~
* ~~this may need Tcl core changes to support it~~
* ~~$2,500~~

Status: complete by Rami Khaldi.

## ~~Stop Tcl from eating child process exit status gratuitously~~
* ~~currently if you want to retrieve child status for subprocesses yourself asynchronously, there are a bunch of things you must avoid, including "open |foo" even if it's a completely unrelated child~~
* ~~Tcl core should either not call waitpid for children it is not directly managing, or it should have a mechanism for preserving the return statuses it consumes via waitpid so the app can retrieve them when needed~~
* ~~this makes any non-trivial communication scheme with subprocesses painful (see piaware's fa_sudo to see the lengths you must go to, and then everything must use that and avoid the core pipe functionality)~~
* ~~$5,000~~

Status: Integrated into core, thank you Frédéric Bonnet.

## A reasonable C API for enumerating an array
* (without using any Tcl code, that is, no invoking Tcl_Eval or equivalent)
* $5,000

## "after -at"
* basically some other way to set a point in time when something is to occur rather than a delay time
* we're not married to it being "after -at"
* $2,500

## array default arrayName value
* Default values for arrays, "array default arrayName value", causes that value to be returned any time an attempt is made to access an element of the array that isn't present.
* $2,500

## ~~"array foreach"~~
* ~~this adds a new suboption to the array command, "array foreach varName {code}"~~
* ~~$2,500~~

Status: Bounty conditions met by Brad Lanam, paid.

## ~~Tcl package introspection improvements~~
* ~~A more legit way to get a list of all the source files loaded by a package.~~
* ~~"package files" or something~~
* ~~$2,500~~

Status: bounty conditions met by nijtmans

## ~~Named Parameters~~

Status: No longer part of the program.

## Tcl runtime performance improvements
* $20,000 for Tcl to run 2X faster than Tcl 8.6 for a benchmark program TBD.
* $100,000 for Tcl to run 10X faster than Tcl 8.6.
* (We need help with the benchmark.)

# Rules for Tcl bounties
* All code must be released under the BSD license.
* For bounties under $10,000, the bounty will be paid when the code is accepted into the Tcl core, or if not part of the core, accepted by the package maintainer.
* For bounties $10,000 and over, we’ll pay 50% of the bounty will be paid out when the code is accepted into the Tcl core and the remaining 50% when it appears in a release of Tcl.
* The first person or team to succeed wins the bounty.
* If you succeed in fulfilling the conditions for receiving a bounty as a team then the team has to apportion the bounty among themselves; we are not getting involved in any disputes over who deserves what.
* We request that people or teams publicly announce their intention to pursue a bounty to reduce the likelihood of wasted work, hard feelings, etc.
 * That being said we understand that some people or teams may announce and not succeed, so the fact that someone has announced they are pursuing a bounty does not prevent others from pursuing it as well.
* If due to the nature of their employment someone is not allowed to accept a bounty or their share of a bounty, they can assign their share to others on their team, to a charity of their choosing, or to the Tcl Community Association.
* FlightAware employees can participate but not double-dip; i.e. don't work on it at work.
* When appropriate, the [TIP](http://wiki.tcl.tk/983) process may need to be followed for changes that impact the public interfaces of Tcl core.
