# Tawfeer Delivery - Logistics & Fulfillment 🚛

<p align="center">
  <img src="Tawfeer%20Design.png" width="100%">
</p>

## 📝 General Overview
**Tawfeer Delivery** is an advanced logistics solution designed to bridge the gap between "Tawfeer Market" and its customers. This application serves as the primary tool for delivery captains, transforming complex supermarket logistics into a simple, manageable workflow. By integrating real-time tracking, automated order distribution, and seamless communication, the app ensures that every product—from daily groceries to household essentials—is delivered with speed, precision, and reliability. 🚀

---

## 🏗 System Architecture & Tech Stack
The Tawfeer ecosystem is split into two specialized applications to ensure high performance and scalability:
*   **Tawfeer Market (User App):** 🛒 For browsing products and placing orders.
*   **Tawfeer Delivery (This App):** 📦 Focused on logistics, order acceptance, and real-time delivery management.

### 🏛 Architectural Principles:
The app follows a blend of **Clean Architecture** and **MVVM** (Model-View-ViewModel) to ensure a robust, testable, and maintainable codebase:
*   **Separation of Concerns:** Strict division between Data (Services, Models), Domain (Repositories), and Presentation (Cubits, UI).
*   **Repository Pattern:** Decoupling business logic from data sources using interfaces (e.g., `auth_repo_interface.dart`) and implementations.
*   **Reactive State:** Leveraging **Cubit (Bloc)** for lightweight and reactive state handling. ⚡

