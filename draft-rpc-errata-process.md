---
stand_alone: true
ipr: trust200902
cat: info
submissiontype: IETF
wg: RSWG

docname: draft-rpc-errata-process-latest

title: Current Process for Handling RFC Errata Reports
abbrev: Handling Errata Reports
lang: en
keyword:
  - errata system
  - 
pi: [toc, sortrefs, symrefs]

author:
  ins: A. Russo
  name: Alice Russo
  org: RFC Production Center
  email: arusso@amsl.com
author:
  ins: S. Ginoza
  name: Sandy Ginoza
  org: RFC Production Center
  email: sginoza@amsl.com
author:
  ins: J. Mahoney
  name: Jean Mahoney
  org: RFC Production Center
  email: jmahoney@amsl.com
  
informative:
  RFC4844:
  ERRATA_PAGE:
    target: https://www.rfc-editor.org/errata.php
    title: RFC Errata
    author:
    - org: RFC Editor
  HOW_TO_REPORT:
    target: https://www.rfc-editor.org/how_to_report.html
    title: How to Report Errata
    author:
    - org: RFC Editor
  IESG-Err-Proc:
    target: https://www.ietf.org/about/groups/iesg/statements/processing-errata-ietf-stream/
    title: IESG Processing of RFC Errata for the IETF Stream
    author:
    - org: IESG

--- abstract

This document describes a web-based process for handling the
submission, verification, and posting of errata for the RFC Series.
The main concepts behind this process are (1) distributing the
responsibility for verification to the appropriate organization or
person for each RFC stream, and (2) using a Web portal to automate
the book-keeping for handling errata.

--- middle

#  Introduction

This document describes a new set of the procedures and mechanisms
for handling RFC errata, to improve efficiency and accountability of
errata processing.  The main concepts are (1) distributing
responsibility for errata verification to the appropriate body or
person for each RFC stream, and (2) using a Web portal to automate
the book-keeping task for verifying and posting errata.

The errata process assumes the organization of RFC publication into
four document streams {{RFC4844}}: (1) the IETF stream, which includes
both working group and individual submissions, (2) the IAB stream,
(3) the IRTF stream, and (4) the Independent Submission stream.  We
propose that personnel representing each stream be responsible for
verifying the errata reported for that stream's RFCs.  In particular,
we propose that one or more stream-specific parties (SSPs) be
designated with responsibility for verifying errata for each stream.

At the organizational level, the SSPs might be:

   *  IESG for IETF documents
   *  IAB for IAB documents
   *  IRSG for IRTF documents
   *  RFC Editor/Editorial Board for Independent Submissions

The IETF stream could be considered to be subdivided by area, so that
each Area Director could be an SSP for RFCs originating in that area.
The RFC publication process maintains the AD contact information for
each RFC, so errata reports for RFCs in the IETF document stream
could be sent to the appropriate ADs.

##  Background on RFC Errata

The RFC Editor began to collect and post RFC errata in 2000.  The
idea was to discourage readers from repeatedly pointing out the same
typos in published RFCs.  This evolved into the errata verification
and posting process described in Appendix B, which was a manually
operated, email-based task.

Unfortunately, our understanding of the errata problem was wrong in
several ways.  The number of errors reported turned out to be
significantly greater than anticipated, and the process of vetting
and posting required more human resources.

Another issue with errata is that some of the reported errors are not
simply editorial, but rather correct technical contents of RFCs.  A
savvy implementer of the specification can often, but not always,
figure out what was intended by the RFC as published, but technical
errors should be announced somehow.  Furthermore, posting technical
errata for Standards Track documents should always involve the IESG,
as a matter of correct process.  Technical errata may require much
review and discussion among the author(s), Area Directors, and other
interested parties.  (See {{HOW_TO_REPORT}} for guidelines regarding
editorial vs. technical classification.)

We note that allowing technical errata is a slippery slope: there may
be a temptation to use errata to "fix" protocol design errors, rather
than publishing new RFCs that update the erroneous documents.  In
general, an erratum is intended to report an error in a document,
rather than an error in the design of the protocol or other entity
defined in the document, but this distinction may be too imprecise to
avoid hard choices.  For the IETF stream, these choices should be
made by the IESG, and are discussed in their proposed guidelines on
errata processing {{IESG-Err-Proc}}.

