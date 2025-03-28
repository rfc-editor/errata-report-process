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
    email: arusso@staff.rfc-editor.org
  -
    ins: J. Mahoney
    name: Jean Mahoney
    org: RFC Production Center
    email: jmahoney@staff.rfc-editor.org

informative:
  RFC8729:
  ERRATA_PAGE:
    target: https://www.rfc-editor.org/errata.php
    title: RFC Errata
    author:
    - org: RFC Editor
    date: false
  HOW_TO_REPORT:
    target: https://www.rfc-editor.org/how_to_report.html
    title: How to Report Errata
    author:
    - org: RFC Editor
    date: false
  IESG-Err-Proc-2008:
    target: https://datatracker.ietf.org/doc/statement-iesg-iesg-processing-of-rfc-errata-for-the-ietf-stream-20080730/
    title: IESG Processing of RFC Errata for the IETF Stream
    author:
    - org: IESG
    date: 2008-07-30
  IESG-Err-Proc-2021:
    target: https://www.ietf.org/about/groups/iesg/statements/processing-errata-ietf-stream/
    title: IESG Processing of RFC Errata for the IETF Stream
    author:
    - org: IESG
    date: 2021-05-07
  ERRATA_SYS_PROPOSAL:
    target: https://datatracker.ietf.org/doc/draft-rfc-editor-errata-process/
    title: RFC Editor Proposal for Handling RFC Errata
    author:
    - org: RFC Editor
    date: 2008-05-20

--- abstract

This document describes the current web-based process for handling the
submission, verification, and posting of errata for the RFC Series.
The main concepts behind this process are (1) distributing the
responsibility for verification to the appropriate organization or
person for each RFC stream, and (2) using a Web portal to automate
the processing of erratum reports. This system was launched in November 2007.

This draft documents the existing system as a means to facilitate discussion to revamp how errata are reported, reviewed, and publicized.

--- middle

#  Introduction {#introduction}

This document describes the procedures and mechanisms
for handling RFC erratum reports.  The main concepts are (1) distributing
responsibility for report verification to the appropriate body or
person for each RFC stream, and (2) using a Web portal to automate
the tasks for verifying and posting erratum reports.

This process assumes the organization of RFC publication into
five document streams {{RFC8729}}: (1) the IETF Stream, which includes
both working group and individual submissions (also known as "AD Sponsored"
or "non-working group" documents) plus all RFCs that were
published before a formal source (e.g., working group or stream) existed or was recorded (known as legacy RFCs), (2) the IAB Stream,
(3) the IRTF Stream, (4) the Independent Submission Stream, and
(5) the Editorial Stream.
Personnel representing each stream, called the stream-specific party (SSP), are responsible for
verifying the erratum reports for that stream's RFCs.

At the organizational level, the SSPs are:

   *  IESG for legacy RFCs
   *  IESG for IETF Stream documents
   *  IAB for IAB Stream documents
   *  IRSG for IRTF Stream documents
   *  Independent Submissions Editor for Independent Submission Stream documents
   *  RFC Series Approval Board for Editorial Stream documents

In addition, the RFC Production Center reviews editorial errata reports from all streams and marks them as verified when possible, as per {{IESG-Err-Proc-2021}}.

##  Background on RFC Errata {#background}

