# Smart Money - Personal Finance Tracker

A comprehensive personal finance tracking application built with Next.js and designed to be hosted on AWS Free Tier.

## Features

- **Income & Expense Tracking**: Easily add and categorize your financial transactions
- **Visual Analytics**: Interactive charts and graphs to visualize spending patterns
- **Budget Management**: Set and track budgets across different categories
- **Savings Goals**: Create and monitor progress toward financial goals
- **AI-Powered Suggestions**: Get personalized recommendations to improve your financial health
- **Responsive Design**: Works seamlessly on desktop and mobile devices
- **Dark Mode Support**: Toggle between light and dark themes

## AWS Architecture

This application is designed to leverage five core AWS services within the Free Tier:

### 1. **Amazon S3** - Static Website Hosting
- Hosts the Next.js static build
- Stores user-exported financial reports
- Configured with CloudFront for global CDN

### 2. **AWS Lambda** - Serverless Functions
- `processTransaction`: Handles transaction CRUD operations
- `generateSuggestions`: AI-powered financial recommendations
- `calculateBudgetProgress`: Real-time budget tracking
- `exportData`: Generate and export financial reports

### 3. **Amazon DynamoDB** - NoSQL Database
- `transactions`: Store all income/expense records
- `budgets`: User budget configurations
- `users`: User profiles and preferences
- `suggestions`: AI-generated recommendations

### 4. **Amazon API Gateway** - REST API
- Secure API endpoints for frontend-backend communication
- Authentication and authorization
- Request/response transformation

### 5. **Amazon CloudWatch** - Monitoring & Alerts
- Application performance monitoring
- Budget overage alerts
- Custom metrics for user engagement
- Log aggregation and analysis

## Technology Stack

- **Frontend**: Next.js 14, React, TypeScript
- **UI Components**: shadcn/ui, Tailwind CSS
- **Charts**: Recharts
- **State Management**: React Hooks
- **Authentication**: AWS Cognito (planned)
- **Deployment**: AWS S3 + CloudFront

## Getting Started

### Prerequisites
- Node.js 18+ 
- AWS Account (Free Tier)
- AWS CLI configured

### Installation

1. Clone the repository:
\`\`\`bash
git clone https://github.com/your-username/smart-money.git
cd smart-money
\`\`\`

2. Install dependencies:
\`\`\`bash
npm install
\`\`\`

3. Set up environment variables:
\`\`\`bash
cp .env.example .env.local
\`\`\`

4. Run the development server:
\`\`\`bash
npm run dev
\`\`\`

5. Open [http://localhost:3000](http://localhost:3000) in your browser.

### AWS Deployment

1. Build the application:
\`\`\`bash
npm run build
npm run export
\`\`\`

2. Deploy to S3:
\`\`\`bash
aws s3 sync out/ s3://your-bucket-name --delete
\`\`\`

3. Set up CloudFront distribution for the S3 bucket

4. Deploy Lambda functions:
\`\`\`bash
# Deploy each Lambda function
aws lambda create-function --function-name processTransaction --runtime nodejs18.x --handler index.handler --zip-file fileb://lambda-functions/processTransaction.zip
\`\`\`

5. Configure API Gateway endpoints

6. Set up DynamoDB tables:
\`\`\`bash
aws dynamodb create-table --table-name smart-money-transactions --attribute-definitions AttributeName=userId,AttributeType=S AttributeName=createdAt,AttributeType=S --key-schema AttributeName=userId,KeyType=HASH AttributeName=createdAt,KeyType=RANGE --billing-mode PAY_PER_REQUEST
\`\`\`

## Features Overview

### Dashboard
- Financial overview with key metrics
- Interactive spending charts
- Recent transactions list
- Budget progress indicators
- Savings goals tracking

### Transaction Management
- Add income and expense transactions
- Categorize transactions
- Search and filter capabilities
- Bulk import from CSV

### Analytics
- Monthly spending trends
- Category-wise expense breakdown
- Income vs expense comparisons
- Savings rate analysis

### Budget Management
- Create category-based budgets
- Real-time progress tracking
- Overage alerts and notifications
- Budget vs actual spending analysis

### AI Suggestions
- Personalized saving recommendations
- Spending pattern analysis
- Budget optimization tips
- Investment suggestions

## AWS Free Tier Limits

The application is designed to stay within AWS Free Tier limits:

- **S3**: 5GB storage, 20,000 GET requests, 2,000 PUT requests
- **Lambda**: 1M requests, 400,000 GB-seconds compute time
- **DynamoDB**: 25GB storage, 25 read/write capacity units
- **API Gateway**: 1M API calls
- **CloudWatch**: 10 custom metrics, 10 alarms

## Security Features

- Input validation and sanitization
- Secure API endpoints with authentication
- Data encryption at rest and in transit
- Regular security audits and updates

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

For support and questions, please open an issue on GitHub or contact [support@smartmoney.com](mailto:support@smartmoney.com).
