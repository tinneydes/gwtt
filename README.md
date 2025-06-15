# GENDAI Time Tracking Application

## Overview

This is a full-stack time tracking application built specifically for GENDAI, s.r.o., a Czech company. The application allows employees to track their working hours, manage time entries, view statistics, and generate reports. The system uses Replit authentication for user management and provides a modern, mobile-first interface with multi-language support (Czech, Ukrainian, English).

## System Architecture

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Authentication**: Replit OpenID Connect (OIDC) authentication
- **Database**: PostgreSQL with Drizzle ORM
- **Session Management**: PostgreSQL-backed sessions using connect-pg-simple
- **Database Provider**: Neon Database with serverless connections

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for development and production builds
- **Routing**: Wouter for client-side routing
- **UI Library**: Radix UI components with Tailwind CSS
- **State Management**: TanStack React Query for server state
- **Styling**: Tailwind CSS with custom GENDAI brand colors

### Database Design
- **Users Table**: Stores user profiles with hourly rates, contact info, and preferences
- **Time Entries Table**: Tracks work sessions with date, time, descriptions, and calculations
- **Sessions Table**: Manages authentication sessions (required for Replit Auth)

## Key Components

### Authentication System
- Uses Replit's OIDC provider for secure authentication
- Automatic user creation/update on login
- Session-based authentication with PostgreSQL storage
- Protected API routes with authentication middleware

### Time Tracking Features
- Create, edit, and delete time entries
- Automatic hours calculation from start/end times
- Weekend and non-working day support
- Monthly statistics and payment calculations
- PDF export functionality for reports

### User Interface
- Dark theme optimized design
- Mobile-first responsive layout
- Bottom navigation for mobile users
- Multi-language support (Czech primary, Ukrainian, English)
- Real-time form validation and error handling

### API Structure
- RESTful API design
- Authentication endpoints (`/api/auth/*`)
- Time entry CRUD operations (`/api/time-entries/*`)
- User profile management (`/api/profile`)
- Statistics endpoints (`/api/stats/*`)

## Data Flow

1. **Authentication Flow**:
   - User clicks login → Redirected to Replit OIDC
   - Successful auth → User data stored/updated in database
   - Session created and stored in PostgreSQL
   - Frontend receives user data via `/api/auth/user`

2. **Time Entry Management**:
   - User creates entry via modal form
   - Data validated on client and server
   - Entry stored with automatic calculations
   - Real-time updates to statistics
   - Optional PDF generation for reporting

3. **Statistics Calculation**:
   - Monthly aggregation of hours and payments
   - Progress tracking against target hours
   - Real-time updates when entries change

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: PostgreSQL database connection
- **drizzle-orm**: Type-safe database queries and migrations
- **@tanstack/react-query**: Server state management
- **@radix-ui/**: Accessible UI component primitives
- **wouter**: Lightweight React router
- **@react-pdf/renderer**: PDF generation capabilities

### Development Tools
- **tsx**: TypeScript execution for development
- **esbuild**: Production bundle building
- **tailwindcss**: Utility-first CSS framework
- **vite**: Fast development server and bundler

### Replit Integration
- **@replit/vite-plugin-runtime-error-modal**: Development error handling
- **@replit/vite-plugin-cartographer**: Development tooling

## Deployment Strategy

### Development Environment
- Uses Vite dev server with HMR
- PostgreSQL database provisioned via Replit
- Environment variables for database and session secrets
- Real-time error overlay in development

### Production Deployment
- Vite builds optimized static assets
- Express server serves API and static files
- esbuild bundles server code for production
- Autoscale deployment target on Replit
- Session persistence through database-backed storage

### Environment Configuration
- `DATABASE_URL`: PostgreSQL connection string
- `SESSION_SECRET`: Session encryption key
- `REPL_ID`: Replit environment identifier
- `ISSUER_URL`: OIDC provider URL (defaults to Replit)

## Changelog

```
Changelog:
- June 15, 2025. Initial setup
```

## User Preferences

```
Preferred communication style: Simple, everyday language.
```
