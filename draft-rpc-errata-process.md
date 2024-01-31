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

pi: [toc, sortrefs, symrefs]

author:
  -
    ins: A. Russo
    name: Alice Russo
    org: RFC Production Center
    email: arusso@amsl.com
  -
    ins: S. Ginoza
    name: Sandy Ginoza
    org: RFC Production Center
    email: sginoza@amsl.com
  -
    ins: J. Mahoney
    name: Jean Mahoney
    org: RFC Production Center
    email: jmahoney@amsl.com

informative:
  RFC8729:
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
  ERRATA_SYS_PROPOSAL:
    target: https://datatracker.ietf.org/doc/draft-rfc-editor-errata-process/
    title: RFC Editor Proposal for Handling RFC Errata
    author:
    - org: RFC Editor

--- abstract

This document describes the current web-based process for handling the
submission, verification, and posting of errata for the RFC Series.
The main concepts behind this process are (1) distributing the
responsibility for verification to the appropriate organization or
person for each RFC stream, and (2) using a Web portal to automate
the processing of erratum reports. This system was launched in November 2007.

--- middle

#  Introduction {#introduction}

This document describes the procedures and mechanisms
for handling RFC erratum reports.  The main concepts are (1) distributing
responsibility for report verification to the appropriate body or
person for each RFC stream, and (2) using a Web portal to automate
the tasks for verifying and posting erratum reports.

This process assumes the organization of RFC publication into
five document streams {{RFC8729}}: (1) the IETF Stream, which includes
both working group and individual submissions plus all RFCs that were
published before the concept of streams existed (known as legacy RFCs), (2) the IAB Stream,
(3) the IRTF Stream, (4) the Independent Submission Stream, and
(5) the Editorial Stream.
Personnel representing each stream, called the stream-specific party (SSP), are responsible for
verifying the erratum reports for that stream's RFCs.

At the organizational level, the SSPs are:

   *  IESG for legacy RFCs
   *  The Area Directors for RFCs that originated in one of that area's working groups
   *  IAB for IAB Stream documents
   *  IRSG for IRTF Stream documents
   *  Independent Submissions Editor for Independent Submission Stream documents
   *  RFC Series Approval Board for Editorial Stream documents
   *  RFC Production Center for all editorial erratum reports

##  Background on RFC Errata {#background}

The RFC Production Center (RPC) began to collect and post RFC errata in 2000.  The
idea was to discourage readers from repeatedly pointing out the same
typos in published RFCs.  This evolved into an errata verification
and posting process that was a manually operated, email-based task.
Errata from this period have been made available in the current system
and marked as Reported or Verified, as appropriate. Generally,
the name of the verifier is not given as this information was not
associated with errata records until the new system was put in
place.

Because the number of errors reported turned out to be significantly
greater than anticipated, and the process of vetting
and posting required more human resources, a web-based process {{ERRATA_SYS_PROPOSAL}} was created
and launched in November 2007.

Another reason for the current, web-based approach to handling erratum reports
is that about half the reports are not
simply editorial, but rather apply to the technical contents of RFCs.  A
savvy implementer of the specification can often, but not always,
determine what was intended by the RFC as published, but technical
errors should be announced somehow.  Furthermore, the posting of technical
errata for Standards Track documents should always involve the IESG,
as a matter of correct process.  Technical errata may require much
review and discussion among the author(s), Area Directors, and other
interested parties.  (See {{HOW_TO_REPORT}} for guidelines regarding
editorial vs. technical classification.)

We note that allowing technical errata is a slippery slope: there may
be a temptation to use errata to "fix" protocol design errors, rather
than to publish new RFCs that update the erroneous documents.  In
general, an erratum is intended to report an error in a document,
rather than an error in the design of the protocol or other entity
defined in the document, but this distinction may be too imprecise to
avoid hard choices.  For the IETF Stream, these choices are
made by the IESG and are discussed in their guidelines on
errata processing {{IESG-Err-Proc}}.

#  Current Errata Process Using the Web Portal {#current-process}

