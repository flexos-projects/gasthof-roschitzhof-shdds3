---
id: pages
title: 'Site Architecture: Pages & Content'
description: 'An overview of the website sitemap, detailing the purpose, content sections, and key features of each page.'
type: doc
subtype: core
status: draft
sequence: 3
tags:
  - architecture
  - pages
  - core
createdAt: '2024-05-21T10:00:00Z'
updatedAt: '2024-05-21T10:00:00Z'
---

## 1. Introduction

This document outlines the sitemap and page structure for the Gasthof Roschitzhof Digital Relaunch. Each page is designed with a specific purpose and audience in mind, contributing to a cohesive and intuitive user journey. The architecture is built around the persona-driven navigation introduced in the [Features Document](.flexos/docs/core/002-features.md).

## 2. Public Pages

These pages are accessible to all visitors and form the core of the public-facing website.

### 2.1. Homepage (`/index`)
The homepage is the digital front door and the most critical marketing asset. Its purpose is to captivate visitors within seconds, communicate the unique value proposition, and guide them to the most relevant content path.
*   **Route:** `/`
*   **Key Sections:**
    *   **Alpine Hero Showcase:** Full-screen ambient video loop.
    *   **Dynamic Trust Bar:** Live ratings and opening hours.
    *   **Headline & CTAs:** "Your Basecamp on the Soboth Pass." with "Book a Table" and "Stay Overnight" buttons.
    *   **Choose Your Adventure Grid:** The primary navigation with cards for Biker, Gourmand, and Family.
    *   **Social Proof:** Curated Instagram feed and testimonial slider.
    *   **Comprehensive Footer:** With one-tap contact, map, and certification badges.

### 2.2. Biker's Hub (`/bikers`)
This dedicated landing page serves the primary motorcyclist persona. It acts as a resource hub, providing tangible value beyond just accommodation and food.
*   **Route:** `/bikers`
*   **Key Sections:**
    *   **Biker-Themed Hero:** A powerful image or short video of motorcycles on the Soboth pass.
    *   **Amenities List:** Clearly itemizes biker-friendly features: secure garage, drying room, tool workshop, etc.
    *   **GPX Route Maps:** An interactive map showcasing local routes. Each route will be a downloadable GPX file from the `gpx_routes` collection, as defined in the [Database Schema](.flexos/docs/core/004-database.md).
    *   **Biker Testimonials:** A filtered view of testimonials from other riders.

### 2.3. Gourmand's Delights & Menu (`/menu`)
This page showcases the culinary heart of the Gasthof, focusing on the "zero food miles" philosophy and farm-to-table experience.
*   **Route:** `/menu`
*   **Key Sections:**
    *   **Culinary Story:** A brief narrative about the organic farm, fresh trout pond, and commitment to local sourcing.
    *   **Dynamic Daily Menu:** Fetches and displays items from the `menu_items` collection. The menu will be easy to update via a CMS, as described in the [Admin Update Flow](.flexos/docs/core/005-flows.md).
    *   **Food Gallery:** High-quality, professional photography of the signature dishes.
    *   **Booking CTA:** A persistent "Book Your Table" button.

### 2.4. Family Adventures (`/family`)
This page is tailored for families planning a visit, highlighting the safety, fun, and nature-oriented aspects of the Roschitzhof.
*   **Route:** `/family`
*   **Key Sections:**
    *   **Family-Focused Hero:** An image of a family enjoying the property.
    *   **Facilities Showcase:** Details on the playground, kid-friendly menu options, and high chairs.
    *   **Local Activities:** Information on nearby nature trails, swimming spots, and family-friendly excursions.

### 2.5. Booking & Reservations (`/book`)
A functional, streamlined page for converting user interest into confirmed bookings. It will handle both table and room reservations.
*   **Route:** `/book`
*   **Key Sections:**
    *   **Reservation Type Selector:** Toggles between "Book a Table" and "Stay Overnight."
    *   **Booking Forms:** Simple, intuitive forms with calendar/time pickers and guest counters. Data will be saved to the `bookings` collection.
    *   **Confirmation Step:** A summary of the booking details before final submission.

### 2.6. Contact & Location (`/contact`)
A simple, utility-focused page providing all necessary contact and location information.
*   **Route:** `/contact`
*   **Key Sections:**
    *   **Contact Details:** Large, clickable phone number (+43 3460 362) and email address (a.strutz1@gmx.at).
    *   **Interactive Map:** An embedded Google Map centered on Soboth 162 with a "Get Directions" button.
    *   **Dynamic Hours:** Live display of today's opening hours.

## 3. Authenticated Pages

These pages are accessible only to logged-in users.

### 3.1. Login / Signup (`/auth`)
The gateway for user authentication, providing access to personalized features.
*   **Route:** `/auth`
*   **Key Sections:**
    *   Login & Signup forms.
    *   "Forgot Password" functionality.

### 3.2. User Settings & Profile (`/settings`)
A private dashboard for registered users to manage their information and preferences.
*   **Route:** `/settings`
*   **Key Sections:**
    *   Profile editor (name, email, password).
    *   Booking history list (references the `bookings` collection).
    *   Saved GPX routes.