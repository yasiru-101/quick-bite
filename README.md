# QuickBite

Campus food ordering MVP built with React Native and Expo.

## Run it

```sh
npm install
npx expo start
```

Open the QR code with Expo Go, or press `a` / `i` for an Android emulator / iOS simulator.

## Included flows

- Splash and guest welcome screen
- Searchable, category-filtered menu with item details and quantity selection
- Persistent cart with live subtotal, checkout, and pickup selection
- Order confirmation, order tracking, and order history in the profile
- Adaptive two-column phone / three-column tablet menu

Cart and recent order state are stored locally with AsyncStorage. The order status advances from placed/preparing to ready-state presentation; this is a front-end prototype with local sample menu data.
