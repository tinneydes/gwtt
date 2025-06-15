# Product Requirements Document (PRD)
## GENDAI Work Time Tracker

### Project Overview
**Product Name:** GENDAI Work Time Tracker  
**Version:** 1.0  
**Date:** June 15, 2025  
**Target Platform:** Web Application (React-based)  
**Company:** GENDAI, s.r.o.  

### Executive Summary
The GENDAI Work Time Tracker is a modern, native React application designed for efficient work time management. The application features a clean, modern UI inspired by the GENDAI brand identity with dark theme aesthetics. It provides comprehensive time tracking capabilities with multilingual support for Czech, Ukrainian, and English languages.

### Core Functional Requirements

#### 1. Authentication System
- **User Registration & Login:** Secure authentication system with user account creation
- **Session Management:** Persistent user sessions with secure logout functionality
- **User Profiles:** Personal profile management with editable user information

#### 2. Time Tracking Features
- **Time Entry Creation:** Form-based time entry with start/end time selection
- **Time Entry Editing:** Full CRUD operations for existing time entries
- **Time Entry Deletion:** Secure deletion with user confirmation
- **Flexible Time Input:** Support for both worked and non-worked days
- **Weekend Support:** Special handling for weekend entries

#### 3. Data Management & Export
- **PDF Export:** Export functionality using template file `výkaz práce_2022.xls`
- **Report Generation:** Monthly and custom date range reports
- **Data Persistence:** Reliable data storage with backup capabilities

#### 4. Multilingual Support
- **Czech Language:** Primary language support with full localization
- **Ukrainian Language:** Complete Ukrainian translation for all UI elements
- **English Language:** English language support for international users
- **Language Switching:** Dynamic language switching without page reload

#### 5. User Interface Requirements
- **Modern Design:** Super modern and clean UI design
- **Dark Theme:** Dark color scheme matching GENDAI brand identity
- **Mobile Responsive:** Optimized for mobile and desktop devices
- **Reference Design:** UI/UX based on provided screenshot references
- **Intuitive Navigation:** User-friendly interface with clear navigation patterns

### Technical Specifications

#### Frontend Architecture
- **Framework:** React 18 with TypeScript
- **Styling:** Tailwind CSS with custom GENDAI theme
- **Components:** Radix UI component library
- **State Management:** TanStack React Query for server state
- **Routing:** Wouter for client-side routing
- **Build Tool:** Vite for development and production builds

#### Backend Architecture
- **Server:** Express.js with TypeScript
- **Database:** PostgreSQL with Drizzle ORM
- **Authentication:** Replit OpenID Connect integration
- **Session Storage:** PostgreSQL-backed sessions
- **API Design:** RESTful API with proper error handling

#### Design System
- **Primary Colors:** 
  - GENDAI Green: hsl(123, 38.5%, 55.1%)
  - Dark Background: hsl(0, 0%, 7.1%)
  - Card Background: hsl(0, 0%, 11.8%)
  - Input Background: hsl(0deg 3.19% 9.56%)
- **Typography:** Inter font family with various weights
- **Spacing:** Consistent spacing system using Tailwind classes
- **Borders:** Subtle borders with hsl(0, 0%, 20%) color

### User Experience Requirements

#### Dashboard Features
- **Statistics Cards:** Monthly overview with worked hours, total payment, hourly rate
- **Progress Indicator:** Circular progress showing monthly completion percentage
- **Recent Entries:** List of recent time entries with editing capabilities
- **Quick Actions:** Easy access to common functions like adding new entries

#### Time Entry Management
- **Date Selection:** Calendar-based date picker for entry dates
- **Time Selection:** Dropdown selectors for start and end times
- **Activity Description:** Text area for describing work performed
- **Rate Configuration:** Configurable hourly rate per entry
- **Work Status:** Toggle for worked/non-worked days and weekends

#### Profile Management
- **Personal Information:** Full name, email, phone, position
- **Work Settings:** Default hourly rate, preferred language
- **Account Security:** Password change and logout functionality
- **Avatar Display:** User initials or profile image display

