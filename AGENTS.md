# AGENTS.md

## 1. Project Overview

This is a multi-repository adaptive analytics platform consisting of three main components:

### 1.1 Repository Structure

- **adaptive** (`/adaptive`) - React frontend application
- **adaptive-backend** (`/adaptive-backend`) - Serverless AWS analytics backend  
- **adaptive-engine** (`/adaptive-engine`) - TypeScript analytics SDK

Each repository has its own AGENTS.md file with specific guidelines for that component. This document provides an overview of the entire platform and cross-repository conventions.

---

## 2. Platform Architecture

### 2.1 Frontend (adaptive)
- Modern React app with TypeScript
- Chadcn UI for styling and components
- Vite and Tailwind CSS for development
- Uses adaptive-engine SDK for analytics integration

### 2.2 Backend (adaptive-backend) 
- Serverless AWS architecture
- DynamoDB for application data storage
- ClickHouse DB for analytics data and queries
- AWS Lambda functions with API Gateway
- AWS Cognito for authentication

### 2.3 SDK (adaptive-engine)
- TypeScript-based analytics SDK
- React context providers for easy integration
- Feature flag management and cohort analysis
- Data collection and event tracking utilities

---

## 3. Cross-Repository Development Guidelines

### 3.1 Shared Conventions
- All repositories use TypeScript for type safety
- Zod for schema validation across all components
- kebab-case naming conventions for files and directories
- Immutable data patterns - never mutate directly
- DRY principles - minimize code duplication

### 3.2 Integration Patterns
- Frontend consumes backend APIs through the SDK
- SDK handles data collection and sends to backend
- Backend processes and stores analytics data
- All components use consistent event schemas

### 3.3 Development Workflow
- Each repository can be developed independently
- Use semantic versioning for SDK releases
- Backend API changes should maintain backward compatibility
- Frontend should use latest SDK version for new features

---

## 4. Technology Stack Summary

| Component | Language | Framework | Database | Key Libraries |
|-----------|----------|-----------|----------|---------------|
| Frontend | TypeScript | React | - | Chadcn UI, Zod, Zustand |
| Backend | TypeScript | AWS Lambda | DynamoDB, ClickHouse | Middy, Zod, AWS SDK |
| SDK | TypeScript | React | - | Zod, Biome, tsup |

---

## 5. Common Naming Conventions

### 5.1 File Names (All Repositories)
- **Components:** kebab-case (`users-list.tsx`)
- **Utilities:** kebab-case (`format-date.ts`) 
- **API Files:** kebab-case (`.api.ts` suffix for backend)
- **Types:** kebab-case with `.types.ts` suffix
- **Schemas:** kebab-case with `-schema.ts` suffix

### 5.2 Code Naming
- **Functions:** camelCase (`getUserData`)
- **Components:** PascalCase (`UsersList`)
- **Types/Interfaces:** PascalCase (`UserType`, `IUserData`)
- **Constants:** kebab-case (`api-config`)

---

## 6. Security & Data Flow

### 6.1 Authentication Flow
1. Frontend uses AWS Cognito for user authentication
2. Backend validates JWT tokens in API Gateway
3. SDK handles authentication state in React context

### 6.2 Data Collection Flow
1. Frontend integrates SDK for event tracking
2. SDK validates events with Zod schemas
3. SDK sends events to backend Lambda functions
4. Backend processes and stores in DynamoDB/ClickHouse

### 6.3 Security Standards
- All user input validated with Zod schemas
- AWS Cognito for authentication and authorization
- KMS encryption for sensitive data in backend
- CORS enabled for all API endpoints
- Proper error handling with appropriate HTTP status codes

---

## 7. Development Commands by Repository

### 7.1 Frontend (adaptive)
- Development: `npm run dev`
- Build: `npm run build`
- Type Check: `npm run typecheck`

### 7.2 Backend (adaptive-backend)
- Build: `npm run build`
- Deploy to EU: `npm run deploy:eu`
- Deploy to US: `npm run deploy:us`

### 7.3 SDK (adaptive-engine)
- Build: `npm run build`
- Development: `npm run dev`
- Lint: `npm run lint`
- Format: `npm run format`
- Type Check: `npm run typecheck`
- Test: `npm test`

---

## 8. Repository-Specific Guidelines

For detailed guidelines specific to each repository, please refer to:
- `/adaptive/AGENTS.md` - Frontend-specific conventions
- `/adaptive-backend/AGENTS.md` - Backend-specific conventions  
- `/adaptive-engine/AGENTS.md` - SDK-specific conventions

---

## Documentation Standards

- Each repository maintains its own AGENTS.md
- Include README.md in major directories
- Document complex business logic with inline comments
- Keep component props and API parameters well-documented
- Update relevant AGENTS.md when adding new patterns or changing conventions
- Cross-repository changes should update documentation in affected repositories
