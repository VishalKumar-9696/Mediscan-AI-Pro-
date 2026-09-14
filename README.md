# Mediscan AI Pro – AI-Powered Healthcare Assistant & Blood Finder

**College Hackathon Project**  
**Team**: Team The Code Burner  
**Institution**: Maharana Pratap Institute of Technology (MPIT), Gorakhpur  
**Project Path**: `C:\Users\Asus\.gemini\antigravity\scratch\mediscan-ai-pro`

---

## 🌟 Executive Summary

**Mediscan AI Pro** is an emergency-ready healthcare intelligence web platform designed to streamline medical specialist discovery, prescription organization, medication adherence tracking, and critical blood resource allocation across the Gorakhpur region.

Built with a high-contrast healthcare UI palette (Deep Navy `#0f172a`, Clinical Teal `#0d9488`, Pure White, Emerald Green `#10b981`, and Emergency Crimson `#ef4444`), the application operates with **zero command/build prerequisites**. It can be opened directly in any modern browser by double-clicking `index.html` or running a lightweight local server.

---

## 🚀 Key Modules & Functional Workflows

### 1. Best Doctors & Healthcare Specialists Finder (`js/modules/specialists.js`)
- **Specialty Selection Cards**: Filter across 7 categories (Dermatology, Ophthalmology, Orthopedic, Nutritionist, Cardiology, General Physician, Pediatrics).
- **Featured Demo Listings (Gorakhpur)**:
  - **Dr. Naveen Verma** – Dermatology / Skin, Gorakhpur
  - **Raj Eye Hospital** – Eye Care, Gorakhpur
  - **Dr. Aggarwal** – Orthopedics / Bone Care, Buxipur, Gorakhpur
  - **Dr. Rinky Gupta** – Nutrition and Diet Consultation, Sadar, Gorakhpur
  - *Plus Dr. Anand Srivastava (Cardiology), Dr. Priya Pandey (General Medicine), Dr. K.K. Rai (Pediatrics)*.
- **Safety Badge**: Labeled with `"Demo listing — verification required"`.
- **Search & Filter**: Real-time search by doctor name, hospital, or Gorakhpur locality (Buxipur, Sadar, Golghar, Medical College Rd, etc.).
- **Appointment Request Lifecycle**:
  - `Requested` → `Accepted` / `Declined` → `Completed` / `Cancelled`.
  - Stored in persistent database and linked to Patient Medical Health Passport.

### 2. Prescription Organizer & Medicine Reminder (`js/modules/prescriptions.js`)
- **Document Upload**: Supports PDF, JPG, and PNG with visual preview.
- **OCR Text Extraction Simulation**: Extracts draft text with mandatory clinical disclaimer:
  > *"Draft extracted text — user verification required. Never assume OCR medicine names or dosages are correct."*
- **Medicine Reminders Schedule**:
  - Sample 3-slot daily schedule: **8:00 AM** (Medicine A), **2:00 PM** (Medicine B), **8:00 PM** (Medicine A).
  - Actions: **Mark as Taken**, **Mark as Skipped**, and track Missed doses.
  - Interactive **Daily Adherence Percentage Progress Ring**.
  - **Missed-Dose Clinical Advisory**: Advises patients to follow prescriptions and consult physicians rather than doubling doses.
  - Browser notifications permission toggle + in-app alert cards.

### 3. Blood Finder — Main Emergency Feature (`js/modules/bloodFinder.js`)
- **Emergency Requisition Form**:
  - Patient Name / Ref ID, Blood Group (A+, A-, B+, B-, AB+, AB-, O+, O-), Units Needed, Current Location (Gorakhpur), Hospital Name, Urgency (Normal, Urgent, Emergency), Contact Information, Clinical Notes.
- **Clinical Compatibility Engine**:
  - Full ABO and Rh compatibility rules (O- universal donor, AB+ universal recipient, Rh- constraints).
- **Multi-Factor Ranking Algorithm**:
  1. Compatibility match score
  2. Reported stock adequacy
  3. Distance from patient (Haversine calculation in km)
  4. Urgency weight
  5. Recency of facility updates
- **Emergency Pipeline Lifecycle**:
  - `Submitted` → `Searching` → `Contacted` → `Provider Confirmation Pending` → `Confirmed by Provider` → `Completed` / `Cancelled`.
- **Safety Warning**:
  > *"Blood availability shown in this prototype is illustrative. Always confirm availability and compatibility with the hospital or blood bank."*

### 4. Blood Donor Registration & Donor Network (`js/modules/donorNetwork.js`)
- **Voluntary Donor Registration**:
  - Name, Blood Group, Locality (Mohaddipur, Betiahata, Golghar, Rapti Nagar, etc.), Preferred Contact Method, Availability Status, Last Donation Date, Privacy & Emergency Alerts Consent.
