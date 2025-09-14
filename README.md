# Documentation / App flow 

<!-- #SafarDadddy Hotel Booking App - Complete User Flow Guide -->

<!-- ## 🎯 App Overview
SafarDadddy is a mobile hotel and villa booking platform with 5 main sections accessible through bottom navigation tabs.

---

## 📱 Main Navigation Structure

```
Bottom Navigation Bar (Always Visible)
├── 🏠 Search (Home)
├── 📅 My Trips  
├── ❤️ Favorites
├── 🤖 AI Buddy
└── 👤 Profile
```

---

## 🔄 Complete User Journey Flowchart

### 1️⃣ **SEARCH TAB** (Starting Point)

**🏠 Search Page (Home Screen)**
```
User opens app → Search Page loads
├── App Header: "SafarDadddy - Find your perfect stay"
├── Search Form:
│   ├── 📍 Destination input
│   ├── 📅 Check-in date
│   ├── 📅 Check-out date  
│   └── 👥 Number of guests
├── Quick Filters: [Hotels] [Villas] [Advanced Filters]
├── Popular Destinations (6 quick buttons)
└── Featured Properties (3 property cards)
```

**User Actions & What Happens:**

1. **🔍 User fills search form and clicks "Search Hotels & Villas"**
   - Function: `handleSearch()` 
   - Data collected: destination, dates, guests
   - Navigation: → **Search Results Page**

2. **📍 User clicks Popular Destination button**
   - Function: `setDestination()`
   - Action: Auto-fills destination field

3. **🏨 User clicks Featured Property card**
   - Function: `onNavigate('property', property)`
   - Navigation: → **Property Details Page**

---

### 2️⃣ **SEARCH RESULTS FLOW**

**📋 Search Results Page**
```
Results Page loads with:
├── Header: Shows search criteria (destination, dates, guests)
├── [← Back] [🗺️ Map View]
├── Filters: [🎛️ Filters] [Sort: recommended]
├── Results count: "X properties found"
└── Property List (scrollable cards)
```

**User Actions & What Happens:**

1. **🏨 User clicks any property card**
   - Function: `onNavigate('property', property)`
   - Data passed: Full property details
   - Navigation: → **Property Details Page**

2. **❤️ User clicks heart icon on property**
   - Function: `toggleFavorite(propertyId)`
   - Action: Adds/removes from favorites list
   - Visual: Heart turns red/gray

3. **← User clicks back arrow**
   - Function: `onNavigate('search')`
   - Navigation: → **Search Page**

4. **🎛️ User clicks Filters button**
   - Action: Opens filter options (hotels/villas/amenities)

---

### 3️⃣ **PROPERTY DETAILS FLOW**

**🏨 Property Details Page**
```
Property Page shows:
├── Image Gallery (swipeable, 3+ photos)
├── [← Back] [📤 Share] [❤️ Favorite]
├── Property Info:
│   ├── Name, location, rating, reviews
│   ├── Price per night
│   └── Property type badge
├── 🏪 Amenities Grid (WiFi, Pool, Spa, etc.)
├── 📝 Description text
├── 🗺️ Location Map
├── ⭐ Guest Reviews (3 sample reviews)
└── 💳 Booking Footer: [Select dates] [Book Now]
```

**User Actions & What Happens:**

1. **💳 User clicks "Book Now" button**
   - Function: `onNavigate('booking', property)`
   - Data passed: Property details for booking
   - Navigation: → **Booking Page**

2. **❤️ User clicks heart icon**
   - Function: `setIsFavorite(!isFavorite)`
   - Action: Saves property to favorites
   - Visual: Heart turns red

3. **← User clicks back arrow**
   - Function: `onNavigate('results')`
   - Navigation: → **Search Results Page**

4. **📤 User clicks share button**
   - Action: Opens device share options

---

### 4️⃣ **BOOKING FLOW**

