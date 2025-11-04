# 📋 **PROMPT MY SITE - Complete Project Documentation**

## **1. PROJECT OVERVIEW**

### **1.1 What is CodeMind AI?**

PROMPT MY SITE is an **open-source micro SaaS application** that serves as an AI-powered code generation companion. Inspired by Bolt.new (StackBlitz), it allows users to describe what they want to build in natural language, and the AI generates complete React projects with functional code, ready to preview and edit.

### **1.2 Core Purpose**

- **Democratize Coding**: Makes web development accessible to both beginners and experienced developers
- **Rapid Prototyping**: Convert ideas to working code in seconds
- **Interactive Learning**: Learn React, Tailwind CSS, and modern web development through AI-generated examples
- **Micro SaaS Model**: Token-based system where users pay for what they use

### **1.3 Key Features**

1. **🤖 AI Code Generation**: Converts natural language prompts into full React projects
2. **💬 Intelligent Chat Assistant**: Ask questions, get explanations, debug issues
3. **🖥 Interactive Workspace**: Split-screen with chat on left, live code editor/preview on right
4. **💻 Live Code Preview**: Real-time code editing powered by Sandpack (CodeSandbox)
5. **💰 Token-Based Pricing**: Free tier (50,000 tokens) + paid upgrades
6. **🔒 Google OAuth**: Secure authentication
7. **💳 PayPal Integration**: Seamless payment processing
8. **💾 Persistent Storage**: All projects saved with Convex database
9. **🎨 Modern UI**: Dark theme with Tailwind CSS + Radix UI components

---

## **2. TECHNOLOGY STACK**

### **2.1 Frontend**

| Technology         | Version | Purpose                                                         |
| ------------------ | ------- | --------------------------------------------------------------- |
| **Next.js**        | 15.1.4  | React framework with App Router, SSR, API routes                |
| **React**          | 18.0.0  | UI component library                                            |
| **Tailwind CSS**   | 3.4.1   | Utility-first CSS framework for styling                         |
| **Radix UI**       | Various | Accessible, unstyled UI components (Dialog, Tooltip, Separator) |
| **Lucide React**   | 0.471.0 | Beautiful icon library (Heart, Shield, Clock, etc.)             |
| **Sandpack**       | 2.19.10 | Live code editor and preview (by CodeSandbox)                   |
| **React Markdown** | 9.0.3   | Render AI responses as formatted markdown                       |
| **Sonner**         | 1.7.1   | Toast notifications                                             |
| **Next Themes**    | 0.4.4   | Dark/light theme management                                     |

### **2.2 Backend**

| Technology               | Version | Purpose                                                         |
| ------------------------ | ------- | --------------------------------------------------------------- |
| **Convex**               | 1.17.4  | Backend-as-a-Service: database, serverless functions, real-time |
| **Google Generative AI** | 0.21.0  | Gemini AI for code generation and chat                          |
| **Axios**                | 1.7.9   | HTTP client for API calls                                       |

### **2.3 Authentication & Payments**

| Technology                  | Version | Purpose                              |
| --------------------------- | ------- | ------------------------------------ |
| **@react-oauth/google**     | 0.12.1  | Google OAuth sign-in (implicit flow) |
| **@paypal/react-paypal-js** | 8.7.0   | PayPal payment integration           |

### **2.4 Utilities**

- **class-variance-authority** (0.7.1): Type-safe component variants
- **clsx** (2.1.1): Conditional CSS class management
- **tailwind-merge** (2.6.0): Merge Tailwind classes intelligently
- **dedent** (1.5.3): Clean multi-line strings in prompts
- **uuid4** (2.0.3): Generate unique IDs

---

## **3. PROJECT ARCHITECTURE**

### **3.1 Folder Structure**

