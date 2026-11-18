# Higio

[Try Higio in the browser](https://higio-dcirko.netlify.app/)

Higio is a local-first mobile app for tracking personal hygiene, care routines, daily supplements, and dog care. The main screen lets you log a completed activity with one tap and undo the entry if needed.

## Features

- Daily slots, selected weekdays, recurring intervals, and unscheduled activities
- Morning and evening routines, activity templates, and pause or archive controls
- History, manual corrections, and 7- and 30-day statistics
- Local reminders and a separate dog care section
- Supplement dose history and versioned backups
- On mobile, a persistent SQLite database, local JSON backup and restore, and optional biometric locking

Higio is Android-first, with iOS support in the code and a browser preview. The mobile app uses Expo SDK 57, React Native, TypeScript, SQLite, and Drizzle. The browser stores data in its own localStorage. It has no mobile sync, local notifications, biometric lock, screenshot protection, or backup import and export. Browser data can be lost if site storage is cleared.

## Browser preview

```bash
cd apps/mobile
npm ci
npm run web
```

Run `npm run build:web` in `apps/mobile` to build the preview into `apps/mobile/dist`. The hosted preview uses Netlify. See the [deployment notes](docs/NETLIFY_DEPLOYMENT.md).

## Android development

Install Node.js 22.13 or later, npm, JDK 21, and Android SDK 36 with platform tools and an emulator. From the repository root:

```powershell
cd apps/mobile
npm ci
npm run lint
npm run typecheck
npm test
npm start
```

Use `npm run android` to launch on an Android device or emulator. Run `npm run db:generate` only after an intentional change to `src/data/db/schema.ts` and commit the generated migrations.

## Status and documentation

The Android preview has been built and tested in the emulator. Real-device checks for backup and restore, biometrics, notifications, and other native behavior remain part of acceptance. Widgets, accounts, and cloud sync are deferred.

- [Product specification](docs/PRODUCT_SPEC.md)
- [Roadmap](docs/MASTER_PLAN.md)
- [Local data model](docs/DATA_MODEL.md)
- [Android setup](docs/ANDROID_SETUP.md)
- [Android device checklist](docs/ANDROID_DEVICE_CHECKLIST.md)
- [Backup format](docs/BACKUP_FORMAT.md)
- [Privacy and security audit](docs/PRIVACY_SECURITY_AUDIT.md)
- [Original Croatian README with detailed phase and test history](https://github.com/dcirko-side-projects/higio/blob/24f90ca72dbe9246e56b2b064be9aee916a246fd/README.md)
