# LabResults

Transform your health data into actionable insights with a beautiful, accessible dashboard.  
Redesigning the experience of receiving, interpreting, and taking action on lab test results through an intuitive mobile-first interface that makes health monitoring effortless.

[![npm version](https://img.shields.io/npm/v/lab-results?style=flat-square)](https://www.npmjs.com/package/lab-results)
[![Build Status](https://img.shields.io/github/actions/workflow/status/abgneudev/Lab_Results/ci.yml?branch=main&style=flat-square)](https://github.com/abgneudev/Lab_Results/actions)
[![License](https://img.shields.io/github/license/abgneudev/Lab_Results?style=flat-square)](LICENSE)
[![Latest Release](https://img.shields.io/github/v/release/abgneudev/Lab_Results?style=flat-square)](https://github.com/abgneudev/Lab_Results/releases)

## Demo & Screenshots

🚀 **[Live Demo](https://lab-results-dusky.vercel.app/results)**

## Table of Contents

- [Features](#features)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Design Philosophy & UX Considerations](#design-philosophy--ux-considerations)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Authors & Acknowledgments](#authors--acknowledgments)
- [Contact & Community](#contact--community)

## Features

- 🏥 **Smart Health Metrics Tracking** - Monitor blood work, vitamins, heart health, and organ function
- 📊 **Visual Trend Analysis** - Interactive charts showing health improvements over time
- 🎯 **Personalized Status Indicators** - Color-coded alerts (Balanced, Manage, Review, Book) for easy understanding
- 📱 **Mobile-First Design** - Optimized for on-the-go health monitoring
- ♿ **WCAG 2.1 AA Compliant** - Accessible to users with disabilities
- 🎨 **Modern UI Components** - Built with Radix UI and Tailwind CSS
- 🔄 **Real-time Data Sync** - Local storage with seamless state management
- 📋 **Test Results Management** - Upload, view, and organize lab reports
- 💊 **Medication Tracking** - Integration with vitals and health preferences
- 🚀 **Performance Optimized** - Fast loading with Next.js 15 and React 19

## Getting Started

### Prerequisites

- **Node.js** 18.0 or higher
- **pnpm** 8.0+ (recommended) or npm/yarn
- **Modern browser** with ES2020 support
- **TypeScript** knowledge (helpful for customization)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/abgneudev/Lab_Results.git
   cd Lab_Results
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   # or
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env.local
   # Edit .env.local with your configuration
   ```

4. **Run the development server**
   ```bash
   pnpm dev
   # or
   npm run dev
   ```

5. **Open your browser**
   Navigate to [http://localhost:3000](http://localhost:3000) to see the application.

## Usage

### Basic Health Metrics Tracking

```typescript
import { usePatient } from '@/context/patient-context';

export function HealthDashboard() {
  const { patientData, addMetric } = usePatient();
  
  // Add a new health metric
  const newMetric = {
    id: 'cholesterol',
    name: 'Total Cholesterol',
    value: 180,
    unit: 'mg/dL',
    status: 'balanced',
    category: 'blood',
    lastUpdated: new Date().toISOString()
  };
  
  addMetric(newMetric);
  
  return (
    <div>
      {patientData.metrics.map(metric => (
        <HealthCard key={metric.id} metric={metric} />
      ))}
    </div>
  );
}
```

### API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/metrics` | GET | Fetch all health metrics |
| `/api/metrics` | POST | Add new metric |
| `/api/reports` | GET | List lab reports |
| `/api/upload` | POST | Upload lab results |

### CLI Commands

```bash
# Development
pnpm dev          # Start development server
pnpm build        # Build for production
pnpm start        # Start production server
pnpm lint         # Run ESLint

# Testing
pnpm test         # Run test suite
pnpm test:watch   # Run tests in watch mode
```

## Project Structure

```
LabResults-main/
├── app/                    # Next.js 13+ app directory
│   ├── results/           # Lab results pages
│   ├── vitals/            # Health vitals dashboard
│   ├── upload/            # File upload interface
│   └── reports/           # Historical reports
├── components/            # Reusable UI components
│   ├── ui/               # Shadcn/ui components
│   ├── health-card.tsx   # Main metric display card
│   └── vitals-dashboard.tsx # Dashboard layout
├── context/              # React context providers
│   └── patient-context.tsx # Global patient state
├── hooks/                # Custom React hooks
├── lib/                  # Utilities and configurations
└── public/               # Static assets
```

**Key Directories:**
- **`app/`** - Next.js app router pages and layouts
- **`components/`** - Modular UI components with TypeScript
- **`context/`** - Global state management for patient data
- **`hooks/`** - Reusable logic for data fetching and UI state

## Design Philosophy & UX Considerations

### Mobile-First Approach
- **Responsive Design** - Optimized for screens 320px and up
- **Touch-Friendly** - 44px minimum touch targets following iOS guidelines
- **Progressive Enhancement** - Works on basic devices, enhanced on modern ones

### Accessibility Standards
- **WCAG 2.1 AA Compliance** - Screen reader compatible with semantic HTML
- **Color Contrast** - 4.5:1 ratio for all text elements
- **Keyboard Navigation** - Full app functionality without mouse
- **Plain Language** - Grade 9 readability level for health information

### Visual Design System
- **Primary Color**: `#03659C` (Medical blue for trust and professionalism)
- **Status Colors**: Teal (balanced), Amber (manage), Rose (review), Blue (book)
- **Typography**: Open Sans for readability across devices
- **Animations**: Framer Motion for smooth, accessible transitions

### Health Data Privacy
- **Local Storage** - No sensitive data transmitted to external servers
- **Progressive Disclosure** - Complex medical terms explained on demand
- **Clear Status Indicators** - Visual hierarchy guides user attention to priorities

## Roadmap

- 🔄 **Real-time Sync** - Cloud backup and multi-device synchronization
- 🤖 **AI Health Insights** - Personalized recommendations based on trends
- 📧 **Automated Reminders** - Smart notifications for upcoming tests
- 🏥 **Provider Integration** - Direct import from major lab networks
- 📊 **Advanced Analytics** - Correlation analysis between metrics
- 🌍 **Internationalization** - Multi-language support for global users

**Want to influence our roadmap?** [Share your feedback](https://github.com/abgneudev/Lab_Results/discussions)

## Contributing

We welcome contributions from the community! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Code of Conduct
This project follows the [Contributor Covenant](https://www.contributor-covenant.org/) code of conduct.

### Running Tests
```bash
pnpm test              # Run all tests
pnpm test:coverage     # Generate coverage report
pnpm test:e2e         # Run end-to-end tests
```

### Development Workflow
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Make your changes and add tests
4. Run the test suite: `pnpm test`
5. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

**SPDX-License-Identifier: MIT**

## Authors & Acknowledgments
- **[@abgneudev](https://github.com/abgneudev)** - Project Lead

## Contact & Community

- �🐛 **[Found a bug?](https://github.com/abgneudev/Lab_Results/issues)** - Report issues on GitHub
- 💡 **[Feature Requests](https://github.com/abgneudev/Lab_Results/discussions)** - Suggest improvements

---

**Made with ❤️ for better health outcomes.** Star ⭐ this project if it helps you take control of your health data!