```
code-mind-ai-bolt-clone/
├── app/                          # Next.js App Router
│   ├── (main)/                   # Main application routes
│   │   ├── pricing/              # Pricing page
│   │   │   └── page.jsx          # Token purchase page
│   │   └── workspace/[id]/       # Dynamic workspace route
│   │       └── page.jsx          # Code editor + chat interface
│   ├── api/                      # Server-side API routes
│   │   ├── ai-chat/route.jsx     # Chat API endpoint
│   │   └── gen-ai-code/route.jsx # Code generation API endpoint
│   ├── ConvexClientProvider.jsx  # Convex setup for client components
│   ├── globals.css               # Global styles (Tailwind base)
│   ├── layout.js                 # Root layout with providers
│   ├── page.js                   # Homepage with hero
│   └── provider.jsx              # Global state providers wrapper
│
├── components/
│   ├── custom/                   # Application-specific components
│   │   ├── AppSideBar.jsx        # Main sidebar with history
│   │   ├── ChatView.jsx          # Chat interface with AI
│   │   ├── CodeView.jsx          # Sandpack code editor/preview
│   │   ├── Header.jsx            # Navigation header
│   │   ├── Hero.jsx              # Landing page with prompt input
│   │   ├── PricingModel.jsx      # Pricing cards with PayPal buttons
│   │   ├── SandpackPreviewClient.jsx # Live preview component
│   │   ├── SideBarFooter.jsx     # User info in sidebar
│   │   ├── SignInDialog.jsx      # Google OAuth dialog
│   │   └── WorkspaceHistory.jsx  # List of user's past workspaces
│   └── ui/                       # Shadcn UI components (Radix wrappers)
│       ├── button.jsx
│       ├── dialog.jsx
│       ├── input.jsx
│       ├── separator.jsx
│       ├── sheet.jsx
│       ├── sidebar.jsx
│       ├── skeleton.jsx
│       ├── sonner.jsx
│       └── tooltip.jsx
│
├── configs/
│   └── AiModel.jsx               # Gemini AI configuration (model, prompts)
│
├── context/                      # React Context for global state
│   ├── ActionContext.jsx         # Deploy/export actions
│   ├── MessagesContext.jsx       # Chat message history
│   └── UserDetailContext.jsx     # User authentication state
│
├── convex/                       # Convex backend
│   ├── schema.js                 # Database schema (users, workspace)
│   ├── users.js                  # User CRUD operations
│   ├── workspace.js              # Workspace CRUD operations
│   └── _generated/               # Auto-generated Convex files
│
├── data/                         # Static configuration data
│   ├── Colors.jsx                # Color constants for theming
│   ├── Lookup.jsx                # UI text, suggestions, pricing tiers
│   └── Prompt.jsx                # AI prompt templates
│
├── hooks/
│   └── use-mobile.jsx            # Responsive design hook
│
├── lib/
│   └── utils.js                  # Utility functions (cn for classnames)
│
├── public/                       # Static assets (logo, images)
│
├── .env                          # Environment variables (API keys)
├── .env.example                  # Template for environment variables
├── components.json               # Shadcn UI configuration
├── jsconfig.json                 # JavaScript configuration (path aliases)
├── next.config.mjs               # Next.js configuration
├── package.json                  # Dependencies and scripts
├── postcss.config.mjs            # PostCSS configuration
├── tailwind.config.mjs           # Tailwind CSS configuration
└── README.md                     # Project documentation
```

---

## **4. DETAILED COMPONENT BREAKDOWN**

### **4.1 Core User Flow Components**

#### **Hero.jsx** (Landing Page)

**Purpose**: Entry point where users describe what they want to build

**Key Features**:

- Large textarea for natural language input
- Suggestion chips (e.g., "Create a todo app", "Build a calculator")
- Token validation (requires 10+ tokens)
- Authentication check (opens sign-in dialog if not logged in)
- Creates new workspace on submit

**Flow**:

1. User types prompt or clicks suggestion
2. Validates authentication and token balance
3. Creates message object: `{ role: 'user', content: input }`
4. Calls `CreateWorkspace` mutation with user ID and message
5. Redirects to `/workspace/[workspaceId]`

#### **Workspace Page** (`app/(main)/workspace/[id]/page.jsx`)