In summary, errata have become a much larger, more complex, and more
important issue than they were originally.  This proposal attempts to
address these problems.

#  Proposed Errata Process Using the Web Portal

To manage and automate the reporting, verifying, and posting of
errata, the RFC Editor has transitioned to a Web application
("portal").  This Web portal allows for a more uniform reporting
process, eases communication among the parties responsible for
verification, and automates the posting of errata as soon as they are
reported.

There are four possible states for an erratum under this proposal:

   1.  Reported - The erratum has been reported but is unverified.
   2.  Verified - The erratum has been edited as necessary and verified.
   3.  Rejected - The erratum was redundant or incorrect and has been discarded.
   4.  Archived - The erratum is not a necessary update to the RFC. However, it should be considered in future revisions of the RFC. (Note that this state is not yet available; it is pending the IESG's statement regarding errata processing {{IESG-Err-Proc}}.)

Currently, Reported and Verified errata are posted (see Section 2.4
for more details).

For more information on the states and their definitions, and the
guidelines by which the IESG intends to classify errata into the the
above states, see {{IESG-Err-Proc}}.

The Web interface supports the following functions:

   1.  Retrieve -- display all posted errata for a specific RFC number or display a particular erratum by its errata ID number.
   2.  Report -- report a new erratum, as described below.  (See {{HOW_TO_REPORT}} for up-to-date instructions on reporting a new erratum.)
   3.  Edit/Verify/Reject -- used by an SSP to edit the contents of an erratum and change its state.

The following sections describe the proposed process in more detail.

##  Reporting Errata

A member of the Internet community (the "reporter") navigates to the
RFC errata page {{ERRATA_PAGE}} and enters the RFC number of the
document containing the error.  All earlier errata for that RFC are
displayed, and the reporter is asked to check that the erratum does
not already appear in the full list of errata for any given RFC.
This should help prevent multiple reports of the same error.

The user then reports the erratum using a Web form to create a report
record in the RFC errata database.  The report is composed of
information provided by the reporter, and is supplemented by data
drawn from the primary RFC Editor database.  The erratum report
record includes the following fields:

This information is requested from the reporter:

   * RFC #
   * Type: editorial, technical
   * Reporter name
   * Reporter email address (Note that the address is provided for communication purposes with the relevant SSPs and authors, but it is not displayed in the online errata report.)
   * Section #
   * Original text
   * Corrected text
   * Notes

The above information is supplemented by information pulled from the
database:

   * Errata ID number
   * RFC title and associated draft string (if available)
   * Publication Date
   * Author(s)
   * Category ("status") of RFC
   * Source (Working Group Name, IAB, IRTF, or INDEPENDENT)
   * Area (for IETF stream)
   * Stream (IETF, IAB, IRTF, or INDEPENDENT)
   * Verifying Party (SSP Identity)
   * URL to the distinct erratum report

Generally, we want the reporter to enter a new erratum using the
Original and Corrected Text fields, as this allows for easier
verification.  The free-text Notes field can be used for providing
rationale or for describing those errata that cannot easily be put
into the Original/Corrected format.

The Report page allows a set number of reports (i.e., 4) for the same
RFC to be submitted at the same time, using the Original/Corrected
form.  By having the user separate the errata entries, the SSP should
have an easier time verifying each entry.  We also hope that this
encourages users to submit only the most valuable errata.

The reporter is asked to make a judgment on the errata type --
technical vs. editorial.  If the reporter has both editorial and
technical errors in the same RFC, the two classes of errata must be
entered as separate reports.  This initial classification is useful
to the SSP; for example, it might allow technical errata to be
processed with higher priority than editorial errata, and it allows
the RFC Editor to monitor editorial errata to note frequent editorial
errors that could possibly lead to improvements in the editorial
process.

We expect that the reporter will usually make the right technical/
editorial classification, with the aid of published guidelines (see
{{HOW_TO_REPORT}}).  However, in case of misclassification by the
reporter, the SSP can fix it when logged in as a verifier.

##  Initial Notification Message

Submitting the report triggers an email notification message to the
appropriate SSP, the RFC author(s), and the RFC Editor.  Including
them all as addressees in one message facilitates cooperation in
verifying the error.

The message includes the information listed in Section 2.1.  The SSP
could forward the notification email further; for example, an Area
Director might forward it to the chair of the responsible working
group, if it still exists.

In the case of early RFCs for which the RFC Editor does not have
associated stream or area information, the reports will be sent to
the IESG (as a whole) and the authors.

Author email addresses are often out of date.  In these cases, the
relevant SSPs have the option of seeking current author contact
information or relying on other individuals with knowledge of the
subject matter to help determine the validity of the errata.

##  Verifying Errata

The initial notification message starts the verification process.
The SSP and the authors are expected to determine the validity of the
reported erratum, by whatever procedure the SSP or the stream owner
determines.  The RFC Editor does not intend to (normally) track the
verification process.  The SSP, not the author(s) or the RFC Editor,
has final responsibility for verifying or rejecting each report.
This helps to avoid a great deal of complexity and confusion.

Each SSP has a login account on the errata portal to edit errata
records as necessary.  The SSP identity is added to the record and
the individual is able to edit, verify, or reject each erratum.

The Notes field allows users to submit information in any fashion
they like, so there is a possibility of multiple errors being
reported in this field.  The SSP is able to edit the record and split
it into multiple records to maintain one record per erratum, as
necessary.

Based on experience, we know that some errata reports will require
significant email discussion between the reporter and the author(s)
and/or SSPs (in particular, the IESG) before the final decision on a
record can be made.  The final outcome will be captured in the errata
entry, and any controversy or explanatory material can be recorded in
the Notes field.

##  Posting Errata

As soon as an erratum is submitted, it is available online, i.e., it
is posted as described below.  The erratum entry is marked Reported
until its state is updated by verifiers as described above.

In this document, posting an erratum means that it is:

   1.  Available from the RFC errata page: http://www.rfc-editor.org/errata.php.
   2.  Linked to from the results of the RFC search engine: http://www.rfc-editor.org/rfcsearch.html.
   3.  Linked to from some HTML versions of the RFC.  For example, see http://tools.ietf.org/html/rfc2119.

The state of errata determines whether they are posted.  Currently,
Reported and Verified errata are posted, and Rejected errata are not
posted.  However, this can be altered to improve the errata display
for readers and implementers.  For example, Rejected and Archived
errata could be hidden behind a link (as has been suggested).

The order in which errata are displayed for a single RFC (e.g.,
Verified Technical, Reported Technical, Verified Editorial, Reported
Editorial) also can be altered to improve the usability.

It sometimes happens that there are errata for errata, i.e., earlier
postings must be altered.  In this case, the RFC Editor can do the
update as requested by an SSP or can grant an SSP temporary write
access to the record to be updated.

There are other possibilities for errata posting that should be
considered by the community; see Appendix A.

##  Errata Announcements

The RFC Editor proposes to announce verified technical errata
postings to the rfc-distribution list.  If the SSP felt the errata
was important enough, they might want to submit a note to the ietf-
announce list.  However, we do not believe it is necessary to
inundate the ietf-announce list with mail each time an errata is
verified, rejected, or edited.

#  Role of the RFC Editor

The role of the RFC Editor in errata processing is to:

   1.  Operate the Web portal.
   2.  Maintain the errata database.
   3.  Make changes in previously posted errata at the request of the corresponding SSP, or give the SSP temporary write access to the record.
   4.  Act as SSP for Independent Submissions.
   5.  Send periodic nudge messages to SSPs for errata that are in the Reported state.
   6.  Track SSP and community requests for various features that will make the job of reporting and verifying errata more efficient.

#  Transition

Errata from the original errata page have been made available from
the new Web portal.  Generally, they are marked Verified without
listing the name of the verifier, as this information was not
associated with the errata records until November 2007.

Errata that were posted in the pending file (as described in
Appendix B) have been made available from the Web portal and are
marked as Reported or Verified, as appropriate.  Lists of unverified
reports have been sent to the appropriate SSPs for review and
verification.

#  Security Considerations

It is necessary to have access control for errata reports.  A
logged-in SSP is able to edit, verify, or reject any errata report on
an RFC that is the product of their stream.  However, we propose that
once the SSP has submitted an erratum's final state (Verified or
Rejected) and the record entry has been committed to the errata
database, the SSP will lose write access to it.  This is a safety
feature to prevent inadvertent or malicious changes to the database,
even if the passwords for some SSP logins may become fairly widely
known.  However, the RFC Editor will always have write access to
posted entries and can make later changes if necessary.

