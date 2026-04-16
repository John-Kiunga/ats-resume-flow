# CVForge AI - Project Plan

## 1. Project Overview

CVForge AI is a modern SaaS web application designed to help users generate ATS-optimized CVs tailored to specific job listings. It offers a premium, minimal user experience with features like CV management, AI-powered optimization, LinkedIn profile enhancement, and version history.

## 2. Core Features

*   **Landing Page:** Minimal, premium aesthetic (e.g., Linear.app, Notion.so).
*   **User Authentication:** Secure sign-up and login.
*   **Dashboard:** Central hub for all features.
*   **CV Manager:**
    *   Upload CVs (PDF, DOCX).
    *   Store and edit CVs.
    *   CV cards displaying Title, Job URL, Last Optimized Date.
    *   Plan-based limits (Starter: 2, Pro: 4, Elite: 8 CVs).
*   **Job Targeting Flow:**
    *   Input job listing URL.
    *   Parse job description to extract keywords, required skills, experience signals.
*   **AI Optimization Engine:**
    *   Compare user CV against job description.
    *   Rewrite CV for ATS keyword matching, tone alignment, and quantified achievements.
    *   Provide an ATS-optimized version.
    *   Highlight improvements made.
*   **Export & Storage:**
    *   Download optimized CV as PDF.
    *   Auto-save optimized versions.
    *   Version history per CV.
*   **LinkedIn Optimization Tool:**
    *   Input LinkedIn URL, skills, experience summary.
    *   AI suggestions for Headline, About section, Experience bullets.
    *   Keyword optimization tips.
*   **Monetization:**
    *   Subscription tiers (KES pricing): Starter (360 KES, 2 CVs), Pro (800 KES, 4 CVs), Elite (1500 KES, 8 CVs).
    *   Payment integration (M-Pesa primary, Stripe fallback).
    *   Feature gating based on subscription plan.
    *   Upgrade nudges.

## 3. Tech Stack

*   **Frontend:** Next.js (App Router), Tailwind CSS, shadcn UI, Lucide React (icons).
*   **Backend:** Node.js (within Next.js App Router), OpenAI API.
*   **Database & Auth:** Supabase (PostgreSQL, Auth, Edge Functions).
*   **File Handling:** `pdf-parse` (or similar for PDF/DOCX parsing).
*   **Scraping:** Lightweight job parser (fallback to manual JD text input).
*   **Payments:** M-Pesa Daraja API, Stripe API.

## 4. UX/UI Direction

*   Minimalist, whitespace-heavy design.
*   Premium feel: Soft shadows, rounded cards, subtle gradients.
*   Dashboard-centric layout (e.g., Linear, Stripe).
*   Microinteractions: Loading states, progress indicators.

## 5. Key Differentiators

*   Job-specific CV generation.
*   ATS scoring indicator (conceptual).
*   Versioning per job application.
*   Localized payments (M-Pesa).
*   Bundled LinkedIn optimization.

## 6. Edge Cases & Constraints

*   Handle poorly formatted CVs (normalization).
*   Prevent duplicate CV uploads from counting towards limits.
*   Gracefully handle broken job URLs (fallback to manual JD paste).
*   Optimize OpenAI API costs (caching, diff-based rewrites).

## 7. Agent Assignments

*   **`frontend_engineer`**:
    *   Develop the Next.js application (landing page, dashboard UI, components).
    *   Implement user flows for CV management, job targeting, LinkedIn optimization.
    *   Integrate frontend with Supabase Auth.
    *   Implement microinteractions and UI polish.
    *   Integrate with backend APIs for AI, scraping, and payments.
    *   Handle file upload components.
    *   Ensure `generate_images_bulk` is run first.
*   **`supabase_engineer`**:
    *   Set up Supabase project.
    *   Design and implement database schema (users, cvs, jobs, subscriptions, versions).
    *   Configure Supabase Auth.
    *   Develop Supabase Edge Functions for backend tasks like AI calls, complex parsing, payment processing logic, and handling subscription limits.
    *   Manage database migrations.
*   **`architect` (Self - for final validation)**:
    *   Oversee the build process.
    *   Call `validate_build` upon completion.

## 8. Development Workflow

1.  `architect` creates `plan.md`.
2.  `architect` transfers tasks to `frontend_engineer` and `supabase_engineer`.
3.  `frontend_engineer` develops the frontend application, ensuring `generate_images_bulk` is executed first.
4.  `supabase_engineer` sets up the database, auth, and backend functions.
5.  `frontend_engineer` integrates frontend with Supabase backend APIs and services.
6.  Implement payment gateway integrations (M-Pesa, Stripe).
7.  Thorough testing of all features, including edge cases.
8.  `architect` calls `validate_build` to verify the complete implementation.
