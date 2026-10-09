# Shared Housing Teams and Two-Way Rental Matching — PRD

- Document version: v0.1
- Updated: 2026-10-09
- Status: Product discussion draft; baseline for prototypes and subsequent development
- Project name: TBD (current workspace: Rent)
- Initial validation markets: Rotterdam and Amsterdam, Netherlands
- Long-term market: Global, with country and city adaptations
- Platforms: Web and mobile, sharing accounts, business data, and permission rules
- Document language: English

## 1. Product Overview

The platform serves housing seekers and housing providers. Both sides can publish listings and receive recommendations. The initial focus is shared housing, with a housing team as a first-class business object and two matching stages:

1. Person-to-person matching: Seekers discover one another, communicate, and mutually agree to form a team.
2. Team-to-property matching: Teams establish shared housing requirements, then teams and housing providers receive recommendations and connect in either direction.

The experience borrows personal profiles and mutual expressions of interest from dating apps, and recruitment and team formation from multiplayer games. The platform provides recommendations and coordination tools; users decide whether to form a team, apply for a property, or live together.

Lifestyle photos, nicknames, and identity verification can coexist. A user can display a nickname and a verification badge without publicly disclosing their legal name or identity documents.

### 1.1 Value Proposition

| User                        | Main problem                                                                                                        | Product value                                                                          |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Housing seeker              | Finding roommates and housing separately, repeatedly discussing requirements, and coordinating multiple preferences | Describe needs once, find compatible people, and search together                       |
| Existing housing team       | No agreed budget, location, or dates; fragmented applications                                                       | Maintain shared requirements, member decisions, and coordinated communication          |
| Resident seeking a roommate | Difficulty assessing both housing suitability and living preferences                                                | Advertise an available room and household preferences, then invite suitable candidates |
| Housing provider            | Incomplete applications and repeated questions about occupancy and timing                                           | Connect with individuals or teams whose requirements are clear and confirmed           |

### 1.2 Confirmed Direction and Hypotheses

Confirmed direction:

- Design for a global market, starting validation in Rotterdam and Amsterdam.
- Support all rental types, prioritizing shared housing team formation.
- Allow both housing offers and housing requests, with either side initiating interest.
- Match roommates into teams before matching teams with housing providers.
- Support lifestyle photos, public anonymity or nicknames, and identity verification.
- Plan for both web and mobile; begin with the PRD and page prototypes.

Hypotheses to validate:

- Seekers will form teams with people they do not yet know before finding a property.
- Complete team profiles reduce provider effort and improve meaningful response rates.
- Members will use the platform to confirm shared requirements and application decisions.
- Users will pay for selected additional services, or professional providers will subscribe to management tools.

## 2. Objectives and Scope

### 2.1 Initial Objectives

- Complete the journey from individual discovery to team formation, joint housing search, and provider contact.
- Support individual seekers, existing groups, and residents recruiting roommates.
- Explain matching reasons, incompatibilities, and unresolved information.
- Give members control over shared requirements, public information, and applications.
- Validate meaningful conversations, team formation, viewings, and housing outcomes through real trials.

### 2.2 MVP Scope

| Module                | Included in the initial release                                                                          |
| --------------------- | -------------------------------------------------------------------------------------------------------- |
| Accounts and profiles | Registration, login, nicknames, introductions, photos, account and privacy settings                      |
| Verification          | Identity verification entry point, status, and visibility; integration reviewed separately before launch |
| Housing requests      | Individual and team needs, budget, location, dates, occupancy, and other conditions                      |
| Property listings     | Entire homes, private rooms, shared rooms; long-term, short-term, and flexible stays                     |
| Roommate matching     | Search, filters, recommendations, interest requests, and conversation after acceptance                   |
| Team coordination     | Creation, invitations, join requests, member approvals, shared requirements, departure, and replacement  |
| Property matching     | Two-way recommendations, interest requests, and formal applications after unanimous approval             |
| Communication         | Direct messages, team chats, group conversations with providers, and notifications                       |
| Trust and operations  | Reporting, blocking, basic moderation, listing expiry, and handling records                              |
| Outcome tracking      | Viewing status, self-reported rental outcomes, and listing pause or closure                              |

### 2.3 Out of Scope for the Initial Release

