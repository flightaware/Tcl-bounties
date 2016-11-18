# Tcl-bounties
Bounty program for improvements to Tcl and certain Tcl packages

This page outlines some changes or improvements that we want in Tcl and may be willing to pay somebody to implement.

## Support for SO_REUSEPORT on server sockets

* This would allow multiple programs to open the same port from a server socket.
* It's pretty easy.
* $2500

## Support for epoll()/kqueue() to replace select() in socket handling
* This could vastly reduce the overhead for Tcl programs that have thousands of sockets open.
* There was a google summer of code project to do this that never got integrated and might not have been completed but could be a starting point.
* $10,000

## Clean up of tcltls
* support all TLS versions.
* fix hangs in protocol negotiation.
* fix background errors to provide an error message.
* test and get it working with LibreSSL -- drop SSLv2, SSLv3, etc.
* plus light maintenance for a year
* $5,000

## Call-by-name syntactic sugar for proc definitions that would obviate most uses of upvar
* something like... proc find_flightplan_from_position {*flightplan *position}  {}
* ...that would replace proc find_flightplan_from_position {_flightplan position} ... upvar $flightplan flightplan $_position position, etc
* $10,000

## Speed up clock format and clock scan
* 2X for $5,000
* 4X for $10,000
* 10X for $20,000
* Revive the Tcl Pro debugger
* $20,000

## Make TclX's signal trap handlers safe to use with threaded Tcl
* currently they are prone to deadlock as the signal can be delivered to the select thread and this will self-deadlock if it happens at the wrong time
* this will need Tcl core changes to support it
* $5,000

## Make TclX's profiler work properly with Tcl 8.6 (currently it crashes Tcl)
* $2,500

## Stop Tcl from eating child process exit status gratuitously
* currently if you want to retrieve child status for subprocesses yourself asynchronously, there are a bunch of things you must avoid, including "open |foo" even if it's a completely unrelated child
* Tcl core should either not call waitpid for children it is not directly managing, or it should have a mechanism for preserving the return statuses it consumes via waitpid so the app can retrieve them when needed
* this makes any non-trivial communication scheme with subprocesses painful (see piaware's fa_sudo to see the lengths you must go to, and then everything must use that and avoid the core pipe functionality)
* $5,000

## Look through TIP proposals and see if there are any we want to push on
* A reasonable C API for enumerating an array
* $5,000

## "after -at" or some other way to set a point in time when something is to occur rather than a delay time
* $2,500

## Default values for arrays "array default arrayName value", causes that value to be returned any time an attempt is made to access an element of the array that isn't present.
* $2,500

## "array foreach"
* $2,500

## A more legit way to get a list of all the source files loaded by a package.
* $2,500

## A first class, high-performance, non-hackish way to do named parameters
* $20,000

# Rules for Tcl bounties
* All code must be released under the BSD license.
* For bounties under $10,000, the bounty will be paid when the code is accepted into the Tcl core, or if not part of the core, accepted by the package maintainer.
* For bounties $10,000 and over, we’ll pay 50% of the bounty will be paid out when the code is accepted into the Tcl core and the remaining 50% when it appears in a release of Tcl.
* The first person or team to succeed wins the bounty.
* If you succeed in fulfilling the conditions for receiving a bounty as a team then the team has to apportion the bounty among themselves; we are not getting involved in any disputes over who deserves what.
* We request that people or teams publicly announce their intention to pursue a bounty to reduce the likelihood of wasted work, hard feelings, etc.
 * That being said we understand that some people or teams may announce and not succeed, so the fact that someone has announced they are pursuing a bounty does not prevent others from pursuing it as well.


