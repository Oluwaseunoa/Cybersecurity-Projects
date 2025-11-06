# Digital Forensic Analysis of a Phishing Email Impersonating DHL


**Author:** Oluwaseun Osunsola    
**Environment:** Windows OS, Chrome Browser & Roundcube Webmail   

**Project link:** https://github.com/Oluwaseunoa/Cybersecurity-Projects/tree/main/Cyber-Security-Fundamentals

This report documents the steps taken during the analysis of a suspicious email claiming to be from DHL. The aim is to determine whether the message was legitimate or a phishing attempt, and to document the investigative process for awareness and training.

## Project Overview

A suspicious email was received with a subject line suggesting an urgent DHL shipment delivery notice. The visual appearance of the email attempted to create a sense of urgency to prompt the recipient to click a link or open an attachment.

This report walks through each step used to verify the authenticity of the email.

## Investigation Steps

### 1. Received Suspicious Email

![Suspicious Email](img/1.received_email_with_the_subject-DHL_Shipment_Deliver_Air_Waybill_carefully_open_in_new_window.png)
The email subject appeared to reference a DHL shipment, which is a common tactic used in phishing to create urgency.

### 2. Checked Sender Address

![Sender Hover](img/2.moused_on_sender_DHL_Global_Mail_Inc_and_found_the_enbedded_link_to_be_unrelated_suspicious.png)
Hovering over the sender name revealed the email domain did not belong to DHL.

### 3. Opened Message Headers

![Opening Headers](img/3.carefully_clicked_on_the_mail_headers.png)
The headers were opened to verify details about the sending server and domain authentication.

### 4. Sender Domain Mismatch

![Header Sender Check](img/4.message_headers_open_and_found_that_sender_does_not_relate_to_dhl(ceo@09ceos-com).png)
The "From" address did not match official DHL systems.

### 5. DKIM Signature Review

![DKIM Signature](img/5.scroll_down_and_found_DKIM-Signature_however_it_only_show_the_malicious.png)
The DKIM signature only verified the domain `09ceos.com`, not DHL.

### 6. Suspicious Mail Routing

![Routing Review](img/6.scroll_further_under_received_found_suspicious_mail_routing_hostname-powered.png)
Routing traced through a server associated with compromised RDP hosts.

### 7. Urgent Subject Pattern

![Urgency Pattern](img/7.check_From_and_found_DHL_Shipment_Delivery_Air_Waybill_NO-86468545215485_common_to_dh.png)
The subject mimicked DHL/FedEx shipment notices, a known phishing tactic.

### 8. SPF Failure Confirmed

![SPF Fail](img/8.confirm_X-SPF-Fail_says_yes_meaning_server_not_authorized_by_09ceos-com.png)
The email failed SPF validation, meaning the sender was not authorized to send from that domain.

### 9. Suspicious Embedded Image Link

![Body Link Hover](img/9.moused_on_the_document_image_embedded_in_the_body_for_me_to_click_and_the.png)
The embedded "document" image contained a dangerous external link.

### 10. Extracted Link for Analysis

![Copy Link](img/10.carefully_right-click_on_the_image_document_and_copy_link_address.png).

### 11. Submitted to VirusTotal

![VirusTotal Submission](img/11.proceeded_to_virustotal-com_website_and_paste_the_copied_link_in_the_search_bar.png)
The link was tested using VirusTotal.

### 12. Malicious Detection

![VirusTotal Result](img/12.the_result_show_that_2_security_vendor_flagged_link_as_malicious.png)
Two security vendors flagged the link as malicious.

### 13. Prior Phishing Confirmation

![Prior Report](img/13.note_the_same_link_was_analyzed_by_another_person_3days_ago_and_ESET_categorized_link_as_phishing.png)
Another user previously identified the link as phishing.

### 14. Additional Malicious Link Found

![Email Contact Hover](img/14.mouse_on_contact_email_and_found_the_embedded_link_to_be_a_link_to_be_malicious.png)
The contact email in the footer was also linked to a known malicious domain.

### 15. Fake DHL Link Masking

![Masked Link](img/15.moused_on_dhl_link_provided_and_the_malicious_embendded_link_shows.png)
A real DHL link was included to create trust, while malicious links were hidden elsewhere.

### 16. Final Action

![Delete or Escalate](img/16.delete_the_maicious_email_or_escalate_or_forward_archive_for_security_awareness_training_if_need_be.png)
The email was deleted or escalated depending on security policy.

## Conclusion

This email was confirmed to be a phishing attempt. Key indicators included:

* Sender domain mismatch
* SPF authentication failure
* Suspicious routing path
* Malicious link flagged by VirusTotal

### Recommendation

* Do not click suspicious links.
* Always verify sender information.
* Report similar phishing attempts to IT/security.



Below are common terms used in the report explained in plain language:

| Term                                  | Simple Explanation                                                                                                                     |
| ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Phishing**                          | A scam where attackers pretend to be someone trustworthy (like a bank or DHL) to trick you into clicking a link or giving information. |
| **Spoofing**                          | When a scammer fakes an email address or name to make it look real.                                                                    |
| **Email Header**                      | The hidden technical details of an email that show where it came from and the servers it passed through.                               |
| **Domain**                            | The website or email company's name, e.g., `dhl.com`. Fake emails often use similar-looking domains.                                   |
| **SPF (Sender Policy Framework)**     | A security check that verifies if an email is allowed to be sent from a domain. If it **fails**, the sender is likely fake.            |
| **DKIM (DomainKeys Identified Mail)** | Another security check that verifies if an email was modified or faked during transit.                                                 |
| **Malicious Link**                    | A link designed to cause harm — like stealing passwords, downloading viruses, or redirecting to fake websites.                         |
| **VirusTotal**                        | A website that checks whether a link or file is safe by comparing it to many security databases.                                       |
| **Urgency-Based Attack**              | A scam technique where the attacker tries to make you panic and act quickly (like “urgent shipment notice”).                           |
| **Social Engineering**                | The psychological manipulation of people to trick them into unsafe decisions.                                                          |



