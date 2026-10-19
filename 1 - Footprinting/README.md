# Footprinting Techniques -- Lab Tasks

## Overview

This lab covers four basic footprinting and reconnaissance techniques
used to collect publicly available information about a domain or email:

1.  Google Search Operators (Google Hacking)
2.  Email Header Analysis
3.  DNS Lookup using `nslookup`
4.  Domain Registration Lookup using `whois`

These techniques help demonstrate how information can be gathered during
the information-gathering phase of a security assessment.

> **Ethical use:** Perform these exercises only for educational purposes
> and on domains, email messages, and systems you are authorized to
> examine. Do not use discovered information to access accounts, target
> systems, or invade anyone's privacy.

------------------------------------------------------------------------

## Task 1: Google Search Operators (Google Hacking)

### Objective

Use Google search operators to narrow search results and locate publicly
indexed information.

### Procedure

1.  Open [Google](https://www.google.com).
2.  Enter each query below into the search box.
3.  Review the results and record relevant page titles and observations.

  -------------------------------------------------------------------------------------------------
  Use case          Operator          Example query                               What to observe
  ----------------- ----------------- ------------------------------------------- -----------------
  Search within a   `site:`           `site:nytimes.com cybersecurity`            Results from the
  specific website                                                                specified website

  Find specific     `filetype:`       `filetype:pdf machine learning`             PDF documents
  file types                                                                      related to the
                                                                                  topic

  Search pages with `intitle:`        `intitle:"data privacy"`                    Pages with the
  specific titles                                                                 phrase in their
                                                                                  titles

  Find pages        `link:`           `link:bbc.co.uk/news/technology-57339947`   Any results
  linking to a URL                                                                Google returns
                                                                                  for the link
                                                                                  query

  Find specific     `intext:`         `intext:"cyber threat"`                     Pages whose
  text on a page                                                                  indexed text
                                                                                  includes the
                                                                                  phrase
  -------------------------------------------------------------------------------------------------

### Notes

-   Search results can change over time.
-   Google's `link:` operator is limited and may return few or no
    results.
-   Record the results actually observed; do not assume every query will
    return results.

### Observation

Record the search query, a result title or URL, and a short description
of what the operator helped you find.

------------------------------------------------------------------------

## Task 2: Email Footprinting and Header Analysis

### Objective

Save an email in `.eml` format and inspect its raw headers to understand
the message's route and authentication information.

### Procedure

1.  Open Outlook and select the email provided for the exercise.
2.  Open the email's context menu.
3.  Select **Save as** and choose **Save as EML**.
4.  Save the `.eml` file in an easy-to-find folder.
5.  Open the file with Notepad, Notepad++, or another text editor.
6.  Inspect the email headers and record relevant fields.

### Header fields to examine

  -----------------------------------------------------------------------
  Header or field                     Meaning
  ----------------------------------- -----------------------------------
  `From`                              Address displayed as the sender

  `To`                                Intended recipient

  `Subject`                           Email subject

  `Date`                              Date and time recorded for the
                                      message

  `Received`                          Mail-server hops recorded as the
                                      message was transferred

  `Authentication-Results`            Results of checks such as SPF,
                                      DKIM, and DMARC, when present
  -----------------------------------------------------------------------

### Notes

-   Email headers can help investigate a message's origin and delivery
    path.
-   A displayed sender address can be spoofed.
-   SPF, DKIM, and DMARC passing is useful evidence, but it does not by
    itself prove that a message is safe or that its contents are
    trustworthy.
-   Avoid sharing the full `.eml` file publicly because it may contain
    personal addresses, message contents, or other sensitive
    information.

### Observation

Record the sender, recipient (redact personal information in submitted
screenshots if needed), date, mail-server information, and
authentication results visible in the sample email.

------------------------------------------------------------------------

## Task 3: DNS Footprinting with `nslookup`

### Objective

Use `nslookup` to query DNS and identify IP addresses or other DNS
records associated with a domain.

### Procedure (Windows)

1.  Press `Win + R`.
2.  Type `cmd` and press **Enter**.
3.  Run the following command:

``` bash
nslookup google.com
```

4.  Review the DNS server and returned address information.
5.  If required, query other record types:

``` bash
nslookup -type=MX google.com
nslookup -type=NS google.com
nslookup -type=TXT google.com
```

### What the commands query

  -----------------------------------------------------------------------
  Command                             Purpose
  ----------------------------------- -----------------------------------
  `nslookup google.com`               Queries the domain's address
                                      records

  `nslookup -type=MX google.com`      Queries mail-exchange records

  `nslookup -type=NS google.com`      Queries name-server records

  `nslookup -type=TXT google.com`     Queries text records, which may
                                      include verification or
                                      email-security information
  -----------------------------------------------------------------------

### Observation

Record the command used, DNS server shown, returned IP addresses or
records, and any errors. Results can differ depending on the DNS
resolver and time of the query.

------------------------------------------------------------------------

## Task 4: WHOIS Domain Footprinting

### Objective

Retrieve publicly available domain-registration information, such as the
registrar, registration dates, and name servers.

### Method A: Online lookup

1.  Open [ICANN Lookup](https://lookup.icann.org/).
2.  Search for `google.com` or the domain specified by your instructor.
3.  Review the registration information returned.
4.  Record the available fields.

### Method B: Command-line utility

Windows Command Prompt does not normally include a `whois` command by
default. If a WHOIS utility is installed, run:

``` bash
whois google.com
```

If the command is not recognized, use the ICANN Lookup website or
install Microsoft's [Sysinternals
Whois](https://learn.microsoft.com/en-us/sysinternals/downloads/whois)
utility.

### Information to record

-   Domain name
-   Registrar, if shown
-   Registration or creation date, if available
-   Expiration date, if available
-   Name servers
-   Any privacy-protection or redaction information

### Notes

-   Some registration fields may be hidden, redacted, or unavailable.
-   WHOIS/RDAP data and the fields displayed can vary by domain and
    registry.
-   Use only the domain specified for the exercise or one you are
    authorized to investigate.

### Observation

Summarize the registration details returned by the lookup tool and note
any unavailable fields.

------------------------------------------------------------------------

## Results Summary

Complete this table after performing the tasks.

  -----------------------------------------------------------------------
  Task                    Tool or technique       Evidence to record
  ----------------------- ----------------------- -----------------------
  1                       Google Search Operators Query used, result
                                                  titles/URLs, and
                                                  observation

  2                       Email header analysis   Relevant headers and
                                                  authentication results

  3                       `nslookup`              DNS server, IP
                                                  addresses, and queried
                                                  record types

  4                       WHOIS / ICANN Lookup    Registrar, dates, name
                                                  servers, and
                                                  unavailable fields
  -----------------------------------------------------------------------

## Conclusion

These exercises demonstrate four basic footprinting techniques. Google
search operators help narrow publicly indexed information; email-header
analysis provides clues about message routing and authentication;
`nslookup` retrieves DNS information; and WHOIS/RDAP lookup provides
domain-registration details. The results should be documented accurately
and interpreted carefully, since no single result guarantees that a
domain or email is safe or malicious.

------------------------------------------------------------------------

## References

-   [Google Search](https://www.google.com)
-   [ICANN Lookup](https://lookup.icann.org/)
-   [Microsoft Sysinternals
    Whois](https://learn.microsoft.com/en-us/sysinternals/downloads/whois)