**💳 Booking Page**
```
Booking Page contains:
├── [← Back] "Complete Booking"
├── 🏨 Property Summary Card
├── 📅 Your Stay Section:
│   ├── Check-in date
│   ├── Check-out date
│   └── Number of guests
├── 👤 Guest Information:
│   ├── First & Last Name
│   ├── Email address
│   └── Phone number
├── 💳 Payment Details:
│   ├── Card number
│   ├── Expiry date
│   └── CVV
├── 💰 Price Breakdown:
│   ├── Nightly rate × nights
│   ├── Service fee
│   ├── Taxes
│   └── Total amount
├── 📜 Terms agreement text
└── [Complete Booking - $XXX] button
```

**User Actions & What Happens:**

1. **✅ User fills all required fields and clicks "Complete Booking"**
   - Function: `handleBooking()`
   - Action: Simulates booking process (2 second delay)
   - Navigation: → **Booking Confirmation Screen**

2. **← User clicks back arrow**
   - Function: `onNavigate('property', property)`
   - Navigation: → **Property Details Page**

**🎉 Booking Confirmation Screen**
```
Success Page shows:
├── ✅ Green checkmark icon
├── "Booking Confirmed!" message
├── Confirmation details
├── [View My Bookings] button
└── [Back to Home] button
```

**User Actions & What Happens:**

1. **📅 User clicks "View My Bookings"**
   - Function: `onNavigate('trips')`
   - Navigation: → **My Trips Tab**

2. **🏠 User clicks "Back to Home"**
   - Function: `onNavigate('search')`
   - Navigation: → **Search Page**

---

### 5️⃣ **MY TRIPS TAB**

**📅 My Trips Page**
```
Trips Page shows:
├── Header: "My Trips" + description
├── Tabs: [Upcoming] [Past Trips]
└── Trip Cards (for each booking):
    ├── Property image & name
    ├── Location & dates
    ├── Booking status badge
    ├── Guest count & total price
    ├── Booking reference number
    └── Action buttons based on status
```

**User Actions & What Happens:**

1. **📞 User clicks "Contact Property" (upcoming trips)**
   - Action: Opens contact options

2. **📄 User clicks "Download Voucher" (upcoming trips)**
   - Action: Downloads booking confirmation

3. **⭐ User clicks "Write Review" (past trips)**
   - Action: Opens review form

4. **🔄 User clicks "Book Again" (past trips)**
   - Function: Pre-fills search with same property
   - Navigation: → **Property Details Page**

5. **🏠 User clicks "Start Searching" (if no trips)**
   - Function: `onNavigate('search')`
   - Navigation: → **Search Tab**

---

### 6️⃣ **FAVORITES TAB**

**❤️ Favorites Page**
```
Favorites Page shows:
├── Header: "My Favorites" + count
├── Filter tabs: [All] [Hotels] [Villas] [🎛️ Filter]
└── Property Cards:
    ├── Property image with [📤 Share] [❤️ Remove] buttons
    ├── Property details (name, location, rating)
    ├── Saved date
    ├── Price per night
    └── [View Details] [Book Now] buttons
```

**User Actions & What Happens:**

1. **🏨 User clicks "View Details"**
   - Function: `onNavigate('property', property)`
   - Navigation: → **Property Details Page**

2. **💳 User clicks "Book Now"**
   - Function: `onNavigate('booking', property)`
   - Navigation: → **Booking Page**

3. **❤️ User clicks heart icon (remove)**
   - Function: `removeFavorite(id)`
   - Action: Removes from favorites list

4. **🏷️ User clicks filter tabs**
   - Function: `setFilter(type)`
   - Action: Filters list by Hotels/Villas/All

5. **🔍 User clicks "Explore Properties" (if no favorites)**
   - Function: `onNavigate('search')`
   - Navigation: → **Search Tab**

---

### 7️⃣ **AI BUDDY TAB**

