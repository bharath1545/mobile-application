# Google AI Studio Master Prompt — PickleConnect Android Application

> **Purpose:** Copy the master prompt below into Google AI Studio (Build mode) to generate a working Android-focused application for PickleConnect, a three-sided marketplace connecting raw-material vendors, small-scale food manufacturers, and end consumers.

---

## How to use this prompt

1. Open [Google AI Studio](https://aistudio.google.com/).
2. Open **Build** and create a new application.
3. Paste the complete **Master Prompt** below.
4. Let the builder generate the initial project.
5. Test each user journey before asking it to add more features.
6. Keep API keys and secrets out of client-side code.

If Google AI Studio's current builder generates a web application rather than a native Android project, instruct it to create an Android-installable experience using the supported project format, or generate a mobile-first app/PWA first and then package it with an appropriate Android wrapper. Do not assume a generated web preview is automatically a native APK.

---

# MASTER PROMPT

## 1. ROLE

Act as a senior Android application engineer, full-stack architect, product manager, UI/UX designer, Firebase specialist, QA engineer, and Indian marketplace product consultant.

Build a polished, functional, Android-first application called **PickleConnect**. Treat this as a real product that will be tested by actual local vendors, a small family pickle business, and consumers—not as a static college-project mock-up.

Make sensible implementation decisions, explain important trade-offs briefly, and do not claim a feature works unless it is implemented and tested.

## 2. PRODUCT CONTEXT

My family operates a small-scale homemade pickle business in Mangaluru, Karnataka, India. We need raw materials such as:

- Raw mangoes
- Lemons
- Green and red chillies
- Garlic and ginger
- Mustard seeds and fenugreek
- Salt
- Gingelly oil
- Other ingredients and packaging materials

Today, sourcing these items can require physically visiting markets, contacting several suppliers, comparing prices manually, and arranging transport.

Other small food manufacturers face similar challenges. Vendors may struggle to find regular buyers and manage orders. Consumers may find it difficult to discover local homemade food brands and understand product ingredients and quality information.

Build **PickleConnect**, a three-sided marketplace that connects:

1. **Vendors:** Suppliers of raw materials and ingredients.
2. **Manufacturers:** Small businesses that purchase ingredients and make pickles or other food products.
3. **Consumers:** People who discover and purchase finished products from manufacturers.

The initial launch area is Mangaluru and nearby areas in Karnataka. Design the system so it can expand to other Indian cities later.

The platform should eventually support pickle makers, papad makers, masala producers, homemade snack businesses, and other small food manufacturers. Keep the first release focused and achievable.

## 3. PRIMARY PRODUCT GOALS

Build an application that allows:

- Vendors to create a digital storefront and list raw materials.
- Manufacturers to find suppliers, compare prices, place bulk orders, and track procurement.
- Manufacturers to list their finished food products.
- Consumers to discover manufacturers and order finished products.
- All parties to manage orders and communicate clearly.
- The platform administrator to manage users, listings, complaints, and marketplace activity.

Do not combine the three user roles into one confusing interface. Show role-appropriate screens and permissions.

## 4. PLATFORM AND TECHNICAL REQUIREMENTS

Prioritize an Android-first experience.

Before choosing the implementation format, inspect the capabilities of the current Google AI Studio Build environment. State clearly whether the generated project is:

- Native Android (Kotlin/Jetpack Compose),
- React Native/Expo,
- Flutter, or
- A mobile-first web application/PWA.

Do not describe a web preview as a native Android application. If the environment cannot generate a native Android project directly, build the best maintainable mobile-first implementation it supports and provide clear, exact steps to package or recreate it as an Android app.

Preferred stack, where supported:

- **Mobile UI:** React Native with Expo, or Kotlin with Jetpack Compose for native Android.
- **Language:** TypeScript for React Native; Kotlin for native Android.
- **Backend:** Firebase.
- **Authentication:** Firebase Authentication.
- **Database:** Cloud Firestore.
- **Images:** Firebase Storage.
- **Server-side trusted operations:** Cloud Functions.
- **Push notifications:** Firebase Cloud Messaging.
- **Maps/location:** Google Maps Platform, only where needed.
- **AI:** Gemini API only for clearly useful optional features, through a secure server-side integration.

If the builder supports a different stack more reliably, explain the alternative and use one consistent stack. Do not mix incompatible frameworks.

## 5. USER ROLES AND FUNCTIONAL REQUIREMENTS

### A. Vendor

Create a vendor onboarding flow and vendor dashboard.

Vendor features:

1. Register and sign in.
2. Create a business profile:
   - Business name
   - Owner/contact name
   - Phone number
   - Business address and service area
   - Business description
   - Optional business image
3. Add, edit, pause, and remove product listings.
4. Each raw-material listing must support:
   - Product name
   - Category
   - Description
   - Product images
   - Unit (kg, gram, litre, piece, bag, etc.)
   - Price per unit in INR
   - Available quantity
   - Minimum order quantity
   - Optional bulk-price tiers
   - Availability status
   - Delivery or pickup options
5. View incoming orders.
6. Accept or reject orders with a reason.
7. Update order status:
   - Pending
   - Accepted
   - Preparing
   - Ready for pickup
   - Dispatched
   - Delivered
   - Cancelled
8. View order history and basic sales summaries.
9. Receive in-app notifications for new orders and status changes.

Example: A vendor lists 100 kg of raw mangoes at ₹40/kg, with a minimum order quantity of 10 kg. A manufacturer can request 50 kg.

### B. Manufacturer

Create a manufacturer onboarding flow and procurement dashboard.

Manufacturer features:

1. Register and sign in.
2. Create a business profile:
   - Business name
   - Contact person
   - Phone number
   - Address
   - Business category (pickle, papad, masala, snacks, other)
3. Browse and search raw materials.
4. Filter by:
   - Category
   - Price range
   - Vendor location/service area
   - Minimum order quantity
   - Availability
   - Delivery or pickup
5. Compare offers for the same material from different vendors.
6. View vendor profiles and ratings.
7. Add materials to a cart.
8. Specify quantity and delivery/pickup preference.
9. Place an order and see a clear order summary.
10. Track each order and view status history.
11. View previous purchases and reorder.
12. View purchase history and simple monthly spending summaries.
13. List finished food products for consumers.
14. Manage consumer orders for those finished products.

Example procurement basket:
- 50 kg raw mangoes
- 10 kg lemons
- 20 litres gingelly oil

Show item totals, delivery charges if configured, and the final total in INR. Never invent a delivery fee.

### C. Consumer

Create a simple consumer home screen and shopping experience.

Consumer features:

1. Register and sign in.
2. Browse finished products from local manufacturers.
3. Search by product, manufacturer, and category.
4. Filter by price, category, and service area.
5. View product details:
   - Product name and images
   - Manufacturer/business name
   - Description
   - Ingredients
   - Allergen information where supplied
   - Net quantity
   - Price in INR
   - Storage instructions where supplied
   - Manufacturing/packing date and best-before/expiry details where applicable
   - Available stock
6. Add products to cart.
7. Place an order.
8. Track order status.
9. View order history and reorder.
10. Submit a rating/review after an eligible completed order.

Do not fabricate food-safety claims, certifications, ingredient details, shelf life, or FSSAI licence numbers. Display only information supplied and verified by the manufacturer/admin. Include an appropriate reminder that food businesses must comply with applicable Indian food-safety and labelling requirements.

### D. Administrator

Create a basic protected admin area. Do not make admin access available through a public role selector.

Admin capabilities:

- Review and manage user accounts.
- Review vendor/manufacturer business profiles.
- Moderate product listings.
- Suspend or reactivate accounts.
- View orders and reported issues.
- Review reported listings and reviews.
- View basic marketplace metrics.

Use secure server-side authorization or custom claims for admin privileges. Never rely only on a hidden button or client-side role check.

## 6. IMPORTANT MARKETPLACE WORKFLOWS

Implement these end-to-end flows.

### Workflow 1: Vendor-to-manufacturer procurement

1. Vendor signs in.
2. Vendor creates a raw-material listing.
3. Manufacturer signs in.
4. Manufacturer searches for “raw mango”.
5. Manufacturer compares available vendor offers.
6. Manufacturer selects a vendor and enters quantity.
7. App validates minimum quantity and available stock.
8. Manufacturer reviews the order and submits it.
9. Vendor receives an order notification.
10. Vendor accepts or rejects the order.
11. Vendor updates fulfilment status.
12. Manufacturer sees the status updates and order history.

### Workflow 2: Manufacturer-to-consumer sale

1. Manufacturer creates a finished-product listing, such as “Homemade Mango Pickle — 500 g”.
2. Consumer browses or searches for mango pickle.
3. Consumer views the manufacturer and product details.
4. Consumer adds the product to cart and checks out.
5. Manufacturer receives the order.
6. Manufacturer accepts and updates the order status.
7. Consumer tracks the order and can review it after completion.

### Workflow 3: Account onboarding and role handling

1. User registers.
2. User chooses an allowed account type: vendor, manufacturer, or consumer.
3. App creates the appropriate profile.
4. App routes the user to the correct dashboard.
5. Every protected operation checks authorization in the backend/database rules.

A manufacturer may also be a consumer. Design the data model so that a business account can purchase raw materials and sell finished products without duplicating accounts unnecessarily. Explain how this is represented.

## 7. SCREEN LIST AND NAVIGATION

Create a consistent, polished mobile interface.

### Shared screens
- Splash screen
- Welcome/onboarding
- Sign up
- Sign in
- Forgot password
- Role selection during registration
- Profile
- Notifications
- Help/support
- Settings
- Empty, loading, offline, and error states

### Vendor screens
- Vendor dashboard
- Business profile
- Product inventory
- Add/edit raw material
- Incoming orders
- Order detail
- Sales/order history

### Manufacturer screens
- Manufacturer dashboard
- Raw-material categories
- Search results
- Supplier comparison
- Vendor detail
- Raw-material detail
- Cart
- Checkout
- Procurement order tracking
- Purchase history
- Finished-product inventory
- Add/edit finished product
- Consumer orders
- Spending summary

### Consumer screens
- Consumer home
- Categories
- Search results
- Manufacturer storefront
- Product detail
- Cart
- Checkout
- Order tracking
- Order history
- Reviews

Use intuitive navigation, readable typography, accessible contrast, sufficiently large tap targets, and clear Indian currency formatting. Support small Android screens. Use a clean, trustworthy visual identity inspired by fresh ingredients and homemade food, without making the UI cluttered.

Suggested visual direction:
- Deep green as the primary brand colour.
- Warm cream/off-white backgrounds.
- Muted spice/orange accents.
- Clear product photography.
- Simple cards, icons, and bottom navigation.
- Consistent spacing and typography.

Create a reusable design system rather than styling each screen independently.

## 8. DATA MODEL AND FIRESTORE STRUCTURE

Design and implement a normalized, maintainable Firestore data model. Consider collections such as:

- `users`
- `businessProfiles`
- `rawMaterialListings`
- `finishedProductListings`
- `orders`
- `orderItems`
- `reviews`
- `notifications`
- `reports`
- `categories`

You may adjust the structure if there is a better Firestore design. Explain the trade-offs.

For every collection, document:
- Purpose
- Document ID strategy
- Field names and types
- Ownership and access rules
- Important indexes
- Relationships/reference fields

Example raw-material listing:

```json
{
  "vendorId": "USER_ID",
  "name": "Raw Mango",
  "category": "Vegetables",
  "description": "Fresh raw mangoes suitable for pickle preparation",
  "unit": "kg",
  "pricePerUnit": 40,
  "availableQuantity": 100,
  "minimumOrderQuantity": 10,
  "currency": "INR",
  "isAvailable": true,
  "fulfilmentOptions": ["delivery", "pickup"],
  "createdAt": "SERVER_TIMESTAMP",
  "updatedAt": "SERVER_TIMESTAMP"
}
```

Use server timestamps and validate all monetary and quantity fields. Use integer paise for money calculations where appropriate, or explain a consistent safe money representation. Do not trust totals or prices submitted by the client: re-read and validate authoritative listing prices and stock on the server when creating orders.

## 9. SECURITY, PRIVACY, AND TRUST

Implement:

- Firebase Authentication.
- Firestore Security Rules with least-privilege access.
- Storage rules for user/product images.
- Server-side validation for order creation and price/stock checks.
- Protected admin authorization.
- Safe handling of personal information and phone numbers.
- Input validation and error handling.
- Rate limiting or abuse protections where appropriate.
- No secrets, private service-account keys, or unrestricted API keys in client code.

A user must not be able to edit another user's profile, change another vendor's listing, alter an order they do not own, or grant themselves admin privileges.

Use Cloud Functions or another trusted backend for sensitive operations. Provide the actual rules and deployment instructions. Do not claim security is complete until rules are configured and tested.

## 10. PAYMENTS, DELIVERY, AND COMMUNICATION

For the first MVP:

- Support “Pay on Delivery” or “Pay directly to vendor” as clearly labelled manual payment methods.
- Do not pretend that a payment has been processed.
- Keep online payment integration as a later phase unless a real provider integration and secure server-side verification are configured.
- Allow vendor delivery or customer pickup.
- Store delivery address and fulfilment details safely.
- Show delivery charges only when configured.
- Provide in-app order status updates.
- Make phone/WhatsApp contact an optional, user-initiated action with appropriate privacy controls.

Do not build fake live GPS tracking. If precise tracking is not implemented, show honest order-status tracking instead.

## 11. OPTIONAL GEMINI FEATURES

Only after core marketplace workflows work, consider:

1. Natural-language search, e.g. “Find 25 kg of raw mangoes under ₹45 per kg near Mangaluru.”
2. Product/category suggestions.
3. Demand summaries for vendors based on their own historical order data.
4. Plain-language monthly purchase summaries for manufacturers.

Use Gemini through a secure backend. Never expose a Gemini API key in the Android client. Do not send personal or sensitive user data to an AI model unnecessarily. AI must not invent supplier availability, prices, food-safety facts, or delivery estimates.

## 12. TEST DATA AND DEMONSTRATION

Provide clearly labelled demo data for local development, not fake live marketplace claims.

Example demo users:
- Vendor: “Coastal Fresh Supplies”
- Manufacturer: “Bharath Homemade Pickles”
- Consumer: “Demo Consumer”

Example listings:
- Raw mangoes — ₹40/kg
- Lemons — ₹60/kg
- Green chillies — ₹50/kg
- Gingelly oil — ₹220/litre

These are illustrative seed values only. Label them as demo data and make them editable. Do not present them as current Mangaluru market prices.

Create a demonstration scenario that exercises both procurement and consumer ordering from start to finish.

## 13. QUALITY REQUIREMENTS

The application must:

- Run without avoidable crashes.
- Have working navigation and functional controls.
- Show useful loading, empty, success, and error states.
- Validate forms and quantities.
- Prevent orders for unavailable or insufficient stock.
- Display totals consistently.
- Handle network failures gracefully.
- Use reusable components and clean project structure.
- Include meaningful comments for complex logic.
- Avoid placeholder buttons that do nothing.
- Avoid fake success messages.
- Avoid hardcoded credentials or secrets.

Do not implement every feature as a mock. Clearly label anything that is only a prototype or not yet connected to a real backend.

## 14. REQUIRED BUILD PROCESS

Work in the following order. Do not skip ahead.

### Phase 1 — Product and project setup
1. Summarize the requirements.
2. Confirm the chosen app framework and whether output is native Android or a web-based mobile app.
3. Show the project folder structure.
4. Identify Firebase setup requirements.
5. Create the app shell, theme, navigation, and shared components.

### Phase 2 — Authentication and profiles
1. Configure Firebase Authentication.
2. Implement registration, login, and password reset.
3. Implement role-aware onboarding.
4. Create and edit profiles.
5. Implement and test access rules.

### Phase 3 — Vendor and procurement MVP
1. Vendor product CRUD.
2. Manufacturer raw-material catalogue.
3. Search and filters.
4. Supplier comparison.
5. Cart and order creation.
6. Vendor order management.
7. Status updates and notifications.

### Phase 4 — Consumer marketplace
1. Manufacturer finished-product listings.
2. Consumer discovery and search.
3. Product details.
4. Cart and checkout.
5. Manufacturer order management.
6. Consumer order history and reviews.

### Phase 5 — Admin, polish, and release
1. Admin moderation.
2. Error/empty/loading states.
3. Accessibility and responsive Android layouts.
4. Security and workflow testing.
5. Build and release instructions for Android.

At the end of each phase:
- List the files created or modified.
- Explain what is now functional.
- Give exact steps to run and test it.
- List any Firebase console configuration still required.
- List known limitations.
- Wait for my confirmation before moving to the next phase.

If a required credential or Firebase project configuration is missing, do not invent it. Use a clearly labelled configuration placeholder and explain how I can supply it securely.

## 15. FINAL DELIVERABLES

Produce:

1. Complete source code in the builder's supported project format.
2. Clear project folder structure.
3. Firebase setup guide.
4. Firestore schema documentation.
5. Firestore and Storage security rules.
6. Any required Cloud Functions.
7. Demo data/seed instructions.
8. Test cases for all three roles.
9. Exact Android run/build instructions.
10. A list of features implemented, partially implemented, and not implemented.

## 16. FIRST RESPONSE INSTRUCTION

Do not immediately generate the entire application.

First respond with:

1. Your understanding of PickleConnect.
2. The three stakeholder journeys.
3. The recommended implementation stack supported by the current Google AI Studio environment.
4. Whether it can produce a native Android app or only a mobile web application.
5. The proposed architecture and project folder structure.
6. The MVP feature list.
7. Firebase setup steps and any information I must provide.

Then begin Phase 1 only.

**Build PickleConnect as a reliable, practical marketplace that solves real procurement and discovery problems for small Indian food businesses and their customers.**
