# MYEDIT Public MVP — starter scaffold

This is a Flutter starter for a public-facing MYEDIT app targeting Android and iOS.

## Included now
- Public-facing welcome screen
- Email sign-in / create-account UI (prototype only; no credentials are sent or stored)
- Video selection and playback preview
- Timeline and editor tool layout
- Dark MYEDIT brand styling

## Important: not production-ready
Authentication is UI-only. Do not enter a real password. Video trim/split, multi-track rendering, AI features, export, cloud sync and multilingual translations are not implemented yet. This scaffold must not be published as a finished editor.

## Run locally
1. Install Flutter SDK.
2. Extract this repository.
3. Run `flutter pub get`.
4. Run `flutter run`.

## Public launch architecture

### Mobile clients
Flutter app for Android and iOS. Keep editing responsive and process media on-device where possible.

### Identity
Firebase Authentication email/password (add email verification, password reset, abuse protection and account deletion before launch).

### Backend
A small API service for project metadata, job orchestration, usage limits and signed upload/download URLs. Never put admin/service credentials in the mobile app.

### Storage
Private object storage for user media. Use short-lived signed URLs, per-user quotas, retention controls and explicit deletion.

### Database
Store project metadata, preferences, language, export job status and account settings. Do not store raw video blobs in the database.

### Media pipeline
On-device preview and editing first. Use a native media engine for frame-accurate trim, split, audio mixing, text overlays, transitions and export. Background rendering jobs should have limits and retry handling.

### AI services
Separate services for speech-to-text captions, scene detection and background segmentation. Add consent, rate limits, cost ceilings, abuse controls and clear upload disclosures.

### Localization
Use Flutter localization (`flutter gen-l10n`) with English as the source locale, then add Hindi and other translated ARB files. Avoid hard-coded UI strings in production.

### Public release checklist
- Privacy policy and terms
- Copyright-safe music, fonts, templates and effects licensing
- Account deletion and data export process
- User support and abuse/reporting contact
- Security rules and penetration testing
- Crash reporting and analytics with privacy controls
- Accessibility, low-memory and low-storage testing
- Play Store and App Store listing, screenshots and review compliance
- Device matrix and staged rollout

## Cost model
A free app still incurs storage, bandwidth, AI inference and support costs. Start with local editing and bounded AI usage. Publish transparent limits; do not promise unlimited cloud AI or storage.
