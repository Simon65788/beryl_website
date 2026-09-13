# Grade 10 Beryl website

Open `dist/index.html` in a modern browser. Keep `index.html`, `styles.css` and `app.js` together. No installation or build is required. The cursive Beryl font is bundled for offline use. Other typography uses Google Fonts when online and local fallback fonts offline.

## Sign in

Click Sign in to use an existing username and password, or Create account to register a new Berylite account. Registration cannot select or grant an admin role. Passwords must be 8–128 characters and are saved as salted PBKDF2-SHA-256 hashes. Accounts are saved only in the current browser.

Temporary admin username: **beryladmin**

Temporary admin password: **Beryl10!Admin2026**

These details are explicitly documented in `dist/admin-config.js`. Edit that file to change them. There is no admin signup form. The old name-only sign-in has been replaced; existing visitors need to create a Berylite account. Classroom content is retained.

This is a local prototype, not secure authentication. The password and role logic are visible in the JavaScript. Before public use, replace demo sign-in with server-verified accounts and permissions, and use shared database and image storage. Visitors currently see only what is saved in their own browser; changes do not synchronize between devices or users. Signing out does not erase classroom content. Avoid using real student personal information until an appropriate private deployment is ready.

## Make it your class

- Admin: upload both sides of the class photo. Click the large photo to flip it.
- Admin: add student names and gender groups. Open a student to upload two photos and edit their quote. Students cannot edit profiles.
- Everyone signed in: post colored notes and optional photos. Admin can delete messages and manage attached photos.
- Admin: create albums and add one or more photos. Open albums to view the full gallery.
- Photo controls: upload or replace, resize / crop with zoom and position sliders, or delete. Photos are compressed to a maximum dimension of 1200 pixels to reduce storage use.
- Bad Day: 100 unique messages are shuffled and used once per round. The sequence survives a refresh and avoids an immediate repeat between rounds.

The class roster contains 44 students imported from the supplied Beryl.xlsx: 25 Males followed by 19 Females. Names preserve the spreadsheet spelling. No class photographs have been invented. The introductory note remains; albums start empty.

## Local saving

Class content and encouragement progress use localStorage under `beryl-class-v1`. The active sign-in is temporary and resets on reload. Browser storage is limited; storage errors leave the previous saved data unchanged. Clearing browser data removes your class content. File URL storage behavior differs between browsers; use the same browser and file path, or serve the `dist` folder through a local static web server for a stable local origin.

The main sections target one screen each on ordinary desktops. Short screens, mobile devices, enlarged text and admin controls can require additional scrolling so content remains usable. Dialogs lock scrolling behind them and allow scrolling inside long galleries and lists. Escape and the close button dismiss dialogs.

## Files

- `dist/index.html` — semantic structure and all five sections
- `dist/styles.css` — green theme, responsive layouts, flip and breathing animations
- `dist/app.js` — classroom interactions and persistence

The optional WebMCP encouragement tool registers only in browsers that support it. Browser visual testing and WebMCP runtime validation were not performed in this environment.

## Publishing later

Upload the contents of `dist` to a static host when ready for a local-data demonstration. Real shared classroom use requires the account and storage changes described above; simply uploading these files will not add secure permissions or shared content.

## Bright classroom redesign

This edition adds a sunny original anime classroom background, a transparent stationery sticker sheet, a uniform Beryl gem mark, colorful square student portraits, taped sticky notes, a lined notebook composer with color swatches, improved navigation, and a skippable cursive opening. The Beryl letters draw in sequence, followed by a flourish, and the classroom opens only when the visitor selects Enter classroom. The animation plays on each page entry; reduced-motion preferences show static lettering and retain the entry button.

Native vertical scroll snapping centers panels in the space below the fixed header. Taller panels remain scrollable so mobile users and enlarged text do not lose access to content. The header highlights the current panel and shows reading progress. The existing local storage key is unchanged; content remains available when you replace files in the original folder and use the same browser and origin.