**🤖 AI Travel Buddy Page**
```
AI Chat Page shows:
├── Header: "AI Travel Buddy" with online status
├── Chat Messages:
│   ├── AI welcome message
│   ├── User messages (blue, right side)
│   ├── AI responses (white, left side)
│   └── Typing indicator when AI is responding
├── Quick Suggestions (when chat is new):
│   ├── "Best hotels in Paris"
│   ├── "Plan weekend trip"
│   ├── "Luxury villa recommendations"
│   └── "Instagram-worthy places"
├── Message Input:
│   ├── Text input field
│   ├── [🎤 Mic] button
│   └── [📤 Send] button
└── Quick Action buttons: [🏨 Browse Hotels] [❤️ My Favorites]
```

**User Actions & What Happens:**

1. **📝 User types message and clicks Send**
   - Function: `handleSendMessage()`
   - Action: Adds user message to chat
   - AI Response: Simulated AI reply after 2 seconds

2. **⚡ User clicks Quick Suggestion button**
   - Function: `handleQuickMessage(message)`
   - Action: Auto-sends that message

3. **🏨 User clicks "Browse Hotels"**
   - Function: `onNavigate('search')`
   - Navigation: → **Search Tab**

4. **❤️ User clicks "My Favorites"**
   - Function: `onNavigate('favorites')`
   - Navigation: → **Favorites Tab**

---

### 8️⃣ **PROFILE TAB**

**👤 Profile Page**
```
Profile Page shows:
├── Header: User info with avatar & loyalty status
├── 📊 Travel Stats Grid:
│   ├── Total Bookings
│   ├── Countries Visited
│   ├── Nights Stayed
│   └── Loyalty Points
├── 🎯 Quick Actions: [📅 My Trips] [⭐ Favorites]
├── ⚙️ Account Settings Menu:
│   ├── Personal Information
│   ├── Payment Methods
│   ├── Notifications
│   ├── Privacy & Security
│   ├── Loyalty Program
│   └── Help & Support
├── 🔔 Notification Preferences (with toggle switches)
├── ℹ️ App Info & Legal links
└── [🚪 Sign Out] button
```

**User Actions & What Happens:**

1. **📅 User clicks "My Trips" quick action**
   - Function: `onNavigate('trips')`
   - Navigation: → **My Trips Tab**

2. **⭐ User clicks "Favorites" quick action**
   - Function: `onNavigate('favorites')`
   - Navigation: → **Favorites Tab**

3. **🔔 User toggles notification switches**
   - Function: `setNotifications()`
   - Action: Updates notification preferences

4. **⚙️ User clicks any settings menu item**
   - Action: Opens respective settings page

5. **🚪 User clicks "Sign Out"**
   - Action: Logs user out of app

---

## 🔄 Cross-Tab Navigation Summary

**How users can move between sections:**

```
Any Tab → Any Other Tab
├── Bottom Navigation: Always visible
├── Direct tab switching preserves current state
└── Each tab maintains its own navigation history

Search Flow → Other Tabs
├── From Property Details → Add to Favorites
├── From Booking Confirmation → View My Trips
└── From anywhere → Use bottom navigation

AI Buddy → Other Tabs  
├── Quick actions link to Search & Favorites
└── AI can recommend checking specific properties

Profile → Other Tabs
├── Quick actions to My Trips & Favorites
└── Standard bottom navigation
```

---

## 🎯 Key App Functions (Technical Overview)

**Navigation System:**
- `handleNavigation(page, data)` - Controls all page transitions
- `handleTabChange(tab)` - Manages bottom tab switching
- `renderCurrentPage()` - Displays correct page based on current state

**Data Flow:**
- `currentPage` - Tracks which page is active
- `currentData` - Passes data between pages (search results, property details, etc.)
- `activeTab` - Manages bottom navigation highlighting

**User Actions:**
- Search: `handleSearch()` → Collects form data → Navigate to results
- Favorites: `toggleFavorite()` → Add/remove from favorites list
- Booking: `handleBooking()` → Process booking → Show confirmation
- AI Chat: `handleSendMessage()` → Add to chat → Generate AI response

---

