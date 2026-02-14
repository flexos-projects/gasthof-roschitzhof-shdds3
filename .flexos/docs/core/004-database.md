---
id: database
title: 'Database Schema & Data Models'
description: 'Defines the structure of the database collections, including fields, types, and relationships for the project.'
type: doc
subtype: core
status: draft
sequence: 4
tags:
  - database
  - schema
  - technical
createdAt: '2024-05-21T10:00:00Z'
updatedAt: '2024-05-21T10:00:00Z'
---

## 1. Introduction

This document specifies the database schema for the Gasthof Roschitzhof project. We will use Firebase Firestore, a NoSQL document database, which offers flexibility and scalability. The schema is designed to support all core features, from user authentication to dynamic content management. Each top-level entity is represented as a collection.

## 2. Core Collections

### 2.1. `users`
This collection stores information for registered users, enabling personalization and secure access as defined in the [Features Document](.flexos/docs/core/002-features.md).
*   **Description:** Manages user accounts for authentication and preferences.
*   **Fields:**
    *   `id` (String, Required): Unique ID from Firebase Authentication, used as the document ID.
    *   `email` (Email, Required): User's login email.
    *   `display_name` (String): User's chosen public name.
    *   `role` (Enum, Required): User's permission level. Defaults to `guest`. Can be `admin` for content management.
    *   `preferences` (Object): Stores user-specific settings, e.g., `{ "darkMode": true, "newsletterSubscribed": false }`.
    *   `created_at` (Timestamp, Required): Server timestamp of account creation.

### 2.2. `bookings`
This collection is critical for the business, managing all table and room reservations made through the website.
*   **Description:** Stores all reservation data for both the restaurant and lodging.
*   **Fields:**
    *   `id` (String, Required): Auto-generated unique booking ID.
    *   `user_id` (String): Foreign key referencing the `users` collection if the booking is made by a logged-in user.
    *   `type` (Enum, Required): The type of reservation: `table` or `room`.
    *   `status` (Enum, Required): The current state of the booking: `pending`, `confirmed`, `cancelled`.
    *   `start_time` (Timestamp, Required): The date and time for a table booking, or the check-in date for a room.
    *   `end_time` (Timestamp): The check-out date for room bookings.
    *   `guests` (Number, Required): The number of people in the party.
    *   `contact_name` (String, Required): Name provided for the reservation.
    *   `contact_email` (Email, Required): Confirmation email address.
    *   `contact_phone` (String): Contact phone number.
    *   `notes` (String): Any special requests from the user.
    *   `created_at` (Timestamp, Required): Server timestamp of when the booking was made.

### 2.3. `menu_items`
This collection powers the dynamic [Gourmand's Menu page](.flexos/docs/core/003-pages.md). It allows for easy updates by an admin user.
*   **Description:** Contains all food and beverage items available at the Gasthof.
*   **Fields:**
    *   `id` (String, Required): Auto-generated unique item ID.
    *   `name` (String, Required): The name of the dish (e.g., "Frische Forelle 'Müllerin Art'").
    *   `description` (RichText, Required): A detailed description, including sourcing details (e.g., "From our own pond, served with parsley potatoes").
    *   `price` (Number, Required): Price in Euros.
    *   `category` (Enum, Required): `starter`, `main`, `dessert`, `special`, `drink`.
    *   `image_url` (Image): URL to a high-quality photo of the dish, stored in Firebase Storage.
    *   `is_active` (Boolean, Required): Toggles visibility on the public menu.
    *   `updated_at` (Timestamp, Required): Server timestamp of the last modification.

### 2.4. `gpx_routes`
This collection stores the GPX route data offered on the [Biker's Hub page](.flexos/docs/core/003-pages.md).
*   **Description:** Manages downloadable GPX routes for motorcyclists and hikers.
*   **Fields:**
    *   `id` (String, Required): Auto-generated unique route ID.
    *   `name` (String, Required): The name of the route (e.g., "Soboth Panorama Tour").
    *   `description` (RichText, Required): A compelling description of the route's highlights.
    *   `distance_km` (Number, Required): The route's total distance in kilometers.
    *   `type` (Enum, Required): The route type: `motorcycle` or `hike`.
    *   `gpx_file_url` (File, Required): URL to the `.gpx` file, stored in Firebase Storage.
    *   `thumbnail_image_url` (Image): URL to a representative image for the route card.

### 2.5. `testimonials`
This collection aggregates social proof for display on the homepage and other relevant pages.
*   **Description:** Stores curated customer testimonials and social media posts.
*   **Fields:**
    *   `id` (String, Required): Auto-generated unique ID.
    *   `author_name` (String, Required): Name of the person who gave the testimonial.
    *   `author_source` (String): The platform it came from (e.g., "Outdooractive", "Instagram").
    *   `content` (RichText, Required): The text of the testimonial.
    *   `rating` (Number): An optional star rating (1-5).
    *   `is_approved` (Boolean, Required): Must be `true` to be displayed on the site. Allows for moderation.
    *   `created_at` (Timestamp, Required): Date the testimonial was recorded or imported.