- **Privacy Protection**:
  - Shielding exact residential address and private telephone numbers; public cards display pseudonymized ID/display name, blood group, and locality.
- **Consent-Based Request Workflow**:
  - Requester sends request → Donor dashboard receives notification → Donor can **Accept** or **Decline** → Status updates in requester view.
- **Medical Eligibility Notice**: Donors must undergo mandatory hemoglobin and infection screening at licensed facilities before donation.

### 5. Blood Bank Management & Staff Portal (`js/modules/bloodBanks.js`)
- **Gorakhpur Facilities Included**:
  - BRD Medical College Blood Center
  - District Hospital Blood Bank
  - Indian Red Cross Society Blood Bank
  - AIIMS Gorakhpur Blood Transfusion Center
- **Role-Based Staff Mode**:
  - Switch active persona to **Blood Bank Staff** or **Admin** to unlock the inventory modification panel.
  - Update unit counts per blood group and verify instantaneous synchronization with the Blood Finder and Map.

### 6. Interactive Blood Finder Map (`js/modules/mapView.js`)
- **Leaflet & OpenStreetMap**:
  - Centered on Gorakhpur (26.7588° N, 83.3697° E).
  - Custom colored SVG markers: Blood Banks (Crimson), Hospitals (Blue), Donors (Orange), Patient SOS location (Pulse marker).
  - Interactive radius slider (1 km to 30 km) with dynamic visual circle overlay.
  - Marker popups with reported stock, distance, and direct 1-click requisition buttons.

### 7. Patient Medical Health Passport (`js/modules/passport.js`)
- **Unified Health Record**:
  - Baseline health profile (Blood Group O+, Penicillin allergies, Chronic conditions, Emergency contacts, ABHA ID).
  - Document Vault storing prescriptions, CBC lab reports, and vaccination certificates.
  - Unified Chronological Activity Timeline combining prescriptions, taken doses, doctor appointments, and emergency blood requests.
  - **Paramedic Emergency QR**: Offline-ready rapid scan card for first responders.

### 8. Patient Dashboard Command Center (`js/modules/dashboard.js`)
- 9 dedicated responsive cards:
  1. *My Blood Group* with compatibility helper
  2. *Find Blood Now* (Emergency crimson 1-click trigger)
  3. *Register as Blood Donor*
  4. *My Medical Passport* quick summary
  5. *Today's Medicine Reminders* with quick take action
  6. *Upcoming Appointment Requests* status tracker
  7. *Recommended Specialists* shortcuts
  8. *Recent Blood Requests* live tracking pill
  9. *Emergency Assistance* hotlines (Ambulance 108, 102, Police 112, Blood 104)

### 9. Persistent Database & State Engine (`js/db.js`)
- Implements all 14 requested entities:
  - `User`, `PatientProfile`, `MedicalDocument`, `Prescription`, `Medicine`, `MedicineReminder`, `Doctor`, `Hospital`, `BloodBank`, `BloodInventory`, `DonorProfile`, `BloodRequest`, `DonationRequest`, `AppointmentRequest`, `Notification`.
- Persistent synchronization in `localStorage` with instant reset capability.

### 10. 1-Click Hackathon Evaluator Scenarios (`js/demoPresets.js`)
- Dedicated **Demo Testing Bar** in the top navigation offering 1-click test runs for all requested workflows:
  - *Demo 1: Gorakhpur Specialists Directory*
  - *Demo 2: Emergency O+ Blood Request (2 Units, Gorakhpur)*
  - *Demo 3: Prescription & Medicine Schedule (8 AM / 2 PM / 8 PM)*
  - *Demo 4: Donor Network & Accept Request*
  - *Demo 5: Blood Bank Staff Inventory Update*
  - *Demo 6: Interactive Leaflet Map & Radius Filter*
  - *Demo 7: Medical Health Passport & Paramedic QR*

---

## 💻 How to Run the Application

Because Mediscan AI Pro uses standalone modern web modules and standard CDNs (Tailwind CSS, Leaflet.js, Google Fonts), **no build step, npm install, or terminal compilation is needed!**

1. Simply navigate to:
   ```
   C:\Users\Asus\.gemini\antigravity\scratch\mediscan-ai-pro
   ```
2. Double-click **`index.html`** to open directly in Google Chrome, Microsoft Edge, Firefox, or any modern web browser.
3. Or serve using any local static file server (such as Python `python -m http.server 8000`, VS Code Live Server, or Node `npx serve`).

---

## 🏆 Hackathon Submission Details

- **Application Name**: Mediscan AI Pro – AI-Powered Healthcare Assistant & Blood Finder
- **Team**: The Code Burner
- **College**: Maharana Pratap Institute of Technology, Gorakhpur
- **Location**: Gorakhpur, Uttar Pradesh, India
- **Year**: 2026