To manage and automate the reporting, verifying, and posting of
errata, the rfc-editor.org website provides a web application
("portal").  This web portal allows for a more uniform reporting
process, eases communication among the parties responsible for
verification, and automates the posting of erratum reports as soon as they are
reported.

There are four possible states for an erratum report:

   1.  Reported - The erratum has been reported but is unverified.
   2.  Verified - The erratum has been edited as necessary and verified.
   3.  Rejected - The erratum was redundant or incorrect and has been discarded.
   4.  Held for Document Update - The erratum is not a necessary update to the RFC. However, it should be considered in future revisions of the RFC.

Currently, reports in all states are posted (see {{posting-erratum-reports}}
for more details).

For more information on the states and their definitions, and the
guidelines by which the IESG classifies erratum reports into the
above states, see {{IESG-Err-Proc}}.

The Web interface supports the following functions:

   1.  Retrieve -- display all posted errata for a specific RFC number or display a particular erratum by its errata ID number.
   2.  Report -- report a new erratum, as described below.  (See {{HOW_TO_REPORT}} for instructions on reporting a new erratum.)
   3.  Edit/Verify/Reject -- used by an SSP to edit the contents of an erratum and change its state.

The following sections describe the process in more detail.

##  Reporting Errata {#reporting-errata}

A member of the Internet community (the "reporter") navigates to the
RFC errata page {{ERRATA_PAGE}}, enters the RFC number of the
document containing the error, and clicks the Search button.
All earlier erratum reports for that RFC are
displayed. These reports include verified errata, reported errata,
issues that are held for document update, and rejected reports.
The reporter is asked to check that the erratum does
not already appear on the errata page for any given RFC.
This step is to prevent multiple reports of the same error.

The reporter then reports the erratum using a Web form to create a report
record in the RFC errata database.  The report is composed of
information provided by the reporter and is supplemented by data
drawn from the primary rfc-editor.org database.  The erratum report
record includes the following fields:

The following information is requested from the reporter. All fields must be filled in:

   * Reporter name
   * Reporter email address (Note that the address is provided for communication purposes with the relevant SSPs and authors, but it is not displayed in the online erratum report.)
   * Publication format: Text, PDF, HTML
   * Type: editorial, technical
   * Section #
   * Original text
   * Corrected text
   * Notes

The reporter is asked to make a judgment on the erratum type --
technical vs. editorial.  If the reporter has both editorial and
technical errors in the same RFC, the two classes of errata must be
entered as separate reports.  This initial classification is useful
to the SSP; for example, it might allow technical errata to be
processed with higher priority than editorial errata, and it allows
the RPC to verify editorial erratum reports and to note frequent editorial
errors that could possibly lead to improvements in the editorial
process.

With the aid of published guidelines (see
{{HOW_TO_REPORT}}), the reporter should make the right technical/editorial
classification.  However, if the reporter does misclassify the
report, the SSP can fix the classification when logged in as a verifier.

The reporter should enter a new erratum using the
Original and Corrected Text fields, as this allows for easier
verification.  The reporter can use the free-text Notes field to provide
the rationale or to describe those errata that cannot easily be put
into the Original/Corrected format.

When the reporter submits the report, they are shown a preview of it.
They can choose to edit the report, cancel, or submit. They must successfully
navigate a reCAPTCHA in order to complete the report submission.

The information provided by the reporter is supplemented by information pulled from the
database:

   * Errata ID number
   * RFC title and associated draft string (if available)
   * Publication Date
   * Author(s)
   * Category ("status") of RFC
   * Source (Working Group Name, IAB, IRTF, or INDEPENDENT)
   * Area (for IETF Stream)
   * Stream (IETF, IAB, IRTF, or INDEPENDENT)
   * Verifying Party (SSP Identity)
   * URL to the distinct erratum report

When a report is successfully submitted, a notification is sent via email
(see {{initial-notification-message}}), and the report is posted to the rfc-editor.org website
(see {{posting-erratum-reports}}).

##  Initial Notification Message {#initial-notification-message}

Submitting the report triggers an email notification message to
multiple parties; see the notification lists below.  Including
multiple parties facilitates cooperation in
verifying the error and transparency in the process.

