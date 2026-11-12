---
name: flowingwells
hosts: [careers.flowingwellsschools.org]
apply_path: /applications/new
---
The form is one page for Flowing Wells Unified School District. A cookie banner may cover it: click its button with `aria-label="Decline all non-necessary cookies"` and go on.

The questions come first, then "Personal information", the attachments, the consent checkbox, and `input[name=commit]` ("Submit application"). Read the page before filling.

Question fields are `candidate[answers_attributes][N][...]`. The first question is employment status: choose the visible label "I am not an employee". The certificate question: choose "Yes, I hold an Arizona Department of Education Certificate." The fingerprint question: choose "Yes". A yes/no input is hidden, so click its visible label, not the input.

Uploads: certificate at `#candidate_answers_attributes_2_upload_attributes_file_remote_url`; fingerprint card at `#candidate_answers_attributes_4_upload_attributes_file_remote_url`; resume at `#candidate_resume_remote_url`; additional files at `#candidate_file_remote_url` (multiple). The file inputs clear after a successful upload; the page shows the file name. Upload the CV first, then the rest.

Education is a custom menu: a button with `aria-haspopup="menu"` opens it; choose the option that matches the answers ("Bachelor's Degree"). Years of experience is a slider `#candidate_answers_attributes_6_range` with a maximum of 8. Grade levels are checkboxes; check the ones the answers name.

The supervisor contact is `#candidate_answers_attributes_8_text`. Personal details are `#candidate_first_name`, `#candidate_last_name`, `#candidate_email`, `#candidate_phone`, and the address combobox `#candidate_location` (type the address and pick a suggestion). The cover letter is a text area, `#candidate_job_applications_attributes_0_cover_letter`, not a file.

Leave all legal and disclosure questions (license revoked, investigation, relative of a board member, essential functions, work eligibility, dismissal, conviction, child-abuse/sex-offender) for the candidate. Do not answer them from the CV or answers. Do not tick the consent checkbox. Do not submit: report ready only after every non-legal required field is filled, with `input[name=commit]` as the send selector.

After sending: the address gains `/thanks/` and the page confirms receipt. If the form is still there, nothing was received.
