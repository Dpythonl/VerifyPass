# VerifyPass
A privacy-first browser extension concept for user-approved form autofill and age verification on compatible websites, designed to minimize disclosure of sensitive identity data. No age-gate bypasses or form submissions without user approval.

# VerifyPass

**Privacy-preserving age verification and user-approved form autofill.**

VerifyPass is a browser extension concept designed to reduce repetitive form entry and unnecessary sharing of identity data. On compatible websites, it aims to let users prove they meet an age threshold without revealing their full date of birth. For supported forms, users can review and approve autofill values from a locally stored profile.

> **Project status:** Concept and planned MVP. Age verification depends on a compatible website, protocol, verifier, and valid credential.

## Goals

- Share only the information needed for a task.
- Keep profile data local where practical.
- Show users what information will be filled or disclosed.
- Require user approval before autofilling or sharing a proof.
- Keep form submission under the user's control.

## Planned features

- **Privacy-preserving age proof:** Provide proof of an age threshold only when a website supports a compatible verification protocol and the user has a valid credential.
- **User-approved autofill:** Map selected profile fields to supported form fields, show a preview, and fill only after approval.
- **Profile controls:** Let users review, edit, and delete saved profile fields.
- **Clear fallback:** Explain when a website or request is unsupported, invalid, or unavailable.

## How it is intended to work

1. The user chooses which profile fields to save.
2. On a supported page, VerifyPass detects an eligible age request or supported form fields.
3. The extension explains the request and shows the proposed proof or autofill values.
4. The user approves or cancels.
5. If approved, VerifyPass provides the proof or fills the selected fields.
6. The user reviews the page and submits any form manually.

## Privacy and safety

- VerifyPass does not bypass age gates or claim a website has verified a user unless a compatible verifier confirms the proof.
- Unsupported websites continue to use their normal verification process.
- Autofill is user-initiated; forms are never submitted automatically.
- The extension should not silently accept terms, make purchases, or submit legal or government forms.
- The MVP should use synthetic test credentials. Do not use real Aadhaar details, identity-document images, OTPs, or authentication secrets in development.
- A zero-knowledge proof does not establish that a date of birth is accurate by itself. Credential authenticity must be established by a trusted issuer or verification process.
- Sensitive profile data should be minimized and protected. Encryption keys must not be stored beside encrypted data without protection.

## Proposed technology

The implementation stack is still to be selected. The current proposal is:

- TypeScript, React, and Manifest V3
- Browser extension popup and options pages
- Content scripts for supported field detection and user-approved autofill
- Browser storage for non-sensitive settings and an appropriately protected local vault for sensitive values
- A reviewed credential and proof protocol; VerifyPass should not invent its own cryptography
- A local test website and synthetic credentials for age-proof development

## Roadmap

### 1. Form autofill demo

- Create a profile with synthetic information.
- Detect common form fields.
- Preview suggested field mappings.
- Fill selected fields only after user approval.
- Leave form submission to the user.

### 2. Age-verification test site

- Build a local website that issues clearly identified test requests.
- Use a synthetic, signed test credential.
- Integrate a reviewed proof system.
- Reject invalid, expired, or replayed requests.
- Show a clear fallback for unsupported sites.

### 3. Privacy and security controls

- Add per-site permissions and disclosure previews.
- Confirm that cancelling an action shares no data.
- Test ambiguous field mappings and malformed requests.
- Add profile deletion controls and document sensitive-data handling.

### 4. Compatibility evaluation

- Test only with websites that explicitly support the selected protocol.
- Measure proof verification time and autofill accuracy.
- Document what the verifier learns and what remains private.

## Success criteria

- The extension reports age verification only after confirmation from a compatible verifier.
- No form is submitted without an explicit user action.
- Users can inspect and edit autofill values before submission.
- Invalid, expired, and replayed proofs are rejected in the test environment.
- Unsupported sites receive an explanation instead of a bypass.
- Users can revoke site access and delete their local profile.

## Contributing

The project is at the concept stage. Contributions should preserve the principles of data minimization, explicit user approval, and compatibility-based age verification.

## License

No license has been selected yet.
