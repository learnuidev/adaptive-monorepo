# Adaptive Analytics Platform

Adaptive is a next-generation analytics platform consisting of three integrated components: a React frontend, serverless AWS backend, and TypeScript SDK. Built for modern applications requiring comprehensive analytics and user behavior tracking.

## 🏗️ Architecture

This monorepo contains three main repositories:

- **[adaptive](./adaptive/)** - React frontend application for analytics visualization
- **[adaptive-backend](./adaptive-backend/)** - Serverless AWS backend for data processing and storage  
- **[adaptive-engine](./adaptive-engine/)** - TypeScript SDK for analytics integration

## ✨ Key Features

- **Real-time Analytics**: Track user events and behaviors in real-time
- **Feature Flags**: Dynamic feature flag management with A/B testing support
- **Cohort Analysis**: Advanced user cohort segmentation and analysis
- **Event Tracking**: Comprehensive event collection and validation
- **Serverless Architecture**: Scalable AWS-based backend infrastructure
- **TypeScript First**: Full type safety across all components
- **Open Source**: MIT licensed and community driven

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ 
- AWS CLI (for backend deployment)
- TypeScript knowledge

### Installation

```bash
# Clone the repository
git clone <YOUR_GIT_URL>
cd adaptive

# Install dependencies for all repositories
npm run install:all

# Or install individually:
cd adaptive && npm i
cd ../adaptive-backend && npm i  
cd ../adaptive-engine && npm i
```

### Development

```bash
# Start frontend development server
cd adaptive && npm run dev

# Start SDK development mode
cd adaptive-engine && npm run dev

# Backend runs on AWS Lambda - deploy with:
cd adaptive-backend && npm run deploy:dev
```

## 📁 Repository Structure

```
adaptive/
├── adaptive/                 # React frontend
│   ├── src/
│   │   ├── components/       # React components
│   │   ├── pages/           # Page components
│   │   ├── modules/         # Business logic modules
│   │   └── utils/           # Utility functions
│   └── package.json
├── adaptive-backend/         # AWS serverless backend
│   ├── src/
│   │   ├── functions/       # Lambda functions
│   │   ├── adaptive-research/ # Analytics logic
│   │   ├── lib/             # Third-party libraries
│   │   └── utils/           # Utility functions
│   ├── serverless.yml       # AWS infrastructure
│   └── package.json
├── adaptive-engine/          # TypeScript SDK
│   ├── src/
│   │   ├── adaptive/        # Core SDK functionality
│   │   ├── adaptive-storage/ # Data storage layer
│   │   └── utils/           # Utility functions
│   └── package.json
├── AGENTS.md                # Development guidelines
└── README.md               # This file
```

## 🛠️ Technology Stack

| Component | Technologies |
|-----------|-------------|
| **Frontend** | React, TypeScript, Vite, Tailwind CSS, Chadcn UI |
| **Backend** | AWS Lambda, DynamoDB, ClickHouse, API Gateway, Cognito |
| **SDK** | TypeScript, React, Zod, Biome |

## 📖 Documentation

- **[Development Guidelines](./AGENTS.md)** - Coding standards and conventions
- **[Frontend Guidelines](./adaptive/AGENTS.md)** - Frontend-specific development rules
- **[Backend Guidelines](./adaptive-backend/AGENTS.md)** - Backend-specific development rules  
- **[SDK Guidelines](./adaptive-engine/AGENTS.md)** - SDK-specific development rules

## 🔧 Development Commands

### Frontend (adaptive)
```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run typecheck    # Type checking
```

### Backend (adaptive-backend)
```bash
npm run build        # Build TypeScript
npm run deploy:dev   # Deploy to development environment
npm run deploy:prod  # Deploy to production environment
```

### SDK (adaptive-engine)
```bash
npm run build        # Build the SDK
npm run dev          # Watch mode for development
npm run lint         # Lint code
npm run format       # Format code
npm run test         # Run tests
```

## 🔌 SDK Usage

Install the SDK in your React application:

```bash
npm install adaptive-engine
```

```typescript
import { AdaptiveProvider } from 'adaptive-engine';

function App() {
  return (
    <AdaptiveProvider apiKey="your-api-key">
      <YourApp />
    </AdaptiveProvider>
  );
}
```

## 🏃‍♂️ Data Flow

1. **Event Collection**: Frontend apps use the SDK to track user events
2. **Validation**: SDK validates events using Zod schemas
3. **Transmission**: Events are sent to AWS Lambda functions
4. **Processing**: Backend processes and stores data in DynamoDB/ClickHouse
5. **Analysis**: Analytics queries process data for insights
6. **Visualization**: Frontend displays analytics through dashboards

## 🔐 Security

- AWS Cognito for user authentication
- KMS encryption for sensitive data
- Zod schema validation for all inputs
- CORS enabled API endpoints
- Proper IAM roles per Lambda function

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Follow the [development guidelines](./AGENTS.md)
4. Submit a pull request

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🔗 Links

- **Live Demo**: https://adaptive.fyi
- **Documentation**: See individual repository READMEs
- **Issues**: Report issues in the respective repository

---

Built with ❤️ for the analytics community