### Data Models

#### User Entity
```
- ID (String, Primary Key)
- Email (String, Unique)
- First Name (String)
- Last Name (String)
- Full Name (String)
- Phone (String)
- Position (String)
- Hourly Rate (Decimal, Default: 190 CZK)
- Language (String, Default: 'uk')
- Profile Image URL (String)
- Created At (Timestamp)
- Updated At (Timestamp)
```

#### Time Entry Entity
```
- ID (Serial, Primary Key)
- User ID (String, Foreign Key)
- Date (Date)
- Start Time (Time)
- End Time (Time)
- Description (Text)
- Hourly Rate (Decimal)
- Total Hours (Decimal, Calculated)
- Total Payment (Decimal, Calculated)
- Is Worked (Boolean, Default: true)
- Is Weekend (Boolean, Default: false)
- Created At (Timestamp)
- Updated At (Timestamp)
```

### API Endpoints

#### Authentication
- `GET /api/auth/user` - Get current user information
- `GET /api/login` - Initiate login flow
- `GET /api/logout` - Logout user
- `GET /api/callback` - OAuth callback handler

#### User Management
- `PATCH /api/profile` - Update user profile

#### Time Entries
- `GET /api/time-entries` - List time entries with optional date filtering
- `POST /api/time-entries` - Create new time entry
- `PATCH /api/time-entries/:id` - Update existing time entry
- `DELETE /api/time-entries/:id` - Delete time entry

#### Statistics
- `GET /api/stats/monthly` - Get monthly statistics

### Security Requirements
- **Authentication:** Secure OAuth-based authentication via Replit
- **Authorization:** User-specific data access controls
- **Data Validation:** Server-side input validation using Zod schemas
- **Session Security:** Secure session management with proper expiration
- **HTTPS:** All communications over HTTPS in production

### Performance Requirements
- **Load Time:** Initial page load under 3 seconds
- **Responsiveness:** UI interactions respond within 200ms
- **Database Queries:** Optimized queries for large datasets
- **Caching:** Appropriate caching strategies for static assets

### Localization Requirements
- **Language Files:** Structured translation files for each supported language
- **Date Formatting:** Locale-specific date and time formatting
- **Number Formatting:** Currency and number formatting per locale
- **RTL Support:** Future consideration for right-to-left languages

### Export & Reporting Requirements
- **PDF Generation:** High-quality PDF reports using React PDF renderer
- **Template Compliance:** Match structure of `výkaz práce_2022.xls` template
- **Branding:** Include GENDAI branding in exported documents
- **Data Formats:** Support for multiple export formats (PDF primary)

### Quality Assurance
- **TypeScript:** Full type safety throughout the application
- **Error Handling:** Comprehensive error handling with user-friendly messages
- **Loading States:** Appropriate loading indicators for all async operations
- **Validation:** Client and server-side validation for all user inputs

### Future Enhancements
- **Mobile App:** Native mobile applications for iOS and Android
- **Advanced Reporting:** More detailed analytics and reporting features
- **Team Management:** Multi-user organizations with role-based access
- **Time Tracking:** Real-time timer functionality
- **Integrations:** Third-party calendar and project management integrations

### Success Metrics
- **User Adoption:** 100% of GENDAI employees actively using the system
- **Data Accuracy:** 99%+ accuracy in time tracking records
- **User Satisfaction:** 4.5+ star rating from user feedback
- **Performance:** 99.9% uptime and fast response times
- **Efficiency:** 50% reduction in time spent on timesheet management

### Constraints & Assumptions
- **Technology Stack:** Must use React and modern web technologies
- **Authentication:** Must integrate with Replit authentication system
- **Design:** Must follow GENDAI brand guidelines and dark theme
- **Languages:** Must support Czech, Ukrainian, and English initially
- **Budget:** Development within allocated budget and timeline
- **Compliance:** Must comply with Czech labor law requirements for time tracking