- Rent or deposit escrow, electronic contracts, and automated credit decisions.
- Guarantees about roommate compatibility, property safety, or the legality of a rental.
- Complex personality tests or inferring personality or trustworthiness from photos.
- Complex recommendation models trained on browsing behavior.
- Provider team CRM, automatic bill splitting, and complete post-move-in management.
- Launching every country's rules at once; the initial markets come first, with an extensible structure.

These features may be evaluated later. Supporting short stays or sublets as listing categories does not confirm that a particular provider is authorized to offer them.

## 3. User Roles and Scenarios

One account may hold multiple roles without requiring separate registrations.

| Role             | Permissions and goals                                                                                                  |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Housing seeker   | Manage profile and needs, contact potential roommates, join teams, and apply for housing                               |
| Team coordinator | Maintain drafts, initiate votes, invite members, and coordinate viewings; cannot consent on another member's behalf    |
| Team member      | Confirm shared requirements, vote, communicate, control personal information, and leave                                |
| Housing provider | Manage listings, view authorized information, invite candidates or teams, and respond to applications                  |
| Operations staff | Review listings, handle reports, and restrict abusive accounts within assigned permissions; sensitive access is logged |

Core scenarios:

1. Find people before housing: An individual publishes a request, connects with others, and forms a team that recruits further or starts searching.
2. Search as an existing group: People who already know one another join by invitation and individually confirm profiles and shared needs.
3. Find a roommate for an existing home: Residents list an available room and household conditions; candidates and relevant members mutually approve.
4. Find a team as a provider: A provider publishes a property, reviews suitable teams, and sends an invitation linked to that property.
5. Search individually: Team formation is optional; an individual can contact suitable properties directly.

## 4. Core Business Objects and Information

### 4.1 Personal Profile

- Display information: Nickname, optional avatar and lifestyle photos, introduction, and communication languages.
- Living preferences: Daily schedule, cleaning habits, smoking, pets, guests, and social activity.
- Trust information: Separate email, phone, and identity verification indicators.
- Private information: Identity verification references, contact details, and privacy settings.
- Activity indicators disclose only necessary detail; precise online times are not public by default.

Living preferences are self-reported and optional. Missing information does not mean incompatibility. The initial design assumes adult users; the age threshold and verification method must be confirmed before launch.

### 4.2 Housing Request

| Field                | Requirement                                                                                |
| -------------------- | ------------------------------------------------------------------------------------------ |
| Location             | Multiple cities or areas within one request; commute-time calculation is a later extension |
| Budget               | Amount range, currency, billing period, and whether additional costs are included          |
| Occupancy            | Actual number of residents, stored separately from the number of platform accounts         |
| Housing needs        | Entire home or room, minimum bedrooms, and willingness to share a bedroom                  |
| Timing               | Move-in window, intended duration, and negotiable flexibility                              |
| Address registration | Whether needed, number of people requiring it, local terminology, and unresolved details   |
| Other needs          | Furnishings, pets, and specific accessibility facilities                                   |
| Condition priority   | Mark applicable conditions as required or negotiable                                       |
| Status               | Draft, published, paused, housing found, expired, or closed                                |

Individuals may save multiple requests. The proposed MVP default is membership in only one active housing-seeking team per account to avoid conflicting commitments. Concurrent teams remain a future decision.

### 4.3 Housing Team

- Name, description, target member count, intended occupancy, and current members.
- Linked shared housing request, internal budget allocation, agreed total budget, and cost definition.
- Bedroom needs, preferred locations, move-in window, rental duration, and household agreements.
- Invitations or join requests, member approval status, and shared requirement version.
- Public information, verified member count, recruitment status, and property applications.
- Coordinator, conversations, tasks, and decision records.

The shared budget requires explicit confirmation; it must not be published by automatically adding individual maximum budgets. Verification is shown as a count, such as "2 of 3 members identity verified."

### 4.4 Property Listing

