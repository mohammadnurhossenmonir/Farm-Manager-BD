# Farm Manager BD — Starter Project

এটি Farm Manager BD-এর Flutter + Supabase starter source code। এটি এখনো Play Store/App Store-এ প্রকাশিত বা সম্পূর্ণ production-ready অ্যাপ নয়।

## যা আছে
- Flutter Android/iOS/Web project scaffold
- বাংলা UI-এর প্রাথমিক ড্যাশবোর্ড
- পশু যোগ করার প্রাথমিক স্ক্রিন
- Supabase schema: farms, members, animals, health, feed, milk, invitations
- Supabase Auth integration point

## চালানোর আগে
1. Flutter SDK ইনস্টল করুন।
2. Supabase-এ একটি project তৈরি করুন।
3. SQL Editor-এ `supabase/schema.sql` চালান।
4. Supabase Authentication-এ Phone provider কনফিগার করুন এবং SMS provider যুক্ত করুন।
5. Flutter project-এ URL ও anon key দিয়ে চালান:

```bash
flutter pub get
flutter run --dart-define=SUPABASE_URL=https://YOUR_PROJECT.supabase.co --dart-define=SUPABASE_ANON_KEY=YOUR_ANON_KEY
```

Web build:
```bash
flutter build web --dart-define=SUPABASE_URL=... --dart-define=SUPABASE_ANON_KEY=...
```

Android build:
```bash
flutter build apk --release --dart-define=SUPABASE_URL=... --dart-define=SUPABASE_ANON_KEY=...
```

## গুরুত্বপূর্ণ নিরাপত্তা ও অসম্পূর্ণ কাজ
- `service_role` key কখনো Flutter app-এ দেবেন না।
- Invitation code তৈরি/রিডিম trusted Edge Function বা secure RPC দিয়ে করতে হবে; raw code database-এ নয়, hash রাখতে হবে।
- Owner/Manager/Employee-এর granular permissions production-এ প্রয়োগ করতে হবে।
- বর্তমান schema-র member access policy সদস্যদের রেকর্ডে প্রবেশ দেয়; employee restrictions ও owner-only destructive actions আরও কঠোর করতে হবে।
- OTP SMS-এর জন্য Supabase Auth phone provider এবং SMS gateway configuration দরকার।
- Farm creation, farm switching, breeding, weight history, income/expense, reports, localization, push notifications এবং audit log পরবর্তী development task।
- App Store/Play Store release-এর আগে testing, privacy policy, terms, backups ও security review দরকার।
