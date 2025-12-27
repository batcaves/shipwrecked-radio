# Weekly Plan (Clean): Flutter Radio App (AzuraCast) → Android + iOS by Feb 1

**Start date:** 2025-12-27  
**Target date:** 2026-02-01  
**Time budget:** ~1 hour/day + 1 full day/week (aim for ~12–15 hrs/week)  
**Platforms:** Android + iOS (single Flutter codebase)  
**MVP scope:** 4 separate AzuraCast mounts, background audio + media controls, push notifications (announcements), basic now-playing display, store release.

---

## Assumptions / non-negotiables
- **Apple Developer Program (Individual)** must be active to ship iOS.
- You must have **Mac access at least 3 times** before submission (build, push setup, upload).
- Push notifications use **Firebase Cloud Messaging (FCM)** with a topic like `announcements`.
- Keep scope tight (no logins, no reminders/scheduling, no ads) until after release.

---

## Week 1 (Dec 27 – Jan 2): Unblock everything + playable Android prototype
**Outcome:** accounts in progress + Android app plays streams.

### Admin / Accounts (critical path)
- [ ] Create an **Apple ID**
- [ ] Enroll in **Apple Developer Program (Individual)**
- [ ] Create **Google Play Developer** account
- [ ] Create **Firebase project** (for notifications)
- [ ] Create a simple **Privacy Policy** page (can be a basic hosted page; needed for stores)

### Technical (mostly Windows)
- [ ] Create Flutter repo + basic project structure
- [ ] Implement player screen:
  - [ ] list of 4 stations/mounts
  - [ ] play/pause
  - [ ] current station displayed
  - [ ] loading/error state
- [ ] Verify all 4 stream URLs play on Android device

### Mac session #1 (this week if possible)
- [ ] Confirm Mac is set up (Xcode, Flutter, CocoaPods)
- [ ] Build/run the Flutter app on iOS simulator or device (sanity check)

---

## Week 2 (Jan 3 – Jan 9): Background audio + stream switching quality
**Outcome:** “radio app behavior” works (background + controls + switching).

- [ ] Background playback works (screen off / app background)
- [ ] Lock screen / notification media controls (play/pause, title)
- [ ] Switching between 4 streams is reliable and quick
- [ ] Handle interruptions (calls, headphone disconnect) without crashes
- [ ] Basic network resilience (recover after loss)

**End of week checkpoint:** Android experience feels stable and “real”.

---

## Week 3 (Jan 10 – Jan 16): Push notifications end-to-end (Android + iOS)
**Outcome:** you can send an announcement push and receive it on both platforms.

### Firebase / FCM
- [ ] Add Firebase to Android build
- [ ] App subscribes to topic: `announcements`
- [ ] Test push from Firebase Console → Android device receives it

### Mac session #2 (required this week)
- [ ] Add Firebase to iOS build
- [ ] Configure APNs for Firebase (APNs auth key path)
- [ ] Request notification permission on iOS
- [ ] Test push from Firebase Console → iPhone receives it

**Optional (if time):**
- [ ] Display “Now Playing” metadata in app using AzuraCast API

---

## Week 4 (Jan 17 – Jan 23): Store readiness + beta tracks (TestFlight + Play testing)
**Outcome:** store listing assets ready + builds distributed to testers.

### Product polish / compliance
- [ ] Final app name + icon set + splash screen
- [ ] About screen + Privacy Policy + Support/Contact links
- [ ] Confirm “data collected” (keep minimal; disclose push token usage)

### Android release pipeline (Play Console)
- [ ] Create app in Play Console
- [ ] Fill required forms (Data Safety, content declarations)
- [ ] Upload AAB to **Internal testing** (or required track)
- [ ] Add a small tester list (friends/devices) and verify install + playback + push

### iOS release pipeline (App Store Connect)
- [ ] Create app record in App Store Connect
- [ ] Upload build to **TestFlight**
- [ ] Test on a real iPhone (audio background + push + switching)

---

## Week 5 (Jan 24 – Feb 1): Submission + review buffer + last fixes
**Outcome:** approved and live (or as close as possible with review timing).

### Submission targets
- [ ] **Submit iOS** no later than **Jan 24–Jan 26** (gives buffer)
- [ ] **Move Android** from testing to production as soon as Play requirements allow

### Final QA checklist (both platforms)
- [ ] All 4 mounts play
- [ ] Background audio works
- [ ] Stream switching works while playing
- [ ] Push announcements arrive
- [ ] App doesn’t crash on start/stop/switch
- [ ] Store screenshots match UI
- [ ] Privacy Policy link works publicly

### Mac session #3 (submission / fixes)
- [ ] Archive + upload final build(s)
- [ ] Fix any signing/provisioning issues
- [ ] Respond to store review feedback quickly

---

## Weekly cadence (recommended use of your time)
**Daily (1 hour):**
- UI + player logic + testing + small incremental improvements

**Weekly full day (6–8 hours):**
- “Release engineering” work:
  - Firebase config + push tests
  - iOS build/signing
  - store console forms, screenshots, submissions
  - regression testing on real devices

---

## Definition of Done (Feb 1)
- [ ] Android app live on Play Store (production)
- [ ] iOS app live on App Store (production)
- [ ] Push announcement workflow works (Firebase Console is OK)
- [ ] Stable playback + stream switching + background audio on both platforms

---

## Info you should add to docs (fill these in)
- **Stream 1 name + URL:**
- **Stream 2 name + URL:**
- **Stream 3 name + URL:**
- **Stream 4 name + URL:**
- **AzuraCast Now Playing API endpoint (if used):**
- **Firebase project name:**
- **Privacy policy URL:**
- **Support/contact email:**