**Purpose**: Main coding interface with split layout

**Layout**:

- **Left (1/3)**: `ChatView` - conversational AI assistant
- **Right (2/3)**: `CodeView` - code editor and live preview

#### **ChatView.jsx**

**Purpose**: AI chat assistant for questions, debugging, explanations

**Key Features**:

- Message history display (user messages + AI responses)
- Markdown rendering for AI responses
- Token-based API calls
- Auto-updates database with new messages

**Flow**:

1. User types message in textarea
2. Adds message to context: `{ role: 'user', content: input }`
3. Sends to `/api/ai-chat` with full conversation history
4. Gemini AI responds with explanation
5. Adds AI response: `{ role: 'ai', content: aiResponse }`
6. Updates Convex database + deducts tokens

**Token Calculation**: Counts words in AI response to deduct from user balance

#### **CodeView.jsx**

**Purpose**: Code generation, editing, and live preview

**Key Features**:

- Sandpack integration (CodeSandbox editor)
- Two tabs: "Code" (editor) and "Preview" (live app)
- File explorer showing project structure
- Real-time code updates

**Flow**:

1. Watches for new user messages in `MessagesContext`
2. When user message arrives, calls `GenerateAiCode()`
3. Sends conversation history + code generation prompt to `/api/gen-ai-code`
4. Gemini AI returns JSON:
   ```json
   {
     "projectTitle": "React Todo App",
     "explanation": "...",
     "files": {
       "/App.js": { "code": "..." },
       "/components/TodoList.js": { "code": "..." }
     },
     "generatedFiles": ["/App.js", "/components/TodoList.js"]
   }
   ```
5. Merges AI files with default files (index.html, styles.css)
6. Updates Convex database with new files
7. Deducts tokens based on response size

**Default Files** (from `Lookup.jsx`):

- `/index.html`: HTML entry point
- `/styles.css`: Basic CSS reset

**Available Packages** (auto-installed in Sandpack):

- `date-fns`: Date formatting
- `react-chartjs-2`: Charts and graphs
- `firebase`: Firebase SDK
- `@google/generative-ai`: Gemini AI SDK
- `lucide-react`: Icons

#### **WorkspaceHistory.jsx**

**Purpose**: Sidebar component showing user's past projects

**Features**:

- Fetches all workspaces for logged-in user
- Displays first message content as title
- Links to each workspace (`/workspace/[id]`)
- Responsive (collapses on mobile)

---

### **4.2 Authentication & User Management**

#### **SignInDialog.jsx**

**Purpose**: Google OAuth authentication popup

**Features**:

- Radix UI Dialog component
- `GoogleOAuthProvider` with client ID
- `GoogleLogin` button with popup flow
- On success: calls `CreateUser` mutation, stores user in context

**User Object**:

```javascript
{
  name: "John Doe",
  email: "john@example.com",
  picture: "https://lh3.googleusercontent.com/...",
  uid: "google-user-id",
  token: 50000 // Free tier tokens
}
```

#### **Provider.jsx**

**Purpose**: Global state provider wrapper

**Provides**:

- `UserDetailContext`: User authentication state
- `MessagesContext`: Chat message history
- `ActionContext`: Deploy/export actions
- `GoogleOAuthProvider`: Google OAuth setup
- `PayPalScriptProvider`: PayPal setup
- `ThemeProvider`: Dark/light theme (next-themes)

---

### **4.3 Pricing & Payment System**

#### **Pricing Page** (`app/(main)/pricing/page.jsx`)

**Purpose**: Display token balance and upgrade options

**Features**:

- Shows current token balance
- Displays pricing tiers from `Lookup.PRICING_OPTIONS`
- Renders `PricingModel` component

#### **PricingModel.jsx**

**Purpose**: Pricing cards with PayPal payment buttons

**Pricing Tiers** (from `Lookup.jsx`):

1. **Basic**: $5 → 100,000 tokens
2. **Premium**: $15 → 500,000 tokens
3. **Ultimate**: $25 → 1,000,000 tokens

