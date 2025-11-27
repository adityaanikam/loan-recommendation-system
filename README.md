# FinTrust - AI-Powered Loan Recommendation System

A modern, intelligent loan recommendation platform powered by machine learning. FinTrust provides instant loan eligibility assessments, personalized recommendations, and optimal interest rates through an intuitive web interface.

![Next.js](https://img.shields.io/badge/Next.js-15.5.2-black)
![React](https://img.shields.io/badge/React-19.1.0-blue)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-4.0-38bdf8)

## 🚀 Features

### Core Functionality
- **ML-Powered Loan Prediction**: Instant eligibility assessment using machine learning models
- **Multi-Step Application Form**: Streamlined 3-step application process with real-time validation
- **CIBIL Integration**: Automatic credit score verification and validation
- **Personalized Recommendations**: AI-driven loan product recommendations based on applicant profile
- **Real-Time Analytics Dashboard**: System health monitoring, model information, and CIBIL statistics

### User Experience
- **Modern UI/UX**: Beautiful, responsive design with smooth animations
- **Dark Mode Support**: System-aware theme switching
- **Form Validation**: Comprehensive client-side validation with helpful error messages
- **Loading States**: Clear feedback during API requests
- **Error Handling**: Graceful error handling with user-friendly messages

### Technical Features
- **Type-Safe**: Full TypeScript implementation
- **Component Library**: Reusable UI components built with Radix UI
- **API Integration**: Centralized API configuration and request handling
- **Performance Optimized**: Next.js App Router with optimized builds

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- **Node.js** 18.x or higher
- **npm** or **yarn** or **pnpm**
- **Git** (for version control)

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd loan-recommendation-system
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   # or
   pnpm install
   ```

3. **Set up environment variables**
   
   Create a `.env.local` file in the root directory:
   ```env
   NEXT_PUBLIC_API_URL=https://cogni-ml.onrender.com
   API_URL=https://cogni-ml.onrender.com
   NODE_ENV=development
   ```

   > **Note**: See `env.example` for a template of required environment variables.

4. **Run the development server**
   ```bash
   npm run dev
   # or
   yarn dev
   # or
   pnpm dev
   ```

5. **Open your browser**
   
   Navigate to [http://localhost:3000](http://localhost:3000) to see the application.

## 📁 Project Structure

```
loan-recommendation-system/
├── src/
│   ├── app/                    # Next.js App Router pages
│   │   ├── page.tsx            # Home page
│   │   ├── layout.tsx          # Root layout with theme provider
│   │   ├── apply/
│   │   │   └── page.tsx        # Loan application page
│   │   └── dashboard/
│   │       └── page.tsx        # System dashboard page
│   ├── components/             # React components
│   │   ├── ui/                 # Reusable UI components
│   │   │   ├── button.tsx
│   │   │   ├── card.tsx
│   │   │   ├── input.tsx
│   │   │   ├── label.tsx
│   │   │   └── select.tsx
│   │   ├── theme-provider.tsx  # Theme context provider
│   │   └── theme-toggle.tsx    # Dark mode toggle
│   └── lib/                    # Utility functions
│       ├── api.ts              # API request handlers
│       ├── config.ts           # API configuration
│       └── utils.ts            # Helper functions
├── public/                     # Static assets
│   └── logo.PNG               # FinTrust logo
├── package.json               # Dependencies and scripts
├── tsconfig.json              # TypeScript configuration
├── tailwind.config.ts         # Tailwind CSS configuration
├── next.config.ts             # Next.js configuration
├── vercel.json                # Vercel deployment configuration
└── README.md                  # This file
```

## 🎯 Application Workflow

### 1. Home Page (`/`)
- **Hero Section**: Introduction to FinTrust with call-to-action buttons
- **Features Section**: Highlights key benefits (Lightning Fast, Smart Rates, Strategic Plans)
- **Testimonials**: Rotating customer testimonials
- **Navigation**: Access to Apply and Dashboard pages

### 2. Loan Application (`/apply`)
- **Step 1 - Personal Information**:
  - Age (18-70 years)
  - Gender
  - Marital Status
  - Education Level
  
- **Step 2 - Financial Details**:
  - Employment Status (Salaried, Self-Employed, Unemployed, Student, Retired)
  - Work Experience (0-40 years)
  - Annual Salary (minimum ₹15,000 for certain employment types)
  - CIBIL ID (9-digit validation, must exist in database)
  
- **Step 3 - Verification & Submit**:
  - Review all entered information
  - Submit application to ML backend
  
- **Results Display**:
  - Eligibility Status (Eligible/Not Eligible)
  - Eligibility Probability Score
  - Recommended Product Type
  - Optimal Loan Amount
  - Tenure (in months)
  - Interest Rate
  - Monthly EMI
  - Personalized Recommendations

### 3. System Dashboard (`/dashboard`)
- **System Health**:
  - Overall system status
  - ML models loaded status
  - Database connection status
  - Total CIBIL records count
  
- **AI Models Information**:
  - List of loaded ML models
  - Label encoders status
  
- **CIBIL Analytics**:
  - Total records count
  - Average credit score
  - Minimum/Maximum scores
  - Score distribution breakdown

## 🔌 API Integration

The application integrates with a backend ML API hosted at `https://cogni-ml.onrender.com`.

### API Endpoints Used

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/predict` | POST | Submit loan application and get ML prediction |
| `/validate-cibil/{cibil_id}` | GET | Validate CIBIL ID existence |
| `/health` | GET | Check system health status |
| `/cibil-stats` | GET | Get CIBIL statistics |
| `/model-info` | GET | Get loaded ML models information |

### API Configuration

API configuration is centralized in `src/lib/config.ts`:
- Base URL: Configurable via `NEXT_PUBLIC_API_URL` environment variable
- Default: `https://cogni-ml.onrender.com`
- Request headers: JSON content type, automatic authorization token handling

### Request/Response Format

**Loan Application Request**:
```typescript
{
  age: number,
  gender: string,
  marital_status: string,
  property_type: string,
  education: string,
  employment: string,
  experience: number,
  salary: number,
  cibil_id: string
}
```

**Loan Prediction Response**:
```typescript
{
  eligibility_status: string,
  recommended_product_type: string,
  optimal_loan_amount: number,
  tenure_months: number,
  interest_rate: number,
  eligibility_probability: number,
  monthly_emi: number,
  recommendations: string[]
}
```

## 🎨 Styling & Theming

- **Tailwind CSS 4**: Utility-first CSS framework
- **Custom Theme**: Extended color palette with blue/sky gradients
- **Dark Mode**: System-aware theme switching via `next-themes`
- **Animations**: Framer Motion for smooth page transitions and interactions
- **Fonts**: Poppins font family (Google Fonts)

## 🧪 Validation Rules

### Form Validation
- **Age**: Must be between 18 and 70 years
- **Work Experience**: 0-40 years maximum
- **Salary**: Minimum ₹15,000 for Salaried, Self-Employed, and Retired
- **CIBIL ID**: 
  - Exactly 9 digits
  - Must exist in backend database
  - Validated before submission
- **Retired Employees**: Must have work experience > 0

## 📦 Dependencies

### Core Dependencies
- `next`: 15.5.2 - React framework
- `react`: 19.1.0 - UI library
- `react-dom`: 19.1.0 - React DOM renderer
- `typescript`: 5.x - Type safety

### UI & Styling
- `tailwindcss`: 4.x - CSS framework
- `framer-motion`: 12.23.12 - Animation library
- `@radix-ui/*`: UI component primitives
- `lucide-react`: Icon library
- `@fortawesome/react-fontawesome`: FontAwesome icons

### Utilities
- `clsx`: Class name utility
- `tailwind-merge`: Tailwind class merging
- `next-themes`: Theme management
- `class-variance-authority`: Component variants

## 🚀 Deployment

### Vercel Deployment (Recommended)

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Ready for deployment"
   git push origin main
   ```

2. **Connect to Vercel**
   - Go to [Vercel Dashboard](https://vercel.com/dashboard)
   - Click "New Project"
   - Import your GitHub repository
   - Vercel will auto-detect Next.js settings

3. **Configure Environment Variables**
   - In Vercel project settings, add:
     - `NEXT_PUBLIC_API_URL` = `https://cogni-ml.onrender.com`
     - `API_URL` = `https://cogni-ml.onrender.com`
     - `NODE_ENV` = `production`

4. **Deploy**
   - Click "Deploy"
   - Your app will be live at `https://your-project.vercel.app`

### Build Commands

```bash
# Development
npm run dev          # Start development server

# Production
npm run build        # Build for production
npm run start        # Start production server

# Code Quality
npm run lint         # Run ESLint
```

For detailed deployment instructions, see [DEPLOYMENT.md](./DEPLOYMENT.md).

## 🔧 Configuration

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `NEXT_PUBLIC_API_URL` | Backend API base URL | `https://cogni-ml.onrender.com` |
| `API_URL` | Alternative API URL | `https://cogni-ml.onrender.com` |
| `NODE_ENV` | Environment mode | `development` |

### TypeScript Configuration

- Strict mode enabled
- Path aliases: `@/*` → `./src/*`
- ES2017 target
- Next.js plugin integration

### Next.js Configuration

- Default configuration
- Optimized for production builds
- Automatic code splitting

## 🐛 Troubleshooting

### Common Issues

**1. API Connection Errors**
- Verify backend API is accessible: `https://cogni-ml.onrender.com`
- Check environment variables are set correctly
- Ensure CORS is configured on backend

**2. CIBIL ID Validation Fails**
- Ensure CIBIL ID is exactly 9 digits
- Verify CIBIL ID exists in backend database
- Check network connectivity

**3. Build Errors**
- Run `npm run lint` to check for TypeScript/ESLint errors
- Ensure all dependencies are installed: `npm install`
- Clear `.next` folder and rebuild: `rm -rf .next && npm run build`

**4. Styling Issues**
- Clear browser cache
- Verify Tailwind CSS is properly configured
- Check that `globals.css` is imported in `layout.tsx`

## 📝 Development Guidelines

### Code Style
- Use TypeScript for all new files
- Follow Next.js App Router conventions
- Use functional components with hooks
- Implement proper error boundaries

### Component Structure
- Keep components in `src/components/`
- Use UI components from `src/components/ui/`
- Implement proper prop types/interfaces
- Add loading and error states

### API Integration
- Use centralized API functions from `src/lib/api.ts`
- Handle errors gracefully
- Show loading states during requests
- Validate data before API calls

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the terms specified in the [LICENSE](./LICENSE) file.

## 🔗 Links

- **Backend API**: [https://cogni-ml.onrender.com](https://cogni-ml.onrender.com)
- **Next.js Documentation**: [https://nextjs.org/docs](https://nextjs.org/docs)
- **Tailwind CSS**: [https://tailwindcss.com](https://tailwindcss.com)
- **Framer Motion**: [https://www.framer.com/motion](https://www.framer.com/motion)

## 📞 Support

For issues, questions, or contributions:
- Check existing issues in the repository
- Review [DEPLOYMENT.md](./DEPLOYMENT.md) for deployment help
- Ensure all prerequisites are met
- Verify environment variables are configured

---

**Built with ❤️ using Next.js, React, and TypeScript**
