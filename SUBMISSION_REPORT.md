# QuickBite — Submission Report

**Course activity:** Cross-Platform Mobile App Development & Testing  
**Framework:** React Native with Expo (JavaScript)  
**Repository:** https://github.com/yasiru-101/quick-bite  
**Build date:** 24 September 2026

## 1. Project summary

QuickBite is a campus canteen ordering prototype. Students can continue as guests or enter a first name, browse a local sample menu, search and filter by category, add dishes to a persistent cart, choose a pickup estimate, place a simulated order, and view the order's progress and recent history.

## 2. Implemented screens and behavior

| Screen | Behavior |
|---|---|
| Splash | Branded entry and transition to welcome |
| Login / guest access | Optional first-name profile or guest access |
| Home | Search, category filters, menu cards and responsive grid (two columns on phones, three on wider screens) |
| Item detail | Description, price, quantity selector and add-to-bag action |
| Cart | Shared cart state, quantities, item count, subtotal and checkout |
| Checkout | Pickup estimate, optional note and order summary |
| Confirmation | Generated order number and pickup estimate |
| Tracking | Simulated placed/preparing/ready progression |
| Profile | Name or guest label, order count and recent order history |

Menu items are local sample data. Cart, user name and order history are persisted on-device using AsyncStorage. No payment or live canteen/backend integration is included in this MVP.

## 3. Key implementation notes

- **Shared state and persistence:** React Context exposes cart operations, subtotal, profile and order history. AsyncStorage restores and saves the user's local state.
- **Responsive menu:** `useWindowDimensions` chooses a two-column phone grid or a three-column layout at widths of 700 points and above.
- **Order flow:** Checkout generates a `QB-xxxxxx` ID, records the order, clears the cart and starts tracking at preparation. Tracking simulates readiness after eight seconds.
- **Navigation:** React Navigation native stack and bottom tabs connect the screens.

## 4. Manual test log

The activity sheet calls for manual execution on phone and tablet sizes, a Pass/Fail record and screenshot evidence. These cases are prepared below; execution and screenshots are **pending** because Expo dependencies and a device/emulator were not available in the development environment. Do not submit pending rows as passed; execute them in Expo Go or simulators and attach the screenshots before LMS submission.

| ID | Test case | Expected result | Result | Evidence |
|---|---|---|---|---|
| T1 | Open app, enter a first name and continue | Home opens and greeting/profile show the name | Pending device run | Screenshot pending |
| T2 | Continue as guest, search “matcha”, then clear search and select Beverages | Guest home opens; matching menu item appears; category filter works | Pending device run | Screenshot pending |
| T3 | Open a dish, increase quantity to 2, add to bag | Cart shows two units and updates item count and subtotal | Pending device run | Screenshot pending |
| T4 | Navigate away from and back to cart; restart app | Cart state remains while navigating and is restored after restart | Pending device run | Screenshot pending |
| T5 | Submit checkout with pickup selection and optional note | Confirmation shows a generated order ID and selected pickup estimate | Pending device run | Screenshot pending |
| T6 | Open tracking and wait for simulated status update | Status advances from preparation to ready for pickup | Pending device run | Screenshot pending |
| T7 | Open profile after an order | Profile shows entered name (or guest), order count and order history | Pending device run | Screenshot pending |
| T8 | Run Home on phone-size and tablet-size viewport | Menu remains readable; two columns on phone and three on wider viewport | Pending phone/tablet run | Screenshots pending |

## 5. Screenshots

**Pending capture:** splash/welcome, phone menu, tablet menu, item detail, cart, confirmation/tracking, and profile. Capture from the running app and replace this section with the images before submission.

## 6. Setup and run

```sh
npm install
npx expo start
```

Scan the Expo Go QR code or launch an Android emulator. iOS Simulator requires macOS. Verify Expo with `npx expo --version` before the manual test run.

## 7. Submission checklist

- [x] React Native / Expo source and navigation
- [x] Local menu, search, category filters, shared cart and local persistence
- [x] Checkout, generated order IDs, tracking simulation and profile history
- [ ] Install dependencies and run on Android/iOS or Expo Go
- [ ] Execute and record each manual test on phone and tablet sizes
- [ ] Capture and insert app screenshots
- [ ] Push the final report and any evidence to the GitHub repository
- [ ] Submit the report through the LMS/designated folder