**Payment Flow**:

1. User clicks PayPal button on pricing card
2. PayPal popup opens with order details
3. On successful payment (`onApprove`):
   - Calculates new token balance: `currentTokens + purchasedTokens`
   - Calls `UpdateToken` mutation
   - Updates `UserDetailContext`

---

## **5. BACKEND ARCHITECTURE (CONVEX)**

### **5.1 Database Schema** (`convex/schema.js`)

#### **users** Table

```javascript
{
  name: v.string(),           // User's full name
  email: v.string(),          // Primary identifier
  picture: v.string(),        // Profile picture URL
  uid: v.string(),            // Google user ID
  token: v.optional(v.number()) // Token balance (default: 50000)
}
```

#### **workspace** Table

```javascript
{
  messages: v.any(),          // Array of chat messages (JSON)
  fileData: v.optional(v.any()), // Generated code files (JSON)
  user: v.id('users')         // Foreign key to users table
}
```

---

### **5.2 Convex Mutations & Queries**

#### **users.js**

**CreateUser** (Mutation)

- **Input**: name, email, picture, uid
- **Logic**:
  - Checks if user exists by email
  - If not, inserts new user with 50,000 free tokens
- **Output**: User ID

**GetUser** (Query)

- **Input**: email
- **Output**: User object

**UpdateToken** (Mutation)

- **Input**: token (number), userId
- **Logic**: Updates user's token balance
- **Output**: Update result

#### **workspace.js**

**CreateWorkspace** (Mutation)

- **Input**: messages (array), user (ID)
- **Output**: Workspace ID

**GetWorkspace** (Query)

- **Input**: workspaceId
- **Output**: Workspace object with messages and fileData

**UpdateMessages** (Mutation)

- **Input**: workspaceId, messages (array)
- **Logic**: Updates message history in workspace

**UpdateFiles** (Mutation)

- **Input**: workspaceId, files (object)
- **Logic**: Saves generated code files to workspace

**GetAllWorkspace** (Query)

- **Input**: userId
- **Output**: Array of all workspaces for user

---

## **6. AI INTEGRATION**

### **6.1 Gemini AI Configuration** (`configs/AiModel.jsx`)

**Model**: `gemini-2.0-flash-exp` (experimental, faster responses)

**Generation Config**:

```javascript
{
  temperature: 1,           // Creativity level (0-2)
  topP: 0.95,              // Nucleus sampling threshold
  topK: 40,                // Token selection diversity
  maxOutputTokens: 8192,   // Max response length
  responseMimeType: 'application/json' // For code generation
}
```

**Two Chat Sessions**:

1. **chatSession**: Text responses for chat (MIME: text/plain)
2. **GenAiCode**: JSON responses for code generation (MIME: application/json)

---

### **6.2 Prompt Engineering**

#### **Chat Prompt** (`data/Prompt.jsx`)

```
You are a AI Assistant and experience in React Development.
GUIDELINES:
- Tell user what you are building
- Response less than 15 lines
- Skip code examples and commentary
```

#### **Code Generation Prompt** (`data/Prompt.jsx`)

**Guidelines**:

- Generate React project with Vite
- Use `.js` file extensions
- Use Tailwind CSS for styling
- Use Lucide React icons only when needed
- Available packages: date-fns, react-chartjs-2, firebase, @google/generative-ai
- Use `https://archive.org/download/placeholder-image/placeholder-image.jpg` for placeholders
- Add emoji icons for better UX
- Make designs beautiful and production-ready
- Use Unsplash for stock photos (valid URLs only)

**Required JSON Response**:

```json
{
  "projectTitle": "App Name",
  "explanation": "One paragraph description",
  "files": {
    "/App.js": { "code": "..." },
    "/components/Component.js": { "code": "..." }
  },
  "generatedFiles": ["/App.js", "/components/Component.js"]
}
```

---

### **6.3 API Routes**

#### **`/api/ai-chat` (POST)**

**Purpose**: Chat responses for questions/explanations

**Input**:

```json
{ "prompt": "Full conversation history + CHAT_PROMPT" }
```

**Process**:

1. Calls `chatSession.sendMessage(prompt)`
2. Extracts text response
3. Returns: `{ result: "AI response text" }`

**Error Handling**: Catches Gemini errors, returns error response

#### **`/api/gen-ai-code` (POST)**

**Purpose**: Generate React code from description

**Input**:

```json
{ "prompt": "Full conversation history + CODE_GEN_PROMPT" }
```

**Process**:

1. Calls `GenAiCode.sendMessage(prompt)`
2. Parses JSON response
3. Returns: AI-generated file structure

**Error Handling**: Catches parsing/API errors

---

## **7. TOKEN SYSTEM**

### **7.1 Token Economics**

**Free Tier**: 50,000 tokens on sign-up

**Token Consumption**:

- **Chat Messages**: ~10-100 tokens per AI response (word count)
- **Code Generation**: ~500-2000 tokens per project (JSON size)

**Calculation Method**:

```javascript
const countToken = (inputText) => {
  return inputText
    .trim()
    .split(/\s+/)
    .filter((word) => word).length;
};
```

_Note: This is a simple word count, not true token count_

**Minimum Balance**: 10 tokens required to generate code/chat

---

### **7.2 Token Purchase Flow**

1. User clicks "Upgrade" on pricing page
2. Selects pricing tier (Basic/Premium/Ultimate)
3. PayPal button appears
4. User completes payment
5. `onPaymentSuccess` callback:
   - Calculates: `newBalance = currentTokens + purchasedTokens`
   - Calls `UpdateToken` mutation
   - Updates UI with new balance

---

## **8. ENVIRONMENT VARIABLES**

### **8.1 Required Variables** (`.env`)

```ini
# Google OAuth (https://console.cloud.google.com)
NEXT_PUBLIC_GOOGLE_AUTH_CLIENT_ID=your_client_id.apps.googleusercontent.com

# Convex Backend (https://dashboard.convex.dev)
CONVEX_DEPLOYMENT=dev:your-deployment-name
NEXT_PUBLIC_CONVEX_URL=https://your-deployment.convex.cloud

# Google Gemini AI (https://aistudio.google.com/app/apikey)
NEXT_PUBLIC_GEMINI_API_KEY=AIzaSy...

# PayPal (https://developer.paypal.com)
NEXT_PUBLIC_PAYPAL_CLIENT_ID=your_paypal_client_id
```

### **8.2 Setup Instructions**

**Google OAuth**:

1. Go to Google Cloud Console → APIs & Services → Credentials
2. Create OAuth 2.0 Client ID (Web application)
3. Add authorized origin: `http://localhost:3000`
4. No redirect URI needed (implicit flow)

**Convex**:

1. Sign up at convex.dev
2. Create new project
3. Run `npx convex dev` to get deployment URL
4. Copy `CONVEX_DEPLOYMENT` and `NEXT_PUBLIC_CONVEX_URL`

**Gemini AI**:

1. Visit https://aistudio.google.com/app/apikey
2. Create new API key
3. Copy key (starts with `AIzaSy`)

**PayPal**:

1. Sign up at developer.paypal.com
2. Create Sandbox account
3. Go to Apps & Credentials → Create App
4. Copy Client ID

---

## **9. KEY FEATURES DEEP DIVE**

### **9.1 Live Code Preview (Sandpack)**