The RFC Production Center (RPC) began to collect and post RFC errata in 2000. A 
[very early snapshot](https://web.archive.org/web/20001029084225/http://www.rfc-editor.org/errata.html)
can be seen at the Wayback Machine. The
idea was to discourage readers from repeatedly pointing out the same
typos in published RFCs.  Initially, errata were not separated into technical and
editorial errata. This classification started in 2002. This evolved into an errata verification
and posting process that was a manually operated, email-based task.
Errata were listed on one page and grouped by RFC number. See this
[snapshot from 2003](https://web.archive.org/web/20031202151009/http://www.rfc-editor.org/cgi-bin/errata.pl).
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
is that about half the reports apply to the technical contents of RFCs,
and the posting of technical
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
errata processing {{IESG-Err-Proc-2021}}.

After consulting with the RPC in 2021, the IESG requested that the RPC
perform the initial review of editorial errata reports (including the backlog of
openeditorial reports) and resolve those that are clearly editorial
in nature {{IESG-Err-Proc-2021}}. The other streams adopted the same processing
for editorial reports.

### The Creation of the 'Hold For Document Update' State

When errata reports started to be collected and posted, there were only two states:
Verified and Rejected.

The IESG proposed the "Held for Document Update" (HFDU) state in 2008. See {{IESG-Err-Proc-2008}}.
HFDU initially applied to the following:

* Things that are clearly wrong but could not cause an implementation or deployment problem
* Trivial grammar corrections
* Typographical errors which would not cause any confusions to implementation or deployments
* Changes which are simply stylistic issues or simply make things read better
* Changes that modify the working of a protocol to something that might be different from the
intended consensus when the document was approved should be either Hold for Document Update or
Rejected. Deciding between these two depends on judgment. In unclear situations, small changes
can be Hold for Document Update.

The application of HFDU changed when the IESG updated their guidelines in 2021 (see {{IESG-Err-Proc-2021}}).
The first three items above were moved from HFDU to Verified. Currently, HFDU applies to the following:

- Changes that are stylistic issues or simply make things read better
- Clearly wrong technical items that do not have a clear resolution or requires further discussion

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
above states, see {{IESG-Err-Proc-2021}}.

The Web interface supports the following functions:

   1.  Retrieve -- display all posted errata for a specific RFC number or display a particular erratum by its errata ID number.
   2.  Report -- report a new erratum, as described below.  (See {{HOW_TO_REPORT}} for instructions on reporting a new erratum.)
   3.  Edit/Verify/Reject -- used by an SSP to edit the contents of an erratum and change its status.

The following sections describe the process in more detail.

##  Reporting Errata {#reporting-errata}

A member of the Internet community (the "reporter") navigates to the
RFC errata page {{ERRATA_PAGE}}, enters the RFC number of the
document containing the error, and clicks the Search button.
All earlier erratum reports for that RFC are
displayed. This includes reports of any status (Verified, Reported,
Held for Document Update, and Rejected).
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
   * Publication format: Text, PDF, HTML (This field is present for only RFC 8650 and higher.)
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
   * Source (working group name, IETF - NON WORKING GROUP, IAB, IRTF, INDEPENDENT, or Editorial)
   * Area (for IETF Stream)
   * Stream (IETF, IAB, IRTF, INDEPENDENT, or Editorial)
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

IETF Stream (working group):

* To: authors, ADs of the area from which the document came, document shepherd
* CC: reporter, working group, rfc-editor@rfc-editor.org

IETF Stream (non-working group):

* To: IESG, authors
* CC: reporter, rfc-editor@rfc-editor.org

IAB Stream:

* To: authors, IAB
* CC: reporter, rfc-editor@rfc-editor.org

IRTF Stream:

* To: authors, IRSG
* CC: reporter, rfc-editor@rfc-editor.org, research group

Independent Submission Stream:

* To: authors, ISE
* CC: reporter, rfc-editor@rfc-editor.org

Editorial Stream:

* To: authors, RSAB
* CC: reporter, rfc-editor@rfc-editor.org, RSWG

### Editorial Erratum Reports

All editorial erratum reports are sent to rfc-editor@rfc-editor.org,
and other SSPs are CCed:

Legacy RFCs:

* To: rfc-editor@rfc-editor.org
* CC: reporter

IETF Stream (working group):

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors, working group

IETF Stream (non-working group):

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors

IAB Stream:

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors, IAB

IRTF Stream:

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors, research group

Independent Submission Stream:

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors

Editorial Stream:

* To: rfc-editor@rfc-editor.org
* CC: reporter, authors, RSWG

The message includes the information listed in {{reporting-errata}}.

##  Posting Erratum Reports {#posting-erratum-reports}

As soon as an erratum report is submitted, it is available online
as described below.  The erratum report is marked Reported
until its state is updated by verifiers as described in {{verifying-erratum-reports}}.
Duplicate and junk reports are available and marked as Reported
only until they are deleted from the database by the RPC.

In this document, posting an erratum report means that:

   *  The report can be discovered through the RFC errata search page: <https://www.rfc-editor.org/errata.php>.
   *  A link to the RFC's errata page appears on the following:
      * the results of the RFC search engine: <https://www.rfc-editor.org/rfcsearch.html>.
      * the RFC's info page. For example, see <https://www.rfc-editor.org/info/rfc2119>.
      * On the HTML format of the RFC. For example, <https://www.rfc-editor.org/rfc/rfc2119.html>.
      * On the datatracker status page for the RFC. For example, <https://datatracker.ietf.org/doc/rfc2119/>.
      The datatracker learns that at least one erratum report exists via <https://www.rfc-editor.org/rfc-index.xml>
      and sets a badge on the RFC's datatracker status page.

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
the individual is able to edit, verify, hold, or reject each erratum.

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

Once verified, the erratum is available for viewing in the RFC's HTML format "inline" (for example, see <https://www.rfc-editor.org/rfc/inline-errata/rfc3261.html>) in addition to being on the RFC's errata page and discoverable through errata search functionality.

In addition, once a report is verified, it is locked against further updates to ensure the stability of the report.
However, sometimes there are mistakes in the report that need correction.  In this case, the RFC Editor can
update the report as requested by an SSP or can grant an SSP temporary write
access to the report that needs to be updated.

##  Erratum Report Announcements {#erratum-report-announcements}

Like the notification of submissions, the announcement of a verified (or held or rejected) erratum report varies by stream and type of erratum report.

### Technical Erratum Reports

The announcement of technical erratum reports are sent from rfc-editor@rfc-editor.org to the following:

Legacy RFCs:

* To: reporter, authors
* CC: verifier, IESG, rfc-editor@rfc-editor.org

IETF Stream (working group):

* To: reporter, authors
* CC: verifier, IESG, working group, IANA, rfc-editor@rfc-editor.org

IETF Stream (non-working group):

* To: reporter, authors
* CC: verifier, IESG, IANA, rfc-editor@rfc-editor.org

IAB Stream:

* To: reporter, authors
* CC: verifier, IAB, IAB chair, rfc-editor@rfc-editor.org

IRTF Stream:

* To: reporter, authors
* CC: verifier, IRSG, research group, IANA, rfc-editor@rfc-editor.org

Independent Submission Stream:

* To: reporter, authors
* CC: verifier, ISE, Document Shepherd, IANA, rfc-editor@rfc-editor.org

Editorial Stream:

* To: reporter, authors
* CC: verifier, RSAB, RSWG, IANA, rfc-editor@rfc-editor.org

### Editorial Erratum Reports

The announcement of verified editorial erratum reports are sent from rfc-editor@rfc-editor.org to the following:

Legacy RFCs:

* To: reporter, author
* CC: verifier, rfc-ed@rfc-editor.org, IESG, IANA

IETF Stream (working group):

* To: reporter, authors
* CC: verifier, rfc-ed@rfc-editor.org, IESG, working group, IANA

IETF Stream (non-working group):

* To: reporter, authors
* CC: verifier, rfc-ed@rfc-editor.org, IESG, IANA

IAB Stream:

* To: reporter, authors
* CC: verifier, rfc-ed@rfc-editor.org, IAB, IAB chair

IRTF Stream:

* To: reporter, authors
* CC: verifier, rfc-ed@rfc-editor.org, IRSG, research group, IANA

Independent Submission Stream:

* To: reporter, authors
* CC: verifier, rfc-ed@rfc-editor.org, ISE, IANA

Editorial Stream:

* To: reporter, authors
* CC: verifier, RSAB, RSWG, IANA, rfc-ed@rfc-editor.org

#  Role of the RPC {#rpc-role}

The role of the RPC in errata processing is to:

   1.  Operate the Web portal.
   2.  Maintain the errata database.
   3.  Make changes in previously posted errata at the request of the corresponding SSP, or give the SSP temporary write access to the record.
   4.  Act as verifier for editorial erratum reports.
   5.  Remove junk and duplicate reports.
   6.  Track SSP and community requests for various features that will make the job of reporting and verifying errata more efficient.

#  Security Considerations {#security-considerations}

It is necessary to have access control in order to process erratum reports.  A
logged-in SSP is able to edit, verify, or reject any erratum report on
an RFC that is the product of their stream.
Once the SSP has submitted an erratum's final state (Verified, Held, or
Rejected) and the record entry has been committed to the erratum
database, the SSP loses write access to it.  This is
to prevent inadvertent or malicious changes to the database,
even if the passwords for some SSP logins may become fairly widely
known.  However, the RPC continues to have write access to
posted entries and can make later changes if necessary.

The portal uses HTTPS as a reasonably secure login
mechanism.  Also, the rfc-editor.org website has a signed certificate
from a CA, so that SSPs have
confidence that they are logging into the rfc-editor.org website.

#  IANA Considerations

This document has no IANA actions.

--- back

# Acknowledgements
{: numbered="false"}

This document is based on {{ERRATA_SYS_PROPOSAL}}, written by
Alice Russo (née Hagens), Sandy Ginoza, and Bob Braden. This document
received helpful feedback from Sandy Ginoza, TBD...