- Country, city, address, and the approximate area displayed publicly.
- Space type: Entire home, private room, or shared room.
- Stay type: Long-term, short-term, or flexible; publisher role: Owner, agent, or current tenant.
- Area and units, bedroom count, existing residents, available additional occupancy, and maximum occupancy.
- Base rent, known additional charges, unknown charges, deposit, currency, and billing period.
- Availability date, permitted duration, acceptance of joint applications, and related explanations.
- Address registration declaration: Supported, conditionally supported, unsupported, or awaiting confirmation; relevant conditions and capacity.
- Furnishings, pets, smoking, and specific accessibility facilities.
- Photos, description, listing expiry, and verification status.

Registration and rental conditions are provider declarations. Platform verification is recorded separately. Locally applicable options must be confirmed when reviewing launch-market requirements.

### 4.5 Interest Requests and Applications

- Each contact is linked to a specific personal request, team, or property to avoid context-free bulk messages.
- Interest requests include a short introduction and can be accepted, declined, withdrawn, or expired.
- Expressing interest indicates willingness to learn more; it is not a rental commitment.
- A formal application records participating members, the shared requirement version, and unanimous approval. It is not a signed contract.
- Applications preserve a submission snapshot. Later changes must not silently overwrite historical applications.

## 5. Two-Stage Matching

### 5.1 Stage One: Person-to-Person or Person-to-Team

1. Check for a feasible overlap in locations, dates, budgets, and intended team size.
2. Rank suggestions using self-reported living preferences.
3. Show compatible conditions, differences to discuss, and missing information.
4. Open a conversation after an interest request is accepted.
5. Admit a new team member only after the applicant and all existing members confirm.

Do not filter housing recommendations by sensitive characteristics such as ethnicity or religion, rank people by appearance, or present identity verification as a guarantee of character or reliability.

### 5.2 Stage Two: Individual-or-Team-to-Property

Prioritize occupancy and bedroom needs, costs, dates, location, joint application conditions, address registration, and essential facilities.

| Category                            | Behavior                                                                               |
| ----------------------------------- | -------------------------------------------------------------------------------------- |
| Known required conditions satisfied | Recommend normally and explain the main reasons                                        |
| Essential information missing       | Show under awaiting confirmation; do not claim the requirement is satisfied            |
| Negotiable differences              | Explain the difference or amount, and let users choose whether to browse these results |
| Known required conditions conflict  | Exclude from matching results; reassess if requirements change                         |

Unknown costs are not zero. Different billing periods must not be compared directly. The MVP prioritizes matching in the same currency; any future conversion must disclose the exchange-rate date and estimated nature of the amount.

Use explainable rule-based filtering and preference ranking initially. Do not show unsupported precise match percentages. Reassess eligibility when teams change, listings change or expire, or blocking relationships change.

## 6. Team Lifecycle and Group Decisions

### 6.1 States

| State                        | Entry condition                                                                   | Available actions                                                             |
| ---------------------------- | --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Draft                        | Coordinator creates a team                                                        | Edit and invite                                                               |
| Recruiting                   | Creator publishes recruitment                                                     | Receive requests, chat, and approve members                                   |
| Awaiting member confirmation | Target membership reached and a shared requirement version prepared               | Confirm or propose changes                                                    |
| Searching for housing        | All members approve current requirements and visibility                           | Receive recommendations, express interest, and initiate application decisions |
| Updating                     | A member leaves or key requirements change                                        | Replace members, revise requirements, and reconfirm                           |
| Housing found                | Members confirm the rental outcome                                                | Close the search and new recommendations; access history                      |
| Closed                       | Team dissolves, closes voluntarily, or becomes inactive beyond the allowed period | Access authorized historical records                                          |

Viewing and application states belong to individual property applications, not mutually exclusive team states. A team may explore multiple properties simultaneously.

### 6.2 Decision Rules

- Joining a team, submitting a formal property application, and confirming housing found require explicit agreement from all relevant members.
- Changes to occupancy, total budget, dates, areas, or bedroom needs create a new version requiring confirmation.
- The coordinator may draft requirements, send exploratory interest, and arrange communication, but cannot submit formal applications without member approval.
- Silence, timeout, or unread messages do not count as consent. Pending decisions may expire and be restarted.
- Any member can leave without approval. Remove their public team card and access to future team conversations immediately.
- After departure, pause new applications, notify providers in active discussions, and mark existing applications as requiring updates.
- Previously shared application snapshots follow the retention policy; the platform cannot promise to retract information already read by a provider.
- A departing coordinator may initiate a handover. Without a successor, the team enters Updating and pauses external actions.
- New members do not automatically receive all historical messages containing former members' private information.

