# FurAndFound — Full Design & Product Documentation

**Version:** 2.0  
**Date:** 2026-05-10  
**Author:** Marcus Kwan  
**Status:** Active

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Problem Statement](#2-problem-statement)
3. [Target Audience](#3-target-audience)
4. [Branding & Visual Design](#4-branding--visual-design)
5. [Component Library](#5-component-library)
6. [Navigation](#6-navigation)
7. [Footer](#7-footer)
8. [Pages](#8-pages)
   - 8.1 Home
   - 8.2 Browse Breeds
   - 8.3 Why Adopt
   - 8.4 Pet Care
   - 8.5 How It Works
   - 8.6 Lost Pet
   - 8.7 Found a Pet
   - 8.8 Success Stories
   - 8.9 FAQ
   - 8.10 Contact Us
   - 8.11 About Us
   - 8.12 Local Shelters & Vets
   - 8.13 User Profile
   - 8.14 Pet Detail Page
9. [User Flows](#9-user-flows)
10. [Data Models](#10-data-models)
11. [Feature Specifications](#11-feature-specifications)
12. [Must-Have vs Stretch Goals](#12-must-have-vs-stretch-goals)
13. [Tech Stack](#13-tech-stack)
14. [Out of Scope](#14-out-of-scope)

---

## 1. Project Overview

FurAndFound is a lost pet finder website that helps first-time dog and cat owners know exactly what to do when their pet goes missing. It combines a step-by-step action checklist with a community lost-and-found board where owners can post missing pets and finders can report strays.

---

## 2. Problem Statement

When a pet goes missing, first-time owners panic and waste critical time because they do not know what to do. There is no single, simple place that gives them a calm step-by-step plan AND lets them post their pet so the local community can help find it.

**FurAndFound solves two problems at once:**
- A clear checklist of actions to take in the first 24 hours.
- A community board to post lost pets and search for found ones.

---

## 3. Target Audience

| Property | Detail |
|---|---|
| Primary user | First-time dog or cat owner whose pet just went missing |
| Secondary user | Anyone who found a stray and wants to reunite it with its owner |
| Age range | Any age |
| Experience level | No experience with lost pet situations |
| Emotional state | Panicked, confused — needs calm and clear guidance |
| Devices | Desktop computer and mobile phone |

---

## 4. Branding & Visual Design

### 4.1 Site Name
**FurAndFound**

### 4.2 Logo
- Paw print icon (🐾) + bold text "FurAndFound"
- Top-left corner of every page
- Clicking the logo always returns to the Home page
- Colour: deep orange `#c05010`

### 4.3 Colour Palette

| Name | Hex | Used For |
|---|---|---|
| Cream | `#faeade` | Page background (light mode) |
| Deep orange | `#c05010` | Logo, primary buttons, active nav, highlights |
| Light orange | `#e8621a` | Button hover states |
| Dark text | `#1a1a1a` | All headings |
| Body gray | `#444444` | Paragraph text |
| Subtle gray | `#777777` | Subtitles, captions, placeholders |
| White | `#ffffff` | Cards, modals, form inputs |
| Green (success) | `#28a745` | Reunited badge, success messages |
| Red (error) | `#dc3545` | Error messages, delete buttons |
| Urgent red | `#e63946` | URGENT label on posts |
| Dark bg | `#1a1a1a` | Dark mode page background |
| Dark card | `#2a2a2a` | Dark mode card background |
| Dark nav | `#111111` | Dark mode nav background |

### 4.4 Typography

| Element | Size | Weight | Colour |
|---|---|---|---|
| Hero heading (H1) | 3rem | 800 | `#1a1a1a` |
| Page heading (H1) | 2.2rem | 800 | `#1a1a1a` |
| Section heading (H2) | 1.5rem | 700 | `#1a1a1a` |
| Card heading (H3) | 1.1rem | 700 | `#1a1a1a` |
| Body text | 1rem | 400 | `#444444` |
| Small/caption | 0.85rem | 400 | `#777777` |
| Label | 0.88rem | 600 | `#1a1a1a` |
| Font family | `Segoe UI`, Arial, sans-serif | — | — |

### 4.5 Spacing & Layout

| Property | Value |
|---|---|
| Max content width | 1100px, centred |
| Page padding (desktop) | 48px left and right |
| Page padding (mobile) | 16px left and right |
| Card border radius | 16px |
| Button border radius | 50px (pill shape) |
| Input border radius | 8px |
| Card box shadow | `0 2px 16px rgba(0,0,0,0.07)` |

### 4.6 Dark Mode

- Toggled by a moon/sun icon button in the nav bar
- Saves user preference in localStorage
- Swaps background, card, nav, and text colours using CSS variables
- All orange accent colours stay the same in both modes

### 4.7 Responsive Design

| Breakpoint | Behaviour |
|---|---|
| Desktop (> 768px) | Full nav bar, multi-column grids |
| Mobile (≤ 768px) | Hamburger menu (☰), single column layout |

---

## 5. Component Library

### 5.1 Buttons

| Name | Style | Used For |
|---|---|---|
| Primary | Orange fill, white text, pill shape | Main actions (Post, Submit, Sign In) |
| Outline | Orange border, orange text, transparent fill | Secondary actions (Learn More) |
| Danger | Red fill, white text | Delete post |
| Ghost | No border, orange text | Subtle links (toggle auth) |

**States for all buttons:** default → hover (slightly lighter) → disabled (50% opacity)

### 5.2 Cards

| Name | Description |
|---|---|
| Info card | White background, emoji icon, heading, short paragraph. Used on Browse Breeds, Why Adopt, Pet Care |
| Pet card | Photo or emoji placeholder at top, pet name, type badge, details, action buttons |
| Story card | Photo, pet name, short reunited story, date |
| Shelter card | Shelter name, address, phone, opening hours |

### 5.3 Badges & Labels

| Badge | Colour | Meaning |
|---|---|---|
| REUNITED | Green | Pet has been found and is home |
| URGENT | Red | Owner flagged as time-sensitive |
| Dog / Cat | Orange pill | Animal type on search cards |

### 5.4 Form Inputs

All inputs share the same style:
- Background: `#fafafa` (light mode), `#333` (dark mode)
- Border: `1.5px solid #ddd`
- Border on focus: `1.5px solid #c05010` (orange)
- Padding: `10px 14px`
- Border radius: `8px`
- Font size: `0.95rem`

### 5.5 Modals

- Triggered by buttons (Sign In, Forgot Password, Report Post, I Found This Pet)
- Semi-transparent dark backdrop behind modal
- White card, rounded corners, ✕ close button top-right
- Clicking backdrop also closes the modal

### 5.6 Loading Animations

- **Spinner:** A small circular orange spinner for button loading states
- **Skeleton cards:** Grey pulsing placeholder cards shown while the pet grid loads
- Used on: pet grid load, form submit, photo upload

### 5.7 Toast Notifications

- Small banner that slides in from the bottom-right
- Green for success, red for error
- Disappears automatically after 3 seconds

---

## 6. Navigation

### 6.1 Desktop Nav Layout

```
+------------------------------------------------------------------------+
| 🐾 FurAndFound  Home  Browse  Why Adopt  Pet Care  How It Works        |
|                 Lost Pet  Found a Pet  Stories    🌙  [Sign In] [Adopt Now] |
+------------------------------------------------------------------------+
```

### 6.2 Nav Items (Desktop)

| Label | Destination | Notes |
|---|---|---|
| Home | Home page | |
| Browse Breeds | Browse Breeds page | |
| Why Adopt | Why Adopt page | |
| Pet Care | Pet Care page | |
| How It Works | How It Works page | |
| Lost Pet | Lost Pet page | Core feature |
| Found a Pet | Found a Pet page | |
| Stories | Success Stories page | |
| 🌙 / ☀️ | Toggles dark mode | Icon button, no label |
| Sign In | Opens auth modal | Hidden when logged in |
| Sign Out | Logs user out | Visible when logged in |
| 👤 Name chip | User's profile page | Visible when logged in |
| Adopt Now | petfinder.com (new tab) | Orange pill button, always visible |

### 6.3 Active State
- Current page nav link turns orange with an underline
- Only one link is active at a time

### 6.4 Mobile Nav (≤ 768px)

```
+-------------------------------------------+
| 🐾 FurAndFound                        ☰  |
+-------------------------------------------+
```

- Hamburger icon (☰) on the right
- Tapping ☰ slides down a full-width dropdown menu
- All nav links stacked vertically
- Adopt Now button full width at the bottom of the menu
- Tapping any link closes the menu

---

## 7. Footer

Shown at the bottom of every page.

### 7.1 Layout

```
+----------------------------------------------------------------+
| 🐾 FurAndFound                                                 |
| Helping reunite pets with their families.                      |
|                                                                |
| Quick Links        Resources         Legal                     |
| Home               FAQ               Privacy Policy            |
| Lost Pet           Contact Us        Terms of Use              |
| Found a Pet        About Us                                    |
| Success Stories    Local Shelters                              |
|                                                                |
| © 2026 FurAndFound. Made with ❤️ by Marcus Kwan.              |
+----------------------------------------------------------------+
```

### 7.2 Footer Columns

| Column | Links |
|---|---|
| Quick Links | Home, Lost Pet, Found a Pet, Success Stories |
| Resources | FAQ, Contact Us, About Us, Local Shelters |
| Legal | Privacy Policy, Terms of Use |

---

## 8. Pages

---

### 8.1 Home Page

**URL:** `/` (index)  
**Purpose:** Welcome visitors, explain what FurAndFound does, and push them toward the most important actions.

#### Wireframe

```
+----------------------------------------------------------------+
| NAV                                                            |
+----------------------------------------------------------------+
|                                                                |
|  Give a Pet a              +----------------------------+      |
|  Second Chance             |                            |      |
|  (orange: Second Chance)   |     Dog photo              |      |
|                            |     420 x 320px            |      |
|  Subheading paragraph      |     rounded corners        |      |
|  3–4 sentences             |                            |      |
|                            +----------------------------+      |
|  💡 Callout box                                                |
|  (orange left border)                                          |
|                                                                |
|  [Browse Breeds]  [Learn Why It Matters]                       |
|                                                                |
+----------------------------------------------------------------+
|  🚨 EMERGENCY SECTION                                          |
|  "Did your pet just go missing?"                               |
|  Big orange button: [Report a Lost Pet Right Now →]            |
+----------------------------------------------------------------+
|  HOW IT WORKS — 3 ICON STEPS                                   |
|  [📝 Post your pet] → [🔍 Community searches] → [🏠 Reunited] |
+----------------------------------------------------------------+
|  RECENTLY POSTED LOST PETS                                     |
|  Row of 4 pet cards (most recent posts)                        |
|  [View All Lost Pets →]                                        |
+----------------------------------------------------------------+
|  STATS BAR                                                     |
|  🐾 48 Pets Posted   ✅ 12 Reunited   👥 200 Members          |
+----------------------------------------------------------------+
| FOOTER                                                         |
+----------------------------------------------------------------+
```

#### Sections

| Section | Details |
|---|---|
| Hero | Heading, subtext, callout box, two buttons, dog photo |
| Emergency banner | Red/orange background strip, heading, single big CTA button linking to Post a Lost Pet form |
| How It Works summary | 3 steps shown as icons in a row — Post, Search, Reunited |
| Recently posted pets | 4 most recent pet cards pulled from posted data |
| Stats bar | Shows total pets posted, total reunited, total members — pulled from localStorage data |

---

### 8.2 Browse Breeds Page

**URL:** `/browse-breeds`  
**Purpose:** Help visitors learn about common dog and cat breeds before adopting.

#### Wireframe

```
+----------------------------------------------------------------+
| PAGE BANNER (hero image + title overlay)                       |
| "Browse Breeds"                                                |
+----------------------------------------------------------------+
|  Learn about different breeds to find your perfect match.      |
|                                                                |
|  +----------+  +----------+  +----------+                     |
|  | 🐕        |  | 🐩        |  | 🐈        |                   |
|  | Golden   |  | Poodle   |  | Siamese  |                     |
|  | Retriever|  |          |  |          |                     |
|  +----------+  +----------+  +----------+                     |
|  (repeats for all breeds)                                      |
|                                                                |
|  [Find a Breed on Petfinder →]                                 |
+----------------------------------------------------------------+
```

#### Breed Cards (6 total)

| Breed | Emoji | Description |
|---|---|---|
| Golden Retriever | 🐕 | Friendly, reliable, great with families and children |
| Poodle | 🐩 | Highly intelligent and energetic, very trainable |
| Siamese Cat | 🐈 | Vocal, social, and affectionate, loves people |
| Maine Coon | 🐱 | Gentle giant, playful, great with kids |
| Labrador Retriever | 🦮 | Popular, kind, outgoing, and active |
| Mixed Breed | 🐾 | Unique, often healthier, just as loving |

---

### 8.3 Why Adopt Page

**URL:** `/why-adopt`  
**Purpose:** Educate visitors on the benefits of adopting rather than buying.

#### Info Cards (4 total)

| Card | Emoji | Heading | Detail |
|---|---|---|---|
| 1 | ❤️ | Save a Life | Millions of healthy pets are in shelters |
| 2 | 💰 | Lower Cost | Adopted pets are usually vaccinated and microchipped |
| 3 | 🏠 | Fight Puppy Mills | Reduces demand for inhumane breeding |
| 4 | 😊 | Better for You | Pet owners have lower stress and blood pressure |

**External link:** "Read More at Humane Society →" opens humanesociety.org in a new tab.

---

### 8.4 Pet Care Page

**URL:** `/pet-care`  
**Purpose:** Give new pet owners tips on keeping their dog or cat healthy.

#### Info Cards (6 total)

| Card | Emoji | Topic | Key tip |
|---|---|---|---|
| 1 | 🥗 | Nutrition | Fresh water always available, avoid grapes and chocolate |
| 2 | 🏃 | Exercise | Dogs: 30 min daily. Cats: interactive play twice a day |
| 3 | 🏥 | Vet Visits | Annual check-ups, keep vaccines up to date |
| 4 | 🔖 | ID & Microchip | Always use an ID tag, ask vet about microchipping |
| 5 | 🛁 | Grooming | Brush regularly, trim nails monthly, bathe dogs every 4–8 weeks |
| 6 | 🧠 | Mental Health | Rotate toys, train new tricks, give plenty of love |

---

### 8.5 How It Works Page

**URL:** `/how-it-works`  
**Purpose:** Walk new visitors through the 5-step process of using FurAndFound.

#### Steps (5 total)

| # | Title | Description |
|---|---|---|
| 1 | Create a free account | Sign up with name, email, city, and password |
| 2 | Post your lost pet | Fill in details, upload up to 4 photos, add your contact number |
| 3 | Your post goes live | Anyone visiting the site can search and see your listing immediately |
| 4 | Follow the 24-hour checklist | Our step-by-step guide tells you exactly what to do |
| 5 | Mark as found when reunited | Your post gets a green REUNITED badge |

**CTA button:** "Go to Lost Pet →" navigates to the Lost Pet page.

---

### 8.6 Lost Pet Page

**URL:** `/lost-pet`  
**Purpose:** Core feature. Contains three sub-tabs: checklist, post form, and search.

#### Sub-Tab Bar

```
+----------------------------------------------------------------+
|  📋 What To Do  |  📢 Post a Lost Pet  |  🔍 Search Lost Pets  |
+----------------------------------------------------------------+
```

---

#### 8.6.1 Sub-Tab: What To Do (Checklist)

**Purpose:** Calm, step-by-step tick-off guide for the first 24 hours after a pet goes missing.

##### Wireframe

```
+----------------------------------------------------------------+
|  SELECT YOUR PET TYPE:  [🐶 Dog]  [🐱 Cat]                    |
|                                                                |
|  Your pet is missing. Stay calm and follow these steps.        |
|                                                                |
|  +----------------------------------------------------------+  |
|  | ① Search your home and yard first                  [ ] |  |
|  |   Check hiding spots — under beds, in closets          |  |
|  +----------------------------------------------------------+  |
|  | ② Walk around the neighbourhood                    [ ] |  |
|  |   Call your pet's name. Bring a favourite toy.         |  |
|  +----------------------------------------------------------+  |
|  | (steps 3–8...)                                          |  |
|  +----------------------------------------------------------+  |
|                                                                |
|  [+ Add a Custom Step]       [🖨 Print Checklist]             |
+----------------------------------------------------------------+
```

##### Dog Checklist (8 steps)

| # | Title | Tip |
|---|---|---|
| 1 | Search your home and yard first | Check under beds, behind furniture, in closets |
| 2 | Walk around the neighbourhood | Call their name, bring a favourite toy or treat |
| 3 | Call your local animal shelter | Give a description, ask them to hold your dog if found |
| 4 | Contact your vet | Let them know in case someone brings your dog in |
| 5 | Post your dog on this site | Add a photo so neighbours can help |
| 6 | Put up posters in your neighbourhood | Include photo, name, and your phone number |
| 7 | Ask your neighbours | Knock on nearby doors |
| 8 | Check back with the shelter daily | New animals come in every day |

##### Cat Checklist (8 steps)

| # | Title | Tip |
|---|---|---|
| 1 | Search inside your home thoroughly | Cats hide in very small, dark spaces |
| 2 | Check your yard at dusk and dawn | Cats are most active at these times |
| 3 | Set out food and their litter box outside | Familiar smells help cats find their way home |
| 4 | Call your local animal shelter | Describe your cat's markings and colour |
| 5 | Contact your vet | Alert them in case someone brings your cat in |
| 6 | Post your cat on this site | Add a clear close-up photo |
| 7 | Put up posters in your neighbourhood | Include photo, name, and your phone number |
| 8 | Ask neighbours to check garages and sheds | Cats often get accidentally trapped |

##### Custom Steps

- Users can add their own steps using a text input
- Plain text only — no links or special characters allowed
- Maximum 10 custom steps per user
- Custom steps are saved in localStorage

##### Other Behaviours

| Behaviour | Detail |
|---|---|
| Checkbox save | Checked state saved in localStorage, persists after closing the browser |
| Auto reset | Checked steps reset automatically after 30 days |
| Step number colour | Orange circle by default, turns green with ✓ when checked |
| Pet type toggle | Switching between Dog and Cat loads the correct checklist |
| Print button | Opens the browser print dialog showing only the checklist |

---

#### 8.6.2 Sub-Tab: Post a Lost Pet

**Purpose:** Let signed-in owners submit a lost pet report with full details and up to 4 photos.

##### Wireframe

```
+-----------------------------------------------+
|  POST A LOST PET                               |
|                                                |
|  [ ] Mark as URGENT                            |
|                                                |
|  Pet's Name          Animal Type               |
|  [______________]    [Dog / Cat ▼]             |
|                                                |
|  Breed / Description   Colour                  |
|  [______________]    [______________]          |
|                                                |
|  Age                  Has microchip/ID tag?    |
|  [______________]    [Yes / No / Not sure ▼]   |
|                                                |
|  Date went missing    Last Seen Location        |
|  [______________]    [______________]          |
|                                                |
|  Your Phone Number                             |
|  [____________________________________]        |
|                                                |
|  Extra Details (optional)                      |
|  [____________________________________]        |
|  [____________________________________]        |
|                                                |
|  Add Photos (up to 4)                          |
|  +------+ +------+ +------+ +------+           |
|  |  +   | |  +   | |  +   | |  +   |          |
|  +------+ +------+ +------+ +------+           |
|                                                |
|  [  Post Lost Pet  ]                           |
+-----------------------------------------------+
```

##### Form Fields

| Field | Input Type | Required | Notes |
|---|---|---|---|
| URGENT toggle | Checkbox | No | Adds red URGENT badge to the post |
| Pet's Name | Text | Yes | |
| Animal Type | Dropdown | Yes | Dog or Cat |
| Breed / Description | Text | No | |
| Colour | Text | No | |
| Age | Text | No | e.g. "2 years" or "8 months" |
| Microchip / ID Tag | Dropdown | No | Yes / No / Not sure |
| Date went missing | Date picker | Yes | Owner selects from calendar |
| Last Seen Location | Text | Yes | |
| Your Phone Number | Tel | Yes | |
| Extra Details | Textarea | No | Any other helpful info |
| Photos | File (multi) | No | Up to 4 images, JPG or PNG |

##### Photo Upload Behaviour

- 4 upload slots shown as boxes with a + icon
- Clicking a box opens the OS file picker
- After selecting, a thumbnail preview fills the box
- Clicking a filled box replaces the photo
- An ✕ button on each preview removes that photo
- Photos stored as base64 data URLs in localStorage

##### Auth Requirement

- Logged-out users see: notice + "Sign In to Post" button
- After signing in the form appears without page reload

##### On Submit

- Validates all required fields, shows inline error if missing
- Shows a green toast notification: "[Pet name] has been posted!"
- Clears the form
- New post appears immediately on the Search tab

---

#### 8.6.3 Sub-Tab: Search Lost Pets

**Purpose:** Let anyone browse and search all posted lost pets.

##### Wireframe

```
+----------------------------------------------------------------+
|  [Search by name or location...]  [All Animals ▼]  [Sort ▼]  |
|  [Date: All time ▼]                                            |
|                                                                |
|  +----------+  +----------+  +----------+  +----------+       |
|  | [Photo]  |  | [Photo]  |  |    🐶     |  |    🐱     |      |
|  | URGENT   |  |          |  |           |  | REUNITED |      |
|  |          |  |          |  |           |  |          |      |
|  | Buddy    |  | Luna     |  | Max       |  | Mochi    |      |
|  | Dog 🔶   |  | Cat 🔶   |  | Dog 🔶    |  | Cat 🔶   |      |
|  | 👤 Marcus|  | 👤 Sara  |  | 👤 James  |  | 👤 Priya |      |
|  | 📍 Park  |  | 📍 School|  | 📍 Mall   |  | 📍 Home  |      |
|  | 📅 May 9 |  | 📅 May 8 |  | 📅 May 7  |  | 📅 May 6 |      |
|  | [Found?] |  | [Found?] |  | [Found?]  |  | [Found?] |      |
|  +----------+  +----------+  +----------+  +----------+       |
+----------------------------------------------------------------+
```

##### Filter & Sort Controls

| Control | Options |
|---|---|
| Text search | Filters by name or last seen location, live as you type |
| Animal type dropdown | All Animals / Dog / Cat |
| Sort dropdown | Newest First / Oldest First |
| Date filter dropdown | All Time / Last 7 Days / Last 30 Days |

##### Pet Card Fields

| Field | Detail |
|---|---|
| Photo | Top of card, full width; emoji placeholder if no photo |
| URGENT badge | Red, shown if owner flagged post as urgent |
| REUNITED badge | Green, shown if owner marked as found |
| Pet name | Bold orange |
| Type badge | Small orange pill (Dog / Cat) |
| Owner name | 👤 icon + first name |
| Last seen location | 📍 icon |
| Date went missing | 📅 icon |
| "I Think I Found This Pet" button | Opens a contact modal |

##### "I Think I Found This Pet" Modal

```
+--------------------------------------+
|  I Think I Found This Pet        [✕] |
|                                      |
|  You are contacting the owner of:    |
|  Buddy (Dog)                         |
|                                      |
|  Owner's phone: [Show Contact Info]  |
|  (phone number hidden by default)    |
|                                      |
|  Leave a message for the owner:      |
|  [________________________________]  |
|  [________________________________]  |
|                                      |
|  [  Send Message  ]                  |
+--------------------------------------+
```

- Phone number is hidden behind a "Show Contact Info" button for privacy
- Message is saved and shown to the owner on their profile page
- Visitor does not need to be logged in to send a message

---

### 8.7 Found a Pet Page

**URL:** `/found-a-pet`  
**Purpose:** Let someone who found a stray post it so the owner can find it.

#### Sub-Tabs

```
+----------------------------------------------------+
|  📢 Post a Found Pet  |  🔍 Search Found Pets       |
+----------------------------------------------------+
```

#### Post a Found Pet Form Fields

| Field | Input Type | Required |
|---|---|---|
| Animal Type | Dropdown (Dog / Cat) | Yes |
| Description | Text | Yes |
| Colour | Text | No |
| Breed (if known) | Text | No |
| Where you found it | Text | Yes |
| Date found | Date picker | Yes |
| Your Phone Number | Tel | Yes |
| Extra details | Textarea | No |
| Photos (up to 4) | File (multi) | No |

#### Search Found Pets
- Same card layout and filter controls as the lost pet search
- Shows "Found" badge instead of "URGENT" or "REUNITED"
- "This Is My Pet!" button replaces "I Think I Found This Pet"

---

### 8.8 Success Stories Page

**URL:** `/success-stories`  
**Purpose:** Show real reunited pet stories to build trust and inspire users.

#### Wireframe

```
+----------------------------------------------------------------+
| PAGE BANNER: "Success Stories"                                 |
| Pets that found their way home thanks to FurAndFound.          |
+----------------------------------------------------------------+
|  +--------------------+  +--------------------+               |
|  | [Pet photo]        |  | [Pet photo]        |               |
|  | Buddy is home! 🏠  |  | Luna found! 🏠    |               |
|  | "We posted on...   |  | "Someone spotted...|               |
|  | and found him in   |  | her near the park  |               |
|  | 2 days!"           |  | and called us."    |               |
|  | — Marcus, May 2026 |  | — Sara, May 2026   |               |
|  +--------------------+  +--------------------+               |
+----------------------------------------------------------------+
```

#### Story Card Fields

| Field | Detail |
|---|---|
| Pet photo | Top of card |
| Pet name + "is home!" | Bold heading |
| Short quote from owner | 1–2 sentences |
| Owner first name + date | Small gray caption |

#### Behaviour
- Stories are automatically created when an owner marks their post as "My Pet Has Been Found!"
- The post's details and photo are copied into a story card
- Displayed newest first

---

### 8.9 FAQ Page

**URL:** `/faq`  
**Purpose:** Answer the most common questions visitors have.

#### Questions & Answers

| Question | Short Answer |
|---|---|
| What do I do if I find someone else's pet? | Go to the Found a Pet page and post it so the owner can see it |
| Is FurAndFound free to use? | Yes, completely free |
| Do I need an account to search? | No, anyone can search. You only need an account to post |
| How long do posts stay up? | Until the owner marks the pet as found or deletes the post |
| What if my pet is not a dog or cat? | We currently only support dogs and cats |
| How do I contact the owner of a found pet? | Click "I Think I Found This Pet" on their post |
| Can I edit my post after submitting? | Yes, go to your profile page and click Edit on your post |

#### Layout
- Accordion style: clicking a question expands the answer below it
- Only one answer open at a time

---

### 8.10 Contact Us Page

**URL:** `/contact`  
**Purpose:** Let visitors send a message to the FurAndFound team.

#### Wireframe

```
+----------------------------------------------------------------+
|  Contact Us                                                    |
|  Have a question or want to report a problem? Reach out.       |
|                                                                |
|  Your Name          Your Email                                 |
|  [______________]   [______________]                           |
|                                                                |
|  Subject                                                       |
|  [________________________________]                            |
|                                                                |
|  Message                                                       |
|  [________________________________]                            |
|  [________________________________]                            |
|  [________________________________]                            |
|                                                                |
|  [  Send Message  ]                                            |
+----------------------------------------------------------------+
```

#### Form Fields

| Field | Type | Required |
|---|---|---|
| Your Name | Text | Yes |
| Your Email | Email | Yes |
| Subject | Text | Yes |
| Message | Textarea | Yes |

#### Behaviour
- On submit, shows success message: "Thanks! We will get back to you soon."
- Message saved in localStorage (no real email sending for class project)

---

### 8.11 About Us Page

**URL:** `/about`  
**Purpose:** Explain what FurAndFound is and who made it.

#### Sections

| Section | Content |
|---|---|
| Mission statement | 2–3 sentences about why FurAndFound was made |
| Who made it | Name, grade, school project context |
| What we believe | Short bullet list of values (every pet deserves to go home, etc.) |
| External partners | Logos/links to Petfinder, Humane Society, ASPCA |

---

### 8.12 Local Shelters & Vets Page

**URL:** `/shelters`  
**Purpose:** Give owners a list of places to call when their pet goes missing.

#### Wireframe

```
+----------------------------------------------------------------+
|  Local Shelters & Vets                                         |
|  Places to contact right away when your pet is missing.        |
|                                                                |
|  +---------------------------+  +---------------------------+  |
|  | 🏠 City Animal Shelter    |  | 🏥 Main Street Vet Clinic |  |
|  | 123 Shelter Road          |  | 456 Vet Avenue            |  |
|  | 📞 555-0100               |  | 📞 555-0200               |  |
|  | Mon–Fri 9am–5pm           |  | Mon–Sat 8am–6pm           |  |
|  +---------------------------+  +---------------------------+  |
+----------------------------------------------------------------+
```

#### Shelter Card Fields

| Field | Detail |
|---|---|
| Icon | 🏠 for shelter, 🏥 for vet clinic |
| Name | Bold heading |
| Address | Street address |
| Phone | 📞 icon + number |
| Hours | Opening days and times |

---

### 8.13 User Profile Page

**URL:** `/profile`  
**Purpose:** Let logged-in users manage their account and view their posts.

#### Wireframe

```
+----------------------------------------------------------------+
|  👤 My Profile                                                 |
|                                                                |
|  Name: Marcus Kwan              [Edit]                         |
|  Email: marcus@email.com        [Edit]                         |
|  City: Vancouver                [Edit]                         |
|  Password: ••••••••             [Change Password]              |
|                                                                |
+----------------------------------------------------------------+
|  MY LOST PET POSTS                                             |
|                                                                |
|  +----------+  +----------+                                   |
|  | [Photo]  |  | [Photo]  |                                   |
|  | Buddy    |  | Luna     |                                   |
|  | Dog      |  | Cat      |                                   |
|  | [Edit]   |  | [Edit]   |                                   |
|  | [Delete] |  | [Found!] |                                   |
|  +----------+  +----------+                                   |
|                                                                |
+----------------------------------------------------------------+
|  MESSAGES FROM FINDERS                                         |
|                                                                |
|  "I saw a dog matching Buddy's description near the mall"      |
|  — Anonymous, May 9 2026                                       |
+----------------------------------------------------------------+
```

#### Profile Sections

| Section | Details |
|---|---|
| Account info | Name, email, city — each editable inline |
| Change password | Old password + new password + confirm new password |
| My lost pet posts | All posts by this user with Edit, Delete, and "My Pet Was Found!" buttons |
| Messages from finders | All messages sent via the "I Think I Found This Pet" button |

#### Edit Post Behaviour
- Clicking Edit on a post opens the post form pre-filled with that post's data
- User can change any field and re-submit
- Post updates immediately

#### Delete Post Behaviour
- Clicking Delete shows a confirmation dialog: "Are you sure? This cannot be undone."
- On confirm, post is removed from localStorage and disappears from search

#### "My Pet Was Found!" Behaviour
- Clicking the button adds the green REUNITED badge to the post
- Post also appears as a story on the Success Stories page
- Button changes to "Already Reunited ✓" (disabled)

---

### 8.14 Pet Detail Page

**URL:** `/pet/:id`  
**Purpose:** A full-page view of a single lost or found pet post with all details.

#### Wireframe

```
+----------------------------------------------------------------+
|  ← Back to Search                                             |
|                                                                |
|  🔴 URGENT           Buddy — Golden Retriever                 |
|                                                                |
|  +----------+ +----------+ +----------+ +----------+          |
|  | Photo 1  | | Photo 2  | | Photo 3  | | Photo 4  |          |
|  +----------+ +----------+ +----------+ +----------+          |
|  (clicking a photo enlarges it)                                |
|                                                                |
|  Animal: Dog          Colour: Golden                           |
|  Age: 2 years         Microchip: Yes                           |
|  Date Missing: May 8, 2026                                     |
|  Last Seen: Main Street Park                                   |
|                                                                |
|  Extra Details:                                                |
|  "Wearing a red collar, responds to Buddy"                     |
|                                                                |
|  Posted by: Marcus | May 9, 2026                               |
|                                                                |
|  [📞 Show Contact Info]   [📤 Share This Post]                |
|  [⚑ Report This Post]                                         |
|                                                                |
|  [  I Think I Found This Pet  ]                               |
+----------------------------------------------------------------+
|  COMMENTS (3)                                                  |
|                                                                |
|  "Saw a dog like this near the school on Sunday"               |
|  — Anonymous, May 9                                            |
|                                                                |
|  [Leave a comment...]             [Post Comment]               |
+----------------------------------------------------------------+
```

#### Detail Page Components

| Component | Detail |
|---|---|
| Back link | Returns to the search tab |
| Photo gallery | Up to 4 photos, clicking enlarges in a lightbox overlay |
| All post fields | Every field from the form displayed clearly |
| Show Contact Info button | Reveals the owner's phone number on click |
| Share button | Opens share options for Facebook, X (Twitter), and copy link |
| Report button | Opens a small modal to report the post |
| Found button | Opens the finder contact modal |
| Comments section | Displays all comments, any visitor can leave a comment |

#### Comment Fields

| Field | Detail |
|---|---|
| Comment text | Textarea, required |
| Name (optional) | Text input — shows as "Anonymous" if left blank |
| Post Comment button | Adds comment to localStorage, appears immediately |

#### Report Post Modal

```
+--------------------------------------+
|  Report This Post                [✕] |
|                                      |
|  Why are you reporting this?         |
|  ○ Fake or spam                      |
|  ○ Incorrect information             |
|  ○ Inappropriate content             |
|  ○ Other                             |
|                                      |
|  [  Submit Report  ]                 |
+--------------------------------------+
```

---

## 9. User Flows

### 9.1 Lost Pet Owner Flow

```
Owner's pet goes missing
        ↓
Visits FurAndFound home page
        ↓
Clicks "Report a Lost Pet Right Now" emergency button
        ↓
Is logged in? 
  NO  → Auth modal opens → Sign up or sign in → Form appears
  YES → Post form appears immediately
        ↓
Fills in pet details + uploads up to 4 photos
        ↓
Clicks "Post Lost Pet"
        ↓
Success toast: "Buddy has been posted!"
        ↓
Switches to "What To Do" checklist tab
        ↓
Ticks off steps as they complete them
        ↓
Later: visits Profile page to see messages from finders
        ↓
Pet is found → clicks "My Pet Was Found!" on their post
        ↓
Post gets green REUNITED badge
        ↓
Story appears on Success Stories page
```

### 9.2 Pet Finder Flow

```
Person finds a stray dog or cat
        ↓
Visits FurAndFound
        ↓
Searches "Lost Pet" tab by animal type and location
        ↓
Finds a matching post
        ↓
Clicks pet card → goes to detail page
        ↓
Clicks "Show Contact Info" to see phone number
  OR
Clicks "I Think I Found This Pet" → leaves a message
        ↓
Owner receives the message on their profile page
```

### 9.3 Sign Up Flow

```
Visitor clicks "Sign In" in nav bar
        ↓
Auth modal opens (login form)
        ↓
Clicks "Sign up for free"
        ↓
Fills in: Name, Email, City, Password
        ↓
Clicks "Create Account"
        ↓
Logged in automatically
        ↓
Modal closes, name chip appears in nav bar
```

### 9.4 Forgot Password Flow

```
User clicks "Sign In"
        ↓
Clicks "Forgot my password"
        ↓
Enters their email address
        ↓
New password is set (for class project: password is reset to a default)
        ↓
Success message shown
```

---

## 10. Data Models

### 10.1 User Object

```json
{
  "name": "Marcus Kwan",
  "email": "marcus@email.com",
  "password": "hashed_password",
  "city": "Vancouver",
  "joinedDate": "2026-05-10"
}
```

### 10.2 Lost Pet Post Object

```json
{
  "id": "pet_001",
  "name": "Buddy",
  "type": "Dog",
  "breed": "Golden Retriever",
  "colour": "Golden",
  "age": "2 years",
  "microchip": "Yes",
  "dateMissing": "2026-05-08",
  "location": "Main Street Park",
  "phone": "555-1234",
  "details": "Wearing a red collar",
  "photos": ["data:image/..."],
  "urgent": true,
  "reunited": false,
  "postedBy": "marcus@email.com",
  "postedDate": "2026-05-09",
  "comments": [],
  "reports": []
}
```

### 10.3 Comment Object

```json
{
  "id": "comment_001",
  "petId": "pet_001",
  "name": "Anonymous",
  "text": "I saw a dog like this near the school",
  "date": "2026-05-09"
}
```

### 10.4 Message Object (Finder Contact)

```json
{
  "id": "msg_001",
  "petId": "pet_001",
  "fromName": "Anonymous",
  "text": "I think I found your dog near the mall",
  "date": "2026-05-09",
  "read": false
}
```

### 10.5 Found Pet Post Object

```json
{
  "id": "found_001",
  "type": "Dog",
  "description": "Small brown dog with white spots",
  "colour": "Brown",
  "breed": "Unknown",
  "foundLocation": "Oak Street",
  "dateFound": "2026-05-09",
  "phone": "555-5678",
  "details": "Very friendly, no collar",
  "photos": [],
  "postedBy": "anonymous",
  "postedDate": "2026-05-09"
}
```

---

## 11. Feature Specifications

### 11.1 Dark Mode

| Property | Detail |
|---|---|
| Toggle | Moon icon (🌙) in nav bar, switches to sun icon (☀️) when active |
| Saves in | localStorage key: `faf_darkmode` |
| Applies to | All pages, cards, modals, inputs, nav, footer |
| Transition | `0.2s` CSS transition on background and colour changes |

### 11.2 Social Sharing

Clicking the Share button on a pet detail page opens a small panel with:
- **Facebook:** Opens Facebook share dialog with the page URL
- **X (Twitter):** Opens Twitter/X share with a pre-written message
- **Copy Link:** Copies the pet's detail page URL to clipboard, shows "Copied!" toast

### 11.3 Comments

- Any visitor (logged in or not) can leave a comment on a pet detail page
- Name field is optional — blank name shows as "Anonymous"
- Comments are saved in localStorage under the pet's ID
- Comments show newest first
- No editing or deleting of comments (keep it simple)

### 11.4 URGENT Label

- Checkbox on the post form: "Mark as URGENT"
- Adds a red URGENT badge to the top-left corner of the pet card
- Also adds a red border to the card on the search page so it stands out
- Owner can remove the URGENT flag by editing their post

### 11.5 Photo Gallery (Detail Page)

- Up to 4 thumbnail images shown in a row
- Clicking any thumbnail opens a lightbox (full-screen overlay) showing the full image
- Left/right arrows navigate between photos in the lightbox
- Clicking outside the lightbox or pressing Escape closes it

---

## 12. Must-Have vs Stretch Goals

### Must-Have (Build First)

| # | Feature |
|---|---|
| 1 | Sign up and log in with email and password |
| 2 | City/neighbourhood field on sign-up |
| 3 | Dog and cat checklists with checkboxes, custom steps, print button, 30-day reset |
| 4 | Post a lost pet form (all fields, up to 4 photos, URGENT flag, date picker) |
| 5 | Search and filter lost pets (text, type, sort, date filter) |
| 6 | Pet detail page with photo gallery, comments, share, report, found button |
| 7 | "I Think I Found This Pet" modal with hidden phone number |
| 8 | "My Pet Has Been Found!" REUNITED badge |
| 9 | Found a Pet section (post and search) |
| 10 | User profile page (edit account, view posts, read messages) |
| 11 | Success Stories page (auto-populated from reunited posts) |
| 12 | FAQ, Contact Us, About Us, Local Shelters pages |
| 13 | Footer on every page |
| 14 | Dark mode toggle |
| 15 | Mobile hamburger menu |
| 16 | Loading animations and toast notifications |
| 17 | Adopt Now button → petfinder.com |
| 18 | Emergency "Report a Lost Pet" button on home page |
| 19 | Social sharing (Facebook, X, copy link) |
| 20 | Report this post button |

### Stretch Goals (Add Later)

| # | Feature | Why It Can Wait |
|---|---|---|
| 1 | AI moderation of custom checklist steps | Requires an external API and server |
| 2 | Forgot my password (real reset email) | Needs a back-end email service |
| 3 | Map showing last seen location | Requires Google Maps API integration |
| 4 | Email or SMS notifications to owner | Needs a back-end server |
| 5 | Admin moderation dashboard | Not needed for class project |
| 6 | Multiple language support | Future expansion |
| 7 | Push notifications on mobile | Requires PWA setup |

---

## 13. Tech Stack

| Layer | Technology | Reason |
|---|---|---|
| Structure | HTML5 | Standard, works in all browsers |
| Styling | Plain CSS with CSS variables | Full control, no dependencies, easy dark mode |
| Behaviour | Vanilla JavaScript (no framework) | Simple to write and understand |
| Data storage | localStorage (browser) | No server needed for class project |
| Images | Base64 data URLs | No file hosting server needed |
| External links | Petfinder, Humane Society, ASPCA | Trusted real organisations |
| Dev server | VS Code Live Server extension | Instant preview on save |

---

## 14. Out of Scope

The following will NOT be built for this project:

- Real back-end server or database (all data stays in the browser)
- User accounts that sync across different devices or browsers
- Real email sending for contact forms or password resets
- GPS or map features
- Mobile app (iOS or Android)
- Payment or donation features
- Admin panel for managing all posts