Notifications are determined by stream and type of erratum report
and are sent by rfc-editor@rfc-editor.org to the following SSPs.

Note that while SSP email addresses are maintained by the
database, author email addresses, especially for older RFCs,
are often out of date. In these cases, the
SSP has the option of seeking current author contact
information or relying on other individuals with knowledge of the
subject matter to help determine the validity of the erratum report.

### Technical Erratum Reports

Technical erratum reports are sent to SSPs, and the reporter and
rfc-editor@rfc-editor.org are CCed.

Legacy RFCs:

* To: IESG
* CC: reporter, rfc-editor@rfc-editor.org

IETF Stream:

* To: authors, ADs of the area from which the document came, document shepherd
* CC: reporter, working group, rfc-editor@rfc-editor.org

IAB Stream:

* To: authors, IAB
* CC: reporter, rfc-editor@rfc-editor.org

IRTF Stream:

* To: authors, IRSG, research group
* CC: reporter, rfc-editor@rfc-editor.org

Independent Submission Stream:

* To: authors, ISE
* CC: reporter, rfc-editor@rfc-editor.org

Editorial Stream:

* To: authors, RSAB
* CC: reporter, rfc-editor@rfc-editor.org

### Editorial Erratum Reports

All editorial erratum reports are sent to rfc-editor@rfc-editor.org,
and other SSPs are CCed:

Legacy RFCs:

* To: rfc-editor@rfc-editor.org
* CC: reporter

IETF Stream:

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors, working group

IAB Stream:

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors, IAB

IRTF Stream:

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors

Independent Submission Stream:

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors

Editorial Stream:

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors

The message includes the information listed in {{reporting-errata}}.

##  Posting Erratum Reports {#posting-erratum-reports}

As soon as an erratum is submitted, it is available online
as described below.  The erratum entry is marked Reported
until its state is updated by verifiers as described in {{verifying-erratum-reports}}.
Duplicate and junk reports are available and marked as Reported
only until they are deleted from the database by the RPC.

In this document, posting an erratum means that:

   *  The report can be discovered through the RFC errata search page: <https://www.rfc-editor.org/errata.php>.
   *  A link to the RFC's errata page appears on the following:
      * the results of the RFC search engine: <https://www.rfc-editor.org/rfcsearch.html>.
      * the RFC's info page. For example, see <https://www.rfc-editor.org/info/rfc2119>.
      * On the HTML format of the RFC. For example, <https://www.rfc-editor.org/rfc/rfc2119.html>.

All erratum reports for a single RFC, except for obvious spam reports,
are posted in the following order:

* Verified Technical
* Verified Editorial
* Held for Document Update Technical
* Held for Document Update Editorial
* Rejected Technical
* Rejected Editorial
* Reported Technical
* Reported Editorial

All erratum reports are also available at <https://www.rfc-editor.org/errata.json>.

##  Verifying Erratum Reports {#verifying-erratum-reports}

The initial notification message starts the verification process.

The RPC determines the validity of editorial erratum reports and also
handles any junk or duplicate reports, whether they are labeled as editorial
or technical.

Junk erratum reports contain bogus content in the Original text, Corrected text,
and/or Notes fields. The RPC deletes
such a report from the database and sends an email message to
all recipients of the report notification, except for the reporter,
notifying them that the report has been deleted.

If an erratum report duplicates an existing report, the RPC
deletes the report and sends a reply-all to the notification message
to say the report has been deleted.

The SSP and the authors are expected to determine the validity of
any technical erratum report, by whatever procedure the SSP or the stream owner
determines.

The RPC does not track the
verification process for technical erratum reports.  The SSP, not the author(s) or the RPC,
has final responsibility for verifying or rejecting each technical erratum report.
This helps to avoid a great deal of complexity and confusion.

Each SSP has a login account on the errata portal to edit and verify erratum
reports.  The SSP identity is added to the record and
the individual is able to edit, verify, or reject each erratum.