## 7. Privacy, Verification, and Safety

### 7.1 Public Anonymity

Anonymity means hiding a legal name, avatar, or photos from other users. Participation still requires a stable account and activity records. Users may choose to:

1. Display a nickname, introduction, and selected photos.
2. Use a nickname and a non-identifying avatar while sharing housing needs.
3. Selectively reveal more information or photos after mutual acceptance.

Accepting contact does not automatically reveal a phone number, legal name, identity documents, or all photos.

### 7.2 Permission Principles

| Information                                            | Default visibility                                                                     |
| ------------------------------------------------------ | -------------------------------------------------------------------------------------- |
| Nickname, public introduction, and request summary     | Viewers allowed by the user's visibility settings                                      |
| Lifestyle photos                                       | Audience selected by the user                                                          |
| Individual budget allocation                           | The individual and authorized team members                                             |
| Confirmed team budget and occupancy                    | Providers after the team publishes them                                                |
| Member details                                         | Fields individually authorized by each member; joining does not broaden default access |
| Phone number, exact home address, and income documents | Private; separately authorized within a specific flow                                  |
| Original identity documents                            | Never visible to other users; preferably handled by a specialist verification provider |

Providers see only authorized information. Sending an invitation does not grant additional access. Logged-out access, search indexing, and shared links must limit personal data. The prototype defaults to requiring login for complete personal and team profiles.

### 7.3 Identity and Property Verification

- Distinguish email, phone, identity, and property or rental-authority verification.
- Identity verification states: Not started, processing, verified, failed, and expired.
- Do not expose failure reasons or document information to other users.
- Select a provider and define retention, deletion, and appeal processes before production launch.
- Prototype verification is simulated, collects no real identity documents, and is clearly labeled as a demonstration.

### 7.4 Basic Protections

- Allow reporting accounts, listings, and messages; support blocking and limits on repeated invitations.
- Blocked users stop appearing in each other's recommendations. If they share a team, show the conflict and provide departure or operations support options.
- Apply basic moderation to uploaded photos, listings, and public introductions.
- Users can withdraw visibility permissions, export data, or request deletion; retention exceptions must be defined before launch.
- Log sensitive actions and operations access; rate-limit verification and profile updates.

## 8. Pages and Prototype Scope

### 8.1 Information Architecture

Suggested mobile navigation: Discover, Team, Publish, Messages, and Profile. Web uses top navigation with the same business rules and permissions.

| Page                                 | Main content and actions                                                              |
| ------------------------------------ | ------------------------------------------------------------------------------------- |
| Home / Discover                      | Find roommates, housing, or tenants; select location and request                      |
| Profile editor                       | Photos, introduction, living preferences, and privacy preview                         |
| Housing request wizard               | Location, costs, dates, occupancy, and required or negotiable conditions              |
| Roommate recommendations             | Individual and recruiting-team cards, matching reasons, and interest requests         |
| Personal profile                     | Authorized information, compatible conditions, discussion points, and contact entry   |
| Create / join team                   | Invitations, requests, member approvals, and pre-join disclosure consent              |
| Team workspace                       | Members, shared requirements, confirmation progress, recruitment, decisions, and chat |
| Public team profile                  | Shared needs, authorized member cards, verified count, and current status             |
| Property listing wizard              | Property details, cost breakdown, occupancy arrangements, and local fields            |
| Property recommendations and details | Search, filters, explanations, costs, interest, and applications                      |
| Provider candidate list              | Individual or team recommendations linked to a property, with invitations             |
| Application details                  | Submission snapshot, member approvals, provider response, viewing, and outcome        |
| Messages                             | Interest requests, direct messages, team chats, and provider conversations            |
| Profile / account                    | Listings, saved items, account, verification, privacy, notifications, and reports     |
| Operations console                   | Listing and report handling, account restrictions, and audit records                  |

### 8.2 First Clickable Prototype

Cover these journeys and show the key desktop and mobile screens:

