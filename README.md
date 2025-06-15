# GENDAI Time Tracking Application [EN]

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


# GENDAI Приложение для отслеживания рабочего времени [RU]

## Обзор
Это полнофункциональное приложение для учета рабочего времени, созданное специально для чешской компании GENDAI, s.r.o. Приложение позволяет сотрудникам отслеживать свое рабочее время, управлять записями рабочего времени, просматривать статистику и генерировать отчеты. Система использует аутентификацию Replit для управления пользователями и предоставляет современный, ориентированный на мобильные устройства интерфейс с поддержкой нескольких языков (чешский, украинский, английский).

## Архитектура системы

### Архитектура бэкенда
- **Фреймворк**: Express.js с TypeScript
- **Аутентификация**: Аутентификация Replit OpenID Connect (OIDC)
- **База данных**: PostgreSQL с Drizzle ORM
- **Управление сессиями**: Сессии с поддержкой PostgreSQL с помощью connect-pg-simple
- **Провайдер базы данных**: Neon Database с бессерверными соединениями
*** Переведено с помощью www.DeepL.com/Translator (бесплатная версия) ***

### Архитектура фронтенда
- **Фреймворк**: React 18 с TypeScript
- **Инструмент для сборки**: Vite для разработки и производственных сборок
- **Роутинг**: Wouter для маршрутизации на стороне клиента
- **Библиотека пользовательского интерфейса**: Radix UI компоненты с Tailwind CSS
- **Управление состоянием**: TanStack React Query для состояния сервера
- **Стайлинг**: Tailwind CSS с фирменными цветами GENDAI

### Проектирование базы данных
- Таблица **Users**: Хранит профили пользователей с почасовой оплатой, контактной информацией и предпочтениями.
- **Таблица временных записей**: Отслеживает рабочие сессии с датой, временем, описаниями и расчетами
- Таблица **Сессии**: Управление сеансами аутентификации (требуется для Replit Auth)

## Ключевые компоненты

### Система аутентификации
- Использует OIDC-провайдер Replit для безопасной аутентификации
- Автоматическое создание/обновление пользователя при входе в систему
- Аутентификация на основе сеанса с использованием хранилища PostgreSQL
- Защищенные маршруты API с промежуточным ПО аутентификации

### Особенности учета рабочего времени
- Создание, редактирование и удаление записей о времени
- Автоматический расчет часов по времени начала/окончания
- Поддержка выходных и нерабочих дней
- Ежемесячная статистика и расчеты платежей
- Экспорт отчетов в формате PDF

### Пользовательский интерфейс
- Оптимизированный под темные темы дизайн
- Первичный отзывчивый макет для мобильных устройств
- Нижняя навигация для мобильных пользователей
- Поддержка нескольких языков (чешский основной, украинский, английский)
- Валидация форм и обработка ошибок в режиме реального времени

### Структура API
- Структура RESTful API
- Конечные точки аутентификации (`/api/auth/*`)
- CRUD-операции с временными записями (`/api/time-entries/*`)
- Управление профилем пользователя (`/api/profile`)
- Конечные точки статистики (`/api/stats/*`)

## Поток данных

1. **Поток аутентификации**:
- Пользователь нажимает кнопку входа → Перенаправление на Replit OIDC
- Успешная аутентификация → Данные пользователя сохраняются/обновляются в базе данных
- Сессия создается и хранится в PostgreSQL
- Фронтенд получает данные пользователя через `/api/auth/user`.

2. **Управление временными записями**:
- Пользователь создает запись через модальную форму
- Данные проверяются на клиенте и сервере
- Ввод сохраняется с автоматическими вычислениями
- Обновление статистики в режиме реального времени
- Опциональное создание PDF-файлов для отчетности

3. **Расчет статистики**:
- Ежемесячное суммирование часов и выплат
- Отслеживание прогресса в сравнении с целевыми часами
- Обновления в режиме реального времени при изменении записей

## External Dependencies

### Основные зависимости
- **@neondatabase/serverless**: Соединение с базой данных PostgreSQL
- **drizzle-orm**: Безопасные для типов запросы к базам данных и миграции
- **@tanstack/react-query**: Управление состоянием сервера
- **@radix-ui/**: Доступные примитивы компонентов пользовательского интерфейса
- **wouter**: Легкий React-маршрутизатор
- **@react-pdf/renderer**: Возможности генерации PDF

### Инструменты разработки
- **tsx**: Выполнение TypeScript для разработки
- **esbuild**: Сборка производственного пакета
- **tailwindcss**: Утилитарный CSS-фреймворк
- **vite**: Сервер быстрой разработки и бандлер
- 
### Replit Integration
- **@replit/vite-plugin-runtime-error-modal**: Обработка ошибок разработки
- **@replit/vite-plugin-cartographer**: Инструментарий для разработки

## Стратегия развертывания

### Среда разработки
- Используется Vite dev server с HMR
- База данных PostgreSQL, инициализированная через Replit
- Переменные окружения для базы данных и секретов сессии
- Оверлей ошибок в реальном времени при разработке

### Развертывание в производстве
- Vite собирает оптимизированные статические активы
- Express-сервер обслуживает API и статические файлы
- esbuild собирает код сервера для производства
- Автомасштабируемая цель развертывания на Replit
- Сохранение сессий через хранилище с поддержкой базы данных

### Конфигурация среды
- `DATABASE_URL`: Строка подключения к PostgreSQL
- `SESSION_SECRET`: Ключ шифрования сеанса
- `REPL_ID`: Идентификатор среды репликации
- `ISSUER_URL`: URL-адрес провайдера OIDC (по умолчанию - Replit)

## Changelog
```
Changelog:
- 15 июня 2025 года. Первоначальная настройка
```

## Предпочтения пользователя
```
Предпочитаемый стиль общения: Простой, повседневный язык.
```
