# pwrdown
 Power down facility, to power down the local system if another/remote host goes offline.

 This utility is useful in cases, like mine, you have a local (LAN) unmanaged Linux server which you start (manually or, like me, by using Wake On LAN) when a client system goes up and then, when the same client system shuts down, you want your server to automatically follow (in a few).
 
 There is a "double check", before the server really shuts down: this is made to avoid having "early shutdowns" in case of (1) temporary LAN disconnection of the server and/or the "reference" client, (2) to suit the need, sometimes, to keep the server up, when just starting alone or after a client's shutdown: in such cases you should have the time to access server's console and stop the automation by issuing a command.

*(excerpt from manpage)*
 This system utility will do a check every 5 minutes (accordingly to configuration's default, if unchanged) and, if the remote reference host is found inactive, even the local host will be shut down.
 Options/commands are provided to temporarily or completely stop the automated checks and to see the automation's status, plus a couple of shutdown's related utilities.
 Read the full documentation for further and technical details.

**OPTIONS**

*no option*
    Via Cron automated checks (see /etc/cron.d/pwrdown): after the second check, if the remote system doesn't answer, the local one is shut down.
    Via command line: checks are forced, same behavior as via Cron but without the usual delays (good for testing).

*-a, --auto*
    Automatic processing restored, cleaning the global semaphore PWRDOWN_NO (see --noauto).

*-f, --pwrdown*
    Forces an immediate shutdown/poweroff, same as "shutdown -h now".

*-r, --reboot*
    Forces an immediate reboot, same as "shutdown -r now".

*-s, --noauto*
    Stops the automatic processing, setting the global semaphore PWRDOWN_NO which remains through sessions.

*-S, --status*
    Shows the current automation's status: short and global semaphores, and remote host status.

*-p, --postpone*
    If the first shutdown warning was received, the further shutdown action can be postponed for 5 mins (default) without completely stopping the automation.

*-n, --dry-run*
    Do the same as no option is given (automated process), but without really shutting the system down.

*--playtest1*
    play the system-alive sounds only (test purposes)

*--playtest2*
    play the warning sounds only (test purposes)

*--playtest3*
    play the shutdown sounds only (test purposes)

*-h, --help*
    Display a short help and exits.

*-V, --version*
    Display program's version, build, author, license and exits.