1. Create a personal card → choose anonymity or photo visibility → discover roommates → mutually accept → create a team.
2. A third person requests membership → existing members approve → everyone confirms shared budget and needs → publish the team.
3. Provider publishes a property → reviews recommended teams and authorized member details → offers the property → enters a group conversation.
4. Team discovers a property → members respond individually → everyone approves → submit a formal application.
5. Member leaves → team enters Updating → applications show the change → recruit a replacement and reconfirm.
6. Show no matches, missing information, declined requests, incomplete verification, and expired listings.

The provisional visual direction is simple and trustworthy, emphasizing people and housing conditions. This PRD and prototype annotations are in English. Prototype interface language remains to be confirmed before design; preserve support for future localization.

## 9. Globalization and Initial Market Adaptation

- Model country, city, currency, billing period, area units, dates, and time zones separately.
- Represent country-specific rules as configurable content rather than hardcoding them into universal forms.
- Before the Netherlands launch, verify address-registration explanations, shared occupancy and rental permissions, tenant-selection requirements, and privacy obligations.
- Support multiple cities within one request; do not automatically match budgets across different currencies in the initial release.
- Store original content separately from translations. Label machine translations and preserve the original.
- Support all rental categories structurally while focusing initial operations on shared housing to maintain sufficient local activity.

Fields and flows in this PRD are product proposals, not legal conclusions. Reviewing launch-market requirements is a launch preparation task.

## 10. Nonfunctional Requirements

- Web and mobile follow the same business rules, with server-side authorization.
- Protect photos, sensitive information, and conversations through access controls, not merely hidden buttons.
- Member approvals reference a requirement version. Repeated clicks or retries must not submit duplicate applications.
- Synchronize important state changes across clients. Notification failure does not alter business state.
- Provide feedback for failed uploads, network interruptions, retries, empty results, and expired links.
- Support keyboard navigation, screen-reader labels, and readable contrast; do not convey status through color alone.
- Analytics must exclude unnecessary personal content such as message bodies, identity documents, and contact details.
- Architecture and technology choices will be specified separately. Previously mentioned Next.js and Expo remain candidates, not confirmed decisions.

## 11. Metrics and Validation Plan

### 11.1 Core Metrics

The initial primary metric is the weekly number of individuals or teams receiving a meaningful two-way response. This means an accepted interest request followed by at least one non-system message from each side, deduplicated by housing request.

| Stage             | Metrics                                                                            |
| ----------------- | ---------------------------------------------------------------------------------- |
| Activation        | Percentage of users completing and publishing a valid request                      |
| Recommendations   | Eligible candidates per request and no-result rate                                 |
| Contact           | Time to first meaningful response and interest acceptance rate                     |
| Team formation    | Fully confirmed teams, formation time, and member departure rate                   |
| Property matching | Provider response rate to teams, formal application rate, and viewing rate         |
| Outcomes          | Self-reported and mutually confirmed rentals, tracked separately by evidence level |
| Business          | Acquisition cost, actual paid conversion, and repeat provider usage                |
| Trust             | Report rate, handling time, and stale listing rate                                 |

Segment metrics by city, request type, and time window. Cumulative registrations and likes do not replace housing outcomes.

### 11.2 Initial Trial

- Recruit real seekers and providers in both cities for task-based testing with fictional prototype data.
- With participant permission, run a small manual matching trial using real requirements.
- Test willingness to share information, form teams with unfamiliar people, and confirm shared needs.
- Observe whether providers engage with teams and whether suitable real properties exist for those teams.
- Set numerical targets and further-investment criteria after establishing an interview baseline; do not invent industry benchmarks.

## 12. Business Model Hypotheses

- Validate effective matching first; payment is not a prerequisite for prototype completion.
- Test subscriptions for professional providers covering multiple properties, application management, and collaboration.
- Test user upgrades that deliver clear additional value; do not assume basic safety or reporting should require payment.
- Label paid promotion and do not disguise it as stronger compatibility.
- Evaluate transaction services and fees after establishing delivery capability, outcome tracking, and applicable local requirements.
- Lifestyle photos and verification support experience and trust; they are not independently a defensible competitive advantage.

## 13. Core Acceptance Scenarios

