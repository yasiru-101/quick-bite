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

Executed against the Android emulator build on 24 September 2026 (1080×2400 phone viewport, Android package `edu.quickbite.app`). The menu and order flow are local/simulated. The tablet screenshot was taken by increasing the emulator's Android display size and density; it demonstrates the wide viewport but is not a run on a separate tablet device. iOS was not tested.

| ID | Test case | Result | Evidence |
|---|---|---|---|
| T1 | Enter first name and continue | Pass — home greeting displayed the entered name | [Home](evidence/07-home-phone.png) |
| T2 | Filter by Beverages | Pass — only beverage items displayed | [Category filter](evidence/08-beverages-filter.png) |
| T3 | Open dish detail and add to bag | Pass — item detail and cart subtotal reflected Rs 580 | [Item detail](evidence/09-item-detail.png), [Cart](evidence/10-cart.png) |
| T4 | Move between menu and cart | Pass — cart item and count remained during navigation | [Cart](evidence/10-cart.png) |
| T5 | Place order with pickup selection | Pass — confirmation displayed generated order QB-166886 and ASAP · 15 min | [Checkout](evidence/11-checkout.png), [Confirmation](evidence/13-confirmation.png) |
| T6 | Open tracking and wait for simulated status change | Pass — order status advances to Ready for pickup after eight seconds in app state | [Tracking](evidence/14-tracking-preparing.png), [Ready state](evidence/15-tracking-ready.png) |
| T7 | Open profile after order | Pass — profile showed Yasiru and the recent order | [Profile and order history](evidence/16-profile-history.png) |
| T8 | Check phone and wide viewport layout | Pass — two-column phone menu and wider viewport captured. Wide viewport was simulated using emulator display overrides, not a tablet AVD. | [Phone](evidence/07-home-phone.png), [Wide viewport](evidence/17-tablet-menu.png) |

Persistence is implemented using AsyncStorage. This emulator run verified cart state through navigation, but did not independently verify restoration after force-stop/relaunch. Search input is implemented; the recorded manual filter case used category selection.

## 5. Screenshots

Selected screenshots are linked from the test log above. Additional captures are stored in [`evidence/`](evidence/).
## 6. Setup and run

```sh
npm install
npx expo start
```

Scan the Expo Go QR code or launch an Android emulator. iOS Simulator requires macOS. The Android emulator run and Gradle debug APK build completed. The optional `expo export` bundle command could not run in the restricted Windows environment because launching Hermes failed with `spawn EPERM`.

## 7. Submission checklist

- [x] React Native / Expo source and navigation
- [x] Local menu, search, category filters, shared cart and local persistence
- [x] Checkout, generated order IDs, tracking simulation and profile history
- [x] Install dependencies and run on Android emulator
- [x] Execute Android phone and simulated wide-viewport checks; see limitations in test log
- [x] Capture and insert app screenshots
- [x] Push the final report and evidence to the GitHub repository
- [ ] Submit the report through the LMS/designated folder