Assets were created using built-in image generation. Prompts: sunny mint anime classroom with emerald chalkboard, wooden desks, leafy window views and warm sunlight, no people or text; mint anime stationery stickers with white die-cut borders around the perimeter and a large transparent center. Artwork is included in `dist/assets`. The Beryl logo extends the original gem mark as an SVG. The bundled Z003 font and lettering derive from URW Base35; see `dist/assets/FONT-LICENSE.txt`.

## Roster and mobile update

The yellow progress stripe has been removed. The header now has an opaque white background and a shorter mobile layout. The opening uses a centered mobile layout and never advances automatically.

Search in Berylites searches the entire roster, not only the preview cards. Search ignores letter case and accents. Clear the search to return to the compact preview. View all students displays the complete alphabetical list, Males first then Females.

The Meet our adviser button opens a photo, name and message. Sign in as admin to upload the photo and edit the name and message. The fields are deliberately blank until the adviser fills them in. Adviser images support the existing replace, crop and delete controls.

Signing in and signing out now show a brief loading animation, followed by a confirmation dialog. These animations are part of the local demo, not a network authentication request.

The roster import merges with existing browser data and preserves matching students’ photos and quotes. Existing Boys/Girls groups migrate to Males/Females. Keep the same local folder and browser origin to retain previously saved data.

## Delete students and albums

When signed in as admin, open a student profile and choose Delete student. The confirmation removes that profile, its quote and both photos; its sign-in account is independent and is not deleted. Imported roster profiles remain deleted after refresh.

Open an album as admin and choose Delete album. The confirmation removes the album and all its photos. These changes apply to this browser’s saved classroom. Other accounts do not see the delete controls, and the delete handlers check for admin access.

## Account limitations

`auth.js` implements local registration and password verification. It reserves the configured admin username and always treats registered accounts as Berylites, even if a stored account record contains an admin role. Incorrect credentials, duplicate usernames, mismatched passwords, and unavailable storage produce errors.

Because all code and data are delivered to the browser, a visitor can inspect `admin-config.js` or manipulate local JavaScript/storage. This design prevents ordinary admin signup, but cannot protect admin access from deliberate inspection or tampering. Do not deploy it as secure public authentication. Move credential checking, role assignment, classroom data and delete authorization to a server before shared classroom use. Registered accounts do not synchronize across browsers, and clearing browser storage deletes those accounts.

## Message photo layout

Message attachments appear in square frames to the right of the message text, including on mobile and in message dialogs. Photos use contain sizing so the full image stays visible; portrait or landscape images may have space around them. Previously saved message crop settings are ignored in these frames so they do not cut off the image. Other classroom photo layouts are unchanged.

## Square holders and full album photos

Student profile photo holders, adviser portraits, message frames and photos inside albums are square. Home pictorial frames and Memories album covers keep their existing proportions. Select a square album thumbnail to open the full image in a viewer that follows its original proportions, fitting inside the screen without cropping. Back to album returns to the thumbnail gallery.

## Readable source and login dialogs

HTML, CSS and JavaScript are formatted with consistent indentation and line breaks. Sign-in and create-account forms do not dismiss when clicking the backdrop or pressing Escape. Use the Close button or the account actions. Invalid submissions keep the form open and show the error. Other dialogs retain their existing dismissal behavior.

## Green Yearbook redesign

This edition gives Beryl a new green classroom yearbook design: a centered cursive title above a wide arched class portrait, an emerald navigation header, two directory panels with student ID cards, a chalkboard noticeboard and writing desk, a pinned-photo memory wall, and a quiet forest-green encouragement page. The original classroom artwork is reused with new compositions. The roster, temporary admin details, accounts, photo tools, popup behaviors and storage keys are unchanged.

Replace the files in the same existing folder and use the same browser and origin to retain locally saved content. The code remains formatted for reading.