| ID    | Scenario                                                                                        | Expected outcome                                                                                                          |
| ----- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| AC-01 | A verified user chooses a nickname and hides photos                                             | Recommendations and team cards reveal neither the legal name nor hidden photos                                            |
| AC-02 | Two seekers accept both Rotterdam and Amsterdam                                                 | Eligible results from either city can appear                                                                              |
| AC-03 | An applicant seeks to join a team with a target of three, but only one existing member approves | Membership remains pending                                                                                                |
| AC-04 | A member changes the budget after everyone has approved                                         | Previous approvals become invalid; the new version must be confirmed before a new application                             |
| AC-05 | A provider views a team                                                                         | Shared needs and authorized member fields appear; individual budgets and identity documents are not automatically exposed |
| AC-06 | One member has not approved a formal application                                                | Submission is blocked, including for the coordinator                                                                      |
| AC-07 | A team requires address registration but the listing lacks that information                     | Mark as awaiting confirmation, not fully compatible                                                                       |
| AC-08 | Additional property costs are unknown                                                           | Clearly flag unknown costs; do not treat them as zero when checking the budget                                            |
| AC-09 | A member leaves a team with active applications                                                 | Pause new applications, update membership and permissions, and notify relevant providers                                  |
| AC-10 | A listing is paused or rented                                                                   | Remove it from active recommendations and show its status in existing conversations                                       |
| AC-11 | One user blocks another                                                                         | Stop new recommendations and direct contact; provide a way to resolve an existing shared-team conflict                    |
| AC-12 | An individual does not want to form a team                                                      | Allow direct housing requests, property browsing, and interest requests                                                   |
| AC-13 | A provider invites a team to connect                                                            | Do not automatically create a formal application or reveal private information                                            |
| AC-14 | The same request is submitted repeatedly                                                        | Do not create duplicate memberships, interest requests, or applications                                                   |

## 14. Risks and Open Decisions

| Issue                                                          | Current approach / next step                                                                              |
| -------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Insufficient local supply and demand                           | Enable both cities but prioritize operations where real supply is easier to secure                        |
| Teams form but cannot find properties accepting them           | Validate suitable supply and retain the existing-home roommate recruitment flow                           |
| Photos encourage appearance-led selection                      | Emphasize conditions and agreements, allow hidden photos, and do not rank by appearance                   |
| Frequent membership changes                                    | Use requirement versions, unanimous approval, replacement, and application update mechanisms              |
| Verification mistaken for a safety guarantee                   | Explain verification scope and separate identity from property verification                               |
| Monetization does not fit infrequent usage                     | Validate repeat professional-provider usage and actual willingness to pay                                 |
| Product name and branding                                      | TBD                                                                                                       |
| Prototype interface language                                   | TBD; preserve future localization support                                                                 |
| Whether verification is required for specific actions          | Optional in the prototype; decide before launch based on trial findings                                   |
| Minors, household members, and residents without accounts      | Initially design for adult accounts; distinguish residents from accounts; detailed boundaries remain open |
| Participation of existing residents when recruiting a roommate | Test whether relevant residents should be invited to join and approve                                     |
| Listing validity, invitation timeouts, and retention periods   | Define before launch rather than assigning arbitrary values in this draft                                 |

## 15. Delivery Sequence

1. Review the PRD and resolve outstanding product boundaries.
2. Create the information architecture and low-fidelity screens for people, teams, and properties.
3. Build a clickable prototype covering both matching stages and member departure.
4. Test with users in the initial cities, record behavior and issues, and update the PRD.
5. Confirm the MVP architecture, data model, permission design, and development tasks.
6. Implement and validate the core journey in stages, then prepare a limited launch.

## Appendix: Known Competitors and References

Two-way discovery and forming groups to search for housing are not proven market gaps. These sources are starting points for competitor research, not substitutes for hands-on product evaluation:

- [Kamernet: Providers can search for and contact tenants](https://kamernet.nl/en/safety-landlord)
- [SpareRoom: Room wanted ads and Buddy Up groups](https://www.spareroom.co.uk/content/info-faq/why-rooms-wanted)
- [SpareRoom: Property alerts based on search requirements](https://www.spareroom.co.uk/content/info-faq/why-email-alerts/)

This PRD contains no unvalidated market revenue forecasts. Business viability must be assessed through local user density, real property supply, matching outcomes, and payment experiments.