## 📱 User Experience Flow Summary

1. **🏠 START** → User opens app on Search page
2. **🔍 SEARCH** → Enter destination, dates, guests → View results
3. **📋 BROWSE** → Browse properties → Click on interesting property
4. **🏨 EXPLORE** → View property details → Decide to book
5. **💳 BOOK** → Fill booking form → Complete payment → Get confirmation
6. **📅 MANAGE** → View booking in My Trips → Track upcoming stays
7. **❤️ SAVE** → Add favorite properties → Quick access for future
8. **🤖 DISCOVER** → Use AI Buddy for personalized recommendations
9. **👤 ACCOUNT** → Manage profile and preferences

This creates a complete hotel booking experience similar to Booking.com but focused specifically on hotels and villas with the added AI assistant feature! -->


# SafarDadddy Hotel Booking App - Complete System Flowchart

## Business Context & KPIs

**Marketplace:** Two-sided (Guests vs Hosts)
**Key Offer:** Hotel, Vacation Rental (AirBnB style), Local Bookings
**Value Prop:** AI-powered travel recommendations, seamless booking & payment, end-to-end experience
**Geographically:** Global targeting with local knowledge
**Positioning:** Alternative to Booking.com with AI-enhanced travel planning

---

## High-Level System Architecture (Overview)

**Client:** React Web SPA, React Native mobile apps, Hotel Dashboard, Channel Managers
**Data:** ReactJS + Cloudflare CDM + API + HTML/CSS
**Service:** MongoDB primaries (AppSearch, IdentityAI, Reviews, BIZ Analytics)
**Infra:** AWS / MongoDB + S3 / Postgres / ELK 
**API:** MongoDB + EventBridge → catalogue, ECN Business, Reservability & GDPR integrated

---

## Trust, Payments & Compliance

**Payments:** Stripe Connect (hosts), Paymentbanks, webhooks, refunds, cancel scenarios
**Security:** Enhanced fraud detection, verification, access & trust decisions, third-party integration, compliance check
**Safety:** Content moderation, reporting, escalation paths, human review
**Legal:** Copyright, bookmarking, privacy & data deletion
**Compliance:** KYC, risk reporting, privacy & data decision

---

## Auth & Identity

**JWT + Refresh tokens (secure standard)**
**OAuth:** Google/Facebook, Apple ID integration
**SSO:** OpenID + SAML business integration

**User Types:**
- Guest (booking hotels/villas)
- Host (property owners/managers)
- Admin (platform management)

**Auth Entry Points & Methods:**
- Email/phone number registration with OTP verification
- Social login (Google, Facebook, Apple)
- Guest checkout (limited access for bookings)
- Two-factor authentication for security

**Login — Client Fields & Validation:**
- Identifier: email or phone (normalized, lowercased, required, validated format)
- Password: min length, complexity checks, rate-limited authentication attempts
- Remember me: optional → determines refresh token TTL
- Captcha validation: optional or suspectedActivity activity

**Backend Checks & Defenses:**
- Rate limiting by IP/identifier: prevent account locking during login attempts
- Verify payment w/ encryption/2 using constant-time-compare
- Account checks: active, banned, suspended, kyc required, email verified
- Risk scoring: device fingerprint, IP reputation, velocity anomalies
- On flag risk: require MFA or block and escalate, log to SIEM

**Token Issuance & Session Storage:**
- Access token (JWT): short TTL (e.g., 15min) with minimal claims (userId, roles, etc)
- Refresh token: rotating, long TTL (e.g., 30d), store hashed refresh token in sessions collection
- Set refresh token in httpOnly, Secure, SameSite cookie for web; secure storage for mobile
- Session record: sessionId, userId, device info, refreshHash, issuedAt, expiresAt

**MFA, Recovery & Logout:**
- MFA devices: TOTP (auth apps), WebAuthn (FIDO2), SMS OTP (fallback), Push approval
- Password reset: request → email OTP or reset with short-lived token, rate-limited → Logout: POST /auth/logout → revoke refresh token, mark session revoked