**Technology**: `@codesandbox/sandpack-react` (CodeSandbox's open-source editor)

**Setup**:

```jsx
<SandpackProvider
  files={files} // Generated code files
  template="react" // React template
  theme="dark" // Dark theme
  customSetup={{
    dependencies: {
      "date-fns": "latest",
      "react-chartjs-2": "latest",
      firebase: "latest",
      "@google/generative-ai": "latest",
      "lucide-react": "latest",
    },
  }}
  options={{
    externalResources: ["https://cdn.tailwindcss.com"], // Tailwind CDN
  }}
>
  <SandpackLayout>
    <SandpackFileExplorer /> {/* File tree */}
    <SandpackCodeEditor /> {/* Monaco editor */}
    <SandpackPreview /> {/* Live preview */}
  </SandpackLayout>
</SandpackProvider>
```

**Features**:

- Real-time code compilation
- Browser-based bundling (no server needed)
- Hot module reloading
- Error highlighting
- Console output

---

### **9.2 Message Context System**

**Message Format**:

```javascript
{
  role: 'user' | 'ai',
  content: 'Message text'
}
```

**Flow**:

1. User sends message → adds to context as `{ role: 'user', content }`
2. Component detects new user message via `useEffect`
3. Sends full conversation history to AI
4. AI response added as `{ role: 'ai', content }`
5. Updates Convex database with full message array

**Why Full History?**

- AI needs context of previous messages
- Enables multi-turn conversations
- Allows AI to reference earlier code

---

### **9.3 File Merging System**

**Default Files** (always included):

```javascript
{
  '/index.html': { code: '<!DOCTYPE html>...' },
  '/styles.css': { code: 'body { margin: 0; }' }
}
```

**AI-Generated Files**:

```javascript
{
  '/App.js': { code: 'import React...' },
  '/components/TodoList.js': { code: 'export default...' }
}
```

**Merge Logic**:

```javascript
const mergedFiles = { ...Lookup.DEFAULT_FILE, ...aiGeneratedFiles };
```

**Result**: Complete project with HTML, CSS, and React components

---

## **10. DEPLOYMENT GUIDE**

### **10.1 Development Setup**

```bash
# 1. Clone repository
git clone https://github.com/nasserml/code-mind-ai-bolt-clone.git
cd code-mind-ai-bolt-clone

# 2. Install dependencies
npm install

# 3. Set up environment variables
cp .env.example .env
# Edit .env with your API keys

# 4. Start Convex backend
npx convex dev

# 5. Start Next.js dev server
npm run dev

# 6. Open browser
# Visit http://localhost:3000
```

### **10.2 Production Deployment**

**Recommended**: Vercel (same team as Next.js)

```bash
# 1. Push to GitHub

# 2. Connect to Vercel
# Visit vercel.com → Import Project → Select repo

# 3. Configure environment variables
# Add all 5 variables from .env to Vercel dashboard

# 4. Deploy Convex to production
npx convex deploy

# 5. Update Convex URLs
# Replace dev URLs with prod URLs in Vercel env vars

# 6. Deploy
# Vercel auto-deploys on git push
```

---

## **11. BUSINESS MODEL**

### **11.1 Revenue Streams**

**Token Sales**:

- Basic: $5 → 100,000 tokens (20,000 tokens/$1)
- Premium: $15 → 500,000 tokens (33,333 tokens/$1)
- Ultimate: $25 → 1,000,000 tokens (40,000 tokens/$1)

**Typical Usage**:

- Chat message: ~50 tokens average
- Code generation: ~1,000 tokens average
- Free tier (50,000 tokens) = ~10 full projects

**Monthly Costs** (estimated):

- Gemini API: Free tier (60 requests/min) or $0.0004/1K tokens
- Convex: Free tier (1M function calls) or $25/month
- Vercel: Free tier (100GB bandwidth) or $20/month

---

### **11.2 Target Users**

1. **Beginners**: Learning React through AI-generated examples
2. **Rapid Prototypers**: Quick MVPs for client presentations
3. **Freelancers**: Starter templates for projects
4. **Students**: Homework assignments and practice projects
5. **Educators**: Teaching tool for programming concepts

---

## **12. LIMITATIONS & KNOWN ISSUES**

### **12.1 Current Limitations**

1. **Rate Limits**: Gemini API has 60 requests/minute limit
2. **Token Counting**: Simple word count, not accurate tokenization
3. **Code Quality**: AI-generated code may have bugs/inefficiencies
4. **Package Limitations**: Only 5 packages available (date-fns, react-chartjs-2, etc.)
5. **No Backend Code**: Only generates frontend React code
6. **File Size**: Large projects may hit token limits
7. **Export Feature**: Currently not fully implemented

### **12.2 Common Errors**

**"429 Too Many Requests"**: Gemini API rate limit hit

- **Solution**: Wait 1 minute or get new API key

**"You don't have enough tokens"**: Token balance < 10

- **Solution**: Purchase tokens from pricing page

**HTML Nesting Warning**: Dialog components have strict HTML structure

- **Solution**: Use DialogTitle and DialogDescription correctly

**Workspace Creation Fails**: Usually Convex connection issue

- **Solution**: Check Convex deployment is running (`npx convex dev`)

---

## **13. FUTURE ENHANCEMENTS**

### **13.1 Planned Features**

1. **Export to GitHub**: Direct repository creation
2. **Deploy to Vercel**: One-click deployment
3. **Backend Generation**: Node.js/Express API generation
4. **Database Integration**: MongoDB/PostgreSQL setup
5. **Team Collaboration**: Share workspaces with others
6. **Code History**: Version control within workspaces
7. **Template Library**: Pre-built project starters
8. **Custom Themes**: Light mode, color customization
9. **Advanced AI Models**: GPT-4, Claude integration
10. **Real-time Collaboration**: Multiple users editing simultaneously

---

## **14. CONTRIBUTION GUIDELINES**

### **14.1 How to Contribute**

```bash
# 1. Fork repository on GitHub

# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/code-mind-ai-bolt-clone.git

# 3. Create feature branch
git checkout -b feature/your-feature-name

# 4. Make changes and test locally

# 5. Commit with clear message
git commit -am 'Add new feature: your feature description'

# 6. Push to your fork
git push origin feature/your-feature-name

# 7. Open Pull Request on GitHub
```

### **14.2 Code Standards**

- Use **Tailwind CSS** for styling (no custom CSS)
- Follow **React Hooks** patterns (no class components)
- Add **comments** for complex logic
- Test **authentication flow** before submitting
- Ensure **token deduction** works correctly
- Check **mobile responsiveness**

---

## **15. CREDITS & LICENSE**

**Created by**: Naser (GitHub: @nasserml)  
**Inspired by**: Bolt.new (TubeGuruji)  
**License**: MIT License (open-source)  
**Live Demo**: https://code-mind-ai.vercel.app/  
**GitHub**: https://github.com/nasserml/code-mind-ai-bolt-clone  
**Support**: mnasserone@gmail.com

---

## **16. QUICK REFERENCE**

### **16.1 Important Files**

| File                                 | Purpose                             |
| ------------------------------------ | ----------------------------------- |
| `app/page.js`                        | Landing page with Hero component    |
| `app/(main)/workspace/[id]/page.jsx` | Main workspace interface            |
| `components/custom/Hero.jsx`         | Prompt input and workspace creation |
| `components/custom/ChatView.jsx`     | AI chat assistant                   |
| `components/custom/CodeView.jsx`     | Code editor and preview             |
| `configs/AiModel.jsx`                | Gemini AI configuration             |
| `data/Prompt.jsx`                    | AI prompt templates                 |
| `convex/schema.js`                   | Database schema                     |
| `convex/users.js`                    | User operations                     |
| `convex/workspace.js`                | Workspace operations                |

### **16.2 Useful Commands**

```bash
npm run dev          # Start Next.js dev server
npx convex dev       # Start Convex backend
npm run build        # Build for production
npm run start        # Start production server
npx convex deploy    # Deploy Convex to production
```

### **16.3 Environment Setup**

1. Google OAuth: https://console.cloud.google.com
2. Convex: https://dashboard.convex.dev
3. Gemini AI: https://aistudio.google.com/app/apikey
4. PayPal: https://developer.paypal.com

---

**Last Updated**: November 4, 2025  
**Documentation Version**: 1.0  
**Project Version**: 0.1.0

---

_This comprehensive documentation covers every aspect of the CodeMind AI project. For questions or contributions, please refer to the GitHub repository or contact the maintainers._