The Notes field allows reporters to submit information in any fashion
they like, so there is a possibility of multiple errors being
reported in this field.  The SSP is able to split
the report into multiple records to maintain one record per erratum report, as
necessary.

Some erratum reports require
significant email discussion between the reporter and the author(s)
and/or SSPs (in particular, the IESG) before the final decision on a
report can be made.  The final outcome is captured in the erratum
entry, and any controversy or explanatory material is recorded in
the Notes field.

It sometimes happens that there are errata for errata, i.e., earlier
postings must be altered.  In this case, the RFC Editor can
update the report as requested by an SSP or can grant an SSP temporary write
access to the record to be updated.

Once verified, the erratum is available for viewing in the RFC's HTML format "inline" (for example, see <https://www.rfc-editor.org/rfc/inline-errata/rfc3261.html>) in addition to being on the RFC's errata page and discoverable through errata search functionality.

##  Erratum Report Announcements {#erratum-report-announcements}

Like the notification of submissions, the announcement of a verified erratum report varies by stream:

Notifications are determined by stream and type of erratum report.

### Technical Erratum Reports

The announcement of verified technical erratum reports are sent from rfc-editor@rfc-editor.org to the following:

Legacy RFCs:

* To: reporter, authors
* CC: AD who verified the report, IESG, rfc-editor@rfc-editor.org

IETF Stream:

* To: reporter, authors
* CC: AD who verified the report, IESG, working group, IANA, rfc-editor@rfc-editor.org

IAB Stream:

* To: reporter, authors
* CC: IAB, IAB chair, rfc-editor@rfc-editor.org

IRTF Stream:

* To: reporter, authors
* CC: verifier from IRSG, IRSG, research group, IANA, rfc-editor@rfc-editor.org

Independent Submission Stream:

* To: reporter, authors
* CC: ISE, Document Shepherd, IANA, rfc-editor@rfc-editor.org

Editorial Stream:

* To: reporter, authors
* CC: RSAB, RSWG, IANA, rfc-editor@rfc-editor.org

### Editorial Erratum Reports

The announcement of verified editorial erratum reports are sent from rfc-editor@rfc-editor.org to the following:

Legacy RFCs:

* To: reporter, author
* CC: rfc-ed@rfc-editor.org, IESG, IANA

IETF Stream:

* To: reporter, authors
* CC: rfc-ed@rfc-editor.org, IESG, working group, IANA

IAB Stream:

* To: reporter, authors
* CC: rfc-ed@rfc-editor.org, IAB, IAB chair

IRTF Stream:

* To: reporter, authors
* CC: rfc-ed@rfc-editor.org, IRSG, research group, IANA

Independent Submission Stream:

* To: reporter, authors
* CC: rfc-ed@rfc-editor.org, ISE, IANA

Editorial Stream:

* To: reporter, authors
* CC: RSAB, RSWG, IANA, rfc-ed@rfc-editor.org

#  Role of the RPC {#rpc-role}

The role of the RPC in errata processing is to:

   1.  Operate the Web portal.
   2.  Maintain the errata database.
   3.  Make changes in previously posted errata at the request of the corresponding SSP, or give the SSP temporary write access to the record.
   4.  Act as SSP for editorial erratum reports.
   5.  Remove junk and duplicate reports.
   6.  Track SSP and community requests for various features that will make the job of reporting and verifying errata more efficient.

#  Security Considerations {#security-considerations}

It is necessary to have access control in order to process erratum reports.  A
logged-in SSP is able to edit, verify, or reject any erratum report on
an RFC that is the product of their stream.
Once the SSP has submitted an erratum's final state (Verified or
Rejected) and the record entry has been committed to the erratum
database, the SSP loses write access to it.  This is
to prevent inadvertent or malicious changes to the database,
even if the passwords for some SSP logins may become fairly widely
known.  However, the RPC will always have write access to
posted entries and can make later changes if necessary.

The portal uses HTTPS as a reasonably secure login
mechanism.  Also, the rfc-editor.org website has a signed certificate
from a CA, so that SSPs have
confidence that they are logging into the rfc-editor.org website.

#  IANA Considerations

This document has no IANA actions.

--- back