### 🛠 Technical Core:
* **Networking:** **REST APIs** using [Dio](https://pub.dev/packages/dio) for seamless data synchronization. 🌐
* **Real-time Services:** **Firebase Cloud Messaging (FCM)** for instant logistics alerts. 🔔
* **Geolocation:** **Google Maps API** for precise navigation and route optimization. 📍
* **Localization:** [Easy Localization](https://pub.dev/packages/easy_localization) supporting Arabic & English. 🌍

---

## 📂 Project Structure

The codebase is organized using a standardized, lowercase `snake_case` feature-first architecture:

```
lib/
├── features/                    # Feature-based domain modules
│   ├── auth/                    # Authentication (Login, Register, Forget Password)
│   │   ├── data/                # Data sources, Models, and Repositories
│   │   └── presentation/        # Cubits and UI screens
│   ├── home/                    # Main dashboard & order management
│   ├── order_details/           # Order tracking & logistics details
│   └── splash/                  # App initialization flow
│
├── core/                        # Core application layer (Shared)
│   ├── api/                     # Networking logic & API consumers
│   ├── components/              # Reusable UI components (CustomButton, CustomTextFormField, etc.)
│   ├── config/                  # App routes, constants, and localization
│   ├── helpers/                 # Logic helpers (Image compression, etc.)
│   ├── services/                # Background services (FCM, Notifications)
│   ├── theme/                   # Unified styling and typography
│   └── utils/                   # Shared utility functions and validators
│
├── firebase_options.dart        # Firebase configuration
└── main.dart                    # App entry point
```

### Core Architecture Benefits:
✅ **Clear separation of concerns** - Config, constants, services, and utils are distinct  
✅ **Easy navigation** - Find files based on their purpose  
✅ **Better scalability** - Easy to add new features  
✅ **Maintainability** - Logical grouping makes code easier to understand  
✅ **Industry standards** - Follows Flutter/Dart best practices

---

## 📱 App Walkthrough

### 1️⃣ Splash & Entry Flow 💨
The entry flow is optimized for a fast and responsive user experience, managed by **Cubit** to handle initialization states.
* **Fast Initialization:** A lightweight splash screen to get the driver into the system quickly.
* **State-Driven Entry:** The app checks for valid user tokens via API during the splash phase to route the user correctly.

<p align="center">
  <img src="docs/images/splash.jpeg" width="280">
</p>

---

### 2️⃣ Authentication & Captain Onboarding 🔐
This module manages the secure entry and registration of delivery captains, featuring a multi-step verification process.
* **Secure Login:** Identity management for existing captains with password visibility toggles.
* **Fleet Verification:** Integrated image picker for uploading legal documents (**National ID, Vehicle License, Driving License**).
* **Account Approval:** Upon clicking **"حسنا" (Okay)**, the app intelligently routes the user back to Login until the admin grants access.

| 🔑 Login | 📝 Register | 📄 Docs | ⏳ Review |
|:---:|:---:|:---:|:---:|
| <img src="docs/images/login.jpeg" width="200"> | <img src="docs/images/register.jpeg" width="200"> | <img src="docs/images/vehcileDetails" width="200"> | <img src="docs/images/review.jpeg" width="200"> |

---

### 3️⃣ Home Screen (Active Orders) 🏠
The central hub where the delivery captain manages daily operations and interacts with incoming supermarket orders.
* **Incoming Orders List:** A real-time feed displaying Order ID, item count, and delivery location at a glance.
* **Quick Action Buttons:** Large, intuitive **Accept (قبول)** and **Reject (رفض)** buttons for fast decision-making.
* **Technical Logic:** Integrated with **FCM** to notify the captain of new orders without manual refresh.

<p align="center">
  <img src="docs/images/HomeScreen.jpeg" width="300">
</p>

---

### 4️⃣ Order Details & Logistics Tracking 🗺️
Once a captain selects an order, the app provides a comprehensive breakdown to ensure accuracy.
* **Detailed Specifications:** Itemized receipt with images, quantities, and financial breakdown (EGP).
* **Location Intelligence:** Precise geolocation on an interactive **Google Map** with a **Quick Call** button for customer contact.
* **Status Management:** Prominent **"تم استلام الطلب"** button to track fulfillment progress.

| 📦 Order Specs | 📍 Map & Client |
|:---:|:---:|
| <img src="docs/images/orderDetails.jpeg" width="250"> | <img src="docs/images/clientDetails.jpeg" width="250"> |

---

### 5️⃣ Order History & Status 🕒
A comprehensive archive of activities, categorized by status to maintain clear visibility.
* **Dual-Category System:** Separate tabs for **Active (الحالية)** and **Completed (السابقة)** orders.
* **Status Tags:** High-visibility badges (Orange for processing, Green for completed).
* **Quick Re-entry:** A "Details" button to jump back into any past order breakdown.

| 🔄 In-Progress | ✅ Completed |
|:---:|:---:|
| <img src="docs/images/inprogressOrder.jpeg" width="250"> | <img src="docs/images/doneOrder.jpeg" width="250"> |

---

### 6️⃣ Account & Settings ⚙️
The Account section provides captains with full control over their personal data and app preferences.
* **CRUD Operations:** View and update personal profile and vehicle documentation via secure **PATCH/PUT** requests.
* **Notifications Center:** Chronological log of alerts organized by date (Today, Yesterday, Older).
* **Localization:** Full support for **Arabic & English** languages with a custom switcher.

| 🔔 Alerts | 👤 Profile | 🌍 Language | 📋 Terms |
|:---:|:---:|:---:|:---:|
| <img src="docs/images/notification.jpeg" width="180"> | <img src="docs/images/account.jpeg" width="180"> | <img src="docs/images/language.jpeg" width="180"> | <img src="docs/images/terms.jpeg" width="180"> |

---

## 🔑 Key Features

- ✅ **Multi-language support** - Arabic & English with easy_localization
- ✅ **Firebase integration** - FCM for real-time notifications
- ✅ **Push & Local notifications** - Keep captains informed
- ✅ **Responsive design** - flutter_screenutil for all screen sizes
- ✅ **Clean architecture** - MVVM with organized core layer
- ✅ **Centralized routing** - Easy navigation management
- ✅ **Comprehensive theme system** - Consistent UI/UX
- ✅ **Google Maps integration** - Real-time location tracking
- ✅ **Secure authentication** - Token-based auth with validation
- ✅ **Image upload** - Document verification for captains

---

## 📦 Dependencies

Key packages used:
- `flutter_screenutil` - Responsive UI across devices
- `easy_localization` - Internationalization (AR/EN)
- `firebase_core` & `firebase_messaging` - Firebase services & FCM
- `flutter_local_notifications` - Local notification system
- `shared_preferences` - Local data storage
- `flutter_svg` - SVG asset support
- `google_maps_flutter` - Maps integration
- `bloc` & `flutter_bloc` - State management

---

## 🛠 Installation & Setup

```bash
# 1. Clone the repository
git clone https://github.com/Brmja-Tech/Tawfeer-Delivery.git

# 2. Install dependencies
flutter pub get

# 3. Run the app
flutter run

# 4. Build for release
flutter build apk --release
```

---

## 💻 Development Guidelines

### Naming Conventions:
- **Classes**: PascalCase (e.g., `AppTextStyles`, `CacheService`)
- **Files**: snake_case (e.g., `app_router.dart`, `cache_service.dart`)
- **Constants**: camelCase (e.g., `loginScreen`, `primaryColor`)
- **Routes**: Prefixed with `/` (e.g., `'/login'`, `'/home'`)

### Adding New Features:
1. Place feature-specific code in appropriate `Feautres/` folder
2. Add reusable components to `core/components/`
3. Define new routes in `core/config/routes/route_constants.dart`
4. Add route handling in `core/config/routes/app_router.dart`
5. Add assets paths to `core/constants/assets/`
6. Follow existing MVVM pattern
7. Use Cubit for state management


