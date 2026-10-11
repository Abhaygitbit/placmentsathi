# CDGI Placement App

Training and Placement application for **Chameli Devi Group of Institutions (CDGI), Indore**.

The first version helps students discover placement drives, check their eligibility, apply for drives, and view results. It also gives placement coordinators a simple way to manage drives, mark attendance, update rounds, and export reports.

## Phase 1 features

- Student login with enrollment number and OTP
- Student profile, academics, skills, and PDF resume
- Company and placement-drive management
- Clear eligibility result with reasons
- Drive registration and withdrawal before the deadline
- Coordinator attendance by checklist, enrollment number, and rotating QR code
- Round-wise selection status
- Announcements and notifications
- Student/drive reports and Excel/PDF exports
- CSV/Excel bulk import for students and drives

## Technology

| Part | Technology |
| --- | --- |
| Student and coordinator mobile app | React Native, Expo, TypeScript |
| Admin dashboard | Next.js, TypeScript |
| Backend, authentication, database, files | Supabase |
| Database | PostgreSQL with Row Level Security |
| Notifications | Expo Notifications / FCM |

## Project structure

```text
cdgi-placement/
|- apps/
|  |- mobile/       # Expo app for students and coordinators
|  `- admin/        # Next.js dashboard for TPO, HOD, and coordinators
|- packages/
|  `- shared/       # Shared TypeScript types and constants
|- supabase/
|  |- migrations/   # Database migration SQL
|  |- functions/    # Supabase Edge Functions
|  `- tests/        # Database tests
`- README.md
```

## Prerequisites

- Node.js LTS
- Git
- A Supabase project
- Android phone with the **Expo Go** app installed

## Run the mobile app on Android

Open Command Prompt (CMD), then run:

```cmd
cd /d C:\Users\Abhay\cdgi-placement\apps\mobile
npm install
npx expo start --clear --tunnel
```

Scan the QR code from Expo Go on your Android phone. Tunnel mode works even if the phone and laptop are on different networks.

## Run the admin dashboard

Open another CMD window:

```cmd
cd /d C:\Users\Abhay\cdgi-placement\apps\admin
npm install
npm run dev
```

Open `http://localhost:3000` in the browser.

## Supabase environment variables

Create `apps/mobile/.env`:

```env
EXPO_PUBLIC_SUPABASE_URL=https://YOUR_PROJECT_REF.supabase.co
EXPO_PUBLIC_SUPABASE_PUBLISHABLE_KEY=YOUR_PUBLISHABLE_KEY
```

Create `apps/admin/.env.local`:

```env
NEXT_PUBLIC_SUPABASE_URL=https://YOUR_PROJECT_REF.supabase.co
NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY=YOUR_PUBLISHABLE_KEY
```

Get these values from Supabase Dashboard -> Project Connect.

Never commit `.env` files or a Supabase `service_role` key.

## Security rules

- Students can access only their own profiles, applications, attendance, and notifications.
- Coordinators can manage only drives and branches assigned to them.
- Admins have full placement-module access.
- Marks, attendance, results, imports, and audit logs are protected with Supabase Row Level Security.
- Attendance/result changes must be auditable with actor and timestamp.

## Development status

Phase 1 setup is in progress. The next build order is:

1. Authentication
2. Student profile
3. Drive list and eligibility badge
4. Apply flow
5. Coordinator drive creation
6. Offline attendance
7. Round results, reports, notifications, and dashboard

## Git

Before pushing changes:

```cmd
git status
git add .
git commit -m "describe your change"
git push
```

Do not commit `node_modules`, `.env`, Expo cache files, or build output.