---

## Search & Discovery

**OpenSearch / Elasticsearch:**
- Geo-location search (city, region, country determination)  
- Personalization: algos from ML, personalised search results over 1M+ properties
- Instant book filters, room type, amenities

**Search Server Flow & Ranking:**
- Normalize + geocode location, expand to bibox
- Query OpenSearch with geo + filters, pre-rank by distance & availability & business rules: instant book filter, min nights, host availability window
- Apply business rules: instant book filter, min nights, host availability window

**Performance & Fallbacks:**
- Cache results in Redis indexed by personalized query + region + experiment variant IDs (90% hit)
- Precompute availability snapshots for near-term (e.g., 30d) to reduce DB hits 
- Fallback/full-scan degraded results 
- Circuit breaker and alert system degraded results
- Performance: any loading bias for high UX, thumbnails via CDN optimization, pre pagination

**Search Indexing & Sync:**
- Change streams → instant indexing → OpenSearch (near real-time)
- Index fields: geo, availability/bookings, price/bookings, amenities, hostScore
- Enrichment: auto pricing signals, popularity, ML features during indexing

---

## Listings & Catalog

**Listing CRUD flow with pricing calendar:**
- Host → CMS upload URLs, thumbnails & variants  
- Moderation workflow & cleaning flow

**Payments & Payouts:**
- Stripe Connect/Platform account, refund handling
- Escrow & capture flow: bridge policies to HDS
- Tax & fee calculations

**Host Tools / Channel Sync:**
- Host onboarding & KYC: payout setup
- Calendar sync (iCal), channel manager integrations
- Host analytics & reports

---

## Messaging & Notifications

**Realtime chat (WebSockets, attachments)**  
**Email/SMS & platform email (via HubSpot)**
**Push via APNs SENDING & Android**
**Moderation & abuse flows**

---

## Data & ML Platform

**Event-driven features, feature store**
**Pricing engine & recommendations**
**Batch training & real-time inference**

---

## Booking Orchestrator

**Availability check with distributed locks (hotels)**
**Host → property service (HDS): track availability service (30s hold)**
**Geo-booking prevention & conflict resolution**

**Reviews & Moderation:**
**Post-stay reviews, aggregated ratings**
**Flagging & moderation queue**
**Automated content filtering + human review**

**Primary Document DB (MongoDB):**
**Collections: users, properties, bookings, reviews, transactions, sessions**
**Indexes: MongoDB Live Abatement, bookings (startDate, endDate), users ( email )**
**Search: Full-region or hosted for large scale, TTL for ephemeral collections**

---

## Object Storage (S3) & CDN

**S3 buckets:** Uploads → S3, images (listing, profile photos, docs)**
**Image processing service with different ARs for private content**
**All private trigger image processing services**

**Relational Ledger (RDS Postgres):**
**ACID ledger for payments, refunds, fees, reconciliations**
**Financial reports, tax reporting, audit**
**Guideline to analytics via big ML**

---

## Async Pipeline & Workers

**Event bus:** EventBridge / Kinesis, durable queue, SQS
**Worker Libraries (ECB): image processing, notifications, ML feature updates
**Event processing: service, GUIs, and monitoring**

---

## Notifications & External Providers

**Email: SES, SNS via third-party, Push (APN&ms)**
**Payments: Stripe webhooks → Payment service (DR)**
**Third-party: channel managers, analytics integrations, fraud providers**

---

## Booking Sequence (Detailed Steps)

1. **Guest searches → Search service returns candidates with cached prices & ML signals**
2. **Guest views listing details → Booking service checks availability options (with cached)**
3. **Guest completes checkout → Real-time payment authorization w/ triggerd webhook to Payment service**
4. **Client completes checkout → Real-time payment authorization w/ triggers Payment service (30s)**
5. **Optional payment → Payment service checks → Fare processing services exchanges to Payment service**
6. **Payments get processed → Host confirmation and calendar updated, final booking status validated, Host & guest notified**

