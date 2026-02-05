# 🤖 AI Mock Interview Platform

An intelligent interview preparation platform powered by AI that helps job seekers practice and improve their interview skills. Built with Next.js, TypeScript, and Google's Gemini AI, this application provides personalized mock interviews with real-time feedback and performance analytics.

![AI Mock Interview](public/logo.png)

## ✨ Features

### 🎯 Core Features

- **AI-Powered Interviews**: Dynamic question generation using Google's Gemini AI based on job role and requirements
- **Real-time Speech Recognition**: Practice speaking answers with voice-to-text conversion
- **Webcam Recording**: Record your responses for self-review and improvement
- **Intelligent Feedback**: Get detailed AI-generated feedback on your answers with scoring
- **Performance Analytics**: Track your interview performance and improvement over time

### 🔐 Authentication & User Management

- **Secure Authentication**: Powered by Clerk for seamless sign-up/sign-in experience
- **User Profiles**: Personalized dashboard with interview history
- **Session Management**: Secure user sessions and data protection

### 🎨 Modern UI/UX

- **Responsive Design**: Optimized for desktop and mobile devices
- **Dark/Light Theme**: Comfortable viewing in any environment
- **Intuitive Interface**: Clean and user-friendly design with Tailwind CSS
- **Interactive Components**: Modern UI components with smooth animations

## 🛠️ Tech Stack

### Frontend

- **Framework**: Next.js 15 (React 19)
- **Styling**: Tailwind CSS
- **UI Components**: Radix UI primitives
- **Icons**: Lucide React
- **TypeScript**: Full type safety

### Backend & Database

- **Database**: PostgreSQL (Neon)
- **ORM**: Drizzle ORM
- **API**: Next.js API Routes
- **Storage**: Secure cloud storage

### AI & Services

- **AI Model**: Google Gemini AI
- **Authentication**: Clerk
- **Speech Recognition**: React Hook Speech-to-Text
- **Video Recording**: React Webcam

### Development Tools

- **Language**: TypeScript
- **Linting**: ESLint
- **Formatting**: Prettier (implied)
- **Build Tool**: Next.js built-in

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ and npm/yarn/pnpm
- PostgreSQL database (Neon DB recommended)
- Google Cloud Account (for Gemini AI)
- Clerk Account (for authentication)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/amadhurg0103/ai-mock-interview.git
   cd ai-mock-interview
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Set up environment variables**

   Create a `.env.local` file in the root directory:

   ```env
   # Database
   DATABASE_URL=postgresql://username:password@host:port/database?sslmode=require

   # Clerk Authentication
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_xxxxxxxxxx
   CLERK_SECRET_KEY=sk_test_xxxxxxxxxx

   # Google Gemini AI
   NEXT_PUBLIC_GEMINI_API_KEY=your_gemini_api_key

   # App Configuration
   NEXT_PUBLIC_APP_URL=http://localhost:3000
   ```

4. **Set up the database**

   ```bash
   npm run db:push
   ```

5. **Start the development server**

   ```bash
   npm run dev
   ```