The RFC Editor has chosen to use HTTPS as a reasonably secure login
mechanism.  Also, the RFC Editor has obtained a signed certificate
from a CA for the errata verification pages, so that SSPs have
confidence that they are logging into the RFC Editor site.

#  IANA Considerations

There are no IANA considerations for this document.

--- back

# Possibilities for Posting Errata

   Choosing any of these possibilities for posting errata should be
   decided by the IETF community and its governing bodies.

   1.  Brian Carpenter has suggested an approach similar to that used by W3C: Add a URL to every published RFC that points to its errata (if any). For W3C examples, see: http://www.w3.org/TR/2004/REC-xmlschema-2-20041028/ and http://www.w3.org/TR/2006/REC-xml-names-20060816, which include the text:

            "Please refer to the <errata> for this document, which may
             include some normative corrections."

         where \<errata\> is a hyperlink to the list of all errata or a
         page that says:

            "There are no errata to this document yet."

       Similarly, a URL could be added to all (future) RFCs pointing to
       where the relevant errata are posted.

   2.  Another possibility would be to add new errata files to the RFC repository, e.g., with names of the form: rfcnnnn.err.txt.  Such a file would contain all the errata for the corresponding RFC.
   3.  As mentioned in Section 2.4, there are HTML versions of RFCs with errata links; these are currently hosted by tools.ietf.org, but they could be made available on the RFC Editor Web site as well.

