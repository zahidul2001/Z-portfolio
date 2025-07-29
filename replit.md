# Portfolio & Blog Application

## Overview

This is a modern full-stack portfolio and blog application built with React, Node.js/Express, and PostgreSQL. The application showcases a developer's projects and blog posts with a clean, responsive design using shadcn/ui components and Tailwind CSS. It features a single-page application frontend with a RESTful API backend and database integration using Drizzle ORM.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

The application follows a monorepo structure with clear separation between client, server, and shared components:

- **Frontend**: React SPA with TypeScript and Vite bundler
- **Backend**: Express.js REST API server
- **Database**: PostgreSQL with Drizzle ORM
- **Styling**: Tailwind CSS with shadcn/ui component library
- **Routing**: Client-side routing with Wouter
- **State Management**: TanStack Query for server state management

### Directory Structure

```
├── client/          # React frontend application
├── server/          # Express.js backend API
├── shared/          # Shared TypeScript schemas and types
├── migrations/      # Database migration files
└── dist/           # Build output directory
```

## Key Components

### Frontend Architecture

- **Component Library**: shadcn/ui components with Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **State Management**: TanStack Query for API calls and caching
- **Form Handling**: React Hook Form with Zod validation
- **Routing**: Wouter for lightweight client-side routing
- **UI Features**: Toast notifications, responsive design, smooth scrolling navigation

### Backend Architecture

- **API Framework**: Express.js with TypeScript
- **Storage Layer**: PostgreSQL database with Drizzle ORM (DatabaseStorage implementation)
- **Database**: Neon serverless PostgreSQL with connection pooling
- **Middleware**: JSON parsing, URL encoding, request logging
- **Error Handling**: Centralized error handling middleware
- **Development**: Vite integration for hot reloading in development

### Database Schema

The application uses three main entities:

1. **Projects**: Portfolio projects with title, description, technologies, and URLs
2. **Blog Posts**: Blog entries with content, category, and publishing details
3. **Contact Messages**: User contact form submissions

All schemas are defined using Drizzle ORM with Zod validation schemas for type safety.

## Data Flow

1. **Client Requests**: React components use TanStack Query hooks to fetch data
2. **API Layer**: Express routes handle CRUD operations
3. **Storage Layer**: Abstract storage interface allows for different implementations
4. **Database**: PostgreSQL with Drizzle ORM for type-safe database operations
5. **Response**: JSON responses with proper error handling and logging

### API Endpoints

- `GET /api/projects` - Fetch all projects
- `GET /api/projects/:id` - Fetch single project
- `GET /api/blog-posts` - Fetch all blog posts
- `GET /api/blog-posts/:id` - Fetch single blog post
- `POST /api/contact` - Submit contact form

## External Dependencies

### Core Dependencies

- **Frontend**: React, TypeScript, Vite, TanStack Query, Wouter
- **UI Components**: Radix UI primitives, shadcn/ui, Tailwind CSS
- **Backend**: Express.js, TypeScript
- **Database**: PostgreSQL, Drizzle ORM, Neon Database serverless driver
- **Validation**: Zod for schema validation

### Development Tools

- **Build Tools**: Vite for frontend, esbuild for backend bundling
- **TypeScript**: Strict configuration with path mapping
- **Styling**: PostCSS with Tailwind CSS and Autoprefixer
- **Database**: Drizzle Kit for migrations and schema management

## Deployment Strategy

### Build Process

1. **Frontend Build**: Vite builds React app to `dist/public`
2. **Backend Build**: esbuild bundles server code to `dist/index.js`
3. **Database**: Drizzle migrations applied via `db:push` command

### Environment Configuration

- **Development**: Uses Vite dev server with HMR and Express API
- **Production**: Serves static files from Express with bundled backend
- **Database**: Requires `DATABASE_URL` environment variable for PostgreSQL connection

### Scripts

- `dev`: Start development server with hot reloading
- `build`: Build both frontend and backend for production
- `start`: Run production server
- `db:push`: Apply database schema changes

The application is designed to be deployed on platforms that support Node.js with PostgreSQL, with Neon Database being the preferred provider for serverless PostgreSQL hosting.