6. **Open your browser**

   Navigate to [http://localhost:3000](http://localhost:3000)

## 📖 Usage Guide

### Creating Your First Mock Interview

1. **Sign Up/Sign In**: Create an account or sign in using Clerk authentication
2. **Dashboard**: Access your personalized dashboard
3. **Add New Interview**: Click "Add New Interview" to create a mock interview
4. **Fill Details**:
   - Job Position (e.g., Frontend Developer, Data Scientist)
   - Job Description/Requirements
   - Years of Experience
5. **Generate Questions**: AI will create personalized interview questions
6. **Start Interview**: Begin your practice session with webcam and microphone

### During the Interview

1. **Read Questions**: Review AI-generated questions one by one
2. **Record Response**: Use the webcam to record your answer
3. **Voice Input**: Speak your answers using speech-to-text feature
4. **Submit**: Submit each answer for AI evaluation

### After the Interview

1. **View Feedback**: Get detailed AI-generated feedback for each answer
2. **Performance Metrics**: See your overall score and ratings
3. **Improvement Areas**: Identify areas for improvement
4. **Interview History**: Access all previous interviews from your dashboard

## 📁 Project Structure

```
ai-mock-interview/
├── app/                          # Next.js App Router
│   ├── (auth)/                   # Authentication pages
│   │   ├── sign-in/
│   │   └── sign-up/
│   ├── (dashboard)/              # Protected dashboard routes
│   │   └── dashboard/
│   │       ├── _components/      # Dashboard components
│   │       ├── interview/        # Interview-related pages
│   │       └── upgrade/          # Subscription/upgrade pages
│   ├── api/                      # API routes
│   │   └── gemini/              # Gemini AI integration
│   ├── globals.css              # Global styles
│   ├── layout.tsx               # Root layout
│   └── page.tsx                 # Landing page
├── components/                   # Reusable components
│   ├── ui/                      # UI primitives
│   ├── GeminiChat.tsx           # AI chat component
│   └── loader.tsx               # Loading component
├── lib/                         # Utility libraries
├── public/                      # Static assets
├── types/                       # TypeScript type definitions
├── utils/                       # Utility functions
│   ├── db.ts                    # Database connection
│   ├── schema.ts                # Database schema
│   └── GeminiAIModel.tsx        # AI model integration
└── Data/                        # Static data
```

## 🔧 API Endpoints

### Interview Management

- `GET /api/interview` - Fetch user interviews
- `POST /api/interview` - Create new interview
- `GET /api/interview/[id]` - Get specific interview
- `PUT /api/interview/[id]` - Update interview

### AI Integration

- `POST /api/gemini` - Generate interview questions
- `POST /api/gemini/feedback` - Get answer feedback

## 🗄️ Database Schema

### MockInterview Table

```sql
CREATE TABLE mockInterview (
    id SERIAL PRIMARY KEY,
    jsonMockResp TEXT NOT NULL,
    jobPosition VARCHAR NOT NULL,
    jobDescription VARCHAR NOT NULL,
    jobExperience VARCHAR NOT NULL,
    createdBy VARCHAR NOT NULL,
    createdAt VARCHAR,
    mockId VARCHAR NOT NULL
);
```

### UserAns Table

```sql
CREATE TABLE userAns (
    id SERIAL PRIMARY KEY,
    mockIdRef VARCHAR NOT NULL,
    question VARCHAR NOT NULL,
    correctAns VARCHAR NOT NULL,
    userAns TEXT,
    feedback TEXT,
    rating VARCHAR,
    userEmail VARCHAR,
    createdAt VARCHAR
);
```

## 🎯 Available Scripts

```bash
# Development
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server

# Database
npm run db:push      # Push schema changes to database
npm run db:studio    # Open Drizzle Studio (database GUI)

# Code Quality
npm run lint         # Run ESLint
```

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### Getting Started

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Make your changes
4. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
5. Push to the branch (`git push origin feature/AmazingFeature`)
6. Open a Pull Request

### Contribution Guidelines

- Follow the existing code style and conventions
- Write clear commit messages
- Add tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting

### Issues

- Use issue templates when available
- Provide clear reproduction steps for bugs
- Include relevant screenshots or logs
- Tag issues appropriately

## 🔮 Roadmap & Future Features

### Short Term

- [ ] **Video Analysis**: AI-powered body language and facial expression analysis
- [ ] **Interview Templates**: Pre-built templates for different roles and industries
- [ ] **Progress Tracking**: Advanced analytics with performance trends
- [ ] **Mobile App**: Native mobile applications for iOS and Android

### Long Term

- [ ] **Live Mock Interviews**: Real-time interviews with human interviewers
- [ ] **Team Collaboration**: Features for HR teams and recruiters
- [ ] **Integration APIs**: Connect with job boards and ATS systems
- [ ] **Multilingual Support**: Support for multiple languages

## 🐛 Known Issues

- Speech recognition may have accuracy issues in noisy environments
- Webcam recording requires HTTPS in production
- Database connection may timeout on free tier hosting

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Google Gemini AI** for powering the intelligent question generation
- **Clerk** for seamless authentication
- **Neon** for reliable PostgreSQL hosting
- **Vercel** for hosting and deployment
- **Open Source Community** for the amazing libraries and tools

## 📞 Support

- **GitHub Issues**: [Report bugs or request features](https://github.com/Prabhat2912/ai-mock-interview/issues)
- **Email**: pk993105@gmail.com
- **Twitter**: [@real_prabhat1](https://twitter.com/real_prabhat1)

---

<div align="center">
  <p>Made with ❤️ by <a href="https://github.com/Prabhat2912">Prabhat Kumar</a></p>
  <p>⭐ Star this repository if you found it helpful!</p>
</div>
