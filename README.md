AR Study Hub — starter website
This project contains a frontend and a Supabase schema. It is a starter template, not a deployed website.
Files
`index.html` — responsive website, login, student material list, admin upload form, Supabase API calls.
`schema.sql` — database tables, row-level security, and private storage policies.
Setup
Create a project at https://supabase.com/
In Project Settings / API, copy the Project URL and the anon/publishable key.
Open `index.html` and replace:
`https://YOUR-PROJECT.supabase.co`
`YOUR_SUPABASE_ANON_OR_PUBLISHABLE_KEY`
In Supabase SQL Editor, run all of `schema.sql`.
In Supabase Authentication, create or invite your administrator account and any approved student accounts. Keep public sign-up disabled if you want only admin-approved users.
Find the administrator's user UUID in Authentication > Users. In SQL Editor, run:
`update public.profiles set role = 'admin', display_name = 'Raksha Mam' where id = 'YOUR-REAL-USER-UUID';`
Replace the UUID with the real UUID from your own project. Do not use an example UUID.
Host `index.html` on a static host with HTTPS, or test it using a local development server. Configure your Supabase Auth URL allow-list / redirect URLs for your deployed domain.
Sign in with the admin account and upload study files.
Security notes
The browser may contain the Supabase anon/publishable key; that key is intended for client-side use. NEVER put a Supabase service-role/secret key in HTML or JavaScript.
Admin status is checked in `profiles.role` and enforced with database/storage policies. Do not rely on hiding the admin panel alone.
The supplied SQL is a starter; review policies and test student/admin access before storing private materials.
The storage bucket is private. Files are opened using short-lived signed URLs.
The starter limits uploads to 20 MB and PDF/Word/PowerPoint MIME types. Server-side checks should be added for production, since browser file metadata can be spoofed.
Students can read all materials after login in this version. To require individual approval or limit materials by class/semester, add an approval field and corresponding RLS policies.
No credentials are included in these files.
