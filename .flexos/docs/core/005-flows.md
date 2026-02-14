---
id: flows
title: 'User & System Flows'
description: 'Describes key user journeys and system processes, from booking a table to updating the daily menu.'
type: doc
subtype: core
status: draft
sequence: 5
tags:
  - flows
  - user-journey
  - core
createdAt: '2024-05-21T10:00:00Z'
updatedAt: '2024-05-21T10:00:00Z'
---

## 1. Introduction

This document outlines the primary user and system flows for the Gasthof Roschitzhof website. Understanding these step-by-step processes is crucial for building an intuitive user experience and ensuring backend processes are robust. These flows directly correspond to the features and pages defined in the [Features](.flexos/docs/core/02-features.md) and [Pages](.flexos/docs/core/03-pages.md) documents.

## 2. Core User Flows

### 2.1. Flow: Book a Table (`book-table-flow`)
This is a critical conversion flow for the business, designed to be as frictionless as possible.
*   **Trigger:** User clicks the "Book a Table" CTA on the homepage or navigation.
*   **Steps:**
    1.  **Navigate & Pre-select (System):** The user is navigated to the `/book` page. The system ensures the "Table Booking" form is visible by default.
    2.  **Select Details (User):** The user interacts with form elements to select a date, time, and the number of guests. The system provides real-time validation (e.g., cannot book in the past).
    3.  **Check Availability (System):** Upon selection, the system can perform a quick (optional) check against known busy periods or fully booked slots.
    4.  **Enter Contact Info (User):** The user fills in their name, email, and phone number. If the user is logged in, these fields are pre-populated from their `users` profile.
    5.  **Add Notes (User, Optional):** The user can add special requests (e.g., "window seat," "allergy information") in a dedicated text field.
    6.  **Confirm Reservation (User):** The user reviews a summary of their booking details and clicks a "Confirm Booking" button.
    7.  **Process & Confirm (System):** The system creates a new document in the `bookings` collection with a status of `pending`. It then displays an on-screen confirmation message and sends a confirmation email to the user's provided address.

### 2.2. Flow: Download GPX Route (`download-gpx-route`)
This flow provides direct value to the key motorcyclist persona, establishing the Roschitzhof as a useful resource.
*   **Trigger:** User clicks the "Download GPX Route Maps" CTA on the Biker's Adventure Card or within the `/bikers` page.
*   **Steps:**
    1.  **Access Biker's Hub (User):** The user arrives at the `/bikers` page.
    2.  **Browse Routes (User):** The user sees a list or grid of available routes, each displayed with a name, thumbnail, and key stats (distance, type) pulled from the `gpx_routes` collection.
    3.  **Select Route (User):** The user clicks on a specific route they are interested in.
    4.  **Initiate Download (User/System):** Clicking a "Download GPX" button on the route's detail view triggers the browser's file download functionality. The file is served directly from the `gpx_file_url` stored in the route's Firestore document.
    5.  **Display Confirmation (System):** A subtle notification confirms that the download has started (e.g., "Soboth Panorama Tour.gpx is downloading...").

### 2.3. Flow: First-Time Guest Onboarding (`onboarding-guest`)
This subtle flow helps orient new visitors to the key features of the redesigned site without being intrusive.
*   **Trigger:** A new user session is detected on the homepage.
*   **Steps:**
    1.  **Hero Introduction (System):** After the hero video loads, a small, dismissible tooltip appears, saying "Welcome to the new Roschitzhof!"
    2.  **Highlight Trust Bar (System):** After a brief delay or on the first scroll, a subtle animation draws attention to the Dynamic Trust Bar, with a tooltip explaining "Live Ratings & Hours."
    3.  **Introduce Adventure Cards (System):** As the user scrolls to the "Choose Your Adventure" section, the cards may have a gentle animation to draw the eye, guiding them to the new navigation paradigm.
    4.  **Showcase Mobile Nav (System, Mobile Only):** On mobile devices, the sticky bottom bar will briefly animate or pulse to indicate its interactivity and purpose.
    5.  **End Tour (User):** The user dismisses any tooltips or simply continues to interact with the site, ending the guided experience.

## 3. Admin System Flow

### 3.1. Flow: Admin Updates Daily Menu (`admin-update-daily-menu`)
This flow empowers the Gasthof owner (Ms. Strutz) to keep the online menu fresh and accurate without technical assistance.
*   **Trigger:** An authenticated admin user logs into the Content Management System (CMS) backend.
*   **Steps:**
    1.  **Admin Login (User):** The admin navigates to a secure login portal (e.g., `/admin`) and authenticates using their credentials (role: `admin` in the `users` collection).
    2.  **Navigate to Menu Management (User):** Within the CMS dashboard, the admin clicks on the "Menu" or "Speisekarte" section.
    3.  **View Menu Items (System):** The system displays a list of all current dishes, pulling data from the `menu_items` collection.
    4.  **Edit/Add Items (User):** The admin can click "Edit" on an existing item or "Add New Item." This opens a form with fields for `name`, `description` (using a rich text editor), `price`, `category`, and an `is_active` toggle.
    5.  **Publish Changes (User):** After making changes, the admin clicks "Save & Publish."
    6.  **Update Database (System):** The system updates the corresponding document(s) in the `menu_items` collection in Firestore. The `updated_at` timestamp is automatically set to the current time.
    7.  **Confirmation (System):** The CMS displays a success message, and the changes are immediately reflected on the public-facing `/menu` page.