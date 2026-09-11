# Business Entity Mahjong

A real-time classroom multiplayer card game for IBDP Business Management 1.2.

## What students do
1. Start with 5 cards.
2. On your turn, take 1 card from the deck OR the latest discarded card.
3. You now have 6 cards.
4. Dump 1 card.
5. Build all 5 different characteristics of one business entity.
6. Press **ENTITY!** to claim the win.

The entity name is hidden from each characteristic card, so students must understand the business meaning.

## Supported entities
- Sole Trader
- Partnership
- Private Limited Company
- Public Limited Company / Corporation

There are two copies of each characteristic in the deck. A winning hand still needs all five *different* traits from one entity.

## Firebase setup
This site is static and can be hosted on GitHub Pages, but real-time multiplayer needs Firebase.

### 1. Create / use a Firebase project
In Firebase Console, create or open a project.

### 2. Add a Web App
Project settings → Your apps → Add Web App.
Copy the `firebaseConfig` object.

Open `index.html`, find:

```js
const firebaseConfig = {
  apiKey: "PASTE_API_KEY_HERE",
  ...
};
```

Replace those placeholder values with your Firebase Web App values.

### 3. Enable Anonymous Authentication
Firebase Console → Authentication → Sign-in method → Anonymous → Enable.

### 4. Create Realtime Database
Firebase Console → Realtime Database → Create database.

For a classroom prototype, use these rules:

```json
{
  "rules": {
    "rooms": {
      "$roomId": {
        ".read": "auth != null",
        ".write": "auth != null"
      }
    }
  }
}
```

These rules are suitable for a classroom prototype, not a public production service.

### 5. Upload to GitHub
Upload `index.html` to your repository, then enable GitHub Pages.

## Recommended classroom use
- 2–6 players per room
- For a large class, make several rooms
- Best on phones, tablets, Chromebooks, or laptops
- Teacher can create a room and display the six-character room code

## Teaching note
A player only wins if:
- all 5 cards belong to the same entity, AND
- all 5 are different characteristics.

Two copies of the same characteristic do not count as a complete set.