# Errata Processing before the Web Portal

The following is a summary of the RFC Editor errata verification and
posting process prior to the deployment of the Web portal in November
2007.  The RFC Editor used to:

   *  Review email and relevant RFCs to ensure that the reported errata actually appeared in the RFCs as available from http://www.rfc-editor.org/.  This does not mean that the errata were reviewed and deemed correct, only that the reported erronous text appears in the RFC (i.e., without judgment about the reports correctness).
   *  Disentangle multiple errors reported in one message.
   *  Check that each error has not already been posted.
   *  Attempt to determine whether the errata are editorial or technical.
   *  Forward each erratum report to the author(s) of the published RFC.
   *  Track bounce messages (contact information for authors is often out of date) and try to find current contact information.
   *  Forward the message to the relevant ADs if we were unable to find current author contact information.
   *  Track follow-up email.
   *  Figure out how to post when reporters/authors do not submit errata in the original/new format.  This is often a problem when reporters submit email claiming an error, but do not offer corrective text.
   *  Post verified errata and discard rejected errata.

   There were three possible states for processing an erratum:

   1.  Reported - the erratum has been reported but is unverified.
   2.  Verified - the erratum has been edited as necessary and verified.
   3.  Rejected - the erratum was redundant or incorrect and has been discarded.

Generally speaking, an erratum was posted when it was verified.
(Note that "posted" here means available online from the original RFC
errata page; the list of posting locations in Section 2.4 includes
those developed after 2000.)  The exceptions were the "pending
errata", whose processing was delayed as described below.

During 2006, the RFC Editor was understaffed for the growing load of
RFCs to be published (see
http://www.rfc-editor.org/num_rfc_year.html).  To catch up, the RFC
Editor suspended all activities not directly related to RFC
publication.  As a result, more than a year's worth of errata reports
had not been verified or posted.  As resources allowed, the RFC
Editor provided the following interim measures:

   1.  Made available, from the RFC Editor Web site, a mailbox text file (mbox format) of all errata-related email (ftp:// ftp.rfc-editor.org/in-notes/pending-errata/pending-errata.msgs).
   2.  For those few errata that did get added to the errata database, marked them UNVERIFIED.
