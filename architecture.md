```mermaid
flowchart TB

%% ================= BUSINESS CONTEXT =================
subgraph Business_Context [📊 Business Context & KPIs]
BC1[Marketplace: Two-sided (Guests vs Hosts)]
BC2[Key Offer: Hotels, Villas, Local Bookings]
BC3[Value Prop: AI-powered travel + seamless booking]
BC4[Geographic: Global with local knowledge]
BC5[Positioning: Alternative to Booking.com w/ AI]
end

%% ================= HIGH LEVEL ARCHITECTURE =================
subgraph Architecture [🏗 High-Level System Architecture]
A1[Clients: React Web SPA, React Native Apps, Hotel Dashboard]
A2[Data: ReactJS + Cloudflare + API]
A3[Services: MongoDB (AppSearch, IdentityAI, Reviews, Analytics)]
A4[Infra: AWS, MongoDB, S3, Postgres, ELK]
A5[API: EventBridge → Catalogue, GDPR-integrated]
end

%% ================= TRUST, PAYMENTS & COMPLIANCE =================
subgraph Trust [🔐 Trust, Payments & Compliance]
T1[Payments: Stripe Connect, refunds, cancellations]
T2[Fraud/Security: detection, fingerprinting, verification]
T3[Safety: content moderation, reporting, escalation]
T4[Compliance: KYC, tax, GDPR, privacy]
end

%% ================= AUTH & IDENTITY =================
subgraph Auth [👤 Auth & Identity]
AU1[JWT + Refresh Tokens]
AU2[OAuth: Google, Facebook, Apple]
AU3[SSO: OpenID, SAML]
AU4[User Types: Guest, Host, Admin]
AU5[Login & Validation: Email/Phone, Social, Guest Checkout]
AU6[Backend Defenses: Rate-limits, Risk scoring, MFA]
AU7[Session Storage: Short JWT + Long Refresh TTL]
AU8[MFA, Recovery, Logout]
end

%% ================= SEARCH & DISCOVERY =================
subgraph Search [🔍 Search & Discovery]
S1[OpenSearch/Elasticsearch]
S2[Geo-location search + personalization]
S3[Ranking: distance, availability, ML signals]
S4[Cache: Redis + availability snapshots]
S5[Fallbacks: degraded mode, circuit breakers]
S6[Indexing: Change streams → OpenSearch (near real-time)]
end

%% ================= LISTINGS, CATALOG, PAYMENTS =================
subgraph Listings [🏨 Listings & Catalog]
L1[Listing CRUD + pricing calendar]
L2[Image hosting: S3 + thumbnails]
L3[Moderation workflow]
end

subgraph Payments [💰 Payments & Payouts]
P1[Stripe Connect, refunds, escrow]
P2[Ledger in RDS]
P3[Tax & fee calculation]
end

subgraph HostTools [🛠 Host Tools & Channel Sync]
H1[Onboarding + KYC]
H2[Calendar sync (iCal)]
H3[Analytics & reports]
end

%% ================= MESSAGING & NOTIFICATIONS =================
subgraph Messaging [💬 Messaging & Notifications]
M1[Realtime chat via WebSockets]
M2[Email/SMS via SES/SNS]
M3[Push notifications: APN/FCM]
M4[Abuse & moderation filters]
end

%% ================= DATA & ML PLATFORM =================
subgraph DataML [🤖 Data & ML Platform]
DM1[Event-driven features + feature store]
DM2[Pricing engine + recommendations]
DM3[Batch + real-time inference]
end

%% ================= BOOKING ORCHESTRATOR =================
subgraph Booking [📅 Booking Orchestrator]
B1[Availability check + distributed locks]
B2[Overbooking prevention + conflict resolution]
B3[Reviews & Moderation]
B4[Ratings, moderation queue]
end

%% ================= STORAGE =================
subgraph Storage [🗄 Storage Systems]
ST1[Primary DB: MongoDB → users, listings, bookings, reviews, sessions]
ST2[Object Storage: S3 → images, docs]
ST3[Relational Ledger: Postgres RDS → payments, taxes]
end

%% ================= PIPELINES =================
subgraph Async [⚡ Async Pipeline & Workers]
AS1[EventBridge / Kinesis / SQS]
AS2[Workers: image processing, notifications, ML updates]
end

%% ================= EXTERNAL PROVIDERS =================
subgraph External [🌐 Notifications & External Providers]
EX1[Email: SES/SNS, Push]
EX2[Payments: Stripe webhooks]
EX3[3rd-party: fraud, channel managers, analytics]
end

%% ================= BOOKING SEQUENCE =================
subgraph Sequence [📋 Booking Sequence]
SEQ1[Guest searches → results w/ cached prices + ML signals]
SEQ2[Guest views listing → check availability]
SEQ3[Checkout → Stripe auth]
SEQ4[Payment processed → booking confirmed]
SEQ5[Host & guest notified → calendar updated]
end

%% ================= AI BUDDY =================
subgraph AIBuddy [🤖 AI Travel Buddy]
AI1[Personalized Recommendations: hotels, trips]
AI2[Chat Interface: NLP + instant booking]
AI3[Smart Planning Assistant: budget, transport, weather]
AI4[Learning & Adaptation: feedback loop]
end

%% ================= MY TRIPS =================
subgraph MyTrips [📅 My Trips Management]
MT1[Dashboard: Active, Past, Upcoming]
MT2[Trip Organization: categories, grouping]
MT3[Notifications: reminders, check-in, post-trip reviews]
end

%% ================= FAVORITES =================
subgraph Favorites [❤️ Favorites & Wishlist]
F1[Save Properties: one-click]
F2[Organization: lists, shared wishlists]
F3[Discovery: price drop, availability alerts]
end

%% ================= PROFILE =================
subgraph Profile [👤 User Profile Management]
PR1[Profile customization]
PR2[Verification: email, phone, ID]
PR3[Preference center: budget, amenities]
PR4[Security & Privacy: 2FA, export, delete]
end

%% ================= SCHEMA SNAPSHOT =================
subgraph Schema [🗂 Schema Snapshot – Key Collections]
SC1[users]
SC2[properties]
SC3[bookings]
SC4[reviews]
SC5[searches]
SC6[payments]
SC7[wishlists]
SC8[trips]
end

%% FLOW CONNECTIONS
Business_Context --> Architecture --> Trust --> Auth --> Search --> Listings --> Payments --> HostTools --> Messaging --> DataML --> Booking --> Storage --> Async --> External --> Sequence --> AIBuddy --> MyTrips --> Favorites --> Profile --> Schema
```