---

## Next Steps & Deliverables

**Presentation available: high-quality PDF from PMO Export, Responsive schemas, OpenAPI contracts, PlattoDocumentation diagrams**
**Success validation: booking + rebookings - 0 regression booking + reviews, 1) Design POV helper of Home and revenue function**
**Post-launch: user flow optimizations, mobile app, based on measured user metrics**

---

## AI Travel Buddy Feature Flow

**Personalized Recommendations:**
- User preferences analysis (past bookings, searches, favorites)
- AI-powered destination suggestions based on user behavior
- Personalized hotel recommendations with reasoning
- Custom itinerary generation for multi-day trips

**Interactive Chat Interface:**
- Natural language processing for travel queries
- Context-aware responses based on user profile and preferences
- Integration with search functionality for instant bookings
- Travel tips, local insights, and cultural information

**Smart Planning Assistant:**
- Budget optimization suggestions
- Best time to visit recommendations
- Local transportation and activity suggestions
- Weather-based travel advice

**Learning & Adaptation:**
- Continuous learning from user interactions
- Feedback loop integration for improved recommendations
- Personal travel style analysis and adaptation
- Cross-reference with successful bookings for refinement

---

## My Trips Management System

**Booking Overview Dashboard:**
- Active bookings with countdown timers
- Past trip history with reviews and photos
- Upcoming trips with check-in reminders
- Cancellation and modification options

**Trip Organization:**
- Automatic trip categorization (business, leisure, family)
- Multi-destination trip grouping
- Shared trip planning for group bookings
- Digital receipt and confirmation storage

**Notification System:**
- Pre-trip reminders and check-in notifications
- Real-time booking updates and changes
- Host communication facilitation
- Post-trip review prompts and follow-ups

---

## Favorites & Wishlist System

**Property Saving Mechanism:**
- One-click save functionality across all screens
- Visual indicators for saved properties
- Bulk actions for list management
- Smart collections based on user behavior

**Organization Features:**
- Custom list creation with naming and categorization
- Shared wishlists for group planning
- Price tracking and availability alerts
- Comparison tools for saved properties

**Discovery Enhancement:**
- Similar property recommendations based on favorites
- Price drop notifications for saved items
- Availability alerts for fully booked favorites
- Integration with AI Buddy for personalized suggestions

---

## User Profile Management

**Profile Customization:**
- Personal information and preferences
- Travel style and interest tagging
- Profile photo and verification badges
- Privacy settings and data control

**Verification System:**
- Email and phone number verification
- Government ID verification for enhanced trust
- Host verification for property owners
- Review-based reputation system

**Preference Center:**
- Accommodation type preferences
- Budget range settings
- Amenity preferences and deal-breakers
- Communication and notification preferences

**Security & Privacy:**
- Password management and 2FA setup
- Login history and device management
- Data export and deletion options
- Privacy control granular settings

---

## Schema Snapshot — Key Collections (Hotels & Search)

**users:** { _id, name, email, createdAt, phone, location, savedSearches, paymentMethods, sessions }
**properties:** { _id, hostId, title, description, location: { lng,address }, price, amenities, rating, instant_book }
**bookings:** { _id, listingId, guestId, startDate, endDate, status, total, payments[] }
**reviews:** { _id, bookingId, userId, guestId, reviewText, timestamp }
**searches:** { _id, userId, deviceId, latestSearchTerm, issuedAt, expiresAt, received, ip, userAgent }
**payments:** { _id, bookingId, userId, amount, currency, status, stripePaymentId, fees, payoutsComplete }
**wishlists:** { _id, userId, name, description, properties[], isShared, sharedWith[], createdAt }
**trips:** { _id, userId, bookings[], tripName, startDate, endDate, type, shared[], reminders }

This flowchart provides a comprehensive overview of the SafarDadddy hotel booking platform, detailing every major system component, user flow, and business process in a format suitable for management presentation and technical team alignment.
