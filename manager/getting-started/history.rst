Project History
===============

By `Lex Li`_

The first commit of Jexus Manager was made on March 19, 2014 in a private Git
repo. This project was designed to be the management console of Jexus web
server, which at that time lacks of an easy-to-use GUI tool.

One of the initial goals was to attract IIS users, so its look and feel is
almost the same as IIS Manager. This approach also led to the facts that
``Microsoft.Web.Administration`` API needs to be re-implemented. Mapping of all
Jexus settings (both server and site levels) was done, and soon the work
kicked off. Because Jexus only has a few settings, the needed features were
finished with the first release candidate released on April 20, 2014. The 1.0
release came on May 30, 2014, which enables Jexus web server remote and local
management.

Starting from May 10 2014, the project entered its second phase, trying to
fully support Microsoft IIS/IIS Express servers. Microsoft did not provide a
management console for IIS Express, so Jexus Manager can be a critical tool to
fill the gaps. However, the work on a fully functional
``Microsoft.Web.Administration`` implementation took very long. Although the
first 2.0 Alpha build was made available on November 16, 2014, it lacks of
many important features. The work on ``Microsoft.Web.Management`` started on
December 20, 2014, which soon enabled a redesign of all user interface
elements to match IIS Manager more closely. Refactoring in July 2015
moved it forward to a fast track. In November this tool was demonstrated
to some Microsoft guys. Scott Hanselman suggested it might be open sourced. On
January 16, 2015, Jexus Manager's ``Microsoft.Web.Administration``
implementation went public on GitHub. The entire Jexus Manager source code was
made available on June 25, 2015.

The 2.1 release candidates started to be available on July 11, 2017. On July
22, the 2.1 final release was shipped.

Due to a bug report (related to version number) in January 2018, Jexus Manager
version number was bumped, and 12.0.0.0 release was shipped on January 4, 2018.
