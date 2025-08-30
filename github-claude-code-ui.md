├── .env.example
├── .gitignore
├── .nvmrc
├── LICENSE
├── README.md
├── index.html
├── package-lock.json
├── package.json
├── postcss.config.js
├── public
    ├── convert-icons.md
    ├── favicon.png
    ├── favicon.svg
    ├── generate-icons.js
    ├── icons
    │   ├── claude-ai-icon.svg
    │   ├── cursor.svg
    │   ├── generate-icons.md
    │   ├── icon-128x128.png
    │   ├── icon-128x128.svg
    │   ├── icon-144x144.png
    │   ├── icon-144x144.svg
    │   ├── icon-152x152.png
    │   ├── icon-152x152.svg
    │   ├── icon-192x192.png
    │   ├── icon-192x192.svg
    │   ├── icon-384x384.png
    │   ├── icon-384x384.svg
    │   ├── icon-512x512.png
    │   ├── icon-512x512.svg
    │   ├── icon-72x72.png
    │   ├── icon-72x72.svg
    │   ├── icon-96x96.png
    │   ├── icon-96x96.svg
    │   └── icon-template.svg
    ├── logo.svg
    ├── manifest.json
    ├── screenshots
    │   ├── cli-selection.png
    │   ├── desktop-main.png
    │   ├── mobile-chat.png
    │   └── tools-modal.png
    └── sw.js
├── server
    ├── claude-cli.js
    ├── cursor-cli.js
    ├── database
    │   ├── db.js
    │   └── init.sql
    ├── index.js
    ├── middleware
    │   └── auth.js
    ├── projects.js
    ├── routes
    │   ├── auth.js
    │   ├── cursor.js
    │   ├── git.js
    │   ├── mcp-utils.js
    │   ├── mcp.js
    │   └── taskmaster.js
    └── utils
    │   ├── mcp-detector.js
    │   └── taskmaster-websocket.js
├── src
    ├── App.jsx
    ├── components
    │   ├── ChatInterface.jsx
    │   ├── ClaudeLogo.jsx
    │   ├── ClaudeStatus.jsx
    │   ├── CodeEditor.jsx
    │   ├── CreateTaskModal.jsx
    │   ├── CursorLogo.jsx
    │   ├── DarkModeToggle.jsx
    │   ├── ErrorBoundary.jsx
    │   ├── FileTree.jsx
    │   ├── GitPanel.jsx
    │   ├── ImageViewer.jsx
    │   ├── LoginForm.jsx
    │   ├── MainContent.jsx
    │   ├── MicButton.jsx
    │   ├── MobileNav.jsx
    │   ├── NextTaskBanner.jsx
    │   ├── PRDEditor.jsx
    │   ├── ProtectedRoute.jsx
    │   ├── QuickSettingsPanel.jsx
    │   ├── SetupForm.jsx
    │   ├── Shell.jsx
    │   ├── Sidebar.jsx
    │   ├── TaskCard.jsx
    │   ├── TaskDetail.jsx
    │   ├── TaskIndicator.jsx
    │   ├── TaskList.jsx
    │   ├── TaskMasterSetupWizard.jsx
    │   ├── TaskMasterStatus.jsx
    │   ├── TodoList.jsx
    │   ├── ToolsSettings.jsx
    │   ├── Tooltip.jsx
    │   └── ui
    │   │   ├── badge.jsx
    │   │   ├── button.jsx
    │   │   ├── input.jsx
    │   │   └── scroll-area.jsx
    ├── contexts
    │   ├── AuthContext.jsx
    │   ├── TaskMasterContext.jsx
    │   ├── TasksSettingsContext.jsx
    │   ├── ThemeContext.jsx
    │   └── WebSocketContext.jsx
    ├── hooks
    │   ├── useAudioRecorder.js
    │   └── useVersionCheck.js
    ├── index.css
    ├── lib
    │   └── utils.js
    ├── main.jsx
    └── utils
    │   ├── api.js
    │   ├── websocket.js
    │   └── whisper.js
├── tailwind.config.js
├── test.html
└── vite.config.js


/.env.example:
--------------------------------------------------------------------------------
 1 | # Claude Code UI Environment Configuration
 2 | # Only includes variables that are actually used in the code
 3 | 
 4 | # =============================================================================
 5 | # SERVER CONFIGURATION
 6 | # =============================================================================
 7 | 
 8 | # Backend server port (Express API + WebSocket server)
 9 | #API server
10 | PORT=3001
11 | #Frontend port
12 | VITE_PORT=5173


--------------------------------------------------------------------------------
/.gitignore:
--------------------------------------------------------------------------------
  1 | # Dependencies
  2 | node_modules/
  3 | npm-debug.log*
  4 | yarn-debug.log*
  5 | yarn-error.log*
  6 | pnpm-debug.log*
  7 | lerna-debug.log*
  8 | 
  9 | # Build outputs
 10 | dist/
 11 | dist-ssr/
 12 | build/
 13 | out/
 14 | 
 15 | # Environment variables
 16 | .env
 17 | .env.local
 18 | .env.development.local
 19 | .env.test.local
 20 | .env.production.local
 21 | 
 22 | # IDE and editor files
 23 | .vscode/
 24 | .idea/
 25 | *.swp
 26 | *.swo
 27 | *~
 28 | 
 29 | # OS generated files
 30 | .DS_Store
 31 | .DS_Store?
 32 | ._*
 33 | .Spotlight-V100
 34 | .Trashes
 35 | ehthumbs.db
 36 | Thumbs.db
 37 | 
 38 | # Logs
 39 | *.log
 40 | logs/
 41 | 
 42 | # Runtime data
 43 | pids
 44 | *.pid
 45 | *.seed
 46 | *.pid.lock
 47 | 
 48 | # Coverage directory used by tools like istanbul
 49 | coverage/
 50 | *.lcov
 51 | 
 52 | # nyc test coverage
 53 | .nyc_output
 54 | 
 55 | # Dependency directories
 56 | jspm_packages/
 57 | 
 58 | # Optional npm cache directory
 59 | .npm
 60 | 
 61 | # Optional eslint cache
 62 | .eslintcache
 63 | 
 64 | # Optional REPL history
 65 | .node_repl_history
 66 | 
 67 | # Output of 'npm pack'
 68 | *.tgz
 69 | 
 70 | # Yarn Integrity file
 71 | .yarn-integrity
 72 | 
 73 | # dotenv environment variables file
 74 | .env.test
 75 | 
 76 | # parcel-bundler cache (https://parceljs.org/)
 77 | .cache
 78 | .parcel-cache
 79 | 
 80 | # Next.js build output
 81 | .next
 82 | 
 83 | # Nuxt.js build / generate output
 84 | .nuxt
 85 | 
 86 | # Storybook build outputs
 87 | .out
 88 | .storybook-out
 89 | 
 90 | # Temporary folders
 91 | tmp/
 92 | temp/
 93 | .tmp/
 94 | 
 95 | # Vite
 96 | .vite/
 97 | 
 98 | # Local Netlify folder
 99 | .netlify
100 | 
101 | # AI specific
102 | .claude/
103 | .cursor/
104 | .roo/
105 | .taskmaster/
106 | .cline/
107 | .windsurf/
108 | CLAUDE.md
109 | 
110 | 
111 | # Database files
112 | *.db
113 | *.sqlite
114 | *.sqlite3 
115 | 
116 | logs
117 | dev-debug.log
118 | # Editor directories and files
119 | .idea
120 | .vscode
121 | *.suo
122 | *.ntvs*
123 | *.njsproj
124 | *.sln
125 | *.sw?
126 | # OS specific
127 | 
128 | # Task files
129 | # tasks.json
130 | # tasks/ 
131 | 


--------------------------------------------------------------------------------
/.nvmrc:
--------------------------------------------------------------------------------
1 | v20.19.3


--------------------------------------------------------------------------------
/README.md:
--------------------------------------------------------------------------------
  1 | <div align="center">
  2 |   <img src="public/logo.svg" alt="Claude Code UI" width="64" height="64">
  3 |   <h1>Claude Code UI</h1>
  4 | </div>
  5 | 
  6 | 
  7 | A desktop and mobile UI for [Claude Code](https://docs.anthropic.com/en/docs/claude-code), and [Cursor CLI](https://docs.cursor.com/en/cli/overview). You can use it locally or remotely to view your active projects and sessions in Claude Code or Cursor and make changes to them from everywhere (mobile or desktop). This gives you a proper interface that works everywhere. Supports models including **Claude Sonnet 4**, **Opus 4.1**, and **GPT-5**
  8 | 
  9 | ## Screenshots
 10 | 
 11 | <div align="center">
 12 |   
 13 | <table>
 14 | <tr>
 15 | <td align="center">
 16 | <h3>Desktop View</h3>
 17 | <img src="public/screenshots/desktop-main.png" alt="Desktop Interface" width="400">
 18 | <br>
 19 | <em>Main interface showing project overview and chat</em>
 20 | </td>
 21 | <td align="center">
 22 | <h3>Mobile Experience</h3>
 23 | <img src="public/screenshots/mobile-chat.png" alt="Mobile Interface" width="250">
 24 | <br>
 25 | <em>Responsive mobile design with touch navigation</em>
 26 | </td>
 27 | </tr>
 28 | <tr>
 29 | <td align="center" colspan="2">
 30 | <h3>CLI Selection</h3>
 31 | <img src="public/screenshots/cli-selection.png" alt="CLI Selection" width="400">
 32 | <br>
 33 | <em>Select between Claude Code and Cursor CLI</em>
 34 | </td>
 35 | </tr>
 36 | </table>
 37 | 
 38 | 
 39 | 
 40 | </div>
 41 | 
 42 | ## Features
 43 | 
 44 | - **Responsive Design** - Works seamlessly across desktop, tablet, and mobile so you can also use Claude Code from mobile 
 45 | - **Interactive Chat Interface** - Built-in chat interface for seamless communication with Claude Code or Cursor
 46 | - **Integrated Shell Terminal** - Direct access to Claude Code or Cursor CLI through built-in shell functionality
 47 | - **File Explorer** - Interactive file tree with syntax highlighting and live editing
 48 | - **Git Explorer** - View, stage and commit your changes. You can also switch branches 
 49 | - **Session Management** - Resume conversations, manage multiple sessions, and track history
 50 | - **TaskMaster AI Integration** *(Optional)* - Advanced project management with AI-powered task planning, PRD parsing, and workflow automation
 51 | - **Model Compatibility** - Works with Claude Sonnet 4, Opus 4.1, and GPT-5
 52 | 
 53 | 
 54 | ## Quick Start
 55 | 
 56 | ### Prerequisites
 57 | 
 58 | - [Node.js](https://nodejs.org/) v20 or higher
 59 | - [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) installed and configured, and/or
 60 | - [Cursor CLI](https://docs.cursor.com/en/cli/overview) installed and configured
 61 | 
 62 | ### Installation
 63 | 
 64 | 1. **Clone the repository:**
 65 | ```bash
 66 | git clone https://github.com/siteboon/claudecodeui.git
 67 | cd claudecodeui
 68 | ```
 69 | 
 70 | 2. **Install dependencies:**
 71 | ```bash
 72 | npm install
 73 | ```
 74 | 
 75 | 3. **Configure environment:**
 76 | ```bash
 77 | cp .env.example .env
 78 | # Edit .env with your preferred settings
 79 | ```
 80 | 
 81 | 4. **Start the application:**
 82 | ```bash
 83 | # Development mode (with hot reload)
 84 | npm run dev
 85 | 
 86 | ```
 87 | The application will start at the port you specified in your .env
 88 | 
 89 | 5. **Open your browser:**
 90 |    - Development: `http://localhost:3001`
 91 | 
 92 | ## Security & Tools Configuration
 93 | 
 94 | **🔒 Important Notice**: All Claude Code tools are **disabled by default**. This prevents potentially harmful operations from running automatically.
 95 | 
 96 | ### Enabling Tools
 97 | 
 98 | To use Claude Code's full functionality, you'll need to manually enable tools:
 99 | 
100 | 1. **Open Tools Settings** - Click the gear icon in the sidebar
101 | 3. **Enable Selectively** - Turn on only the tools you need
102 | 4. **Apply Settings** - Your preferences are saved locally
103 | 
104 | <div align="center">
105 | 
106 | ![Tools Settings Modal](public/screenshots/tools-modal.png)
107 | *Tools Settings interface - enable only what you need*
108 | 
109 | </div>
110 | 
111 | **Recommended approach**: Start with basic tools enabled and add more as needed. You can always adjust these settings later.
112 | 
113 | ## TaskMaster AI Integration *(Optional)*
114 | 
115 | Claude Code UI supports **[TaskMaster AI](https://github.com/eyaltoledano/claude-task-master)** (aka claude-task-master) integration for advanced project management and AI-powered task planning.
116 | 
117 | It provides
118 | - AI-powered task generation from PRDs (Product Requirements Documents)
119 | - Smart task breakdown and dependency management  
120 | - Visual task boards and progress tracking
121 | 
122 | **Setup & Documentation**: Visit the [TaskMaster AI GitHub repository](https://github.com/eyaltoledano/claude-task-master) for installation instructions, configuration guides, and usage examples.
123 | After installing it you should be able to enable it from the Settings
124 | 
125 | 
126 | ## Usage Guide
127 | 
128 | ### Core Features
129 | 
130 | #### Project Management
131 | The UI automatically discovers Claude Code projects from `~/.claude/projects/` and provides:
132 | - **Visual Project Browser** - All available projects with metadata and session counts
133 | - **Project Actions** - Rename, delete, and organize projects
134 | - **Smart Navigation** - Quick access to recent projects and sessions
135 | - **MCP support** - Add your own MCP servers through the UI 
136 | 
137 | #### Chat Interface
138 | - **Use responsive chat or Claude Code/Cursor CLI** - You can either use the adapted chat interface or use the shell button to connect to your selected CLI. 
139 | - **Real-time Communication** - Stream responses from Claude with WebSocket connection
140 | - **Session Management** - Resume previous conversations or start fresh sessions
141 | - **Message History** - Complete conversation history with timestamps and metadata
142 | - **Multi-format Support** - Text, code blocks, and file references
143 | 
144 | #### File Explorer & Editor
145 | - **Interactive File Tree** - Browse project structure with expand/collapse navigation
146 | - **Live File Editing** - Read, modify, and save files directly in the interface
147 | - **Syntax Highlighting** - Support for multiple programming languages
148 | - **File Operations** - Create, rename, delete files and directories
149 | 
150 | #### Git Explorer
151 | 
152 | 
153 | #### TaskMaster AI Integration *(Optional)*
154 | - **Visual Task Board** - Kanban-style interface for managing development tasks
155 | - **PRD Parser** - Create Product Requirements Documents and parse them into structured tasks
156 | - **Progress Tracking** - Real-time status updates and completion tracking
157 | 
158 | #### Session Management
159 | - **Session Persistence** - All conversations automatically saved
160 | - **Session Organization** - Group sessions by project and timestamp
161 | - **Session Actions** - Rename, delete, and export conversation history
162 | - **Cross-device Sync** - Access sessions from any device
163 | 
164 | ### Mobile App
165 | - **Responsive Design** - Optimized for all screen sizes
166 | - **Touch-friendly Interface** - Swipe gestures and touch navigation
167 | - **Mobile Navigation** - Bottom tab bar for easy thumb navigation
168 | - **Adaptive Layout** - Collapsible sidebar and smart content prioritization
169 | - **Add shortcut to Home Screen** - Add a shortcut to your home screen and the app will behave like a PWA
170 | 
171 | ## Architecture
172 | 
173 | ### System Overview
174 | 
175 | ```
176 | ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
177 | │   Frontend      │    │   Backend       │    │  Claude CLI     │
178 | │   (React/Vite)  │◄──►│ (Express/WS)    │◄──►│  Integration    │
179 | └─────────────────┘    └─────────────────┘    └─────────────────┘
180 | ```
181 | 
182 | ### Backend (Node.js + Express)
183 | - **Express Server** - RESTful API with static file serving
184 | - **WebSocket Server** - Communication for chats and project refresh
185 | - **CLI Integration (Claude Code / Cursor)** - Process spawning and management
186 | - **Session Management** - JSONL parsing and conversation persistence
187 | - **File System API** - Exposing file browser for projects
188 | 
189 | ### Frontend (React + Vite)
190 | - **React 18** - Modern component architecture with hooks
191 | - **CodeMirror** - Advanced code editor with syntax highlighting
192 | 
193 | 
194 | 
195 | 
196 | 
197 | ### Contributing
198 | 
199 | We welcome contributions! Please follow these guidelines:
200 | 
201 | #### Getting Started
202 | 1. **Fork** the repository
203 | 2. **Clone** your fork: `git clone <your-fork-url>`
204 | 3. **Install** dependencies: `npm install`
205 | 4. **Create** a feature branch: `git checkout -b feature/amazing-feature`
206 | 
207 | #### Development Process
208 | 1. **Make your changes** following the existing code style
209 | 2. **Test thoroughly** - ensure all features work correctly
210 | 3. **Run quality checks**: `npm run lint && npm run format`
211 | 4. **Commit** with descriptive messages following [Conventional Commits](https://conventionalcommits.org/)
212 | 5. **Push** to your branch: `git push origin feature/amazing-feature`
213 | 6. **Submit** a Pull Request with:
214 |    - Clear description of changes
215 |    - Screenshots for UI changes
216 |    - Test results if applicable
217 | 
218 | #### What to Contribute
219 | - **Bug fixes** - Help us improve stability
220 | - **New features** - Enhance functionality (discuss in issues first)
221 | - **Documentation** - Improve guides and API docs
222 | - **UI/UX improvements** - Better user experience
223 | - **Performance optimizations** - Make it faster
224 | 
225 | ## Troubleshooting
226 | 
227 | ### Common Issues & Solutions
228 | 
229 | #### "No Claude projects found"
230 | **Problem**: The UI shows no projects or empty project list
231 | **Solutions**:
232 | - Ensure [Claude CLI](https://docs.anthropic.com/en/docs/claude-code) is properly installed
233 | - Run `claude` command in at least one project directory to initialize
234 | - Verify `~/.claude/projects/` directory exists and has proper permissions
235 | d
236 | 
237 | #### File Explorer Issues
238 | **Problem**: Files not loading, permission errors, empty directories
239 | **Solutions**:
240 | - Check project directory permissions (`ls -la` in terminal)
241 | - Verify the project path exists and is accessible
242 | - Review server console logs for detailed error messages
243 | - Ensure you're not trying to access system directories outside project scope
244 | 
245 | 
246 | ## License
247 | 
248 | GNU General Public License v3.0 - see [LICENSE](LICENSE) file for details.
249 | 
250 | This project is open source and free to use, modify, and distribute under the GPL v3 license.
251 | 
252 | ## Acknowledgments
253 | 
254 | ### Built With
255 | - **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** - Anthropic's official CLI
256 | - **[React](https://react.dev/)** - User interface library
257 | - **[Vite](https://vitejs.dev/)** - Fast build tool and dev server
258 | - **[Tailwind CSS](https://tailwindcss.com/)** - Utility-first CSS framework
259 | - **[CodeMirror](https://codemirror.net/)** - Advanced code editor
260 | - **[TaskMaster AI](https://github.com/eyaltoledano/claude-task-master)** *(Optional)* - AI-powered project management and task planning
261 | 
262 | ## Support & Community
263 | 
264 | ### Stay Updated
265 | - **Star** this repository to show support
266 | - **Watch** for updates and new releases
267 | - **Follow** the project for announcements
268 | 
269 | ### Sponsors
270 | - [Siteboon - AI powered website builder](https://siteboon.ai)
271 | ---
272 | 
273 | <div align="center">
274 |   <strong>Made with care for the Claude Code community.</strong>
275 | </div>
276 | 


--------------------------------------------------------------------------------
/index.html:
--------------------------------------------------------------------------------
 1 | <!doctype html>
 2 | <html lang="en">
 3 |   <head>
 4 |     <meta charset="UTF-8" />
 5 |     <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
 6 |     <link rel="icon" type="image/png" href="/favicon.png" />
 7 |     <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover" />
 8 |     <title>Claude Code UI</title>
 9 |     
10 |     <!-- PWA Manifest -->
11 |     <link rel="manifest" href="/manifest.json" />
12 |     
13 |     <!-- iOS Safari PWA Meta Tags -->
14 |     <meta name="apple-mobile-web-app-capable" content="yes" />
15 |     <meta name="apple-mobile-web-app-status-bar-style" content="default" />
16 |     <meta name="apple-mobile-web-app-title" content="Claude UI" />
17 |     
18 |     <!-- iOS Safari Icons -->
19 |     <link rel="apple-touch-icon" sizes="152x152" href="/icons/icon-152x152.png" />
20 |     <link rel="apple-touch-icon" sizes="180x180" href="/icons/icon-192x192.png" />
21 |     
22 |     <!-- Theme Color -->
23 |     <meta name="theme-color" content="#ffffff" />
24 |     <meta name="msapplication-TileColor" content="#ffffff" />
25 |     
26 |     <!-- Prevent zoom on iOS -->
27 |     <meta name="format-detection" content="telephone=no" />
28 |   </head>
29 |   <body>
30 |     <div id="root"></div>
31 |     <script type="module" src="/src/main.jsx"></script>
32 |     
33 |     <!-- Service Worker Registration -->
34 |     <script>
35 |       if ('serviceWorker' in navigator) {
36 |         window.addEventListener('load', () => {
37 |           navigator.serviceWorker.register('/sw.js')
38 |             .then(registration => {
39 |               console.log('SW registered: ', registration);
40 |             })
41 |             .catch(registrationError => {
42 |               console.log('SW registration failed: ', registrationError);
43 |             });
44 |         });
45 |       }
46 |     </script>
47 |   </body>
48 | </html>


--------------------------------------------------------------------------------
/package.json:
--------------------------------------------------------------------------------
 1 | {
 2 |   "name": "claude-code-ui",
 3 |   "version": "1.8.0",
 4 |   "description": "A web-based UI for Claude Code CLI",
 5 |   "type": "module",
 6 |   "main": "server/index.js",
 7 |   "scripts": {
 8 |     "dev": "concurrently --kill-others \"npm run server\" \"npm run client\"",
 9 |     "server": "node server/index.js",
10 |     "client": "vite --host",
11 |     "build": "vite build",
12 |     "preview": "vite preview",
13 |     "start": "npm run build && npm run server"
14 |   },
15 |   "keywords": [
16 |     "claude",
17 |     "ai",
18 |     "code",
19 |     "ui",
20 |     "assistant"
21 |   ],
22 |   "author": "Claude Code UI Contributors",
23 |   "license": "MIT",
24 |   "dependencies": {
25 |     "@codemirror/lang-css": "^6.3.1",
26 |     "@codemirror/lang-html": "^6.4.9",
27 |     "@codemirror/lang-javascript": "^6.2.4",
28 |     "@codemirror/lang-json": "^6.0.1",
29 |     "@codemirror/lang-markdown": "^6.3.3",
30 |     "@codemirror/lang-python": "^6.2.1",
31 |     "@codemirror/theme-one-dark": "^6.1.2",
32 |     "@tailwindcss/typography": "^0.5.16",
33 |     "@uiw/react-codemirror": "^4.23.13",
34 |     "@xterm/addon-clipboard": "^0.1.0",
35 |     "@xterm/addon-webgl": "^0.18.0",
36 |     "bcrypt": "^6.0.0",
37 |     "better-sqlite3": "^12.2.0",
38 |     "chokidar": "^4.0.3",
39 |     "class-variance-authority": "^0.7.1",
40 |     "clsx": "^2.1.1",
41 |     "cors": "^2.8.5",
42 |     "cross-spawn": "^7.0.3",
43 |     "express": "^4.18.2",
44 |     "jsonwebtoken": "^9.0.2",
45 |     "lucide-react": "^0.515.0",
46 |     "mime-types": "^3.0.1",
47 |     "multer": "^2.0.1",
48 |     "node-fetch": "^2.7.0",
49 |     "node-pty": "^1.1.0-beta34",
50 |     "react": "^18.2.0",
51 |     "react-dom": "^18.2.0",
52 |     "react-dropzone": "^14.2.3",
53 |     "react-markdown": "^10.1.0",
54 |     "react-router-dom": "^6.8.1",
55 |     "sqlite": "^5.1.1",
56 |     "sqlite3": "^5.1.7",
57 |     "tailwind-merge": "^3.3.1",
58 |     "ws": "^8.14.2",
59 |     "xterm": "^5.3.0",
60 |     "xterm-addon-fit": "^0.8.0"
61 |   },
62 |   "devDependencies": {
63 |     "@types/react": "^18.2.43",
64 |     "@types/react-dom": "^18.2.17",
65 |     "@vitejs/plugin-react": "^4.6.0",
66 |     "autoprefixer": "^10.4.16",
67 |     "concurrently": "^8.2.2",
68 |     "node-gyp": "^10.0.0",
69 |     "postcss": "^8.4.32",
70 |     "sharp": "^0.34.2",
71 |     "tailwindcss": "^3.4.0",
72 |     "vite": "^7.0.4"
73 |   }
74 | }
75 | 


--------------------------------------------------------------------------------
/postcss.config.js:
--------------------------------------------------------------------------------
1 | export default {
2 |   plugins: {
3 |     tailwindcss: {},
4 |     autoprefixer: {},
5 |   },
6 | }


--------------------------------------------------------------------------------
/public/convert-icons.md:
--------------------------------------------------------------------------------
 1 | # Convert SVG Icons to PNG
 2 | 
 3 | I've created SVG versions of the app icons that match the MessageSquare design from the sidebar. To convert them to PNG format, you can use one of these methods:
 4 | 
 5 | ## Method 1: Online Converter (Easiest)
 6 | 1. Go to https://cloudconvert.com/svg-to-png
 7 | 2. Upload each SVG file from the `/icons/` directory
 8 | 3. Download the PNG versions
 9 | 4. Replace the existing PNG files
10 | 
11 | ## Method 2: Using Node.js (if you have it)
12 | ```bash
13 | npm install sharp
14 | node -e "
15 | const sharp = require('sharp');
16 | const fs = require('fs');
17 | const sizes = [72, 96, 128, 144, 152, 192, 384, 512];
18 | sizes.forEach(size => {
19 |   const svgPath = \`./icons/icon-\${size}x\${size}.svg\`;
20 |   const pngPath = \`./icons/icon-\${size}x\${size}.png\`;
21 |   if (fs.existsSync(svgPath)) {
22 |     sharp(svgPath).png().toFile(pngPath);
23 |     console.log(\`Converted \${svgPath} to \${pngPath}\`);
24 |   }
25 | });
26 | "
27 | ```
28 | 
29 | ## Method 3: Using ImageMagick (if installed)
30 | ```bash
31 | cd public/icons
32 | for size in 72 96 128 144 152 192 384 512; do
33 |   convert "icon-${size}x${size}.svg" "icon-${size}x${size}.png"
34 | done
35 | ```
36 | 
37 | ## Method 4: Using Inkscape (if installed)
38 | ```bash
39 | cd public/icons
40 | for size in 72 96 128 144 152 192 384 512; do
41 |   inkscape --export-type=png "icon-${size}x${size}.svg"
42 | done
43 | ```
44 | 
45 | ## Icon Design
46 | The new icons feature:
47 | - Clean MessageSquare (chat bubble) design matching the sidebar
48 | - Primary color background with rounded corners
49 | - White stroke icon that's clearly visible
50 | - Consistent sizing and proportions across all sizes
51 | - Proper PWA-compliant format
52 | 
53 | Once converted, the PNG files will replace the existing ones and provide a consistent icon experience across all platforms.


--------------------------------------------------------------------------------
/public/favicon.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/favicon.png


--------------------------------------------------------------------------------
/public/favicon.svg:
--------------------------------------------------------------------------------
1 | <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64 64" width="64" height="64">
2 |   <!-- Background fills entire canvas -->
3 |   <rect x="0" y="0" width="64" height="64" fill="hsl(240 5.9% 10%)"/>
4 |   
5 |   <!-- MessageSquare icon - exact same as sidebar -->
6 |   <g transform="translate(32, 32) scale(1.333) translate(-12, -12)" stroke="white" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round">
7 |     <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/>
8 |   </g>
9 | </svg>


--------------------------------------------------------------------------------
/public/generate-icons.js:
--------------------------------------------------------------------------------
 1 | const fs = require('fs');
 2 | const path = require('path');
 3 | 
 4 | // Icon sizes needed
 5 | const sizes = [72, 96, 128, 144, 152, 192, 384, 512];
 6 | 
 7 | // SVG template function
 8 | function createIconSVG(size) {
 9 |   const cornerRadius = Math.round(size * 0.25); // 25% corner radius
10 |   const strokeWidth = Math.max(2, Math.round(size * 0.06)); // Scale stroke width
11 |   
12 |   // MessageSquare path scaled to size
13 |   const padding = Math.round(size * 0.25);
14 |   const iconSize = size - (padding * 2);
15 |   const startX = padding;
16 |   const startY = Math.round(padding * 0.7);
17 |   const endX = startX + iconSize;
18 |   const endY = startY + Math.round(iconSize * 0.6);
19 |   const tailX = startX;
20 |   const tailY = endY + Math.round(iconSize * 0.3);
21 |   
22 |   return `<svg width="${size}" height="${size}" viewBox="0 0 ${size} ${size}" fill="none" xmlns="http://www.w3.org/2000/svg">
23 |   <!-- Background with rounded corners -->
24 |   <rect width="${size}" height="${size}" rx="${cornerRadius}" fill="hsl(262.1 83.3% 57.8%)"/>
25 |   
26 |   <!-- MessageSquare icon -->
27 |   <path d="M${startX} ${startY}C${startX} ${startY - 10} ${startX + 10} ${startY - 20} ${startX + 20} ${startY - 20}H${endX - 20}C${endX - 10} ${startY - 20} ${endX} ${startY - 10} ${endX} ${startY}V${endY - 20}C${endX} ${endY - 10} ${endX - 10} ${endY} ${endX - 20} ${endY}H${startX + Math.round(iconSize * 0.4)}L${tailX} ${tailY}V${startY}Z" 
28 |         stroke="white" 
29 |         stroke-width="${strokeWidth}" 
30 |         stroke-linecap="round" 
31 |         stroke-linejoin="round" 
32 |         fill="none"/>
33 | </svg>`;
34 | }
35 | 
36 | // Generate SVG files for each size
37 | sizes.forEach(size => {
38 |   const svgContent = createIconSVG(size);
39 |   const filename = `icon-${size}x${size}.svg`;
40 |   const filepath = path.join(__dirname, 'icons', filename);
41 |   
42 |   fs.writeFileSync(filepath, svgContent);
43 |   console.log(`Created ${filename}`);
44 | });
45 | 
46 | console.log('\nSVG icons created! To convert to PNG, you can use:');
47 | console.log('1. Online converter like cloudconvert.com');
48 | console.log('2. If you have ImageMagick: convert icon.svg icon.png');
49 | console.log('3. If you have Inkscape: inkscape --export-type=png icon.svg');


--------------------------------------------------------------------------------
/public/icons/claude-ai-icon.svg:
--------------------------------------------------------------------------------
1 | <svg xmlns="http://www.w3.org/2000/svg" shape-rendering="geometricPrecision" text-rendering="geometricPrecision" image-rendering="optimizeQuality" fill-rule="evenodd" clip-rule="evenodd" viewBox="0 0 512 509.64"><path fill="#D77655" d="M115.612 0h280.775C459.974 0 512 52.026 512 115.612v278.415c0 63.587-52.026 115.612-115.613 115.612H115.612C52.026 509.639 0 457.614 0 394.027V115.612C0 52.026 52.026 0 115.612 0z"/><path fill="#FCF2EE" fill-rule="nonzero" d="M142.27 316.619l73.655-41.326 1.238-3.589-1.238-1.996-3.589-.001-12.31-.759-42.084-1.138-36.498-1.516-35.361-1.896-8.897-1.895-8.34-10.995.859-5.484 7.482-5.03 10.717.935 23.683 1.617 35.537 2.452 25.782 1.517 38.193 3.968h6.064l.86-2.451-2.073-1.517-1.618-1.517-36.776-24.922-39.81-26.338-20.852-15.166-11.273-7.683-5.687-7.204-2.451-15.721 10.237-11.273 13.75.935 3.513.936 13.928 10.716 29.749 23.027 38.848 28.612 5.687 4.727 2.275-1.617.278-1.138-2.553-4.271-21.13-38.193-22.546-38.848-10.035-16.101-2.654-9.655c-.935-3.968-1.617-7.304-1.617-11.374l11.652-15.823 6.445-2.073 15.545 2.073 6.547 5.687 9.655 22.092 15.646 34.78 24.265 47.291 7.103 14.028 3.791 12.992 1.416 3.968 2.449-.001v-2.275l1.997-26.641 3.69-32.707 3.589-42.084 1.239-11.854 5.863-14.206 11.652-7.683 9.099 4.348 7.482 10.716-1.036 6.926-4.449 28.915-8.72 45.294-5.687 30.331h3.313l3.792-3.791 15.342-20.372 25.782-32.227 11.374-12.789 13.27-14.129 8.517-6.724 16.1-.001 11.854 17.617-5.307 18.199-16.581 21.029-13.75 17.819-19.716 26.54-12.309 21.231 1.138 1.694 2.932-.278 44.536-9.479 24.062-4.347 28.714-4.928 12.992 6.066 1.416 6.167-5.106 12.613-30.71 7.583-36.018 7.204-53.636 12.689-.657.48.758.935 24.164 2.275 10.337.556h25.301l47.114 3.514 12.309 8.139 7.381 9.959-1.238 7.583-18.957 9.655-25.579-6.066-59.702-14.205-20.474-5.106-2.83-.001v1.694l17.061 16.682 31.266 28.233 39.152 36.397 1.997 8.999-5.03 7.102-5.307-.758-34.401-25.883-13.27-11.651-30.053-25.302-1.996-.001v2.654l6.926 10.136 36.574 54.975 1.895 16.859-2.653 5.485-9.479 3.311-10.414-1.895-21.408-30.054-22.092-33.844-17.819-30.331-2.173 1.238-10.515 113.261-4.929 5.788-11.374 4.348-9.478-7.204-5.03-11.652 5.03-23.027 6.066-30.052 4.928-23.886 4.449-29.674 2.654-9.858-.177-.657-2.173.278-22.37 30.71-34.021 45.977-26.919 28.815-6.445 2.553-11.173-5.789 1.037-10.337 6.243-9.2 37.257-47.392 22.47-29.371 14.508-16.961-.101-2.451h-.859l-98.954 64.251-17.618 2.275-7.583-7.103.936-11.652 3.589-3.791 29.749-20.474-.101.102.024.101z"/></svg>


--------------------------------------------------------------------------------
/public/icons/cursor.svg:
--------------------------------------------------------------------------------
1 | <svg height="1em" style="flex:none;line-height:1" viewBox="0 0 24 24" width="1em" xmlns="http://www.w3.org/2000/svg"><title>Cursor</title><path d="M11.925 24l10.425-6-10.425-6L1.5 18l10.425 6z" fill="url(#lobe-icons-cursorundefined-fill-0)"></path><path d="M22.35 18V6L11.925 0v12l10.425 6z" fill="url(#lobe-icons-cursorundefined-fill-1)"></path><path d="M11.925 0L1.5 6v12l10.425-6V0z" fill="url(#lobe-icons-cursorundefined-fill-2)"></path><path d="M22.35 6L11.925 24V12L22.35 6z" fill="#555"></path><path d="M22.35 6l-10.425 6L1.5 6h20.85z" fill="#000"></path><defs><linearGradient gradientUnits="userSpaceOnUse" id="lobe-icons-cursorundefined-fill-0" x1="11.925" x2="11.925" y1="12" y2="24"><stop offset=".16" stop-color="#000" stop-opacity=".39"></stop><stop offset=".658" stop-color="#000" stop-opacity=".8"></stop></linearGradient><linearGradient gradientUnits="userSpaceOnUse" id="lobe-icons-cursorundefined-fill-1" x1="22.35" x2="11.925" y1="6.037" y2="12.15"><stop offset=".182" stop-color="#000" stop-opacity=".31"></stop><stop offset=".715" stop-color="#000" stop-opacity="0"></stop></linearGradient><linearGradient gradientUnits="userSpaceOnUse" id="lobe-icons-cursorundefined-fill-2" x1="11.925" x2="1.5" y1="0" y2="18"><stop stop-color="#000" stop-opacity=".6"></stop><stop offset=".667" stop-color="#000" stop-opacity=".22"></stop></linearGradient></defs></svg>


--------------------------------------------------------------------------------
/public/icons/generate-icons.md:
--------------------------------------------------------------------------------
 1 | # PWA Icons Required
 2 | 
 3 | Create the following icon files in this directory:
 4 | 
 5 | - icon-72x72.png
 6 | - icon-96x96.png
 7 | - icon-128x128.png
 8 | - icon-144x144.png
 9 | - icon-152x152.png
10 | - icon-192x192.png
11 | - icon-384x384.png
12 | - icon-512x512.png
13 | 
14 | You can use any icon generator tool or create them manually. The icons should be square and represent your Claude Code UI application.
15 | 
16 | For a quick solution, you can:
17 | 1. Create a simple square PNG icon (512x512)
18 | 2. Use online tools like realfavicongenerator.net to generate all sizes
19 | 3. Or use ImageMagick: `convert icon-512x512.png -resize 192x192 icon-192x192.png`


--------------------------------------------------------------------------------
/public/icons/icon-128x128.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/icons/icon-128x128.png


--------------------------------------------------------------------------------
/public/icons/icon-128x128.svg:
--------------------------------------------------------------------------------
 1 | <svg width="512" height="512" viewBox="0 0 512 512" fill="none" xmlns="http://www.w3.org/2000/svg">
 2 |   <!-- Background fills entire canvas - iOS will handle corner rounding -->
 3 |   <rect width="512" height="512" fill="hsl(240 5.9% 10%)"/>
 4 |   
 5 |   <!-- MessageSquare icon - scaled and centered -->
 6 |   <path d="M128 144C128 126.327 142.327 112 160 112H352C369.673 112 384 126.327 384 144V272C384 289.673 369.673 304 352 304H224L128 400V144Z" 
 7 |         stroke="white" 
 8 |         stroke-width="32" 
 9 |         stroke-linecap="round" 
10 |         stroke-linejoin="round" 
11 |         fill="none"/>
12 | </svg>


--------------------------------------------------------------------------------
/public/icons/icon-144x144.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/icons/icon-144x144.png


--------------------------------------------------------------------------------
/public/icons/icon-144x144.svg:
--------------------------------------------------------------------------------
 1 | <svg width="512" height="512" viewBox="0 0 512 512" fill="none" xmlns="http://www.w3.org/2000/svg">
 2 |   <!-- Background fills entire canvas - iOS will handle corner rounding -->
 3 |   <rect width="512" height="512" fill="hsl(240 5.9% 10%)"/>
 4 |   
 5 |   <!-- MessageSquare icon - scaled and centered -->
 6 |   <path d="M128 144C128 126.327 142.327 112 160 112H352C369.673 112 384 126.327 384 144V272C384 289.673 369.673 304 352 304H224L128 400V144Z" 
 7 |         stroke="white" 
 8 |         stroke-width="32" 
 9 |         stroke-linecap="round" 
10 |         stroke-linejoin="round" 
11 |         fill="none"/>
12 | </svg>


--------------------------------------------------------------------------------
/public/icons/icon-152x152.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/icons/icon-152x152.png


--------------------------------------------------------------------------------
/public/icons/icon-152x152.svg:
--------------------------------------------------------------------------------
 1 | <svg width="512" height="512" viewBox="0 0 512 512" fill="none" xmlns="http://www.w3.org/2000/svg">
 2 |   <!-- Background fills entire canvas - iOS will handle corner rounding -->
 3 |   <rect width="512" height="512" fill="hsl(240 5.9% 10%)"/>
 4 |   
 5 |   <!-- MessageSquare icon - scaled and centered -->
 6 |   <path d="M128 144C128 126.327 142.327 112 160 112H352C369.673 112 384 126.327 384 144V272C384 289.673 369.673 304 352 304H224L128 400V144Z" 
 7 |         stroke="white" 
 8 |         stroke-width="32" 
 9 |         stroke-linecap="round" 
10 |         stroke-linejoin="round" 
11 |         fill="none"/>
12 | </svg>


--------------------------------------------------------------------------------
/public/icons/icon-192x192.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/icons/icon-192x192.png


--------------------------------------------------------------------------------
/public/icons/icon-192x192.svg:
--------------------------------------------------------------------------------
 1 | <svg width="512" height="512" viewBox="0 0 512 512" fill="none" xmlns="http://www.w3.org/2000/svg">
 2 |   <!-- Background fills entire canvas - iOS will handle corner rounding -->
 3 |   <rect width="512" height="512" fill="hsl(240 5.9% 10%)"/>
 4 |   
 5 |   <!-- MessageSquare icon - scaled and centered -->
 6 |   <path d="M128 144C128 126.327 142.327 112 160 112H352C369.673 112 384 126.327 384 144V272C384 289.673 369.673 304 352 304H224L128 400V144Z" 
 7 |         stroke="white" 
 8 |         stroke-width="32" 
 9 |         stroke-linecap="round" 
10 |         stroke-linejoin="round" 
11 |         fill="none"/>
12 | </svg>


--------------------------------------------------------------------------------
/public/icons/icon-384x384.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/icons/icon-384x384.png


--------------------------------------------------------------------------------
/public/icons/icon-384x384.svg:
--------------------------------------------------------------------------------
 1 | <svg width="512" height="512" viewBox="0 0 512 512" fill="none" xmlns="http://www.w3.org/2000/svg">
 2 |   <!-- Background fills entire canvas - iOS will handle corner rounding -->
 3 |   <rect width="512" height="512" fill="hsl(240 5.9% 10%)"/>
 4 |   
 5 |   <!-- MessageSquare icon - scaled and centered -->
 6 |   <path d="M128 144C128 126.327 142.327 112 160 112H352C369.673 112 384 126.327 384 144V272C384 289.673 369.673 304 352 304H224L128 400V144Z" 
 7 |         stroke="white" 
 8 |         stroke-width="32" 
 9 |         stroke-linecap="round" 
10 |         stroke-linejoin="round" 
11 |         fill="none"/>
12 | </svg>


--------------------------------------------------------------------------------
/public/icons/icon-512x512.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/icons/icon-512x512.png


--------------------------------------------------------------------------------
/public/icons/icon-512x512.svg:
--------------------------------------------------------------------------------
 1 | <svg width="512" height="512" viewBox="0 0 512 512" fill="none" xmlns="http://www.w3.org/2000/svg">
 2 |   <!-- Background fills entire canvas - iOS will handle corner rounding -->
 3 |   <rect width="512" height="512" fill="hsl(240 5.9% 10%)"/>
 4 |   
 5 |   <!-- MessageSquare icon - scaled and centered -->
 6 |   <path d="M128 144C128 126.327 142.327 112 160 112H352C369.673 112 384 126.327 384 144V272C384 289.673 369.673 304 352 304H224L128 400V144Z" 
 7 |         stroke="white" 
 8 |         stroke-width="32" 
 9 |         stroke-linecap="round" 
10 |         stroke-linejoin="round" 
11 |         fill="none"/>
12 | </svg>


--------------------------------------------------------------------------------
/public/icons/icon-72x72.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/icons/icon-72x72.png


--------------------------------------------------------------------------------
/public/icons/icon-72x72.svg:
--------------------------------------------------------------------------------
 1 | <svg width="512" height="512" viewBox="0 0 512 512" fill="none" xmlns="http://www.w3.org/2000/svg">
 2 |   <!-- Background fills entire canvas - iOS will handle corner rounding -->
 3 |   <rect width="512" height="512" fill="hsl(240 5.9% 10%)"/>
 4 |   
 5 |   <!-- MessageSquare icon - scaled and centered -->
 6 |   <path d="M128 144C128 126.327 142.327 112 160 112H352C369.673 112 384 126.327 384 144V272C384 289.673 369.673 304 352 304H224L128 400V144Z" 
 7 |         stroke="white" 
 8 |         stroke-width="32" 
 9 |         stroke-linecap="round" 
10 |         stroke-linejoin="round" 
11 |         fill="none"/>
12 | </svg>


--------------------------------------------------------------------------------
/public/icons/icon-96x96.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/icons/icon-96x96.png


--------------------------------------------------------------------------------
/public/icons/icon-96x96.svg:
--------------------------------------------------------------------------------
 1 | <svg width="512" height="512" viewBox="0 0 512 512" fill="none" xmlns="http://www.w3.org/2000/svg">
 2 |   <!-- Background fills entire canvas - iOS will handle corner rounding -->
 3 |   <rect width="512" height="512" fill="hsl(240 5.9% 10%)"/>
 4 |   
 5 |   <!-- MessageSquare icon - scaled and centered -->
 6 |   <path d="M128 144C128 126.327 142.327 112 160 112H352C369.673 112 384 126.327 384 144V272C384 289.673 369.673 304 352 304H224L128 400V144Z" 
 7 |         stroke="white" 
 8 |         stroke-width="32" 
 9 |         stroke-linecap="round" 
10 |         stroke-linejoin="round" 
11 |         fill="none"/>
12 | </svg>


--------------------------------------------------------------------------------
/public/icons/icon-template.svg:
--------------------------------------------------------------------------------
 1 | <svg width="512" height="512" viewBox="0 0 512 512" fill="none" xmlns="http://www.w3.org/2000/svg">
 2 |   <!-- Background fills entire canvas - iOS will handle corner rounding -->
 3 |   <rect width="512" height="512" fill="hsl(240 5.9% 10%)"/>
 4 |   
 5 |   <!-- MessageSquare icon - scaled and centered -->
 6 |   <path d="M128 144C128 126.327 142.327 112 160 112H352C369.673 112 384 126.327 384 144V272C384 289.673 369.673 304 352 304H224L128 400V144Z" 
 7 |         stroke="white" 
 8 |         stroke-width="32" 
 9 |         stroke-linecap="round" 
10 |         stroke-linejoin="round" 
11 |         fill="none"/>
12 | </svg>


--------------------------------------------------------------------------------
/public/logo.svg:
--------------------------------------------------------------------------------
1 | <svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
2 |   <rect width="32" height="32" rx="8" fill="hsl(262.1 83.3% 57.8%)"/>
3 |   <path d="M8 9C8 8.44772 8.44772 8 9 8H23C23.5523 8 24 8.44772 24 9V18C24 18.5523 23.5523 19 23 19H12L8 23V9Z" 
4 |         stroke="white" 
5 |         stroke-width="2" 
6 |         stroke-linecap="round" 
7 |         stroke-linejoin="round" 
8 |         fill="none"/>
9 | </svg>


--------------------------------------------------------------------------------
/public/manifest.json:
--------------------------------------------------------------------------------
 1 | {
 2 |   "name": "Claude Code UI",
 3 |   "short_name": "Claude UI",
 4 |   "description": "Claude Code UI web application",
 5 |   "start_url": "/",
 6 |   "display": "standalone",
 7 |   "background_color": "#ffffff",
 8 |   "theme_color": "#ffffff",
 9 |   "orientation": "portrait-primary",
10 |   "scope": "/",
11 |   "icons": [
12 |     {
13 |       "src": "/icons/icon-72x72.png",
14 |       "sizes": "72x72",
15 |       "type": "image/png",
16 |       "purpose": "maskable any"
17 |     },
18 |     {
19 |       "src": "/icons/icon-96x96.png",
20 |       "sizes": "96x96",
21 |       "type": "image/png",
22 |       "purpose": "maskable any"
23 |     },
24 |     {
25 |       "src": "/icons/icon-128x128.png",
26 |       "sizes": "128x128",
27 |       "type": "image/png",
28 |       "purpose": "maskable any"
29 |     },
30 |     {
31 |       "src": "/icons/icon-144x144.png",
32 |       "sizes": "144x144",
33 |       "type": "image/png",
34 |       "purpose": "maskable any"
35 |     },
36 |     {
37 |       "src": "/icons/icon-152x152.png",
38 |       "sizes": "152x152",
39 |       "type": "image/png",
40 |       "purpose": "maskable any"
41 |     },
42 |     {
43 |       "src": "/icons/icon-192x192.png",
44 |       "sizes": "192x192",
45 |       "type": "image/png",
46 |       "purpose": "maskable any"
47 |     },
48 |     {
49 |       "src": "/icons/icon-384x384.png",
50 |       "sizes": "384x384",
51 |       "type": "image/png",
52 |       "purpose": "maskable any"
53 |     },
54 |     {
55 |       "src": "/icons/icon-512x512.png",
56 |       "sizes": "512x512",
57 |       "type": "image/png",
58 |       "purpose": "maskable any"
59 |     }
60 |   ]
61 | }


--------------------------------------------------------------------------------
/public/screenshots/cli-selection.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/screenshots/cli-selection.png


--------------------------------------------------------------------------------
/public/screenshots/desktop-main.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/screenshots/desktop-main.png


--------------------------------------------------------------------------------
/public/screenshots/mobile-chat.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/screenshots/mobile-chat.png


--------------------------------------------------------------------------------
/public/screenshots/tools-modal.png:
--------------------------------------------------------------------------------
https://raw.githubusercontent.com/siteboon/claudecodeui/e5709d71e055d3835ab71e12291359a9a19436b4/public/screenshots/tools-modal.png


--------------------------------------------------------------------------------
/public/sw.js:
--------------------------------------------------------------------------------
 1 | // Service Worker for Claude Code UI PWA
 2 | const CACHE_NAME = 'claude-ui-v1';
 3 | const urlsToCache = [
 4 |   '/',
 5 |   '/index.html',
 6 |   '/manifest.json'
 7 | ];
 8 | 
 9 | // Install event
10 | self.addEventListener('install', event => {
11 |   event.waitUntil(
12 |     caches.open(CACHE_NAME)
13 |       .then(cache => {
14 |         return cache.addAll(urlsToCache);
15 |       })
16 |   );
17 |   self.skipWaiting();
18 | });
19 | 
20 | // Fetch event
21 | self.addEventListener('fetch', event => {
22 |   event.respondWith(
23 |     caches.match(event.request)
24 |       .then(response => {
25 |         // Return cached response if found
26 |         if (response) {
27 |           return response;
28 |         }
29 |         // Otherwise fetch from network
30 |         return fetch(event.request);
31 |       }
32 |     )
33 |   );
34 | });
35 | 
36 | // Activate event
37 | self.addEventListener('activate', event => {
38 |   event.waitUntil(
39 |     caches.keys().then(cacheNames => {
40 |       return Promise.all(
41 |         cacheNames.map(cacheName => {
42 |           if (cacheName !== CACHE_NAME) {
43 |             return caches.delete(cacheName);
44 |           }
45 |         })
46 |       );
47 |     })
48 |   );
49 | });


--------------------------------------------------------------------------------
/server/cursor-cli.js:
--------------------------------------------------------------------------------
  1 | import { spawn } from 'child_process';
  2 | import crossSpawn from 'cross-spawn';
  3 | import { promises as fs } from 'fs';
  4 | import path from 'path';
  5 | import os from 'os';
  6 | 
  7 | // Use cross-spawn on Windows for better command execution
  8 | const spawnFunction = process.platform === 'win32' ? crossSpawn : spawn;
  9 | 
 10 | let activeCursorProcesses = new Map(); // Track active processes by session ID
 11 | 
 12 | async function spawnCursor(command, options = {}, ws) {
 13 |   return new Promise(async (resolve, reject) => {
 14 |     const { sessionId, projectPath, cwd, resume, toolsSettings, skipPermissions, model, images } = options;
 15 |     let capturedSessionId = sessionId; // Track session ID throughout the process
 16 |     let sessionCreatedSent = false; // Track if we've already sent session-created event
 17 |     let messageBuffer = ''; // Buffer for accumulating assistant messages
 18 |     
 19 |     // Use tools settings passed from frontend, or defaults
 20 |     const settings = toolsSettings || {
 21 |       allowedShellCommands: [],
 22 |       skipPermissions: false
 23 |     };
 24 |     
 25 |     // Build Cursor CLI command
 26 |     const args = [];
 27 |     
 28 |     // Build flags allowing both resume and prompt together (reply in existing session)
 29 |     // Treat presence of sessionId as intention to resume, regardless of resume flag
 30 |     if (sessionId) {
 31 |       args.push('--resume=' + sessionId);
 32 |     }
 33 | 
 34 |     if (command && command.trim()) {
 35 |       // Provide a prompt (works for both new and resumed sessions)
 36 |       args.push('-p', command);
 37 | 
 38 |       // Add model flag if specified (only meaningful for new sessions; harmless on resume)
 39 |       if (!sessionId && model) {
 40 |         args.push('--model', model);
 41 |       }
 42 | 
 43 |       // Request streaming JSON when we are providing a prompt
 44 |       args.push('--output-format', 'stream-json');
 45 |     }
 46 |     
 47 |     // Add skip permissions flag if enabled
 48 |     if (skipPermissions || settings.skipPermissions) {
 49 |       args.push('-f');
 50 |       console.log('⚠️  Using -f flag (skip permissions)');
 51 |     }
 52 |     
 53 |     // Use cwd (actual project directory) instead of projectPath
 54 |     const workingDir = cwd || projectPath || process.cwd();
 55 |     
 56 |     console.log('Spawning Cursor CLI:', 'cursor-agent', args.join(' '));
 57 |     console.log('Working directory:', workingDir);
 58 |     console.log('Session info - Input sessionId:', sessionId, 'Resume:', resume);
 59 |     
 60 |     const cursorProcess = spawnFunction('cursor-agent', args, {
 61 |       cwd: workingDir,
 62 |       stdio: ['pipe', 'pipe', 'pipe'],
 63 |       env: { ...process.env } // Inherit all environment variables
 64 |     });
 65 |     
 66 |     // Store process reference for potential abort
 67 |     const processKey = capturedSessionId || Date.now().toString();
 68 |     activeCursorProcesses.set(processKey, cursorProcess);
 69 |     
 70 |     // Handle stdout (streaming JSON responses)
 71 |     cursorProcess.stdout.on('data', (data) => {
 72 |       const rawOutput = data.toString();
 73 |       console.log('📤 Cursor CLI stdout:', rawOutput);
 74 |       
 75 |       const lines = rawOutput.split('\n').filter(line => line.trim());
 76 |       
 77 |       for (const line of lines) {
 78 |         try {
 79 |           const response = JSON.parse(line);
 80 |           console.log('📄 Parsed JSON response:', response);
 81 |           
 82 |           // Handle different message types
 83 |           switch (response.type) {
 84 |             case 'system':
 85 |               if (response.subtype === 'init') {
 86 |                 // Capture session ID
 87 |                 if (response.session_id && !capturedSessionId) {
 88 |                   capturedSessionId = response.session_id;
 89 |                   console.log('📝 Captured session ID:', capturedSessionId);
 90 |                   
 91 |                   // Update process key with captured session ID
 92 |                   if (processKey !== capturedSessionId) {
 93 |                     activeCursorProcesses.delete(processKey);
 94 |                     activeCursorProcesses.set(capturedSessionId, cursorProcess);
 95 |                   }
 96 |                   
 97 |                   // Send session-created event only once for new sessions
 98 |                   if (!sessionId && !sessionCreatedSent) {
 99 |                     sessionCreatedSent = true;
100 |                     ws.send(JSON.stringify({
101 |                       type: 'session-created',
102 |                       sessionId: capturedSessionId,
103 |                       model: response.model,
104 |                       cwd: response.cwd
105 |                     }));
106 |                   }
107 |                 }
108 |                 
109 |                 // Send system info to frontend
110 |                 ws.send(JSON.stringify({
111 |                   type: 'cursor-system',
112 |                   data: response
113 |                 }));
114 |               }
115 |               break;
116 |               
117 |             case 'user':
118 |               // Forward user message
119 |               ws.send(JSON.stringify({
120 |                 type: 'cursor-user',
121 |                 data: response
122 |               }));
123 |               break;
124 |               
125 |             case 'assistant':
126 |               // Accumulate assistant message chunks
127 |               if (response.message && response.message.content && response.message.content.length > 0) {
128 |                 const textContent = response.message.content[0].text;
129 |                 messageBuffer += textContent;
130 |                 
131 |                 // Send as Claude-compatible format for frontend
132 |                 ws.send(JSON.stringify({
133 |                   type: 'claude-response',
134 |                   data: {
135 |                     type: 'content_block_delta',
136 |                     delta: {
137 |                       type: 'text_delta',
138 |                       text: textContent
139 |                     }
140 |                   }
141 |                 }));
142 |               }
143 |               break;
144 |               
145 |             case 'result':
146 |               // Session complete
147 |               console.log('Cursor session result:', response);
148 |               
149 |               // Send final message if we have buffered content
150 |               if (messageBuffer) {
151 |                 ws.send(JSON.stringify({
152 |                   type: 'claude-response',
153 |                   data: {
154 |                     type: 'content_block_stop'
155 |                   }
156 |                 }));
157 |               }
158 |               
159 |               // Send completion event
160 |               ws.send(JSON.stringify({
161 |                 type: 'cursor-result',
162 |                 data: response,
163 |                 success: response.subtype === 'success'
164 |               }));
165 |               break;
166 |               
167 |             default:
168 |               // Forward any other message types
169 |               ws.send(JSON.stringify({
170 |                 type: 'cursor-response',
171 |                 data: response
172 |               }));
173 |           }
174 |         } catch (parseError) {
175 |           console.log('📄 Non-JSON response:', line);
176 |           // If not JSON, send as raw text
177 |           ws.send(JSON.stringify({
178 |             type: 'cursor-output',
179 |             data: line
180 |           }));
181 |         }
182 |       }
183 |     });
184 |     
185 |     // Handle stderr
186 |     cursorProcess.stderr.on('data', (data) => {
187 |       console.error('Cursor CLI stderr:', data.toString());
188 |       ws.send(JSON.stringify({
189 |         type: 'cursor-error',
190 |         error: data.toString()
191 |       }));
192 |     });
193 |     
194 |     // Handle process completion
195 |     cursorProcess.on('close', async (code) => {
196 |       console.log(`Cursor CLI process exited with code ${code}`);
197 |       
198 |       // Clean up process reference
199 |       const finalSessionId = capturedSessionId || sessionId || processKey;
200 |       activeCursorProcesses.delete(finalSessionId);
201 |       
202 |       ws.send(JSON.stringify({
203 |         type: 'claude-complete',
204 |         exitCode: code,
205 |         isNewSession: !sessionId && !!command // Flag to indicate this was a new session
206 |       }));
207 |       
208 |       if (code === 0) {
209 |         resolve();
210 |       } else {
211 |         reject(new Error(`Cursor CLI exited with code ${code}`));
212 |       }
213 |     });
214 |     
215 |     // Handle process errors
216 |     cursorProcess.on('error', (error) => {
217 |       console.error('Cursor CLI process error:', error);
218 |       
219 |       // Clean up process reference on error
220 |       const finalSessionId = capturedSessionId || sessionId || processKey;
221 |       activeCursorProcesses.delete(finalSessionId);
222 |       
223 |       ws.send(JSON.stringify({
224 |         type: 'cursor-error',
225 |         error: error.message
226 |       }));
227 |       
228 |       reject(error);
229 |     });
230 |     
231 |     // Close stdin since Cursor doesn't need interactive input
232 |     cursorProcess.stdin.end();
233 |   });
234 | }
235 | 
236 | function abortCursorSession(sessionId) {
237 |   const process = activeCursorProcesses.get(sessionId);
238 |   if (process) {
239 |     console.log(`🛑 Aborting Cursor session: ${sessionId}`);
240 |     process.kill('SIGTERM');
241 |     activeCursorProcesses.delete(sessionId);
242 |     return true;
243 |   }
244 |   return false;
245 | }
246 | 
247 | export {
248 |   spawnCursor,
249 |   abortCursorSession
250 | };


--------------------------------------------------------------------------------
/server/database/db.js:
--------------------------------------------------------------------------------
 1 | import Database from 'better-sqlite3';
 2 | import path from 'path';
 3 | import fs from 'fs';
 4 | import { fileURLToPath } from 'url';
 5 | import { dirname } from 'path';
 6 | 
 7 | const __filename = fileURLToPath(import.meta.url);
 8 | const __dirname = dirname(__filename);
 9 | 
10 | const DB_PATH = path.join(__dirname, 'auth.db');
11 | const INIT_SQL_PATH = path.join(__dirname, 'init.sql');
12 | 
13 | // Create database connection
14 | const db = new Database(DB_PATH);
15 | console.log('Connected to SQLite database');
16 | 
17 | // Initialize database with schema
18 | const initializeDatabase = async () => {
19 |   try {
20 |     const initSQL = fs.readFileSync(INIT_SQL_PATH, 'utf8');
21 |     db.exec(initSQL);
22 |     console.log('Database initialized successfully');
23 |   } catch (error) {
24 |     console.error('Error initializing database:', error.message);
25 |     throw error;
26 |   }
27 | };
28 | 
29 | // User database operations
30 | const userDb = {
31 |   // Check if any users exist
32 |   hasUsers: () => {
33 |     try {
34 |       const row = db.prepare('SELECT COUNT(*) as count FROM users').get();
35 |       return row.count > 0;
36 |     } catch (err) {
37 |       throw err;
38 |     }
39 |   },
40 | 
41 |   // Create a new user
42 |   createUser: (username, passwordHash) => {
43 |     try {
44 |       const stmt = db.prepare('INSERT INTO users (username, password_hash) VALUES (?, ?)');
45 |       const result = stmt.run(username, passwordHash);
46 |       return { id: result.lastInsertRowid, username };
47 |     } catch (err) {
48 |       throw err;
49 |     }
50 |   },
51 | 
52 |   // Get user by username
53 |   getUserByUsername: (username) => {
54 |     try {
55 |       const row = db.prepare('SELECT * FROM users WHERE username = ? AND is_active = 1').get(username);
56 |       return row;
57 |     } catch (err) {
58 |       throw err;
59 |     }
60 |   },
61 | 
62 |   // Update last login time
63 |   updateLastLogin: (userId) => {
64 |     try {
65 |       db.prepare('UPDATE users SET last_login = CURRENT_TIMESTAMP WHERE id = ?').run(userId);
66 |     } catch (err) {
67 |       throw err;
68 |     }
69 |   },
70 | 
71 |   // Get user by ID
72 |   getUserById: (userId) => {
73 |     try {
74 |       const row = db.prepare('SELECT id, username, created_at, last_login FROM users WHERE id = ? AND is_active = 1').get(userId);
75 |       return row;
76 |     } catch (err) {
77 |       throw err;
78 |     }
79 |   }
80 | };
81 | 
82 | export {
83 |   db,
84 |   initializeDatabase,
85 |   userDb
86 | };


--------------------------------------------------------------------------------
/server/database/init.sql:
--------------------------------------------------------------------------------
 1 | -- Initialize authentication database
 2 | PRAGMA foreign_keys = ON;
 3 | 
 4 | -- Users table (single user system)
 5 | CREATE TABLE IF NOT EXISTS users (
 6 |     id INTEGER PRIMARY KEY AUTOINCREMENT,
 7 |     username TEXT UNIQUE NOT NULL,
 8 |     password_hash TEXT NOT NULL,
 9 |     created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
10 |     last_login DATETIME,
11 |     is_active BOOLEAN DEFAULT 1
12 | );
13 | 
14 | -- Indexes for performance
15 | CREATE INDEX IF NOT EXISTS idx_users_username ON users(username);
16 | CREATE INDEX IF NOT EXISTS idx_users_active ON users(is_active);


--------------------------------------------------------------------------------
/server/middleware/auth.js:
--------------------------------------------------------------------------------
 1 | import jwt from 'jsonwebtoken';
 2 | import { userDb } from '../database/db.js';
 3 | 
 4 | // Get JWT secret from environment or use default (for development)
 5 | const JWT_SECRET = process.env.JWT_SECRET || 'claude-ui-dev-secret-change-in-production';
 6 | 
 7 | // Optional API key middleware
 8 | const validateApiKey = (req, res, next) => {
 9 |   // Skip API key validation if not configured
10 |   if (!process.env.API_KEY) {
11 |     return next();
12 |   }
13 |   
14 |   const apiKey = req.headers['x-api-key'];
15 |   if (apiKey !== process.env.API_KEY) {
16 |     return res.status(401).json({ error: 'Invalid API key' });
17 |   }
18 |   next();
19 | };
20 | 
21 | // JWT authentication middleware
22 | const authenticateToken = async (req, res, next) => {
23 |   const authHeader = req.headers['authorization'];
24 |   const token = authHeader && authHeader.split(' ')[1]; // Bearer TOKEN
25 | 
26 |   if (!token) {
27 |     return res.status(401).json({ error: 'Access denied. No token provided.' });
28 |   }
29 | 
30 |   try {
31 |     const decoded = jwt.verify(token, JWT_SECRET);
32 |     
33 |     // Verify user still exists and is active
34 |     const user = userDb.getUserById(decoded.userId);
35 |     if (!user) {
36 |       return res.status(401).json({ error: 'Invalid token. User not found.' });
37 |     }
38 |     
39 |     req.user = user;
40 |     next();
41 |   } catch (error) {
42 |     console.error('Token verification error:', error);
43 |     return res.status(403).json({ error: 'Invalid token' });
44 |   }
45 | };
46 | 
47 | // Generate JWT token (never expires)
48 | const generateToken = (user) => {
49 |   return jwt.sign(
50 |     { 
51 |       userId: user.id, 
52 |       username: user.username 
53 |     },
54 |     JWT_SECRET
55 |     // No expiration - token lasts forever
56 |   );
57 | };
58 | 
59 | // WebSocket authentication function
60 | const authenticateWebSocket = (token) => {
61 |   if (!token) {
62 |     return null;
63 |   }
64 |   
65 |   try {
66 |     const decoded = jwt.verify(token, JWT_SECRET);
67 |     return decoded;
68 |   } catch (error) {
69 |     console.error('WebSocket token verification error:', error);
70 |     return null;
71 |   }
72 | };
73 | 
74 | export {
75 |   validateApiKey,
76 |   authenticateToken,
77 |   generateToken,
78 |   authenticateWebSocket,
79 |   JWT_SECRET
80 | };


--------------------------------------------------------------------------------
/server/routes/auth.js:
--------------------------------------------------------------------------------
  1 | import express from 'express';
  2 | import bcrypt from 'bcrypt';
  3 | import { userDb, db } from '../database/db.js';
  4 | import { generateToken, authenticateToken } from '../middleware/auth.js';
  5 | 
  6 | const router = express.Router();
  7 | 
  8 | // Check auth status and setup requirements
  9 | router.get('/status', async (req, res) => {
 10 |   try {
 11 |     const hasUsers = await userDb.hasUsers();
 12 |     res.json({ 
 13 |       needsSetup: !hasUsers,
 14 |       isAuthenticated: false // Will be overridden by frontend if token exists
 15 |     });
 16 |   } catch (error) {
 17 |     console.error('Auth status error:', error);
 18 |     res.status(500).json({ error: 'Internal server error' });
 19 |   }
 20 | });
 21 | 
 22 | // User registration (setup) - only allowed if no users exist
 23 | router.post('/register', async (req, res) => {
 24 |   try {
 25 |     const { username, password } = req.body;
 26 |     
 27 |     // Validate input
 28 |     if (!username || !password) {
 29 |       return res.status(400).json({ error: 'Username and password are required' });
 30 |     }
 31 |     
 32 |     if (username.length < 3 || password.length < 6) {
 33 |       return res.status(400).json({ error: 'Username must be at least 3 characters, password at least 6 characters' });
 34 |     }
 35 |     
 36 |     // Use a transaction to prevent race conditions
 37 |     db.prepare('BEGIN').run();
 38 |     try {
 39 |       // Check if users already exist (only allow one user)
 40 |       const hasUsers = userDb.hasUsers();
 41 |       if (hasUsers) {
 42 |         db.prepare('ROLLBACK').run();
 43 |         return res.status(403).json({ error: 'User already exists. This is a single-user system.' });
 44 |       }
 45 |       
 46 |       // Hash password
 47 |       const saltRounds = 12;
 48 |       const passwordHash = await bcrypt.hash(password, saltRounds);
 49 |       
 50 |       // Create user
 51 |       const user = userDb.createUser(username, passwordHash);
 52 |       
 53 |       // Generate token
 54 |       const token = generateToken(user);
 55 |       
 56 |       // Update last login
 57 |       userDb.updateLastLogin(user.id);
 58 | 
 59 |       db.prepare('COMMIT').run();
 60 |       
 61 |       res.json({
 62 |         success: true,
 63 |         user: { id: user.id, username: user.username },
 64 |         token
 65 |       });
 66 |     } catch (error) {
 67 |       db.prepare('ROLLBACK').run();
 68 |       throw error;
 69 |     }
 70 |     
 71 |   } catch (error) {
 72 |     console.error('Registration error:', error);
 73 |     if (error.code === 'SQLITE_CONSTRAINT_UNIQUE') {
 74 |       res.status(409).json({ error: 'Username already exists' });
 75 |     } else {
 76 |       res.status(500).json({ error: 'Internal server error' });
 77 |     }
 78 |   }
 79 | });
 80 | 
 81 | // User login
 82 | router.post('/login', async (req, res) => {
 83 |   try {
 84 |     const { username, password } = req.body;
 85 |     
 86 |     // Validate input
 87 |     if (!username || !password) {
 88 |       return res.status(400).json({ error: 'Username and password are required' });
 89 |     }
 90 |     
 91 |     // Get user from database
 92 |     const user = userDb.getUserByUsername(username);
 93 |     if (!user) {
 94 |       return res.status(401).json({ error: 'Invalid username or password' });
 95 |     }
 96 |     
 97 |     // Verify password
 98 |     const isValidPassword = await bcrypt.compare(password, user.password_hash);
 99 |     if (!isValidPassword) {
100 |       return res.status(401).json({ error: 'Invalid username or password' });
101 |     }
102 |     
103 |     // Generate token
104 |     const token = generateToken(user);
105 |     
106 |     // Update last login
107 |     userDb.updateLastLogin(user.id);
108 |     
109 |     res.json({
110 |       success: true,
111 |       user: { id: user.id, username: user.username },
112 |       token
113 |     });
114 |     
115 |   } catch (error) {
116 |     console.error('Login error:', error);
117 |     res.status(500).json({ error: 'Internal server error' });
118 |   }
119 | });
120 | 
121 | // Get current user (protected route)
122 | router.get('/user', authenticateToken, (req, res) => {
123 |   res.json({
124 |     user: req.user
125 |   });
126 | });
127 | 
128 | // Logout (client-side token removal, but this endpoint can be used for logging)
129 | router.post('/logout', authenticateToken, (req, res) => {
130 |   // In a simple JWT system, logout is mainly client-side
131 |   // This endpoint exists for consistency and potential future logging
132 |   res.json({ success: true, message: 'Logged out successfully' });
133 | });
134 | 
135 | export default router;


--------------------------------------------------------------------------------
/server/routes/mcp-utils.js:
--------------------------------------------------------------------------------
 1 | /**
 2 |  * MCP UTILITIES API ROUTES
 3 |  * ========================
 4 |  * 
 5 |  * API endpoints for MCP server detection and configuration utilities.
 6 |  * These endpoints expose centralized MCP detection functionality.
 7 |  */
 8 | 
 9 | import express from 'express';
10 | import { detectTaskMasterMCPServer, getAllMCPServers } from '../utils/mcp-detector.js';
11 | 
12 | const router = express.Router();
13 | 
14 | /**
15 |  * GET /api/mcp-utils/taskmaster-server
16 |  * Check if TaskMaster MCP server is configured
17 |  */
18 | router.get('/taskmaster-server', async (req, res) => {
19 |     try {
20 |         const result = await detectTaskMasterMCPServer();
21 |         res.json(result);
22 |     } catch (error) {
23 |         console.error('TaskMaster MCP detection error:', error);
24 |         res.status(500).json({
25 |             error: 'Failed to detect TaskMaster MCP server',
26 |             message: error.message
27 |         });
28 |     }
29 | });
30 | 
31 | /**
32 |  * GET /api/mcp-utils/all-servers
33 |  * Get all configured MCP servers
34 |  */
35 | router.get('/all-servers', async (req, res) => {
36 |     try {
37 |         const result = await getAllMCPServers();
38 |         res.json(result);
39 |     } catch (error) {
40 |         console.error('MCP servers detection error:', error);
41 |         res.status(500).json({
42 |             error: 'Failed to get MCP servers',
43 |             message: error.message
44 |         });
45 |     }
46 | });
47 | 
48 | export default router;


--------------------------------------------------------------------------------
/server/utils/mcp-detector.js:
--------------------------------------------------------------------------------
  1 | /**
  2 |  * MCP SERVER DETECTION UTILITY
  3 |  * ============================
  4 |  * 
  5 |  * Centralized utility for detecting MCP server configurations.
  6 |  * Used across TaskMaster integration and other MCP-dependent features.
  7 |  */
  8 | 
  9 | import { promises as fsPromises } from 'fs';
 10 | import path from 'path';
 11 | import os from 'os';
 12 | 
 13 | /**
 14 |  * Check if task-master-ai MCP server is configured
 15 |  * Reads directly from Claude configuration files like claude-cli.js does
 16 |  * @returns {Promise<Object>} MCP detection result
 17 |  */
 18 | export async function detectTaskMasterMCPServer() {
 19 |     try {
 20 |         // Read Claude configuration files directly (same logic as mcp.js)
 21 |         const homeDir = os.homedir();
 22 |         const configPaths = [
 23 |             path.join(homeDir, '.claude.json'),
 24 |             path.join(homeDir, '.claude', 'settings.json')
 25 |         ];
 26 |         
 27 |         let configData = null;
 28 |         let configPath = null;
 29 |         
 30 |         // Try to read from either config file
 31 |         for (const filepath of configPaths) {
 32 |             try {
 33 |                 const fileContent = await fsPromises.readFile(filepath, 'utf8');
 34 |                 configData = JSON.parse(fileContent);
 35 |                 configPath = filepath;
 36 |                 break;
 37 |             } catch (error) {
 38 |                 // File doesn't exist or is not valid JSON, try next
 39 |                 continue;
 40 |             }
 41 |         }
 42 |         
 43 |         if (!configData) {
 44 |             return {
 45 |                 hasMCPServer: false,
 46 |                 reason: 'No Claude configuration file found',
 47 |                 hasConfig: false
 48 |             };
 49 |         }
 50 | 
 51 |         // Look for task-master-ai in user-scoped MCP servers
 52 |         let taskMasterServer = null;
 53 |         if (configData.mcpServers && typeof configData.mcpServers === 'object') {
 54 |             const serverEntry = Object.entries(configData.mcpServers).find(([name, config]) => 
 55 |                 name === 'task-master-ai' || 
 56 |                 name.includes('task-master') ||
 57 |                 (config && config.command && config.command.includes('task-master'))
 58 |             );
 59 |             
 60 |             if (serverEntry) {
 61 |                 const [name, config] = serverEntry;
 62 |                 taskMasterServer = {
 63 |                     name,
 64 |                     scope: 'user',
 65 |                     config,
 66 |                     type: config.command ? 'stdio' : (config.url ? 'http' : 'unknown')
 67 |                 };
 68 |             }
 69 |         }
 70 | 
 71 |         // Also check project-specific MCP servers if not found globally
 72 |         if (!taskMasterServer && configData.projects) {
 73 |             for (const [projectPath, projectConfig] of Object.entries(configData.projects)) {
 74 |                 if (projectConfig.mcpServers && typeof projectConfig.mcpServers === 'object') {
 75 |                     const serverEntry = Object.entries(projectConfig.mcpServers).find(([name, config]) => 
 76 |                         name === 'task-master-ai' || 
 77 |                         name.includes('task-master') ||
 78 |                         (config && config.command && config.command.includes('task-master'))
 79 |                     );
 80 |                     
 81 |                     if (serverEntry) {
 82 |                         const [name, config] = serverEntry;
 83 |                         taskMasterServer = {
 84 |                             name,
 85 |                             scope: 'local',
 86 |                             projectPath,
 87 |                             config,
 88 |                             type: config.command ? 'stdio' : (config.url ? 'http' : 'unknown')
 89 |                         };
 90 |                         break;
 91 |                     }
 92 |                 }
 93 |             }
 94 |         }
 95 | 
 96 |         if (taskMasterServer) {
 97 |             const isValid = !!(taskMasterServer.config && 
 98 |                              (taskMasterServer.config.command || taskMasterServer.config.url));
 99 |             const hasEnvVars = !!(taskMasterServer.config && 
100 |                                 taskMasterServer.config.env && 
101 |                                 Object.keys(taskMasterServer.config.env).length > 0);
102 | 
103 |             return {
104 |                 hasMCPServer: true,
105 |                 isConfigured: isValid,
106 |                 hasApiKeys: hasEnvVars,
107 |                 scope: taskMasterServer.scope,
108 |                 config: {
109 |                     command: taskMasterServer.config?.command,
110 |                     args: taskMasterServer.config?.args || [],
111 |                     url: taskMasterServer.config?.url,
112 |                     envVars: hasEnvVars ? Object.keys(taskMasterServer.config.env) : [],
113 |                     type: taskMasterServer.type
114 |                 }
115 |             };
116 |         } else {
117 |             // Get list of available servers for debugging
118 |             const availableServers = [];
119 |             if (configData.mcpServers) {
120 |                 availableServers.push(...Object.keys(configData.mcpServers));
121 |             }
122 |             if (configData.projects) {
123 |                 for (const projectConfig of Object.values(configData.projects)) {
124 |                     if (projectConfig.mcpServers) {
125 |                         availableServers.push(...Object.keys(projectConfig.mcpServers).map(name => `local:${name}`));
126 |                     }
127 |                 }
128 |             }
129 | 
130 |             return {
131 |                 hasMCPServer: false,
132 |                 reason: 'task-master-ai not found in configured MCP servers',
133 |                 hasConfig: true,
134 |                 configPath,
135 |                 availableServers
136 |             };
137 |         }
138 |     } catch (error) {
139 |         console.error('Error detecting MCP server config:', error);
140 |         return {
141 |             hasMCPServer: false,
142 |             reason: `Error checking MCP config: ${error.message}`,
143 |             hasConfig: false
144 |         };
145 |     }
146 | }
147 | 
148 | /**
149 |  * Get all configured MCP servers (not just TaskMaster)
150 |  * @returns {Promise<Object>} All MCP servers configuration
151 |  */
152 | export async function getAllMCPServers() {
153 |     try {
154 |         const homeDir = os.homedir();
155 |         const configPaths = [
156 |             path.join(homeDir, '.claude.json'),
157 |             path.join(homeDir, '.claude', 'settings.json')
158 |         ];
159 |         
160 |         let configData = null;
161 |         let configPath = null;
162 |         
163 |         // Try to read from either config file
164 |         for (const filepath of configPaths) {
165 |             try {
166 |                 const fileContent = await fsPromises.readFile(filepath, 'utf8');
167 |                 configData = JSON.parse(fileContent);
168 |                 configPath = filepath;
169 |                 break;
170 |             } catch (error) {
171 |                 continue;
172 |             }
173 |         }
174 |         
175 |         if (!configData) {
176 |             return {
177 |                 hasConfig: false,
178 |                 servers: {},
179 |                 projectServers: {}
180 |             };
181 |         }
182 | 
183 |         return {
184 |             hasConfig: true,
185 |             configPath,
186 |             servers: configData.mcpServers || {},
187 |             projectServers: configData.projects || {}
188 |         };
189 |     } catch (error) {
190 |         console.error('Error getting all MCP servers:', error);
191 |         return {
192 |             hasConfig: false,
193 |             error: error.message,
194 |             servers: {},
195 |             projectServers: {}
196 |         };
197 |     }
198 | }


--------------------------------------------------------------------------------
/server/utils/taskmaster-websocket.js:
--------------------------------------------------------------------------------
  1 | /**
  2 |  * TASKMASTER WEBSOCKET UTILITIES
  3 |  * ==============================
  4 |  * 
  5 |  * Utilities for broadcasting TaskMaster state changes via WebSocket.
  6 |  * Integrates with the existing WebSocket system to provide real-time updates.
  7 |  */
  8 | 
  9 | /**
 10 |  * Broadcast TaskMaster project update to all connected clients
 11 |  * @param {WebSocket.Server} wss - WebSocket server instance
 12 |  * @param {string} projectName - Name of the updated project
 13 |  * @param {Object} taskMasterData - Updated TaskMaster data
 14 |  */
 15 | export function broadcastTaskMasterProjectUpdate(wss, projectName, taskMasterData) {
 16 |     if (!wss || !projectName) {
 17 |         console.warn('TaskMaster WebSocket broadcast: Missing wss or projectName');
 18 |         return;
 19 |     }
 20 | 
 21 |     const message = {
 22 |         type: 'taskmaster-project-updated',
 23 |         projectName,
 24 |         taskMasterData,
 25 |         timestamp: new Date().toISOString()
 26 |     };
 27 | 
 28 |     
 29 |     wss.clients.forEach((client) => {
 30 |         if (client.readyState === 1) { // WebSocket.OPEN
 31 |             try {
 32 |                 client.send(JSON.stringify(message));
 33 |             } catch (error) {
 34 |                 console.error('Error sending TaskMaster project update:', error);
 35 |             }
 36 |         }
 37 |     });
 38 | }
 39 | 
 40 | /**
 41 |  * Broadcast TaskMaster tasks update for a specific project
 42 |  * @param {WebSocket.Server} wss - WebSocket server instance  
 43 |  * @param {string} projectName - Name of the project with updated tasks
 44 |  * @param {Object} tasksData - Updated tasks data
 45 |  */
 46 | export function broadcastTaskMasterTasksUpdate(wss, projectName, tasksData) {
 47 |     if (!wss || !projectName) {
 48 |         console.warn('TaskMaster WebSocket broadcast: Missing wss or projectName');
 49 |         return;
 50 |     }
 51 | 
 52 |     const message = {
 53 |         type: 'taskmaster-tasks-updated',
 54 |         projectName,
 55 |         tasksData,
 56 |         timestamp: new Date().toISOString()
 57 |     };
 58 | 
 59 |     
 60 |     wss.clients.forEach((client) => {
 61 |         if (client.readyState === 1) { // WebSocket.OPEN
 62 |             try {
 63 |                 client.send(JSON.stringify(message));
 64 |             } catch (error) {
 65 |                 console.error('Error sending TaskMaster tasks update:', error);
 66 |             }
 67 |         }
 68 |     });
 69 | }
 70 | 
 71 | /**
 72 |  * Broadcast MCP server status change
 73 |  * @param {WebSocket.Server} wss - WebSocket server instance
 74 |  * @param {Object} mcpStatus - Updated MCP server status
 75 |  */
 76 | export function broadcastMCPStatusChange(wss, mcpStatus) {
 77 |     if (!wss) {
 78 |         console.warn('TaskMaster WebSocket broadcast: Missing wss');
 79 |         return;
 80 |     }
 81 | 
 82 |     const message = {
 83 |         type: 'taskmaster-mcp-status-changed',
 84 |         mcpStatus,
 85 |         timestamp: new Date().toISOString()
 86 |     };
 87 | 
 88 |     
 89 |     wss.clients.forEach((client) => {
 90 |         if (client.readyState === 1) { // WebSocket.OPEN
 91 |             try {
 92 |                 client.send(JSON.stringify(message));
 93 |             } catch (error) {
 94 |                 console.error('Error sending TaskMaster MCP status update:', error);
 95 |             }
 96 |         }
 97 |     });
 98 | }
 99 | 
100 | /**
101 |  * Broadcast general TaskMaster update notification
102 |  * @param {WebSocket.Server} wss - WebSocket server instance
103 |  * @param {string} updateType - Type of update (e.g., 'initialization', 'configuration')
104 |  * @param {Object} data - Additional data about the update
105 |  */
106 | export function broadcastTaskMasterUpdate(wss, updateType, data = {}) {
107 |     if (!wss || !updateType) {
108 |         console.warn('TaskMaster WebSocket broadcast: Missing wss or updateType');
109 |         return;
110 |     }
111 | 
112 |     const message = {
113 |         type: 'taskmaster-update',
114 |         updateType,
115 |         data,
116 |         timestamp: new Date().toISOString()
117 |     };
118 | 
119 |     
120 |     wss.clients.forEach((client) => {
121 |         if (client.readyState === 1) { // WebSocket.OPEN
122 |             try {
123 |                 client.send(JSON.stringify(message));
124 |             } catch (error) {
125 |                 console.error('Error sending TaskMaster update:', error);
126 |             }
127 |         }
128 |     });
129 | }


--------------------------------------------------------------------------------
/src/components/ClaudeLogo.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react';
 2 | 
 3 | const ClaudeLogo = ({className = 'w-5 h-5'}) => {
 4 |   return (
 5 |     <img src="/icons/claude-ai-icon.svg" alt="Claude" className={className} />
 6 |   );
 7 | };
 8 | 
 9 | export default ClaudeLogo;
10 | 
11 | 
12 | 


--------------------------------------------------------------------------------
/src/components/ClaudeStatus.jsx:
--------------------------------------------------------------------------------
  1 | import React, { useState, useEffect } from 'react';
  2 | import { cn } from '../lib/utils';
  3 | 
  4 | function ClaudeStatus({ status, onAbort, isLoading, provider = 'claude' }) {
  5 |   const [elapsedTime, setElapsedTime] = useState(0);
  6 |   const [animationPhase, setAnimationPhase] = useState(0);
  7 |   const [fakeTokens, setFakeTokens] = useState(0);
  8 |   
  9 |   // Update elapsed time every second
 10 |   useEffect(() => {
 11 |     if (!isLoading) {
 12 |       setElapsedTime(0);
 13 |       setFakeTokens(0);
 14 |       return;
 15 |     }
 16 |     
 17 |     const startTime = Date.now();
 18 |     const timer = setInterval(() => {
 19 |       const elapsed = Math.floor((Date.now() - startTime) / 1000);
 20 |       setElapsedTime(elapsed);
 21 |       // Simulate token count increasing over time (roughly 30-50 tokens per second)
 22 |       setFakeTokens(Math.floor(elapsed * (30 + Math.random() * 20)));
 23 |     }, 1000);
 24 |     
 25 |     return () => clearInterval(timer);
 26 |   }, [isLoading]);
 27 |   
 28 |   // Animate the status indicator
 29 |   useEffect(() => {
 30 |     if (!isLoading) return;
 31 |     
 32 |     const timer = setInterval(() => {
 33 |       setAnimationPhase(prev => (prev + 1) % 4);
 34 |     }, 500);
 35 |     
 36 |     return () => clearInterval(timer);
 37 |   }, [isLoading]);
 38 |   
 39 |   if (!isLoading) return null;
 40 |   
 41 |   // Clever action words that cycle
 42 |   const actionWords = ['Thinking', 'Processing', 'Analyzing', 'Working', 'Computing', 'Reasoning'];
 43 |   const actionIndex = Math.floor(elapsedTime / 3) % actionWords.length;
 44 |   
 45 |   // Parse status data
 46 |   const statusText = status?.text || actionWords[actionIndex];
 47 |   const tokens = status?.tokens || fakeTokens;
 48 |   const canInterrupt = status?.can_interrupt !== false;
 49 |   
 50 |   // Animation characters
 51 |   const spinners = ['✻', '✹', '✸', '✶'];
 52 |   const currentSpinner = spinners[animationPhase];
 53 |   
 54 |   return (
 55 |     <div className="w-full mb-6 animate-in slide-in-from-bottom duration-300">
 56 |       <div className="flex items-center justify-between max-w-4xl mx-auto bg-gray-900 dark:bg-gray-950 text-white rounded-lg shadow-lg px-4 py-3">
 57 |         <div className="flex-1">
 58 |           <div className="flex items-center gap-3">
 59 |             {/* Animated spinner */}
 60 |             <span className={cn(
 61 |               "text-xl transition-all duration-500",
 62 |               animationPhase % 2 === 0 ? "text-blue-400 scale-110" : "text-blue-300"
 63 |             )}>
 64 |               {currentSpinner}
 65 |             </span>
 66 |             
 67 |             {/* Status text - first line */}
 68 |             <div className="flex-1">
 69 |               <div className="flex items-center gap-2">
 70 |                 <span className="font-medium text-sm">{statusText}...</span>
 71 |                 <span className="text-gray-400 text-sm">({elapsedTime}s)</span>
 72 |                 {tokens > 0 && (
 73 |                   <>
 74 |                     <span className="text-gray-400">·</span>
 75 |                     <span className="text-gray-300 text-sm hidden sm:inline">⚒ {tokens.toLocaleString()} tokens</span>
 76 |                     <span className="text-gray-300 text-sm sm:hidden">⚒ {tokens.toLocaleString()}</span>
 77 |                   </>
 78 |                 )}
 79 |                 <span className="text-gray-400 hidden sm:inline">·</span>
 80 |                 <span className="text-gray-300 text-sm hidden sm:inline">esc to interrupt</span>
 81 |               </div>
 82 |               {/* Second line for mobile */}
 83 |               <div className="text-xs text-gray-400 sm:hidden mt-1">
 84 |                 esc to interrupt
 85 |               </div>
 86 |             </div>
 87 |           </div>
 88 |         </div>
 89 |         
 90 |         {/* Interrupt button */}
 91 |         {canInterrupt && onAbort && (
 92 |           <button
 93 |             onClick={onAbort}
 94 |             className="ml-3 text-xs bg-red-600 hover:bg-red-700 text-white px-2.5 py-1 sm:px-3 sm:py-1.5 rounded-md transition-colors flex items-center gap-1.5 flex-shrink-0"
 95 |           >
 96 |             <svg className="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
 97 |               <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M6 18L18 6M6 6l12 12" />
 98 |             </svg>
 99 |             <span className="hidden sm:inline">Stop</span>
100 |           </button>
101 |         )}
102 |       </div>
103 |     </div>
104 |   );
105 | }
106 | 
107 | export default ClaudeStatus;


--------------------------------------------------------------------------------
/src/components/CreateTaskModal.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react';
 2 | import { X, Sparkles } from 'lucide-react';
 3 | 
 4 | const CreateTaskModal = ({ currentProject, onClose, onTaskCreated }) => {
 5 | 
 6 |   return (
 7 |     <div className="fixed inset-0 bg-black/50 backdrop-blur-sm flex items-center justify-center z-50 p-4">
 8 |       <div className="bg-white dark:bg-gray-800 rounded-lg shadow-xl w-full max-w-md border border-gray-200 dark:border-gray-700">
 9 |         {/* Header */}
10 |         <div className="flex items-center justify-between p-6 border-b border-gray-200 dark:border-gray-700">
11 |           <div className="flex items-center gap-3">
12 |             <div className="w-8 h-8 bg-blue-100 dark:bg-blue-900/50 rounded-lg flex items-center justify-center">
13 |               <Sparkles className="w-4 h-4 text-blue-600 dark:text-blue-400" />
14 |             </div>
15 |             <h3 className="text-lg font-semibold text-gray-900 dark:text-white">Create AI-Generated Task</h3>
16 |           </div>
17 |           <button
18 |             onClick={onClose}
19 |             className="p-2 text-gray-400 hover:text-gray-600 dark:hover:text-gray-300 rounded-md hover:bg-gray-100 dark:hover:bg-gray-700"
20 |           >
21 |             <X className="w-5 h-5" />
22 |           </button>
23 |         </div>
24 | 
25 |         {/* Content */}
26 |         <div className="p-6 space-y-6">
27 |           {/* AI-First Approach */}
28 |           <div className="bg-blue-50 dark:bg-blue-900/20 rounded-lg p-4 border border-blue-200 dark:border-blue-800">
29 |             <div className="flex items-start gap-3">
30 |               <div className="w-8 h-8 bg-blue-100 dark:bg-blue-900/50 rounded-lg flex items-center justify-center flex-shrink-0 mt-0.5">
31 |                 <Sparkles className="w-4 h-4 text-blue-600 dark:text-blue-400" />
32 |               </div>
33 |               <div className="flex-1">
34 |                 <h4 className="font-semibold text-blue-900 dark:text-blue-100 mb-2">
35 |                   💡 Pro Tip: Ask Claude Code Directly!
36 |                 </h4>
37 |                 <p className="text-sm text-blue-800 dark:text-blue-200 mb-3">
38 |                   You can simply ask Claude Code in the chat to create tasks for you. 
39 |                   The AI assistant will automatically generate detailed tasks with research-backed insights.
40 |                 </p>
41 |                 
42 |                 <div className="bg-white dark:bg-gray-800 rounded border border-blue-200 dark:border-blue-700 p-3 mb-3">
43 |                   <p className="text-xs font-medium text-gray-600 dark:text-gray-400 mb-1">Example:</p>
44 |                   <p className="text-sm text-gray-900 dark:text-white font-mono">
45 |                     "Please add a new task to implement user profile image uploads using Cloudinary, research the best approach."
46 |                   </p>
47 |                 </div>
48 |                 
49 |                 <p className="text-xs text-blue-700 dark:text-blue-300">
50 |                   <strong>This runs:</strong> <code className="bg-blue-100 dark:bg-blue-900/50 px-1 rounded text-xs">
51 |                     task-master add-task --prompt="Implement user profile image uploads using Cloudinary" --research
52 |                   </code>
53 |                 </p>
54 |               </div>
55 |             </div>
56 |           </div>
57 | 
58 |           {/* Learn More Link */}
59 |           <div className="text-center pt-4 border-t border-gray-200 dark:border-gray-700">
60 |             <p className="text-sm text-gray-600 dark:text-gray-400 mb-3">
61 |               For more examples and advanced usage patterns:
62 |             </p>
63 |             <a
64 |               href="https://github.com/eyaltoledano/claude-task-master/blob/main/docs/examples.md"
65 |               target="_blank"
66 |               rel="noopener noreferrer"
67 |               className="inline-block text-sm text-blue-600 dark:text-blue-400 hover:text-blue-700 dark:hover:text-blue-300 underline font-medium"
68 |             >
69 |               View TaskMaster Documentation →
70 |             </a>
71 |           </div>
72 | 
73 |           {/* Footer */}
74 |           <div className="pt-4">
75 |             <button
76 |               onClick={onClose}
77 |               className="w-full px-4 py-2 text-sm font-medium text-gray-700 dark:text-gray-300 bg-white dark:bg-gray-700 border border-gray-300 dark:border-gray-600 rounded-lg hover:bg-gray-50 dark:hover:bg-gray-600 transition-colors"
78 |             >
79 |               Got it, I'll ask Claude Code directly
80 |             </button>
81 |           </div>
82 |         </div>
83 |       </div>
84 |     </div>
85 |   );
86 | };
87 | 
88 | export default CreateTaskModal;


--------------------------------------------------------------------------------
/src/components/CursorLogo.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react';
 2 | 
 3 | const CursorLogo = ({ className = 'w-5 h-5' }) => {
 4 |   return (
 5 |     <img src="/icons/cursor.svg" alt="Cursor" className={className} />
 6 |   );
 7 | };
 8 | 
 9 | export default CursorLogo;
10 | 


--------------------------------------------------------------------------------
/src/components/DarkModeToggle.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react';
 2 | import { useTheme } from '../contexts/ThemeContext';
 3 | 
 4 | function DarkModeToggle() {
 5 |   const { isDarkMode, toggleDarkMode } = useTheme();
 6 | 
 7 |   return (
 8 |     <button
 9 |       onClick={toggleDarkMode}
10 |       className="relative inline-flex h-8 w-14 items-center rounded-full bg-gray-200 dark:bg-gray-700 transition-colors duration-200 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 dark:focus:ring-offset-gray-900"
11 |       role="switch"
12 |       aria-checked={isDarkMode}
13 |       aria-label="Toggle dark mode"
14 |     >
15 |       <span className="sr-only">Toggle dark mode</span>
16 |       <span
17 |         className={`${
18 |           isDarkMode ? 'translate-x-7' : 'translate-x-1'
19 |         } inline-block h-6 w-6 transform rounded-full bg-white shadow-lg transition-transform duration-200 flex items-center justify-center`}
20 |       >
21 |         {isDarkMode ? (
22 |           <svg className="w-3.5 h-3.5 text-gray-700" fill="none" viewBox="0 0 24 24" stroke="currentColor">
23 |             <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" />
24 |           </svg>
25 |         ) : (
26 |           <svg className="w-3.5 h-3.5 text-yellow-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
27 |             <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z" />
28 |           </svg>
29 |         )}
30 |       </span>
31 |     </button>
32 |   );
33 | }
34 | 
35 | export default DarkModeToggle;


--------------------------------------------------------------------------------
/src/components/ErrorBoundary.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react';
 2 | 
 3 | class ErrorBoundary extends React.Component {
 4 |   constructor(props) {
 5 |     super(props);
 6 |     this.state = { hasError: false, error: null, errorInfo: null };
 7 |   }
 8 | 
 9 |   static getDerivedStateFromError(error) {
10 |     // Update state so the next render will show the fallback UI
11 |     return { hasError: true };
12 |   }
13 | 
14 |   componentDidCatch(error, errorInfo) {
15 |     // Log the error details
16 |     console.error('ErrorBoundary caught an error:', error, errorInfo);
17 |     
18 |     // You can also log the error to an error reporting service here
19 |     this.setState({
20 |       error: error,
21 |       errorInfo: errorInfo
22 |     });
23 |   }
24 | 
25 |   render() {
26 |     if (this.state.hasError) {
27 |       // Fallback UI
28 |       return (
29 |         <div className="flex flex-col items-center justify-center p-8 text-center">
30 |           <div className="bg-red-50 border border-red-200 rounded-lg p-6 max-w-md">
31 |             <div className="flex items-center mb-4">
32 |               <div className="flex-shrink-0">
33 |                 <svg className="h-5 w-5 text-red-400" viewBox="0 0 20 20" fill="currentColor">
34 |                   <path fillRule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM8.707 7.293a1 1 0 00-1.414 1.414L8.586 10l-1.293 1.293a1 1 0 101.414 1.414L10 11.414l1.293 1.293a1 1 0 001.414-1.414L11.414 10l1.293-1.293a1 1 0 00-1.414-1.414L10 8.586 8.707 7.293z" clipRule="evenodd" />
35 |                 </svg>
36 |               </div>
37 |               <h3 className="ml-3 text-sm font-medium text-red-800">
38 |                 Something went wrong
39 |               </h3>
40 |             </div>
41 |             <div className="text-sm text-red-700">
42 |               <p className="mb-2">An error occurred while loading the chat interface.</p>
43 |               {this.props.showDetails && this.state.error && (
44 |                 <details className="mt-4">
45 |                   <summary className="cursor-pointer text-xs font-mono">Error Details</summary>
46 |                   <pre className="mt-2 text-xs bg-red-100 p-2 rounded overflow-auto max-h-40">
47 |                     {this.state.error.toString()}
48 |                     {this.state.errorInfo && this.state.errorInfo.componentStack}
49 |                   </pre>
50 |                 </details>
51 |               )}
52 |             </div>
53 |             <div className="mt-4">
54 |               <button
55 |                 onClick={() => {
56 |                   this.setState({ hasError: false, error: null, errorInfo: null });
57 |                   if (this.props.onRetry) this.props.onRetry();
58 |                 }}
59 |                 className="bg-red-600 text-white px-4 py-2 rounded text-sm hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-red-500"
60 |               >
61 |                 Try Again
62 |               </button>
63 |             </div>
64 |           </div>
65 |         </div>
66 |       );
67 |     }
68 | 
69 |     return this.props.children;
70 |   }
71 | }
72 | 
73 | export default ErrorBoundary;


--------------------------------------------------------------------------------
/src/components/FileTree.jsx:
--------------------------------------------------------------------------------
  1 | import React, { useState, useEffect } from 'react';
  2 | import { ScrollArea } from './ui/scroll-area';
  3 | import { Button } from './ui/button';
  4 | import { Folder, FolderOpen, File, FileText, FileCode, List, TableProperties, Eye } from 'lucide-react';
  5 | import { cn } from '../lib/utils';
  6 | import CodeEditor from './CodeEditor';
  7 | import ImageViewer from './ImageViewer';
  8 | import { api } from '../utils/api';
  9 | 
 10 | function FileTree({ selectedProject }) {
 11 |   const [files, setFiles] = useState([]);
 12 |   const [loading, setLoading] = useState(false);
 13 |   const [expandedDirs, setExpandedDirs] = useState(new Set());
 14 |   const [selectedFile, setSelectedFile] = useState(null);
 15 |   const [selectedImage, setSelectedImage] = useState(null);
 16 |   const [viewMode, setViewMode] = useState('detailed'); // 'simple', 'detailed', 'compact'
 17 | 
 18 |   useEffect(() => {
 19 |     if (selectedProject) {
 20 |       fetchFiles();
 21 |     }
 22 |   }, [selectedProject]);
 23 | 
 24 |   // Load view mode preference from localStorage
 25 |   useEffect(() => {
 26 |     const savedViewMode = localStorage.getItem('file-tree-view-mode');
 27 |     if (savedViewMode && ['simple', 'detailed', 'compact'].includes(savedViewMode)) {
 28 |       setViewMode(savedViewMode);
 29 |     }
 30 |   }, []);
 31 | 
 32 |   const fetchFiles = async () => {
 33 |     setLoading(true);
 34 |     try {
 35 |       const response = await api.getFiles(selectedProject.name);
 36 |       
 37 |       if (!response.ok) {
 38 |         const errorText = await response.text();
 39 |         console.error('❌ File fetch failed:', response.status, errorText);
 40 |         setFiles([]);
 41 |         return;
 42 |       }
 43 |       
 44 |       const data = await response.json();
 45 |       setFiles(data);
 46 |     } catch (error) {
 47 |       console.error('❌ Error fetching files:', error);
 48 |       setFiles([]);
 49 |     } finally {
 50 |       setLoading(false);
 51 |     }
 52 |   };
 53 | 
 54 |   const toggleDirectory = (path) => {
 55 |     const newExpanded = new Set(expandedDirs);
 56 |     if (newExpanded.has(path)) {
 57 |       newExpanded.delete(path);
 58 |     } else {
 59 |       newExpanded.add(path);
 60 |     }
 61 |     setExpandedDirs(newExpanded);
 62 |   };
 63 | 
 64 |   // Change view mode and save preference
 65 |   const changeViewMode = (mode) => {
 66 |     setViewMode(mode);
 67 |     localStorage.setItem('file-tree-view-mode', mode);
 68 |   };
 69 | 
 70 |   // Format file size
 71 |   const formatFileSize = (bytes) => {
 72 |     if (!bytes || bytes === 0) return '0 B';
 73 |     const k = 1024;
 74 |     const sizes = ['B', 'KB', 'MB', 'GB'];
 75 |     const i = Math.floor(Math.log(bytes) / Math.log(k));
 76 |     return parseFloat((bytes / Math.pow(k, i)).toFixed(1)) + ' ' + sizes[i];
 77 |   };
 78 | 
 79 |   // Format date as relative time
 80 |   const formatRelativeTime = (date) => {
 81 |     if (!date) return '-';
 82 |     const now = new Date();
 83 |     const past = new Date(date);
 84 |     const diffInSeconds = Math.floor((now - past) / 1000);
 85 |     
 86 |     if (diffInSeconds < 60) return 'just now';
 87 |     if (diffInSeconds < 3600) return `${Math.floor(diffInSeconds / 60)} min ago`;
 88 |     if (diffInSeconds < 86400) return `${Math.floor(diffInSeconds / 3600)} hours ago`;
 89 |     if (diffInSeconds < 2592000) return `${Math.floor(diffInSeconds / 86400)} days ago`;
 90 |     return past.toLocaleDateString();
 91 |   };
 92 | 
 93 |   const renderFileTree = (items, level = 0) => {
 94 |     return items.map((item) => (
 95 |       <div key={item.path} className="select-none">
 96 |         <Button
 97 |           variant="ghost"
 98 |           className={cn(
 99 |             "w-full justify-start p-2 h-auto font-normal text-left hover:bg-accent",
100 |           )}
101 |           style={{ paddingLeft: `${level * 16 + 12}px` }}
102 |           onClick={() => {
103 |             if (item.type === 'directory') {
104 |               toggleDirectory(item.path);
105 |             } else if (isImageFile(item.name)) {
106 |               // Open image in viewer
107 |               setSelectedImage({
108 |                 name: item.name,
109 |                 path: item.path,
110 |                 projectPath: selectedProject.path,
111 |                 projectName: selectedProject.name
112 |               });
113 |             } else {
114 |               // Open file in editor
115 |               setSelectedFile({
116 |                 name: item.name,
117 |                 path: item.path,
118 |                 projectPath: selectedProject.path,
119 |                 projectName: selectedProject.name
120 |               });
121 |             }
122 |           }}
123 |         >
124 |           <div className="flex items-center gap-2 min-w-0 w-full">
125 |             {item.type === 'directory' ? (
126 |               expandedDirs.has(item.path) ? (
127 |                 <FolderOpen className="w-4 h-4 text-blue-500 flex-shrink-0" />
128 |               ) : (
129 |                 <Folder className="w-4 h-4 text-muted-foreground flex-shrink-0" />
130 |               )
131 |             ) : (
132 |               getFileIcon(item.name)
133 |             )}
134 |             <span className="text-sm truncate text-foreground">
135 |               {item.name}
136 |             </span>
137 |           </div>
138 |         </Button>
139 |         
140 |         {item.type === 'directory' && 
141 |          expandedDirs.has(item.path) && 
142 |          item.children && 
143 |          item.children.length > 0 && (
144 |           <div>
145 |             {renderFileTree(item.children, level + 1)}
146 |           </div>
147 |         )}
148 |       </div>
149 |     ));
150 |   };
151 | 
152 |   const isImageFile = (filename) => {
153 |     const ext = filename.split('.').pop()?.toLowerCase();
154 |     const imageExtensions = ['png', 'jpg', 'jpeg', 'gif', 'svg', 'webp', 'ico', 'bmp'];
155 |     return imageExtensions.includes(ext);
156 |   };
157 | 
158 |   const getFileIcon = (filename) => {
159 |     const ext = filename.split('.').pop()?.toLowerCase();
160 |     
161 |     const codeExtensions = ['js', 'jsx', 'ts', 'tsx', 'py', 'java', 'cpp', 'c', 'php', 'rb', 'go', 'rs'];
162 |     const docExtensions = ['md', 'txt', 'doc', 'pdf'];
163 |     const imageExtensions = ['png', 'jpg', 'jpeg', 'gif', 'svg', 'webp', 'ico', 'bmp'];
164 |     
165 |     if (codeExtensions.includes(ext)) {
166 |       return <FileCode className="w-4 h-4 text-green-500 flex-shrink-0" />;
167 |     } else if (docExtensions.includes(ext)) {
168 |       return <FileText className="w-4 h-4 text-blue-500 flex-shrink-0" />;
169 |     } else if (imageExtensions.includes(ext)) {
170 |       return <File className="w-4 h-4 text-purple-500 flex-shrink-0" />;
171 |     } else {
172 |       return <File className="w-4 h-4 text-muted-foreground flex-shrink-0" />;
173 |     }
174 |   };
175 | 
176 |   // Render detailed view with table-like layout
177 |   const renderDetailedView = (items, level = 0) => {
178 |     return items.map((item) => (
179 |       <div key={item.path} className="select-none">
180 |         <div
181 |           className={cn(
182 |             "grid grid-cols-12 gap-2 p-2 hover:bg-accent cursor-pointer items-center",
183 |           )}
184 |           style={{ paddingLeft: `${level * 16 + 12}px` }}
185 |           onClick={() => {
186 |             if (item.type === 'directory') {
187 |               toggleDirectory(item.path);
188 |             } else if (isImageFile(item.name)) {
189 |               setSelectedImage({
190 |                 name: item.name,
191 |                 path: item.path,
192 |                 projectPath: selectedProject.path,
193 |                 projectName: selectedProject.name
194 |               });
195 |             } else {
196 |               setSelectedFile({
197 |                 name: item.name,
198 |                 path: item.path,
199 |                 projectPath: selectedProject.path,
200 |                 projectName: selectedProject.name
201 |               });
202 |             }
203 |           }}
204 |         >
205 |           <div className="col-span-5 flex items-center gap-2 min-w-0">
206 |             {item.type === 'directory' ? (
207 |               expandedDirs.has(item.path) ? (
208 |                 <FolderOpen className="w-4 h-4 text-blue-500 flex-shrink-0" />
209 |               ) : (
210 |                 <Folder className="w-4 h-4 text-muted-foreground flex-shrink-0" />
211 |               )
212 |             ) : (
213 |               getFileIcon(item.name)
214 |             )}
215 |             <span className="text-sm truncate text-foreground">
216 |               {item.name}
217 |             </span>
218 |           </div>
219 |           <div className="col-span-2 text-sm text-muted-foreground">
220 |             {item.type === 'file' ? formatFileSize(item.size) : '-'}
221 |           </div>
222 |           <div className="col-span-3 text-sm text-muted-foreground">
223 |             {formatRelativeTime(item.modified)}
224 |           </div>
225 |           <div className="col-span-2 text-sm text-muted-foreground font-mono">
226 |             {item.permissionsRwx || '-'}
227 |           </div>
228 |         </div>
229 |         
230 |         {item.type === 'directory' && 
231 |          expandedDirs.has(item.path) && 
232 |          item.children && 
233 |          renderDetailedView(item.children, level + 1)}
234 |       </div>
235 |     ));
236 |   };
237 | 
238 |   // Render compact view with inline details
239 |   const renderCompactView = (items, level = 0) => {
240 |     return items.map((item) => (
241 |       <div key={item.path} className="select-none">
242 |         <div
243 |           className={cn(
244 |             "flex items-center justify-between p-2 hover:bg-accent cursor-pointer",
245 |           )}
246 |           style={{ paddingLeft: `${level * 16 + 12}px` }}
247 |           onClick={() => {
248 |             if (item.type === 'directory') {
249 |               toggleDirectory(item.path);
250 |             } else if (isImageFile(item.name)) {
251 |               setSelectedImage({
252 |                 name: item.name,
253 |                 path: item.path,
254 |                 projectPath: selectedProject.path,
255 |                 projectName: selectedProject.name
256 |               });
257 |             } else {
258 |               setSelectedFile({
259 |                 name: item.name,
260 |                 path: item.path,
261 |                 projectPath: selectedProject.path,
262 |                 projectName: selectedProject.name
263 |               });
264 |             }
265 |           }}
266 |         >
267 |           <div className="flex items-center gap-2 min-w-0">
268 |             {item.type === 'directory' ? (
269 |               expandedDirs.has(item.path) ? (
270 |                 <FolderOpen className="w-4 h-4 text-blue-500 flex-shrink-0" />
271 |               ) : (
272 |                 <Folder className="w-4 h-4 text-muted-foreground flex-shrink-0" />
273 |               )
274 |             ) : (
275 |               getFileIcon(item.name)
276 |             )}
277 |             <span className="text-sm truncate text-foreground">
278 |               {item.name}
279 |             </span>
280 |           </div>
281 |           <div className="flex items-center gap-3 text-xs text-muted-foreground">
282 |             {item.type === 'file' && (
283 |               <>
284 |                 <span>{formatFileSize(item.size)}</span>
285 |                 <span className="font-mono">{item.permissionsRwx}</span>
286 |               </>
287 |             )}
288 |           </div>
289 |         </div>
290 |         
291 |         {item.type === 'directory' && 
292 |          expandedDirs.has(item.path) && 
293 |          item.children && 
294 |          renderCompactView(item.children, level + 1)}
295 |       </div>
296 |     ));
297 |   };
298 | 
299 |   if (loading) {
300 |     return (
301 |       <div className="h-full flex items-center justify-center">
302 |         <div className="text-gray-500 dark:text-gray-400">
303 |           Loading files...
304 |         </div>
305 |       </div>
306 |     );
307 |   }
308 | 
309 |   return (
310 |     <div className="h-full flex flex-col bg-card">
311 |       {/* View Mode Toggle */}
312 |       <div className="p-4 border-b border-border flex items-center justify-between">
313 |         <h3 className="text-sm font-medium text-foreground">Files</h3>
314 |         <div className="flex gap-1">
315 |           <Button
316 |             variant={viewMode === 'simple' ? 'default' : 'ghost'}
317 |             size="sm"
318 |             className="h-8 w-8 p-0"
319 |             onClick={() => changeViewMode('simple')}
320 |             title="Simple view"
321 |           >
322 |             <List className="w-4 h-4" />
323 |           </Button>
324 |           <Button
325 |             variant={viewMode === 'compact' ? 'default' : 'ghost'}
326 |             size="sm"
327 |             className="h-8 w-8 p-0"
328 |             onClick={() => changeViewMode('compact')}
329 |             title="Compact view"
330 |           >
331 |             <Eye className="w-4 h-4" />
332 |           </Button>
333 |           <Button
334 |             variant={viewMode === 'detailed' ? 'default' : 'ghost'}
335 |             size="sm"
336 |             className="h-8 w-8 p-0"
337 |             onClick={() => changeViewMode('detailed')}
338 |             title="Detailed view"
339 |           >
340 |             <TableProperties className="w-4 h-4" />
341 |           </Button>
342 |         </div>
343 |       </div>
344 | 
345 |       {/* Column Headers for Detailed View */}
346 |       {viewMode === 'detailed' && files.length > 0 && (
347 |         <div className="px-4 pt-2 pb-1 border-b border-border">
348 |           <div className="grid grid-cols-12 gap-2 px-2 text-xs font-medium text-muted-foreground">
349 |             <div className="col-span-5">Name</div>
350 |             <div className="col-span-2">Size</div>
351 |             <div className="col-span-3">Modified</div>
352 |             <div className="col-span-2">Permissions</div>
353 |           </div>
354 |         </div>
355 |       )}
356 |       
357 |       <ScrollArea className="flex-1 p-4">
358 |         {files.length === 0 ? (
359 |           <div className="text-center py-8">
360 |             <div className="w-12 h-12 bg-muted rounded-lg flex items-center justify-center mx-auto mb-3">
361 |               <Folder className="w-6 h-6 text-muted-foreground" />
362 |             </div>
363 |             <h4 className="font-medium text-foreground mb-1">No files found</h4>
364 |             <p className="text-sm text-muted-foreground">
365 |               Check if the project path is accessible
366 |             </p>
367 |           </div>
368 |         ) : (
369 |           <div className={viewMode === 'detailed' ? '' : 'space-y-1'}>
370 |             {viewMode === 'simple' && renderFileTree(files)}
371 |             {viewMode === 'compact' && renderCompactView(files)}
372 |             {viewMode === 'detailed' && renderDetailedView(files)}
373 |           </div>
374 |         )}
375 |       </ScrollArea>
376 |       
377 |       {/* Code Editor Modal */}
378 |       {selectedFile && (
379 |         <CodeEditor
380 |           file={selectedFile}
381 |           onClose={() => setSelectedFile(null)}
382 |           projectPath={selectedFile.projectPath}
383 |         />
384 |       )}
385 |       
386 |       {/* Image Viewer Modal */}
387 |       {selectedImage && (
388 |         <ImageViewer
389 |           file={selectedImage}
390 |           onClose={() => setSelectedImage(null)}
391 |         />
392 |       )}
393 |     </div>
394 |   );
395 | }
396 | 
397 | export default FileTree;


--------------------------------------------------------------------------------
/src/components/ImageViewer.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react';
 2 | import { Button } from './ui/button';
 3 | import { X } from 'lucide-react';
 4 | 
 5 | function ImageViewer({ file, onClose }) {
 6 |   const imagePath = `/api/projects/${file.projectName}/files/content?path=${encodeURIComponent(file.path)}`;
 7 | 
 8 |   return (
 9 |     <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
10 |       <div className="bg-white dark:bg-gray-800 rounded-lg shadow-xl max-w-4xl max-h-[90vh] w-full mx-4 overflow-hidden">
11 |         <div className="flex items-center justify-between p-4 border-b">
12 |           <h3 className="text-lg font-semibold text-gray-900 dark:text-white">
13 |             {file.name}
14 |           </h3>
15 |           <Button
16 |             variant="ghost"
17 |             size="sm"
18 |             onClick={onClose}
19 |             className="h-8 w-8 p-0"
20 |           >
21 |             <X className="h-4 w-4" />
22 |           </Button>
23 |         </div>
24 | 
25 |         <div className="p-4 flex justify-center items-center bg-gray-50 dark:bg-gray-900 min-h-[400px]">
26 |           <img
27 |             src={imagePath}
28 |             alt={file.name}
29 |             className="max-w-full max-h-[70vh] object-contain rounded-lg shadow-md"
30 |             onError={(e) => {
31 |               e.target.style.display = 'none';
32 |               e.target.nextSibling.style.display = 'block';
33 |             }}
34 |           />
35 |           <div
36 |             className="text-center text-gray-500 dark:text-gray-400"
37 |             style={{ display: 'none' }}
38 |           >
39 |             <p>Unable to load image</p>
40 |             <p className="text-sm mt-2">{file.path}</p>
41 |           </div>
42 |         </div>
43 | 
44 |         <div className="p-4 border-t bg-gray-50 dark:bg-gray-800">
45 |           <p className="text-sm text-gray-600 dark:text-gray-400">
46 |             {file.path}
47 |           </p>
48 |         </div>
49 |       </div>
50 |     </div>
51 |   );
52 | }
53 | 
54 | export default ImageViewer;


--------------------------------------------------------------------------------
/src/components/LoginForm.jsx:
--------------------------------------------------------------------------------
  1 | import React, { useState } from 'react';
  2 | import { useAuth } from '../contexts/AuthContext';
  3 | import { MessageSquare } from 'lucide-react';
  4 | 
  5 | const LoginForm = () => {
  6 |   const [username, setUsername] = useState('');
  7 |   const [password, setPassword] = useState('');
  8 |   const [isLoading, setIsLoading] = useState(false);
  9 |   const [error, setError] = useState('');
 10 |   
 11 |   const { login } = useAuth();
 12 | 
 13 |   const handleSubmit = async (e) => {
 14 |     e.preventDefault();
 15 |     setError('');
 16 |     
 17 |     if (!username || !password) {
 18 |       setError('Please enter both username and password');
 19 |       return;
 20 |     }
 21 |     
 22 |     setIsLoading(true);
 23 |     
 24 |     const result = await login(username, password);
 25 |     
 26 |     if (!result.success) {
 27 |       setError(result.error);
 28 |     }
 29 |     
 30 |     setIsLoading(false);
 31 |   };
 32 | 
 33 |   return (
 34 |     <div className="min-h-screen bg-background flex items-center justify-center p-4">
 35 |       <div className="w-full max-w-md">
 36 |         <div className="bg-card rounded-lg shadow-lg border border-border p-8 space-y-6">
 37 |           {/* Logo and Title */}
 38 |           <div className="text-center">
 39 |             <div className="flex justify-center mb-4">
 40 |               <div className="w-16 h-16 bg-primary rounded-lg flex items-center justify-center shadow-sm">
 41 |                 <MessageSquare className="w-8 h-8 text-primary-foreground" />
 42 |               </div>
 43 |             </div>
 44 |             <h1 className="text-2xl font-bold text-foreground">Welcome Back</h1>
 45 |             <p className="text-muted-foreground mt-2">
 46 |               Sign in to your Claude Code UI account
 47 |             </p>
 48 |           </div>
 49 | 
 50 |           {/* Login Form */}
 51 |           <form onSubmit={handleSubmit} className="space-y-4">
 52 |             <div>
 53 |               <label htmlFor="username" className="block text-sm font-medium text-foreground mb-1">
 54 |                 Username
 55 |               </label>
 56 |               <input
 57 |                 type="text"
 58 |                 id="username"
 59 |                 value={username}
 60 |                 onChange={(e) => setUsername(e.target.value)}
 61 |                 className="w-full px-3 py-2 border border-border rounded-md bg-background text-foreground focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
 62 |                 placeholder="Enter your username"
 63 |                 required
 64 |                 disabled={isLoading}
 65 |               />
 66 |             </div>
 67 | 
 68 |             <div>
 69 |               <label htmlFor="password" className="block text-sm font-medium text-foreground mb-1">
 70 |                 Password
 71 |               </label>
 72 |               <input
 73 |                 type="password"
 74 |                 id="password"
 75 |                 value={password}
 76 |                 onChange={(e) => setPassword(e.target.value)}
 77 |                 className="w-full px-3 py-2 border border-border rounded-md bg-background text-foreground focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
 78 |                 placeholder="Enter your password"
 79 |                 required
 80 |                 disabled={isLoading}
 81 |               />
 82 |             </div>
 83 | 
 84 |             {error && (
 85 |               <div className="p-3 bg-red-100 dark:bg-red-900/20 border border-red-300 dark:border-red-800 rounded-md">
 86 |                 <p className="text-sm text-red-700 dark:text-red-400">{error}</p>
 87 |               </div>
 88 |             )}
 89 | 
 90 |             <button
 91 |               type="submit"
 92 |               disabled={isLoading}
 93 |               className="w-full bg-blue-600 hover:bg-blue-700 disabled:bg-blue-400 text-white font-medium py-2 px-4 rounded-md transition-colors duration-200"
 94 |             >
 95 |               {isLoading ? 'Signing in...' : 'Sign In'}
 96 |             </button>
 97 |           </form>
 98 | 
 99 |           <div className="text-center">
100 |             <p className="text-sm text-muted-foreground">
101 |               Enter your credentials to access Claude Code UI
102 |             </p>
103 |           </div>
104 |         </div>
105 |       </div>
106 |     </div>
107 |   );
108 | };
109 | 
110 | export default LoginForm;


--------------------------------------------------------------------------------
/src/components/MicButton.jsx:
--------------------------------------------------------------------------------
  1 | import React, { useState, useEffect, useRef } from 'react';
  2 | import { Mic, Loader2, Brain } from 'lucide-react';
  3 | import { transcribeWithWhisper } from '../utils/whisper';
  4 | 
  5 | export function MicButton({ onTranscript, className = '' }) {
  6 |   const [state, setState] = useState('idle'); // idle, recording, transcribing, processing
  7 |   const [error, setError] = useState(null);
  8 |   const [isSupported, setIsSupported] = useState(true);
  9 |   
 10 |   const mediaRecorderRef = useRef(null);
 11 |   const streamRef = useRef(null);
 12 |   const chunksRef = useRef([]);
 13 |   const lastTapRef = useRef(0);
 14 |   
 15 |   // Check microphone support on mount
 16 |   useEffect(() => {
 17 |     const checkSupport = () => {
 18 |       if (!navigator.mediaDevices || !navigator.mediaDevices.getUserMedia) {
 19 |         setIsSupported(false);
 20 |         setError('Microphone not supported. Please use HTTPS or a modern browser.');
 21 |         return;
 22 |       }
 23 |       
 24 |       // Additional check for secure context
 25 |       if (location.protocol !== 'https:' && location.hostname !== 'localhost') {
 26 |         setIsSupported(false);
 27 |         setError('Microphone requires HTTPS. Please use a secure connection.');
 28 |         return;
 29 |       }
 30 |       
 31 |       setIsSupported(true);
 32 |       setError(null);
 33 |     };
 34 |     
 35 |     checkSupport();
 36 |   }, []);
 37 | 
 38 |   // Start recording
 39 |   const startRecording = async () => {
 40 |     try {
 41 |       console.log('Starting recording...');
 42 |       setError(null);
 43 |       chunksRef.current = [];
 44 | 
 45 |       // Check if getUserMedia is available
 46 |       if (!navigator.mediaDevices || !navigator.mediaDevices.getUserMedia) {
 47 |         throw new Error('Microphone access not available. Please use HTTPS or a supported browser.');
 48 |       }
 49 | 
 50 |       const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
 51 |       streamRef.current = stream;
 52 | 
 53 |       const mimeType = MediaRecorder.isTypeSupported('audio/webm') ? 'audio/webm' : 'audio/mp4';
 54 |       const recorder = new MediaRecorder(stream, { mimeType });
 55 |       mediaRecorderRef.current = recorder;
 56 | 
 57 |       recorder.ondataavailable = (e) => {
 58 |         if (e.data.size > 0) {
 59 |           chunksRef.current.push(e.data);
 60 |         }
 61 |       };
 62 | 
 63 |       recorder.onstop = async () => {
 64 |         console.log('Recording stopped, creating blob...');
 65 |         const blob = new Blob(chunksRef.current, { type: mimeType });
 66 |         
 67 |         // Clean up stream
 68 |         if (streamRef.current) {
 69 |           streamRef.current.getTracks().forEach(track => track.stop());
 70 |           streamRef.current = null;
 71 |         }
 72 | 
 73 |         // Start transcribing
 74 |         setState('transcribing');
 75 |         
 76 |         // Check if we're in an enhancement mode
 77 |         const whisperMode = window.localStorage.getItem('whisperMode') || 'default';
 78 |         const isEnhancementMode = whisperMode === 'prompt' || whisperMode === 'vibe' || whisperMode === 'instructions' || whisperMode === 'architect';
 79 |         
 80 |         // Set up a timer to switch to processing state for enhancement modes
 81 |         let processingTimer;
 82 |         if (isEnhancementMode) {
 83 |           processingTimer = setTimeout(() => {
 84 |             setState('processing');
 85 |           }, 2000); // Switch to processing after 2 seconds
 86 |         }
 87 |         
 88 |         try {
 89 |           const text = await transcribeWithWhisper(blob);
 90 |           if (text && onTranscript) {
 91 |             onTranscript(text);
 92 |           }
 93 |         } catch (err) {
 94 |           console.error('Transcription error:', err);
 95 |           setError(err.message);
 96 |         } finally {
 97 |           if (processingTimer) {
 98 |             clearTimeout(processingTimer);
 99 |           }
100 |           setState('idle');
101 |         }
102 |       };
103 | 
104 |       recorder.start();
105 |       setState('recording');
106 |       console.log('Recording started successfully');
107 |     } catch (err) {
108 |       console.error('Failed to start recording:', err);
109 |       
110 |       // Provide specific error messages based on error type
111 |       let errorMessage = 'Microphone access failed';
112 |       
113 |       if (err.name === 'NotAllowedError') {
114 |         errorMessage = 'Microphone access denied. Please allow microphone permissions.';
115 |       } else if (err.name === 'NotFoundError') {
116 |         errorMessage = 'No microphone found. Please check your audio devices.';
117 |       } else if (err.name === 'NotSupportedError') {
118 |         errorMessage = 'Microphone not supported by this browser.';
119 |       } else if (err.name === 'NotReadableError') {
120 |         errorMessage = 'Microphone is being used by another application.';
121 |       } else if (err.message.includes('HTTPS')) {
122 |         errorMessage = err.message;
123 |       }
124 |       
125 |       setError(errorMessage);
126 |       setState('idle');
127 |     }
128 |   };
129 | 
130 |   // Stop recording
131 |   const stopRecording = () => {
132 |     console.log('Stopping recording...');
133 |     if (mediaRecorderRef.current && mediaRecorderRef.current.state === 'recording') {
134 |       mediaRecorderRef.current.stop();
135 |       // Don't set state here - let the onstop handler do it
136 |     } else {
137 |       // If recorder isn't in recording state, force cleanup
138 |       console.log('Recorder not in recording state, forcing cleanup');
139 |       if (streamRef.current) {
140 |         streamRef.current.getTracks().forEach(track => track.stop());
141 |         streamRef.current = null;
142 |       }
143 |       setState('idle');
144 |     }
145 |   };
146 | 
147 |   // Handle button click
148 |   const handleClick = (e) => {
149 |     // Prevent double firing on mobile
150 |     if (e) {
151 |       e.preventDefault();
152 |       e.stopPropagation();
153 |     }
154 |     
155 |     // Don't proceed if microphone is not supported
156 |     if (!isSupported) {
157 |       return;
158 |     }
159 |     
160 |     // Debounce for mobile double-tap issue
161 |     const now = Date.now();
162 |     if (now - lastTapRef.current < 300) {
163 |       console.log('Ignoring rapid tap');
164 |       return;
165 |     }
166 |     lastTapRef.current = now;
167 |     
168 |     console.log('Button clicked, current state:', state);
169 |     
170 |     if (state === 'idle') {
171 |       startRecording();
172 |     } else if (state === 'recording') {
173 |       stopRecording();
174 |     }
175 |     // Do nothing if transcribing or processing
176 |   };
177 | 
178 |   // Clean up on unmount
179 |   useEffect(() => {
180 |     return () => {
181 |       if (streamRef.current) {
182 |         streamRef.current.getTracks().forEach(track => track.stop());
183 |       }
184 |     };
185 |   }, []);
186 | 
187 |   // Button appearance based on state
188 |   const getButtonAppearance = () => {
189 |     if (!isSupported) {
190 |       return {
191 |         icon: <Mic className="w-5 h-5" />,
192 |         className: 'bg-gray-400 cursor-not-allowed',
193 |         disabled: true
194 |       };
195 |     }
196 |     
197 |     switch (state) {
198 |       case 'recording':
199 |         return {
200 |           icon: <Mic className="w-5 h-5 text-white" />,
201 |           className: 'bg-red-500 hover:bg-red-600 animate-pulse',
202 |           disabled: false
203 |         };
204 |       case 'transcribing':
205 |         return {
206 |           icon: <Loader2 className="w-5 h-5 animate-spin" />,
207 |           className: 'bg-blue-500 hover:bg-blue-600',
208 |           disabled: true
209 |         };
210 |       case 'processing':
211 |         return {
212 |           icon: <Brain className="w-5 h-5 animate-pulse" />,
213 |           className: 'bg-purple-500 hover:bg-purple-600',
214 |           disabled: true
215 |         };
216 |       default: // idle
217 |         return {
218 |           icon: <Mic className="w-5 h-5" />,
219 |           className: 'bg-gray-700 hover:bg-gray-600',
220 |           disabled: false
221 |         };
222 |     }
223 |   };
224 | 
225 |   const { icon, className: buttonClass, disabled } = getButtonAppearance();
226 | 
227 |   return (
228 |     <div className="relative">
229 |       <button
230 |         type="button"
231 |         style={{
232 |           backgroundColor: state === 'recording' ? '#ef4444' : 
233 |                           state === 'transcribing' ? '#3b82f6' : 
234 |                           state === 'processing' ? '#a855f7' :
235 |                           '#374151'
236 |         }}
237 |         className={`
238 |           flex items-center justify-center
239 |           w-12 h-12 rounded-full
240 |           text-white transition-all duration-200
241 |           focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500
242 |           dark:ring-offset-gray-800
243 |           touch-action-manipulation
244 |           ${disabled ? 'cursor-not-allowed opacity-75' : 'cursor-pointer'}
245 |           ${state === 'recording' ? 'animate-pulse' : ''}
246 |           hover:opacity-90
247 |           ${className}
248 |         `}
249 |         onClick={handleClick}
250 |         disabled={disabled}
251 |       >
252 |         {icon}
253 |       </button>
254 |       
255 |       {error && (
256 |         <div className="absolute top-full mt-2 left-1/2 transform -translate-x-1/2 
257 |                         bg-red-500 text-white text-xs px-2 py-1 rounded whitespace-nowrap z-10
258 |                         animate-fade-in">
259 |           {error}
260 |         </div>
261 |       )}
262 |       
263 |       {state === 'recording' && (
264 |         <div className="absolute -inset-1 rounded-full border-2 border-red-500 animate-ping pointer-events-none" />
265 |       )}
266 |       
267 |       {state === 'processing' && (
268 |         <div className="absolute -inset-1 rounded-full border-2 border-purple-500 animate-ping pointer-events-none" />
269 |       )}
270 |     </div>
271 |   );
272 | }


--------------------------------------------------------------------------------
/src/components/MobileNav.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react';
 2 | import { MessageSquare, Folder, Terminal, GitBranch, Globe, CheckSquare } from 'lucide-react';
 3 | import { useTasksSettings } from '../contexts/TasksSettingsContext';
 4 | 
 5 | function MobileNav({ activeTab, setActiveTab, isInputFocused }) {
 6 |   const { tasksEnabled } = useTasksSettings();
 7 |   // Detect dark mode
 8 |   const isDarkMode = document.documentElement.classList.contains('dark');
 9 |   const navItems = [
10 |     {
11 |       id: 'chat',
12 |       icon: MessageSquare,
13 |       onClick: () => setActiveTab('chat')
14 |     },
15 |     {
16 |       id: 'shell',
17 |       icon: Terminal,
18 |       onClick: () => setActiveTab('shell')
19 |     },
20 |     {
21 |       id: 'files',
22 |       icon: Folder,
23 |       onClick: () => setActiveTab('files')
24 |     },
25 |     {
26 |       id: 'git',
27 |       icon: GitBranch,
28 |       onClick: () => setActiveTab('git')
29 |     },
30 |     // Conditionally add tasks tab if enabled
31 |     ...(tasksEnabled ? [{
32 |       id: 'tasks',
33 |       icon: CheckSquare,
34 |       onClick: () => setActiveTab('tasks')
35 |     }] : [])
36 |   ];
37 | 
38 |   return (
39 |     <>
40 |       <style>
41 |         {`
42 |           .mobile-nav-container {
43 |             background-color: ${isDarkMode ? '#1f2937' : '#ffffff'} !important;
44 |           }
45 |           .mobile-nav-container:hover {
46 |             background-color: ${isDarkMode ? '#1f2937' : '#ffffff'} !important;
47 |           }
48 |         `}
49 |       </style>
50 |       <div 
51 |         className={`mobile-nav-container fixed bottom-0 left-0 right-0 border-t border-gray-200 dark:border-gray-700 z-50 ios-bottom-safe transform transition-transform duration-300 ease-in-out shadow-lg ${
52 |           isInputFocused ? 'translate-y-full' : 'translate-y-0'
53 |         }`}
54 |       >
55 |       <div className="flex items-center justify-around py-1">
56 |         {navItems.map((item) => {
57 |           const Icon = item.icon;
58 |           const isActive = activeTab === item.id;
59 |           
60 |           return (
61 |             <button
62 |               key={item.id}
63 |               onClick={item.onClick}
64 |               onTouchStart={(e) => {
65 |                 e.preventDefault();
66 |                 item.onClick();
67 |               }}
68 |               className={`flex items-center justify-center p-2 rounded-lg min-h-[40px] min-w-[40px] relative touch-manipulation ${
69 |                 isActive
70 |                   ? 'text-blue-600 dark:text-blue-400'
71 |                   : 'text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white'
72 |               }`}
73 |               aria-label={item.id}
74 |             >
75 |               <Icon className="w-5 h-5" />
76 |               {isActive && (
77 |                 <div className="absolute top-0 left-1/2 transform -translate-x-1/2 w-6 h-0.5 bg-blue-600 dark:bg-blue-400 rounded-full" />
78 |               )}
79 |             </button>
80 |           );
81 |         })}
82 |       </div>
83 |     </div>
84 |     </>
85 |   );
86 | }
87 | 
88 | export default MobileNav;


--------------------------------------------------------------------------------
/src/components/ProtectedRoute.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react';
 2 | import { useAuth } from '../contexts/AuthContext';
 3 | import SetupForm from './SetupForm';
 4 | import LoginForm from './LoginForm';
 5 | import { MessageSquare } from 'lucide-react';
 6 | 
 7 | const LoadingScreen = () => (
 8 |   <div className="min-h-screen bg-background flex items-center justify-center p-4">
 9 |     <div className="text-center">
10 |       <div className="flex justify-center mb-4">
11 |         <div className="w-16 h-16 bg-primary rounded-lg flex items-center justify-center shadow-sm">
12 |           <MessageSquare className="w-8 h-8 text-primary-foreground" />
13 |         </div>
14 |       </div>
15 |       <h1 className="text-2xl font-bold text-foreground mb-2">Claude Code UI</h1>
16 |       <div className="flex items-center justify-center space-x-2">
17 |         <div className="w-2 h-2 bg-blue-500 rounded-full animate-bounce"></div>
18 |         <div className="w-2 h-2 bg-blue-500 rounded-full animate-bounce" style={{ animationDelay: '0.1s' }}></div>
19 |         <div className="w-2 h-2 bg-blue-500 rounded-full animate-bounce" style={{ animationDelay: '0.2s' }}></div>
20 |       </div>
21 |       <p className="text-muted-foreground mt-2">Loading...</p>
22 |     </div>
23 |   </div>
24 | );
25 | 
26 | const ProtectedRoute = ({ children }) => {
27 |   const { user, isLoading, needsSetup } = useAuth();
28 | 
29 |   if (isLoading) {
30 |     return <LoadingScreen />;
31 |   }
32 | 
33 |   if (needsSetup) {
34 |     return <SetupForm />;
35 |   }
36 | 
37 |   if (!user) {
38 |     return <LoginForm />;
39 |   }
40 | 
41 |   return children;
42 | };
43 | 
44 | export default ProtectedRoute;


--------------------------------------------------------------------------------
/src/components/QuickSettingsPanel.jsx:
--------------------------------------------------------------------------------
  1 | import React, { useState, useEffect } from 'react';
  2 | import { 
  3 |   ChevronLeft, 
  4 |   ChevronRight, 
  5 |   Maximize2, 
  6 |   Eye, 
  7 |   Settings2,
  8 |   Moon,
  9 |   Sun,
 10 |   ArrowDown,
 11 |   Mic,
 12 |   Brain,
 13 |   Sparkles,
 14 |   FileText,
 15 |   Languages
 16 | } from 'lucide-react';
 17 | import DarkModeToggle from './DarkModeToggle';
 18 | import { useTheme } from '../contexts/ThemeContext';
 19 | 
 20 | const QuickSettingsPanel = ({ 
 21 |   isOpen, 
 22 |   onToggle,
 23 |   autoExpandTools,
 24 |   onAutoExpandChange,
 25 |   showRawParameters,
 26 |   onShowRawParametersChange,
 27 |   autoScrollToBottom,
 28 |   onAutoScrollChange,
 29 |   sendByCtrlEnter,
 30 |   onSendByCtrlEnterChange,
 31 |   isMobile
 32 | }) => {
 33 |   const [localIsOpen, setLocalIsOpen] = useState(isOpen);
 34 |   const [whisperMode, setWhisperMode] = useState(() => {
 35 |     return localStorage.getItem('whisperMode') || 'default';
 36 |   });
 37 |   const { isDarkMode } = useTheme();
 38 | 
 39 |   useEffect(() => {
 40 |     setLocalIsOpen(isOpen);
 41 |   }, [isOpen]);
 42 | 
 43 |   const handleToggle = () => {
 44 |     const newState = !localIsOpen;
 45 |     setLocalIsOpen(newState);
 46 |     onToggle(newState);
 47 |   };
 48 | 
 49 |   return (
 50 |     <>
 51 |       {/* Pull Tab */}
 52 |       <div
 53 |         className={`fixed ${isMobile ? 'bottom-44' : 'top-1/2 -translate-y-1/2'} ${
 54 |           localIsOpen ? 'right-64' : 'right-0'
 55 |         } z-50 transition-all duration-150 ease-out`}
 56 |       >
 57 |         <button
 58 |           onClick={handleToggle}
 59 |           className="bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-l-md p-2 hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors shadow-lg"
 60 |           aria-label={localIsOpen ? 'Close settings panel' : 'Open settings panel'}
 61 |         >
 62 |           {localIsOpen ? (
 63 |             <ChevronRight className="h-5 w-5 text-gray-600 dark:text-gray-400" />
 64 |           ) : (
 65 |             <ChevronLeft className="h-5 w-5 text-gray-600 dark:text-gray-400" />
 66 |           )}
 67 |         </button>
 68 |       </div>
 69 | 
 70 |       {/* Panel */}
 71 |       <div
 72 |         className={`fixed top-0 right-0 h-full w-64 bg-white dark:bg-gray-900 border-l border-gray-200 dark:border-gray-700 shadow-xl transform transition-transform duration-150 ease-out z-40 ${
 73 |           localIsOpen ? 'translate-x-0' : 'translate-x-full'
 74 |         } ${isMobile ? 'h-screen' : ''}`}
 75 |       >
 76 |         <div className="h-full flex flex-col">
 77 |           {/* Header */}
 78 |           <div className="p-4 border-b border-gray-200 dark:border-gray-700 bg-gray-50 dark:bg-gray-900">
 79 |             <h3 className="text-lg font-semibold text-gray-900 dark:text-white flex items-center gap-2">
 80 |               <Settings2 className="h-5 w-5 text-gray-600 dark:text-gray-400" />
 81 |               Quick Settings
 82 |             </h3>
 83 |           </div>
 84 | 
 85 |           {/* Settings Content */}
 86 |           <div className={`flex-1 overflow-y-auto overflow-x-hidden p-4 space-y-6 bg-white dark:bg-gray-900 ${isMobile ? 'pb-20' : ''}`}>
 87 |             {/* Appearance Settings */}
 88 |             <div className="space-y-2">
 89 |               <h4 className="text-xs font-semibold uppercase tracking-wider text-gray-500 dark:text-gray-400 mb-2">Appearance</h4>
 90 |               
 91 |               <div className="flex items-center justify-between p-3 rounded-lg bg-gray-50 dark:bg-gray-800 hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors border border-transparent hover:border-gray-300 dark:hover:border-gray-600">
 92 |                 <span className="flex items-center gap-2 text-sm text-gray-900 dark:text-white">
 93 |                   {isDarkMode ? <Moon className="h-4 w-4 text-gray-600 dark:text-gray-400" /> : <Sun className="h-4 w-4 text-gray-600 dark:text-gray-400" />}
 94 |                   Dark Mode
 95 |                 </span>
 96 |                 <DarkModeToggle />
 97 |               </div>
 98 |             </div>
 99 | 
100 |             {/* Tool Display Settings */}
101 |             <div className="space-y-2">
102 |               <h4 className="text-xs font-semibold uppercase tracking-wider text-gray-500 dark:text-gray-400 mb-2">Tool Display</h4>
103 |               
104 |               <label className="flex items-center justify-between p-3 rounded-lg bg-gray-50 dark:bg-gray-800 hover:bg-gray-100 dark:hover:bg-gray-700 cursor-pointer transition-colors border border-transparent hover:border-gray-300 dark:hover:border-gray-600">
105 |                 <span className="flex items-center gap-2 text-sm text-gray-900 dark:text-white">
106 |                   <Maximize2 className="h-4 w-4 text-gray-600 dark:text-gray-400" />
107 |                   Auto-expand tools
108 |                 </span>
109 |                 <input
110 |                   type="checkbox"
111 |                   checked={autoExpandTools}
112 |                   onChange={(e) => onAutoExpandChange(e.target.checked)}
113 |                   className="h-4 w-4 rounded border-gray-300 dark:border-gray-600 text-blue-600 dark:text-blue-500 focus:ring-blue-500 dark:focus:ring-blue-400 dark:bg-gray-800 dark:checked:bg-blue-600"
114 |                 />
115 |               </label>
116 | 
117 |               <label className="flex items-center justify-between p-3 rounded-lg bg-gray-50 dark:bg-gray-800 hover:bg-gray-100 dark:hover:bg-gray-700 cursor-pointer transition-colors border border-transparent hover:border-gray-300 dark:hover:border-gray-600">
118 |                 <span className="flex items-center gap-2 text-sm text-gray-900 dark:text-white">
119 |                   <Eye className="h-4 w-4 text-gray-600 dark:text-gray-400" />
120 |                   Show raw parameters
121 |                 </span>
122 |                 <input
123 |                   type="checkbox"
124 |                   checked={showRawParameters}
125 |                   onChange={(e) => onShowRawParametersChange(e.target.checked)}
126 |                   className="h-4 w-4 rounded border-gray-300 dark:border-gray-600 text-blue-600 dark:text-blue-500 focus:ring-blue-500 dark:focus:ring-blue-400 dark:bg-gray-800 dark:checked:bg-blue-600"
127 |                 />
128 |               </label>
129 |             </div>
130 |             {/* View Options */}
131 |             <div className="space-y-2">
132 |               <h4 className="text-xs font-semibold uppercase tracking-wider text-gray-500 dark:text-gray-400 mb-2">View Options</h4>
133 |               
134 |               <label className="flex items-center justify-between p-3 rounded-lg bg-gray-50 dark:bg-gray-800 hover:bg-gray-100 dark:hover:bg-gray-700 cursor-pointer transition-colors border border-transparent hover:border-gray-300 dark:hover:border-gray-600">
135 |                 <span className="flex items-center gap-2 text-sm text-gray-900 dark:text-white">
136 |                   <ArrowDown className="h-4 w-4 text-gray-600 dark:text-gray-400" />
137 |                   Auto-scroll to bottom
138 |                 </span>
139 |                 <input
140 |                   type="checkbox"
141 |                   checked={autoScrollToBottom}
142 |                   onChange={(e) => onAutoScrollChange(e.target.checked)}
143 |                   className="h-4 w-4 rounded border-gray-300 dark:border-gray-600 text-blue-600 dark:text-blue-500 focus:ring-blue-500 dark:focus:ring-blue-400 dark:bg-gray-800 dark:checked:bg-blue-600"
144 |                 />
145 |               </label>
146 |             </div>
147 | 
148 |             {/* Input Settings */}
149 |             <div className="space-y-2">
150 |               <h4 className="text-xs font-semibold uppercase tracking-wider text-gray-500 dark:text-gray-400 mb-2">Input Settings</h4>
151 |               
152 |               <label className="flex items-center justify-between p-3 rounded-lg bg-gray-50 dark:bg-gray-800 hover:bg-gray-100 dark:hover:bg-gray-700 cursor-pointer transition-colors border border-transparent hover:border-gray-300 dark:hover:border-gray-600">
153 |                 <span className="flex items-center gap-2 text-sm text-gray-900 dark:text-white">
154 |                   <Languages className="h-4 w-4 text-gray-600 dark:text-gray-400" />
155 |                   Send by Ctrl+Enter
156 |                 </span>
157 |                 <input
158 |                   type="checkbox"
159 |                   checked={sendByCtrlEnter}
160 |                   onChange={(e) => onSendByCtrlEnterChange(e.target.checked)}
161 |                   className="h-4 w-4 rounded border-gray-300 dark:border-gray-600 text-blue-600 dark:text-blue-500 focus:ring-blue-500 dark:focus:ring-blue-400 dark:bg-gray-800 dark:checked:bg-blue-600"
162 |                 />
163 |               </label>
164 |               <p className="text-xs text-gray-500 dark:text-gray-400 ml-3">
165 |                 When enabled, pressing Ctrl+Enter will send the message instead of just Enter. This is useful for IME users to avoid accidental sends.
166 |               </p>
167 |             </div>
168 | 
169 |             {/* Whisper Dictation Settings - HIDDEN */}
170 |             <div className="space-y-2" style={{ display: 'none' }}>
171 |               <h4 className="text-xs font-semibold uppercase tracking-wider text-gray-500 dark:text-gray-400 mb-2">Whisper Dictation</h4>
172 |               
173 |               <div className="space-y-2">
174 |                 <label className="flex items-start p-3 rounded-lg bg-gray-50 dark:bg-gray-800 hover:bg-gray-100 dark:hover:bg-gray-700 cursor-pointer transition-colors border border-transparent hover:border-gray-300 dark:hover:border-gray-600">
175 |                   <input
176 |                     type="radio"
177 |                     name="whisperMode"
178 |                     value="default"
179 |                     checked={whisperMode === 'default'}
180 |                     onChange={() => {
181 |                       setWhisperMode('default');
182 |                       localStorage.setItem('whisperMode', 'default');
183 |                       window.dispatchEvent(new Event('whisperModeChanged'));
184 |                     }}
185 |                     className="mt-0.5 h-4 w-4 border-gray-300 dark:border-gray-600 text-blue-600 dark:text-blue-500 focus:ring-blue-500 dark:focus:ring-blue-400 dark:bg-gray-800 dark:checked:bg-blue-600"
186 |                   />
187 |                   <div className="ml-3 flex-1">
188 |                     <span className="flex items-center gap-2 text-sm font-medium text-gray-900 dark:text-white">
189 |                       <Mic className="h-4 w-4 text-gray-600 dark:text-gray-400" />
190 |                       Default Mode
191 |                     </span>
192 |                     <p className="text-xs text-gray-500 dark:text-gray-400 mt-1">
193 |                       Direct transcription of your speech
194 |                     </p>
195 |                   </div>
196 |                 </label>
197 | 
198 |                 <label className="flex items-start p-3 rounded-lg bg-gray-50 dark:bg-gray-800 hover:bg-gray-100 dark:hover:bg-gray-700 cursor-pointer transition-colors border border-transparent hover:border-gray-300 dark:hover:border-gray-600">
199 |                   <input
200 |                     type="radio"
201 |                     name="whisperMode"
202 |                     value="prompt"
203 |                     checked={whisperMode === 'prompt'}
204 |                     onChange={() => {
205 |                       setWhisperMode('prompt');
206 |                       localStorage.setItem('whisperMode', 'prompt');
207 |                       window.dispatchEvent(new Event('whisperModeChanged'));
208 |                     }}
209 |                     className="mt-0.5 h-4 w-4 border-gray-300 dark:border-gray-600 text-blue-600 dark:text-blue-500 focus:ring-blue-500 dark:focus:ring-blue-400 dark:bg-gray-800 dark:checked:bg-blue-600"
210 |                   />
211 |                   <div className="ml-3 flex-1">
212 |                     <span className="flex items-center gap-2 text-sm font-medium text-gray-900 dark:text-white">
213 |                       <Sparkles className="h-4 w-4 text-gray-600 dark:text-gray-400" />
214 |                       Prompt Enhancement
215 |                     </span>
216 |                     <p className="text-xs text-gray-500 dark:text-gray-400 mt-1">
217 |                       Transform rough ideas into clear, detailed AI prompts
218 |                     </p>
219 |                   </div>
220 |                 </label>
221 | 
222 |                 <label className="flex items-start p-3 rounded-lg bg-gray-50 dark:bg-gray-800 hover:bg-gray-100 dark:hover:bg-gray-700 cursor-pointer transition-colors border border-transparent hover:border-gray-300 dark:hover:border-gray-600">
223 |                   <input
224 |                     type="radio"
225 |                     name="whisperMode"
226 |                     value="vibe"
227 |                     checked={whisperMode === 'vibe' || whisperMode === 'instructions' || whisperMode === 'architect'}
228 |                     onChange={() => {
229 |                       setWhisperMode('vibe');
230 |                       localStorage.setItem('whisperMode', 'vibe');
231 |                       window.dispatchEvent(new Event('whisperModeChanged'));
232 |                     }}
233 |                     className="mt-0.5 h-4 w-4 border-gray-300 dark:border-gray-600 text-blue-600 dark:text-blue-500 focus:ring-blue-500 dark:focus:ring-blue-400 dark:bg-gray-800 dark:checked:bg-blue-600"
234 |                   />
235 |                   <div className="ml-3 flex-1">
236 |                     <span className="flex items-center gap-2 text-sm font-medium text-gray-900 dark:text-white">
237 |                       <FileText className="h-4 w-4 text-gray-600 dark:text-gray-400" />
238 |                       Vibe Mode
239 |                     </span>
240 |                     <p className="text-xs text-gray-500 dark:text-gray-400 mt-1">
241 |                       Format ideas as clear agent instructions with details
242 |                     </p>
243 |                   </div>
244 |                 </label>
245 |               </div>
246 |             </div>
247 |           </div>
248 |         </div>
249 |       </div>
250 | 
251 |       {/* Backdrop */}
252 |       {localIsOpen && (
253 |         <div
254 |           className="fixed inset-0 bg-background/80 backdrop-blur-sm z-30 transition-opacity duration-150 ease-out"
255 |           onClick={handleToggle}
256 |         />
257 |       )}
258 |     </>
259 |   );
260 | };
261 | 
262 | export default QuickSettingsPanel;


--------------------------------------------------------------------------------
/src/components/SetupForm.jsx:
--------------------------------------------------------------------------------
  1 | import React, { useState } from 'react';
  2 | import { useAuth } from '../contexts/AuthContext';
  3 | import ClaudeLogo from './ClaudeLogo';
  4 | 
  5 | const SetupForm = () => {
  6 |   const [username, setUsername] = useState('');
  7 |   const [password, setPassword] = useState('');
  8 |   const [confirmPassword, setConfirmPassword] = useState('');
  9 |   const [isLoading, setIsLoading] = useState(false);
 10 |   const [error, setError] = useState('');
 11 |   
 12 |   const { register } = useAuth();
 13 | 
 14 |   const handleSubmit = async (e) => {
 15 |     e.preventDefault();
 16 |     setError('');
 17 |     
 18 |     if (password !== confirmPassword) {
 19 |       setError('Passwords do not match');
 20 |       return;
 21 |     }
 22 |     
 23 |     if (username.length < 3) {
 24 |       setError('Username must be at least 3 characters long');
 25 |       return;
 26 |     }
 27 |     
 28 |     if (password.length < 6) {
 29 |       setError('Password must be at least 6 characters long');
 30 |       return;
 31 |     }
 32 |     
 33 |     setIsLoading(true);
 34 |     
 35 |     const result = await register(username, password);
 36 |     
 37 |     if (!result.success) {
 38 |       setError(result.error);
 39 |     }
 40 |     
 41 |     setIsLoading(false);
 42 |   };
 43 | 
 44 |   return (
 45 |     <div className="min-h-screen bg-background flex items-center justify-center p-4">
 46 |       <div className="w-full max-w-md">
 47 |         <div className="bg-card rounded-lg shadow-lg border border-border p-8 space-y-6">
 48 |           {/* Logo and Title */}
 49 |           <div className="text-center">
 50 |             <div className="flex justify-center mb-4">
 51 |               <ClaudeLogo size={64} />
 52 |             </div>
 53 |             <h1 className="text-2xl font-bold text-foreground">Welcome to Claude Code UI</h1>
 54 |             <p className="text-muted-foreground mt-2">
 55 |               Set up your account to get started
 56 |             </p>
 57 |           </div>
 58 | 
 59 |           {/* Setup Form */}
 60 |           <form onSubmit={handleSubmit} className="space-y-4">
 61 |             <div>
 62 |               <label htmlFor="username" className="block text-sm font-medium text-foreground mb-1">
 63 |                 Username
 64 |               </label>
 65 |               <input
 66 |                 type="text"
 67 |                 id="username"
 68 |                 value={username}
 69 |                 onChange={(e) => setUsername(e.target.value)}
 70 |                 className="w-full px-3 py-2 border border-border rounded-md bg-background text-foreground focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
 71 |                 placeholder="Enter your username"
 72 |                 required
 73 |                 disabled={isLoading}
 74 |               />
 75 |             </div>
 76 | 
 77 |             <div>
 78 |               <label htmlFor="password" className="block text-sm font-medium text-foreground mb-1">
 79 |                 Password
 80 |               </label>
 81 |               <input
 82 |                 type="password"
 83 |                 id="password"
 84 |                 value={password}
 85 |                 onChange={(e) => setPassword(e.target.value)}
 86 |                 className="w-full px-3 py-2 border border-border rounded-md bg-background text-foreground focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
 87 |                 placeholder="Enter your password"
 88 |                 required
 89 |                 disabled={isLoading}
 90 |               />
 91 |             </div>
 92 | 
 93 |             <div>
 94 |               <label htmlFor="confirmPassword" className="block text-sm font-medium text-foreground mb-1">
 95 |                 Confirm Password
 96 |               </label>
 97 |               <input
 98 |                 type="password"
 99 |                 id="confirmPassword"
100 |                 value={confirmPassword}
101 |                 onChange={(e) => setConfirmPassword(e.target.value)}
102 |                 className="w-full px-3 py-2 border border-border rounded-md bg-background text-foreground focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
103 |                 placeholder="Confirm your password"
104 |                 required
105 |                 disabled={isLoading}
106 |               />
107 |             </div>
108 | 
109 |             {error && (
110 |               <div className="p-3 bg-red-100 dark:bg-red-900/20 border border-red-300 dark:border-red-800 rounded-md">
111 |                 <p className="text-sm text-red-700 dark:text-red-400">{error}</p>
112 |               </div>
113 |             )}
114 | 
115 |             <button
116 |               type="submit"
117 |               disabled={isLoading}
118 |               className="w-full bg-blue-600 hover:bg-blue-700 disabled:bg-blue-400 text-white font-medium py-2 px-4 rounded-md transition-colors duration-200"
119 |             >
120 |               {isLoading ? 'Setting up...' : 'Create Account'}
121 |             </button>
122 |           </form>
123 | 
124 |           <div className="text-center">
125 |             <p className="text-sm text-muted-foreground">
126 |               This is a single-user system. Only one account can be created.
127 |             </p>
128 |           </div>
129 |         </div>
130 |       </div>
131 |     </div>
132 |   );
133 | };
134 | 
135 | export default SetupForm;


--------------------------------------------------------------------------------
/src/components/TaskCard.jsx:
--------------------------------------------------------------------------------
  1 | import React from 'react';
  2 | import { Clock, CheckCircle, Circle, AlertCircle, Pause, X, ArrowRight, ChevronUp, Minus, Flag } from 'lucide-react';
  3 | import { cn } from '../lib/utils';
  4 | import Tooltip from './Tooltip';
  5 | 
  6 | const TaskCard = ({ 
  7 |   task,
  8 |   onClick,
  9 |   showParent = false,
 10 |   className = ''
 11 | }) => {
 12 |   const getStatusConfig = (status) => {
 13 |     switch (status) {
 14 |       case 'done':
 15 |         return {
 16 |           icon: CheckCircle,
 17 |           bgColor: 'bg-green-50 dark:bg-green-950',
 18 |           borderColor: 'border-green-200 dark:border-green-800',
 19 |           iconColor: 'text-green-600 dark:text-green-400',
 20 |           textColor: 'text-green-900 dark:text-green-100',
 21 |           statusText: 'Done'
 22 |         };
 23 |       
 24 |       case 'in-progress':
 25 |         return {
 26 |           icon: Clock,
 27 |           bgColor: 'bg-blue-50 dark:bg-blue-950',
 28 |           borderColor: 'border-blue-200 dark:border-blue-800',
 29 |           iconColor: 'text-blue-600 dark:text-blue-400',
 30 |           textColor: 'text-blue-900 dark:text-blue-100',
 31 |           statusText: 'In Progress'
 32 |         };
 33 |       
 34 |       case 'review':
 35 |         return {
 36 |           icon: AlertCircle,
 37 |           bgColor: 'bg-amber-50 dark:bg-amber-950',
 38 |           borderColor: 'border-amber-200 dark:border-amber-800',
 39 |           iconColor: 'text-amber-600 dark:text-amber-400',
 40 |           textColor: 'text-amber-900 dark:text-amber-100',
 41 |           statusText: 'Review'
 42 |         };
 43 |       
 44 |       case 'deferred':
 45 |         return {
 46 |           icon: Pause,
 47 |           bgColor: 'bg-gray-50 dark:bg-gray-800',
 48 |           borderColor: 'border-gray-200 dark:border-gray-700',
 49 |           iconColor: 'text-gray-500 dark:text-gray-400',
 50 |           textColor: 'text-gray-700 dark:text-gray-300',
 51 |           statusText: 'Deferred'
 52 |         };
 53 |       
 54 |       case 'cancelled':
 55 |         return {
 56 |           icon: X,
 57 |           bgColor: 'bg-red-50 dark:bg-red-950',
 58 |           borderColor: 'border-red-200 dark:border-red-800',
 59 |           iconColor: 'text-red-600 dark:text-red-400',
 60 |           textColor: 'text-red-900 dark:text-red-100',
 61 |           statusText: 'Cancelled'
 62 |         };
 63 |       
 64 |       case 'pending':
 65 |       default:
 66 |         return {
 67 |           icon: Circle,
 68 |           bgColor: 'bg-slate-50 dark:bg-slate-800',
 69 |           borderColor: 'border-slate-200 dark:border-slate-700',
 70 |           iconColor: 'text-slate-500 dark:text-slate-400',
 71 |           textColor: 'text-slate-900 dark:text-slate-100',
 72 |           statusText: 'Pending'
 73 |         };
 74 |     }
 75 |   };
 76 | 
 77 |   const config = getStatusConfig(task.status);
 78 |   const Icon = config.icon;
 79 | 
 80 |   const getPriorityIcon = (priority) => {
 81 |     switch (priority) {
 82 |       case 'high':
 83 |         return (
 84 |           <Tooltip content="High Priority">
 85 |             <div className="w-4 h-4 bg-red-100 dark:bg-red-900/30 rounded flex items-center justify-center">
 86 |               <ChevronUp className="w-2.5 h-2.5 text-red-600 dark:text-red-400" />
 87 |             </div>
 88 |           </Tooltip>
 89 |         );
 90 |       case 'medium':
 91 |         return (
 92 |           <Tooltip content="Medium Priority">
 93 |             <div className="w-4 h-4 bg-amber-100 dark:bg-amber-900/30 rounded flex items-center justify-center">
 94 |               <Minus className="w-2.5 h-2.5 text-amber-600 dark:text-amber-400" />
 95 |             </div>
 96 |           </Tooltip>
 97 |         );
 98 |       case 'low':
 99 |         return (
100 |           <Tooltip content="Low Priority">
101 |             <div className="w-4 h-4 bg-blue-100 dark:bg-blue-900/30 rounded flex items-center justify-center">
102 |               <Circle className="w-1.5 h-1.5 text-blue-600 dark:text-blue-400 fill-current" />
103 |             </div>
104 |           </Tooltip>
105 |         );
106 |       default:
107 |         return (
108 |           <Tooltip content="No Priority Set">
109 |             <div className="w-4 h-4 bg-gray-100 dark:bg-gray-800 rounded flex items-center justify-center">
110 |               <Circle className="w-1.5 h-1.5 text-gray-400 dark:text-gray-500" />
111 |             </div>
112 |           </Tooltip>
113 |         );
114 |     }
115 |   };
116 | 
117 |   return (
118 |     <div
119 |       className={cn(
120 |         'bg-white dark:bg-gray-800 rounded-lg border border-gray-200 dark:border-gray-700',
121 |         'hover:shadow-md hover:border-blue-300 dark:hover:border-blue-600 transition-all duration-200 cursor-pointer',
122 |         'p-3 space-y-3',
123 |         onClick && 'hover:-translate-y-0.5',
124 |         className
125 |       )}
126 |       onClick={onClick}
127 |     >
128 |       {/* Header with Task ID, Title, and Priority */}
129 |       <div className="flex items-start justify-between gap-2 mb-2">
130 |         {/* Task ID and Title */}
131 |         <div className="flex-1 min-w-0">
132 |           <div className="flex items-center gap-2 mb-1">
133 |             <Tooltip content={`Task ID: ${task.id}`}>
134 |               <span className="text-xs font-mono text-gray-500 dark:text-gray-400 bg-gray-100 dark:bg-gray-700 px-2 py-0.5 rounded">
135 |                 {task.id}
136 |               </span>
137 |             </Tooltip>
138 |           </div>
139 |           <h3 className="font-medium text-sm text-gray-900 dark:text-white line-clamp-2 leading-tight">
140 |             {task.title}
141 |           </h3>
142 |           {showParent && task.parentId && (
143 |             <span className="text-xs text-gray-500 dark:text-gray-400 font-medium">
144 |               Task {task.parentId}
145 |             </span>
146 |           )}
147 |         </div>
148 |         
149 |         {/* Priority Icon */}
150 |         <div className="flex-shrink-0">
151 |           {getPriorityIcon(task.priority)}
152 |         </div>
153 |       </div>
154 | 
155 |       {/* Footer with Dependencies and Status */}
156 |       <div className="flex items-center justify-between">
157 |         {/* Dependencies */}
158 |         <div className="flex items-center">
159 |           {task.dependencies && Array.isArray(task.dependencies) && task.dependencies.length > 0 && (
160 |             <Tooltip content={`Depends on: ${task.dependencies.map(dep => `Task ${dep}`).join(', ')}`}>
161 |               <div className="flex items-center gap-1 text-xs text-amber-600 dark:text-amber-400">
162 |                 <ArrowRight className="w-3 h-3" />
163 |                 <span>Depends on: {task.dependencies.join(', ')}</span>
164 |               </div>
165 |             </Tooltip>
166 |           )}
167 |         </div>
168 | 
169 |         {/* Status Badge */}
170 |         <Tooltip content={`Status: ${config.statusText}`}>
171 |           <div className="flex items-center gap-1">
172 |             <div className={cn('w-2 h-2 rounded-full', config.iconColor.replace('text-', 'bg-'))} />
173 |             <span className={cn('text-xs font-medium', config.textColor)}>
174 |               {config.statusText}
175 |             </span>
176 |           </div>
177 |         </Tooltip>
178 |       </div>
179 | 
180 |       {/* Subtask Progress (if applicable) */}
181 |       {task.subtasks && task.subtasks.length > 0 && (
182 |         <div className="ml-3">
183 |           <div className="flex items-center gap-2 mb-1">
184 |             <span className="text-xs text-gray-500 dark:text-gray-400">Progress:</span>
185 |             <Tooltip content={`${task.subtasks.filter(st => st.status === 'done').length} of ${task.subtasks.length} subtasks completed`}>
186 |               <div className="flex-1 bg-gray-200 dark:bg-gray-700 rounded-full h-1.5">
187 |                 <div 
188 |                   className={cn(
189 |                     'h-full rounded-full transition-all duration-300',
190 |                     task.status === 'done' ? 'bg-green-500' : 'bg-blue-500'
191 |                   )}
192 |                   style={{
193 |                     width: `${Math.round((task.subtasks.filter(st => st.status === 'done').length / task.subtasks.length) * 100)}%`
194 |                   }}
195 |                 />
196 |               </div>
197 |             </Tooltip>
198 |             <Tooltip content={`${task.subtasks.filter(st => st.status === 'done').length} completed, ${task.subtasks.filter(st => st.status === 'pending').length} pending, ${task.subtasks.filter(st => st.status === 'in-progress').length} in progress`}>
199 |               <span className="text-xs text-gray-500 dark:text-gray-400">
200 |                 {task.subtasks.filter(st => st.status === 'done').length}/{task.subtasks.length}
201 |               </span>
202 |             </Tooltip>
203 |           </div>
204 |         </div>
205 |       )}
206 |     </div>
207 |   );
208 | };
209 | 
210 | export default TaskCard;


--------------------------------------------------------------------------------
/src/components/TaskIndicator.jsx:
--------------------------------------------------------------------------------
  1 | import React from 'react';
  2 | import { CheckCircle, Settings, X, AlertCircle } from 'lucide-react';
  3 | import { cn } from '../lib/utils';
  4 | 
  5 | /**
  6 |  * TaskIndicator Component
  7 |  * 
  8 |  * Displays TaskMaster status for projects in the sidebar with appropriate
  9 |  * icons and colors based on the project's TaskMaster configuration state.
 10 |  */
 11 | const TaskIndicator = ({ 
 12 |   status = 'not-configured', 
 13 |   size = 'sm',
 14 |   className = '',
 15 |   showLabel = false 
 16 | }) => {
 17 |   const getIndicatorConfig = () => {
 18 |     switch (status) {
 19 |       case 'fully-configured':
 20 |         return {
 21 |           icon: CheckCircle,
 22 |           color: 'text-green-500 dark:text-green-400',
 23 |           bgColor: 'bg-green-50 dark:bg-green-950',
 24 |           label: 'TaskMaster Ready',
 25 |           title: 'TaskMaster fully configured with MCP server'
 26 |         };
 27 |       
 28 |       case 'taskmaster-only':
 29 |         return {
 30 |           icon: Settings,
 31 |           color: 'text-blue-500 dark:text-blue-400',
 32 |           bgColor: 'bg-blue-50 dark:bg-blue-950',
 33 |           label: 'TaskMaster Init',
 34 |           title: 'TaskMaster initialized, MCP server needs setup'
 35 |         };
 36 |         
 37 |       case 'mcp-only':
 38 |         return {
 39 |           icon: AlertCircle,
 40 |           color: 'text-amber-500 dark:text-amber-400',
 41 |           bgColor: 'bg-amber-50 dark:bg-amber-950',
 42 |           label: 'MCP Ready',
 43 |           title: 'MCP server configured, TaskMaster needs initialization'
 44 |         };
 45 |       
 46 |       case 'not-configured':
 47 |       case 'error':
 48 |       default:
 49 |         return {
 50 |           icon: X,
 51 |           color: 'text-gray-400 dark:text-gray-500',
 52 |           bgColor: 'bg-gray-50 dark:bg-gray-900',
 53 |           label: 'No TaskMaster',
 54 |           title: 'TaskMaster not configured'
 55 |         };
 56 |     }
 57 |   };
 58 | 
 59 |   const config = getIndicatorConfig();
 60 |   const Icon = config.icon;
 61 |   
 62 |   const sizeClasses = {
 63 |     xs: 'w-3 h-3',
 64 |     sm: 'w-4 h-4', 
 65 |     md: 'w-5 h-5',
 66 |     lg: 'w-6 h-6'
 67 |   };
 68 | 
 69 |   const paddingClasses = {
 70 |     xs: 'p-0.5',
 71 |     sm: 'p-1',
 72 |     md: 'p-1.5', 
 73 |     lg: 'p-2'
 74 |   };
 75 | 
 76 |   if (showLabel) {
 77 |     return (
 78 |       <div 
 79 |         className={cn(
 80 |           'inline-flex items-center gap-1.5 text-xs rounded-md px-2 py-1 transition-colors',
 81 |           config.bgColor,
 82 |           config.color,
 83 |           className
 84 |         )}
 85 |         title={config.title}
 86 |       >
 87 |         <Icon className={sizeClasses[size]} />
 88 |         <span className="font-medium">{config.label}</span>
 89 |       </div>
 90 |     );
 91 |   }
 92 | 
 93 |   return (
 94 |     <div
 95 |       className={cn(
 96 |         'inline-flex items-center justify-center rounded-full transition-colors',
 97 |         config.bgColor,
 98 |         paddingClasses[size],
 99 |         className
100 |       )}
101 |       title={config.title}
102 |     >
103 |       <Icon className={cn(sizeClasses[size], config.color)} />
104 |     </div>
105 |   );
106 | };
107 | 
108 | export default TaskIndicator;


--------------------------------------------------------------------------------
/src/components/TaskMasterStatus.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react';
 2 | import { useTaskMaster } from '../contexts/TaskMasterContext';
 3 | import TaskIndicator from './TaskIndicator';
 4 | 
 5 | const TaskMasterStatus = () => {
 6 |   const { 
 7 |     currentProject, 
 8 |     projectTaskMaster, 
 9 |     mcpServerStatus,
10 |     isLoading,
11 |     isLoadingMCP,
12 |     error 
13 |   } = useTaskMaster();
14 | 
15 |   if (isLoading || isLoadingMCP) {
16 |     return (
17 |       <div className="flex items-center text-sm text-gray-500 dark:text-gray-400">
18 |         <div className="animate-spin w-3 h-3 border border-gray-300 border-t-blue-500 rounded-full mr-2"></div>
19 |         Loading TaskMaster status...
20 |       </div>
21 |     );
22 |   }
23 | 
24 |   if (error) {
25 |     return (
26 |       <div className="flex items-center text-sm text-red-500 dark:text-red-400">
27 |         <span className="w-2 h-2 bg-red-500 rounded-full mr-2"></span>
28 |         TaskMaster Error
29 |       </div>
30 |     );
31 |   }
32 | 
33 |   // Show MCP server status
34 |   const mcpConfigured = mcpServerStatus?.hasMCPServer && mcpServerStatus?.isConfigured;
35 |   
36 |   // Show project TaskMaster status
37 |   const projectConfigured = currentProject?.taskmaster?.hasTaskmaster;
38 |   const taskCount = currentProject?.taskmaster?.metadata?.taskCount || 0;
39 |   const completedCount = currentProject?.taskmaster?.metadata?.completed || 0;
40 | 
41 |   if (!currentProject) {
42 |     return (
43 |       <div className="flex items-center text-sm text-gray-500 dark:text-gray-400">
44 |         <span className="w-2 h-2 bg-gray-400 rounded-full mr-2"></span>
45 |         No project selected
46 |       </div>
47 |     );
48 |   }
49 | 
50 |   // Determine overall status for TaskIndicator
51 |   let overallStatus = 'not-configured';
52 |   if (projectConfigured && mcpConfigured) {
53 |     overallStatus = 'fully-configured';
54 |   } else if (projectConfigured) {
55 |     overallStatus = 'taskmaster-only';
56 |   } else if (mcpConfigured) {
57 |     overallStatus = 'mcp-only';
58 |   }
59 | 
60 |   return (
61 |     <div className="flex items-center gap-3">
62 |       {/* TaskMaster Status Indicator */}
63 |       <TaskIndicator 
64 |         status={overallStatus} 
65 |         size="md"
66 |         showLabel={true}
67 |       />
68 | 
69 |       {/* Task Progress Info */}
70 |       {projectConfigured && (
71 |         <div className="text-xs text-gray-600 dark:text-gray-400">
72 |           <span className="font-medium">
73 |             {completedCount}/{taskCount} tasks
74 |           </span>
75 |           {taskCount > 0 && (
76 |             <span className="ml-2 opacity-75">
77 |               ({Math.round((completedCount / taskCount) * 100)}%)
78 |             </span>
79 |           )}
80 |         </div>
81 |       )}
82 |     </div>
83 |   );
84 | };
85 | 
86 | export default TaskMasterStatus;


--------------------------------------------------------------------------------
/src/components/TodoList.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react';
 2 | import { Badge } from './ui/badge';
 3 | import { CheckCircle2, Clock, Circle } from 'lucide-react';
 4 | 
 5 | const TodoList = ({ todos, isResult = false }) => {
 6 |   if (!todos || !Array.isArray(todos)) {
 7 |     return null;
 8 |   }
 9 | 
10 |   const getStatusIcon = (status) => {
11 |     switch (status) {
12 |       case 'completed':
13 |         return <CheckCircle2 className="w-4 h-4 text-green-500 dark:text-green-400" />;
14 |       case 'in_progress':
15 |         return <Clock className="w-4 h-4 text-blue-500 dark:text-blue-400" />;
16 |       case 'pending':
17 |       default:
18 |         return <Circle className="w-4 h-4 text-gray-400 dark:text-gray-500" />;
19 |     }
20 |   };
21 | 
22 |   const getStatusColor = (status) => {
23 |     switch (status) {
24 |       case 'completed':
25 |         return 'bg-green-100 dark:bg-green-900/30 text-green-800 dark:text-green-200 border-green-200 dark:border-green-800';
26 |       case 'in_progress':
27 |         return 'bg-blue-100 dark:bg-blue-900/30 text-blue-800 dark:text-blue-200 border-blue-200 dark:border-blue-800';
28 |       case 'pending':
29 |       default:
30 |         return 'bg-gray-100 dark:bg-gray-800 text-gray-600 dark:text-gray-400 border-gray-200 dark:border-gray-700';
31 |     }
32 |   };
33 | 
34 |   const getPriorityColor = (priority) => {
35 |     switch (priority) {
36 |       case 'high':
37 |         return 'bg-red-100 dark:bg-red-900/30 text-red-700 dark:text-red-300 border-red-200 dark:border-red-800';
38 |       case 'medium':
39 |         return 'bg-yellow-100 dark:bg-yellow-900/30 text-yellow-700 dark:text-yellow-300 border-yellow-200 dark:border-yellow-800';
40 |       case 'low':
41 |       default:
42 |         return 'bg-gray-100 dark:bg-gray-800 text-gray-600 dark:text-gray-400 border-gray-200 dark:border-gray-700';
43 |     }
44 |   };
45 | 
46 |   return (
47 |     <div className="space-y-3">
48 |       {isResult && (
49 |         <div className="text-sm font-medium text-gray-700 dark:text-gray-300 mb-3">
50 |           Todo List ({todos.length} {todos.length === 1 ? 'item' : 'items'})
51 |         </div>
52 |       )}
53 |       
54 |       {todos.map((todo, index) => (
55 |         <div
56 |           key={todo.id || `todo-${index}`}
57 |           className="flex items-start gap-3 p-3 bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-lg shadow-sm hover:shadow-md dark:shadow-gray-900/50 transition-shadow"
58 |         >
59 |           <div className="flex-shrink-0 mt-0.5">
60 |             {getStatusIcon(todo.status)}
61 |           </div>
62 |           
63 |           <div className="flex-1 min-w-0">
64 |             <div className="flex items-start justify-between gap-2 mb-2">
65 |               <p className={`text-sm font-medium ${todo.status === 'completed' ? 'line-through text-gray-500 dark:text-gray-400' : 'text-gray-900 dark:text-gray-100'}`}>
66 |                 {todo.content}
67 |               </p>
68 |               
69 |               <div className="flex gap-1 flex-shrink-0">
70 |                 <Badge
71 |                   variant="outline"
72 |                   className={`text-xs px-2 py-0.5 ${getPriorityColor(todo.priority)}`}
73 |                 >
74 |                   {todo.priority}
75 |                 </Badge>
76 |                 <Badge
77 |                   variant="outline"
78 |                   className={`text-xs px-2 py-0.5 ${getStatusColor(todo.status)}`}
79 |                 >
80 |                   {todo.status.replace('_', ' ')}
81 |                 </Badge>
82 |               </div>
83 |             </div>
84 |           </div>
85 |         </div>
86 |       ))}
87 |     </div>
88 |   );
89 | };
90 | 
91 | export default TodoList;


--------------------------------------------------------------------------------
/src/components/Tooltip.jsx:
--------------------------------------------------------------------------------
 1 | import React, { useState } from 'react';
 2 | import { cn } from '../lib/utils';
 3 | 
 4 | const Tooltip = ({ 
 5 |   children, 
 6 |   content, 
 7 |   position = 'top',
 8 |   className = '',
 9 |   delay = 500
10 | }) => {
11 |   const [isVisible, setIsVisible] = useState(false);
12 |   const [timeoutId, setTimeoutId] = useState(null);
13 | 
14 |   const handleMouseEnter = () => {
15 |     const id = setTimeout(() => {
16 |       setIsVisible(true);
17 |     }, delay);
18 |     setTimeoutId(id);
19 |   };
20 | 
21 |   const handleMouseLeave = () => {
22 |     if (timeoutId) {
23 |       clearTimeout(timeoutId);
24 |       setTimeoutId(null);
25 |     }
26 |     setIsVisible(false);
27 |   };
28 | 
29 |   const getPositionClasses = () => {
30 |     switch (position) {
31 |       case 'top':
32 |         return 'bottom-full left-1/2 transform -translate-x-1/2 mb-2';
33 |       case 'bottom':
34 |         return 'top-full left-1/2 transform -translate-x-1/2 mt-2';
35 |       case 'left':
36 |         return 'right-full top-1/2 transform -translate-y-1/2 mr-2';
37 |       case 'right':
38 |         return 'left-full top-1/2 transform -translate-y-1/2 ml-2';
39 |       default:
40 |         return 'bottom-full left-1/2 transform -translate-x-1/2 mb-2';
41 |     }
42 |   };
43 | 
44 |   const getArrowClasses = () => {
45 |     switch (position) {
46 |       case 'top':
47 |         return 'top-full left-1/2 transform -translate-x-1/2 border-t-gray-900 dark:border-t-gray-100';
48 |       case 'bottom':
49 |         return 'bottom-full left-1/2 transform -translate-x-1/2 border-b-gray-900 dark:border-b-gray-100';
50 |       case 'left':
51 |         return 'left-full top-1/2 transform -translate-y-1/2 border-l-gray-900 dark:border-l-gray-100';
52 |       case 'right':
53 |         return 'right-full top-1/2 transform -translate-y-1/2 border-r-gray-900 dark:border-r-gray-100';
54 |       default:
55 |         return 'top-full left-1/2 transform -translate-x-1/2 border-t-gray-900 dark:border-t-gray-100';
56 |     }
57 |   };
58 | 
59 |   if (!content) {
60 |     return children;
61 |   }
62 | 
63 |   return (
64 |     <div 
65 |       className="relative inline-block"
66 |       onMouseEnter={handleMouseEnter}
67 |       onMouseLeave={handleMouseLeave}
68 |     >
69 |       {children}
70 |       
71 |       {isVisible && (
72 |         <div className={cn(
73 |           'absolute z-50 px-2 py-1 text-xs font-medium text-white bg-gray-900 dark:bg-gray-100 dark:text-gray-900 rounded shadow-lg whitespace-nowrap pointer-events-none',
74 |           'animate-in fade-in-0 zoom-in-95 duration-200',
75 |           getPositionClasses(),
76 |           className
77 |         )}>
78 |           {content}
79 |           
80 |           {/* Arrow */}
81 |           <div className={cn(
82 |             'absolute w-0 h-0 border-4 border-transparent',
83 |             getArrowClasses()
84 |           )} />
85 |         </div>
86 |       )}
87 |     </div>
88 |   );
89 | };
90 | 
91 | export default Tooltip;


--------------------------------------------------------------------------------
/src/components/ui/badge.jsx:
--------------------------------------------------------------------------------
 1 | import * as React from "react"
 2 | import { cva } from "class-variance-authority"
 3 | import { cn } from "../../lib/utils"
 4 | 
 5 | const badgeVariants = cva(
 6 |   "inline-flex items-center rounded-md border px-2.5 py-0.5 text-xs font-semibold transition-colors focus:outline-none focus:ring-2 focus:ring-ring focus:ring-offset-2",
 7 |   {
 8 |     variants: {
 9 |       variant: {
10 |         default:
11 |           "border-transparent bg-primary text-primary-foreground shadow hover:bg-primary/80",
12 |         secondary:
13 |           "border-transparent bg-secondary text-secondary-foreground hover:bg-secondary/80",
14 |         destructive:
15 |           "border-transparent bg-destructive text-destructive-foreground shadow hover:bg-destructive/80",
16 |         outline: "text-foreground",
17 |       },
18 |     },
19 |     defaultVariants: {
20 |       variant: "default",
21 |     },
22 |   }
23 | )
24 | 
25 | function Badge({ className, variant, ...props }) {
26 |   return (
27 |     <div className={cn(badgeVariants({ variant }), className)} {...props} />
28 |   )
29 | }
30 | 
31 | export { Badge, badgeVariants }


--------------------------------------------------------------------------------
/src/components/ui/button.jsx:
--------------------------------------------------------------------------------
 1 | import * as React from "react"
 2 | import { cva } from "class-variance-authority"
 3 | import { cn } from "../../lib/utils"
 4 | 
 5 | const buttonVariants = cva(
 6 |   "inline-flex items-center justify-center gap-2 whitespace-nowrap rounded-md text-sm font-medium transition-colors focus-visible:outline-none focus-visible:ring-1 focus-visible:ring-ring disabled:pointer-events-none disabled:opacity-50 [&_svg]:pointer-events-none [&_svg]:size-4 [&_svg]:shrink-0",
 7 |   {
 8 |     variants: {
 9 |       variant: {
10 |         default:
11 |           "bg-primary text-primary-foreground shadow hover:bg-primary/90",
12 |         destructive:
13 |           "bg-destructive text-destructive-foreground shadow-sm hover:bg-destructive/90",
14 |         outline:
15 |           "border border-input bg-background shadow-sm hover:bg-accent hover:text-accent-foreground",
16 |         secondary:
17 |           "bg-secondary text-secondary-foreground shadow-sm hover:bg-secondary/80",
18 |         ghost: "hover:bg-accent hover:text-accent-foreground",
19 |         link: "text-primary underline-offset-4 hover:underline",
20 |       },
21 |       size: {
22 |         default: "h-9 px-4 py-2",
23 |         sm: "h-8 rounded-md px-3 text-xs",
24 |         lg: "h-10 rounded-md px-8",
25 |         icon: "h-9 w-9",
26 |       },
27 |     },
28 |     defaultVariants: {
29 |       variant: "default",
30 |       size: "default",
31 |     },
32 |   }
33 | )
34 | 
35 | const Button = React.forwardRef(({ className, variant, size, ...props }, ref) => {
36 |   return (
37 |     <button
38 |       className={cn(buttonVariants({ variant, size, className }))}
39 |       ref={ref}
40 |       {...props}
41 |     />
42 |   )
43 | })
44 | Button.displayName = "Button"
45 | 
46 | export { Button, buttonVariants }


--------------------------------------------------------------------------------
/src/components/ui/input.jsx:
--------------------------------------------------------------------------------
 1 | import * as React from "react"
 2 | import { cn } from "../../lib/utils"
 3 | 
 4 | const Input = React.forwardRef(({ className, type, ...props }, ref) => {
 5 |   return (
 6 |     <input
 7 |       type={type}
 8 |       className={cn(
 9 |         "flex h-9 w-full rounded-md border border-input bg-transparent px-3 py-1 text-sm shadow-sm transition-colors file:border-0 file:bg-transparent file:text-sm file:font-medium file:text-foreground placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-1 focus-visible:ring-ring disabled:cursor-not-allowed disabled:opacity-50",
10 |         className
11 |       )}
12 |       ref={ref}
13 |       {...props}
14 |     />
15 |   )
16 | })
17 | Input.displayName = "Input"
18 | 
19 | export { Input }


--------------------------------------------------------------------------------
/src/components/ui/scroll-area.jsx:
--------------------------------------------------------------------------------
 1 | import * as React from "react"
 2 | import { cn } from "../../lib/utils"
 3 | 
 4 | const ScrollArea = React.forwardRef(({ className, children, ...props }, ref) => (
 5 |   <div
 6 |     ref={ref}
 7 |     className={cn("relative overflow-hidden", className)}
 8 |     {...props}
 9 |   >
10 |     <div 
11 |       className="h-full w-full rounded-[inherit] overflow-auto"
12 |       style={{
13 |         WebkitOverflowScrolling: 'touch',
14 |         touchAction: 'pan-y'
15 |       }}
16 |     >
17 |       {children}
18 |     </div>
19 |   </div>
20 | ))
21 | ScrollArea.displayName = "ScrollArea"
22 | 
23 | export { ScrollArea }


--------------------------------------------------------------------------------
/src/contexts/AuthContext.jsx:
--------------------------------------------------------------------------------
  1 | import React, { createContext, useContext, useEffect, useState } from 'react';
  2 | import { api } from '../utils/api';
  3 | 
  4 | const AuthContext = createContext({
  5 |   user: null,
  6 |   token: null,
  7 |   login: () => {},
  8 |   register: () => {},
  9 |   logout: () => {},
 10 |   isLoading: true,
 11 |   needsSetup: false,
 12 |   error: null
 13 | });
 14 | 
 15 | export const useAuth = () => {
 16 |   const context = useContext(AuthContext);
 17 |   if (!context) {
 18 |     throw new Error('useAuth must be used within an AuthProvider');
 19 |   }
 20 |   return context;
 21 | };
 22 | 
 23 | export const AuthProvider = ({ children }) => {
 24 |   const [user, setUser] = useState(null);
 25 |   const [token, setToken] = useState(localStorage.getItem('auth-token'));
 26 |   const [isLoading, setIsLoading] = useState(true);
 27 |   const [needsSetup, setNeedsSetup] = useState(false);
 28 |   const [error, setError] = useState(null);
 29 | 
 30 |   // Check authentication status on mount
 31 |   useEffect(() => {
 32 |     checkAuthStatus();
 33 |   }, []);
 34 | 
 35 |   const checkAuthStatus = async () => {
 36 |     try {
 37 |       setIsLoading(true);
 38 |       setError(null);
 39 |       
 40 |       // Check if system needs setup
 41 |       const statusResponse = await api.auth.status();
 42 |       const statusData = await statusResponse.json();
 43 |       
 44 |       if (statusData.needsSetup) {
 45 |         setNeedsSetup(true);
 46 |         setIsLoading(false);
 47 |         return;
 48 |       }
 49 |       
 50 |       // If we have a token, verify it
 51 |       if (token) {
 52 |         try {
 53 |           const userResponse = await api.auth.user();
 54 |           
 55 |           if (userResponse.ok) {
 56 |             const userData = await userResponse.json();
 57 |             setUser(userData.user);
 58 |             setNeedsSetup(false);
 59 |           } else {
 60 |             // Token is invalid
 61 |             localStorage.removeItem('auth-token');
 62 |             setToken(null);
 63 |             setUser(null);
 64 |           }
 65 |         } catch (error) {
 66 |           console.error('Token verification failed:', error);
 67 |           localStorage.removeItem('auth-token');
 68 |           setToken(null);
 69 |           setUser(null);
 70 |         }
 71 |       }
 72 |     } catch (error) {
 73 |       console.error('Auth status check failed:', error);
 74 |       setError('Failed to check authentication status');
 75 |     } finally {
 76 |       setIsLoading(false);
 77 |     }
 78 |   };
 79 | 
 80 |   const login = async (username, password) => {
 81 |     try {
 82 |       setError(null);
 83 |       const response = await api.auth.login(username, password);
 84 | 
 85 |       const data = await response.json();
 86 | 
 87 |       if (response.ok) {
 88 |         setToken(data.token);
 89 |         setUser(data.user);
 90 |         localStorage.setItem('auth-token', data.token);
 91 |         return { success: true };
 92 |       } else {
 93 |         setError(data.error || 'Login failed');
 94 |         return { success: false, error: data.error || 'Login failed' };
 95 |       }
 96 |     } catch (error) {
 97 |       console.error('Login error:', error);
 98 |       const errorMessage = 'Network error. Please try again.';
 99 |       setError(errorMessage);
100 |       return { success: false, error: errorMessage };
101 |     }
102 |   };
103 | 
104 |   const register = async (username, password) => {
105 |     try {
106 |       setError(null);
107 |       const response = await api.auth.register(username, password);
108 | 
109 |       const data = await response.json();
110 | 
111 |       if (response.ok) {
112 |         setToken(data.token);
113 |         setUser(data.user);
114 |         setNeedsSetup(false);
115 |         localStorage.setItem('auth-token', data.token);
116 |         return { success: true };
117 |       } else {
118 |         setError(data.error || 'Registration failed');
119 |         return { success: false, error: data.error || 'Registration failed' };
120 |       }
121 |     } catch (error) {
122 |       console.error('Registration error:', error);
123 |       const errorMessage = 'Network error. Please try again.';
124 |       setError(errorMessage);
125 |       return { success: false, error: errorMessage };
126 |     }
127 |   };
128 | 
129 |   const logout = () => {
130 |     setToken(null);
131 |     setUser(null);
132 |     localStorage.removeItem('auth-token');
133 |     
134 |     // Optional: Call logout endpoint for logging
135 |     if (token) {
136 |       api.auth.logout().catch(error => {
137 |         console.error('Logout endpoint error:', error);
138 |       });
139 |     }
140 |   };
141 | 
142 |   const value = {
143 |     user,
144 |     token,
145 |     login,
146 |     register,
147 |     logout,
148 |     isLoading,
149 |     needsSetup,
150 |     error
151 |   };
152 | 
153 |   return (
154 |     <AuthContext.Provider value={value}>
155 |       {children}
156 |     </AuthContext.Provider>
157 |   );
158 | };


--------------------------------------------------------------------------------
/src/contexts/TaskMasterContext.jsx:
--------------------------------------------------------------------------------
  1 | import React, { createContext, useContext, useEffect, useState, useCallback } from 'react';
  2 | import { api } from '../utils/api';
  3 | import { useAuth } from './AuthContext';
  4 | import { useWebSocketContext } from './WebSocketContext';
  5 | 
  6 | const TaskMasterContext = createContext({
  7 |   // TaskMaster project state
  8 |   projects: [],
  9 |   currentProject: null,
 10 |   projectTaskMaster: null,
 11 |   
 12 |   // MCP server state
 13 |   mcpServerStatus: null,
 14 |   
 15 |   // Tasks state
 16 |   tasks: [],
 17 |   nextTask: null,
 18 |   
 19 |   // Loading states
 20 |   isLoading: false,
 21 |   isLoadingTasks: false,
 22 |   isLoadingMCP: false,
 23 |   
 24 |   // Error state
 25 |   error: null,
 26 |   
 27 |   // Actions
 28 |   refreshProjects: () => {},
 29 |   setCurrentProject: () => {},
 30 |   refreshTasks: () => {},
 31 |   refreshMCPStatus: () => {},
 32 |   clearError: () => {}
 33 | });
 34 | 
 35 | export const useTaskMaster = () => {
 36 |   const context = useContext(TaskMasterContext);
 37 |   if (!context) {
 38 |     throw new Error('useTaskMaster must be used within a TaskMasterProvider');
 39 |   }
 40 |   return context;
 41 | };
 42 | 
 43 | export const TaskMasterProvider = ({ children }) => {
 44 |   // Get WebSocket messages from shared context to avoid duplicate connections
 45 |   const { messages } = useWebSocketContext();
 46 |   
 47 |   // Authentication context
 48 |   const { user, token, isLoading: authLoading } = useAuth();
 49 |   
 50 |   // State
 51 |   const [projects, setProjects] = useState([]);
 52 |   const [currentProject, setCurrentProjectState] = useState(null);
 53 |   const [projectTaskMaster, setProjectTaskMaster] = useState(null);
 54 |   const [mcpServerStatus, setMCPServerStatus] = useState(null);
 55 |   const [tasks, setTasks] = useState([]);
 56 |   const [nextTask, setNextTask] = useState(null);
 57 |   const [isLoading, setIsLoading] = useState(false);
 58 |   const [isLoadingTasks, setIsLoadingTasks] = useState(false);
 59 |   const [isLoadingMCP, setIsLoadingMCP] = useState(false);
 60 |   const [error, setError] = useState(null);
 61 | 
 62 |   // Helper to handle API errors
 63 |   const handleError = (error, context) => {
 64 |     console.error(`TaskMaster ${context} error:`, error);
 65 |     setError({
 66 |       message: error.message || `Failed to ${context}`,
 67 |       context,
 68 |       timestamp: new Date().toISOString()
 69 |     });
 70 |   };
 71 | 
 72 |   // Clear error state
 73 |   const clearError = useCallback(() => {
 74 |     setError(null);
 75 |   }, []);
 76 | 
 77 |   // This will be defined after the functions are declared
 78 | 
 79 |   // Refresh projects with TaskMaster metadata
 80 |   const refreshProjects = useCallback(async () => {
 81 |     // Only make API calls if user is authenticated
 82 |     if (!user || !token) {
 83 |       setProjects([]);
 84 |       setCurrentProjectState(null); // This might be the problem!
 85 |       return;
 86 |     }
 87 | 
 88 |     try {
 89 |       setIsLoading(true);
 90 |       clearError();
 91 |       const response = await api.get('/projects');
 92 |       
 93 |       if (!response.ok) {
 94 |         throw new Error(`Failed to fetch projects: ${response.status}`);
 95 |       }
 96 |       
 97 |       const projectsData = await response.json();
 98 |       
 99 |       // Check if projectsData is an array
100 |       if (!Array.isArray(projectsData)) {
101 |         console.error('Projects API returned non-array data:', projectsData);
102 |         setProjects([]);
103 |         return;
104 |       }
105 |       
106 |       // Filter and enrich projects with TaskMaster data
107 |       const enrichedProjects = projectsData.map(project => ({
108 |         ...project,
109 |         taskMasterConfigured: project.taskmaster?.hasTaskmaster || false,
110 |         taskMasterStatus: project.taskmaster?.status || 'not-configured',
111 |         taskCount: project.taskmaster?.metadata?.taskCount || 0,
112 |         completedCount: project.taskmaster?.metadata?.completed || 0
113 |       }));
114 |       
115 |       setProjects(enrichedProjects);
116 |       
117 |       // If current project is set, update its TaskMaster data
118 |       if (currentProject) {
119 |         const updatedCurrent = enrichedProjects.find(p => p.name === currentProject.name);
120 |         if (updatedCurrent) {
121 |           setCurrentProjectState(updatedCurrent);
122 |           setProjectTaskMaster(updatedCurrent.taskmaster);
123 |         }
124 |       }
125 |     } catch (err) {
126 |       handleError(err, 'load projects');
127 |     } finally {
128 |       setIsLoading(false);
129 |     }
130 |   }, [user, token]); // Remove currentProject dependency to avoid infinite loops
131 | 
132 |   // Set current project and load its TaskMaster details
133 |   const setCurrentProject = useCallback(async (project) => {
134 |     try {
135 |       setCurrentProjectState(project);
136 |       
137 |       // Clear previous project's data immediately when switching projects
138 |       setTasks([]);
139 |       setNextTask(null);
140 |       setProjectTaskMaster(null); // Clear previous TaskMaster data
141 |       
142 |       // Try to fetch fresh TaskMaster detection data for the project
143 |       if (project?.name) {
144 |         try {
145 |           const response = await api.get(`/taskmaster/detect/${encodeURIComponent(project.name)}`);
146 |           if (response.ok) {
147 |             const detectionData = await response.json();
148 |             setProjectTaskMaster(detectionData.taskmaster);
149 |           } else {
150 |             // If individual detection fails, fall back to project data from /api/projects
151 |             console.warn('Individual TaskMaster detection failed, using project data:', response.status);
152 |             setProjectTaskMaster(project.taskmaster || null);
153 |           }
154 |         } catch (detectionError) {
155 |           // If individual detection fails, fall back to project data from /api/projects  
156 |           console.warn('TaskMaster detection error, using project data:', detectionError.message);
157 |           setProjectTaskMaster(project.taskmaster || null);
158 |         }
159 |       } else {
160 |         setProjectTaskMaster(null);
161 |       }
162 |     } catch (err) {
163 |       console.error('Error in setCurrentProject:', err);
164 |       handleError(err, 'set current project');
165 |       // Fall back to project data if available
166 |       setProjectTaskMaster(project?.taskmaster || null);
167 |     }
168 |   }, []);
169 | 
170 |   // Refresh MCP server status
171 |   const refreshMCPStatus = useCallback(async () => {
172 |     // Only make API calls if user is authenticated
173 |     if (!user || !token) {
174 |       setMCPServerStatus(null);
175 |       return;
176 |     }
177 | 
178 |     try {
179 |       setIsLoadingMCP(true);
180 |       clearError();
181 |       const mcpStatus = await api.get('/mcp-utils/taskmaster-server');
182 |       setMCPServerStatus(mcpStatus);
183 |     } catch (err) {
184 |       handleError(err, 'check MCP server status');
185 |     } finally {
186 |       setIsLoadingMCP(false);
187 |     }
188 |   }, [user, token]);
189 | 
190 |   // Refresh tasks for current project - load real TaskMaster data
191 |   const refreshTasks = useCallback(async () => {
192 |     if (!currentProject) {
193 |       setTasks([]);
194 |       setNextTask(null);
195 |       return;
196 |     }
197 | 
198 |     // Only make API calls if user is authenticated
199 |     if (!user || !token) {
200 |       setTasks([]);
201 |       setNextTask(null);
202 |       return;
203 |     }
204 | 
205 |     try {
206 |       setIsLoadingTasks(true);
207 |       clearError();
208 |       
209 |       // Load tasks from the TaskMaster API endpoint
210 |       const response = await api.get(`/taskmaster/tasks/${encodeURIComponent(currentProject.name)}`);
211 |       
212 |       if (!response.ok) {
213 |         const errorData = await response.json();
214 |         throw new Error(errorData.message || 'Failed to load tasks');
215 |       }
216 |       
217 |       const data = await response.json();
218 |       
219 |       setTasks(data.tasks || []);
220 |       
221 |       // Find next task (pending or in-progress)
222 |       const nextTask = data.tasks?.find(task => 
223 |         task.status === 'pending' || task.status === 'in-progress'
224 |       ) || null;
225 |       setNextTask(nextTask);
226 |       
227 |       
228 |     } catch (err) {
229 |       console.error('Error loading tasks:', err);
230 |       handleError(err, 'load tasks');
231 |       // Set empty state on error
232 |       setTasks([]);
233 |       setNextTask(null);
234 |     } finally {
235 |       setIsLoadingTasks(false);
236 |     }
237 |   }, [currentProject, user, token]);
238 | 
239 |   // Load initial data on mount or when auth changes
240 |   useEffect(() => {
241 |     if (!authLoading && user && token) {
242 |       refreshProjects();
243 |       refreshMCPStatus();
244 |     } else {
245 |       console.log('Auth not ready or no user, skipping project load:', { authLoading, user: !!user, token: !!token });
246 |     }
247 |   }, [refreshProjects, refreshMCPStatus, authLoading, user, token]);
248 | 
249 |   // Clear errors when authentication changes
250 |   useEffect(() => {
251 |     if (user && token) {
252 |       clearError();
253 |     }
254 |   }, [user, token, clearError]);
255 | 
256 |   // Refresh tasks when current project changes
257 |   useEffect(() => {
258 |     if (currentProject?.name && user && token) {
259 |       refreshTasks();
260 |     }
261 |   }, [currentProject?.name, user, token, refreshTasks]);
262 | 
263 |   // Handle WebSocket messages for TaskMaster updates
264 |   useEffect(() => {
265 |     const latestMessage = messages[messages.length - 1];
266 |     if (!latestMessage) return;
267 | 
268 | 
269 |     switch (latestMessage.type) {
270 |       case 'taskmaster-project-updated':
271 |         // Refresh projects when TaskMaster state changes
272 |         if (latestMessage.projectName) {
273 |           refreshProjects();
274 |         }
275 |         break;
276 |         
277 |       case 'taskmaster-tasks-updated':
278 |         // Refresh tasks for the current project
279 |         if (latestMessage.projectName === currentProject?.name) {
280 |           refreshTasks();
281 |         }
282 |         break;
283 |         
284 |       case 'taskmaster-mcp-status-changed':
285 |         // Refresh MCP server status
286 |         refreshMCPStatus();
287 |         break;
288 |         
289 |       default:
290 |         // Ignore non-TaskMaster messages
291 |         break;
292 |     }
293 |   }, [messages, refreshProjects, refreshTasks, refreshMCPStatus, currentProject]);
294 | 
295 |   // Context value
296 |   const contextValue = {
297 |     // State
298 |     projects,
299 |     currentProject,
300 |     projectTaskMaster,
301 |     mcpServerStatus,
302 |     tasks,
303 |     nextTask,
304 |     isLoading,
305 |     isLoadingTasks,
306 |     isLoadingMCP,
307 |     error,
308 |     
309 |     // Actions
310 |     refreshProjects,
311 |     setCurrentProject,
312 |     refreshTasks,
313 |     refreshMCPStatus,
314 |     clearError
315 |   };
316 | 
317 |   return (
318 |     <TaskMasterContext.Provider value={contextValue}>
319 |       {children}
320 |     </TaskMasterContext.Provider>
321 |   );
322 | };
323 | 
324 | export default TaskMasterContext;


--------------------------------------------------------------------------------
/src/contexts/TasksSettingsContext.jsx:
--------------------------------------------------------------------------------
 1 | import React, { createContext, useContext, useState, useEffect } from 'react';
 2 | import { api } from '../utils/api';
 3 | 
 4 | const TasksSettingsContext = createContext({
 5 |   tasksEnabled: true,
 6 |   setTasksEnabled: () => {},
 7 |   toggleTasksEnabled: () => {},
 8 |   isTaskMasterInstalled: null,
 9 |   isTaskMasterReady: null,
10 |   installationStatus: null,
11 |   isCheckingInstallation: true
12 | });
13 | 
14 | export const useTasksSettings = () => {
15 |   const context = useContext(TasksSettingsContext);
16 |   if (!context) {
17 |     throw new Error('useTasksSettings must be used within a TasksSettingsProvider');
18 |   }
19 |   return context;
20 | };
21 | 
22 | export const TasksSettingsProvider = ({ children }) => {
23 |   const [tasksEnabled, setTasksEnabled] = useState(() => {
24 |     // Load from localStorage on initialization
25 |     const saved = localStorage.getItem('tasks-enabled');
26 |     return saved !== null ? JSON.parse(saved) : true; // Default to true
27 |   });
28 |   
29 |   const [isTaskMasterInstalled, setIsTaskMasterInstalled] = useState(null);
30 |   const [isTaskMasterReady, setIsTaskMasterReady] = useState(null);
31 |   const [installationStatus, setInstallationStatus] = useState(null);
32 |   const [isCheckingInstallation, setIsCheckingInstallation] = useState(true);
33 | 
34 |   // Save to localStorage whenever tasksEnabled changes
35 |   useEffect(() => {
36 |     localStorage.setItem('tasks-enabled', JSON.stringify(tasksEnabled));
37 |   }, [tasksEnabled]);
38 | 
39 |   // Check TaskMaster installation status asynchronously on component mount
40 |   useEffect(() => {
41 |     const checkInstallation = async () => {
42 |       try {
43 |         const response = await api.get('/taskmaster/installation-status');
44 |         if (response.ok) {
45 |           const data = await response.json();
46 |           setInstallationStatus(data);
47 |           setIsTaskMasterInstalled(data.installation?.isInstalled || false);
48 |           setIsTaskMasterReady(data.isReady || false);
49 |           
50 |           // If TaskMaster is not installed and user hasn't explicitly enabled tasks,
51 |           // disable tasks automatically
52 |           const userEnabledTasks = localStorage.getItem('tasks-enabled');
53 |           if (!data.installation?.isInstalled && !userEnabledTasks) {
54 |             setTasksEnabled(false);
55 |           }
56 |         } else {
57 |           console.error('Failed to check TaskMaster installation status');
58 |           setIsTaskMasterInstalled(false);
59 |           setIsTaskMasterReady(false);
60 |         }
61 |       } catch (error) {
62 |         console.error('Error checking TaskMaster installation:', error);
63 |         setIsTaskMasterInstalled(false);
64 |         setIsTaskMasterReady(false);
65 |       } finally {
66 |         setIsCheckingInstallation(false);
67 |       }
68 |     };
69 | 
70 |     // Run check asynchronously without blocking initial render
71 |     setTimeout(checkInstallation, 0);
72 |   }, []);
73 | 
74 |   const toggleTasksEnabled = () => {
75 |     setTasksEnabled(prev => !prev);
76 |   };
77 | 
78 |   const contextValue = {
79 |     tasksEnabled,
80 |     setTasksEnabled,
81 |     toggleTasksEnabled,
82 |     isTaskMasterInstalled,
83 |     isTaskMasterReady,
84 |     installationStatus,
85 |     isCheckingInstallation
86 |   };
87 | 
88 |   return (
89 |     <TasksSettingsContext.Provider value={contextValue}>
90 |       {children}
91 |     </TasksSettingsContext.Provider>
92 |   );
93 | };
94 | 
95 | export default TasksSettingsContext;


--------------------------------------------------------------------------------
/src/contexts/ThemeContext.jsx:
--------------------------------------------------------------------------------
 1 | import React, { createContext, useContext, useState, useEffect } from 'react';
 2 | 
 3 | const ThemeContext = createContext();
 4 | 
 5 | export const useTheme = () => {
 6 |   const context = useContext(ThemeContext);
 7 |   if (!context) {
 8 |     throw new Error('useTheme must be used within a ThemeProvider');
 9 |   }
10 |   return context;
11 | };
12 | 
13 | export const ThemeProvider = ({ children }) => {
14 |   // Check for saved theme preference or default to system preference
15 |   const [isDarkMode, setIsDarkMode] = useState(() => {
16 |     // Check localStorage first
17 |     const savedTheme = localStorage.getItem('theme');
18 |     if (savedTheme) {
19 |       return savedTheme === 'dark';
20 |     }
21 |     
22 |     // Check system preference
23 |     if (window.matchMedia) {
24 |       return window.matchMedia('(prefers-color-scheme: dark)').matches;
25 |     }
26 |     
27 |     return false;
28 |   });
29 | 
30 |   // Update document class and localStorage when theme changes
31 |   useEffect(() => {
32 |     if (isDarkMode) {
33 |       document.documentElement.classList.add('dark');
34 |       localStorage.setItem('theme', 'dark');
35 |       
36 |       // Update iOS status bar style and theme color for dark mode
37 |       const statusBarMeta = document.querySelector('meta[name="apple-mobile-web-app-status-bar-style"]');
38 |       if (statusBarMeta) {
39 |         statusBarMeta.setAttribute('content', 'black-translucent');
40 |       }
41 |       
42 |       const themeColorMeta = document.querySelector('meta[name="theme-color"]');
43 |       if (themeColorMeta) {
44 |         themeColorMeta.setAttribute('content', '#0c1117'); // Dark background color (hsl(222.2 84% 4.9%))
45 |       }
46 |     } else {
47 |       document.documentElement.classList.remove('dark');
48 |       localStorage.setItem('theme', 'light');
49 |       
50 |       // Update iOS status bar style and theme color for light mode
51 |       const statusBarMeta = document.querySelector('meta[name="apple-mobile-web-app-status-bar-style"]');
52 |       if (statusBarMeta) {
53 |         statusBarMeta.setAttribute('content', 'default');
54 |       }
55 |       
56 |       const themeColorMeta = document.querySelector('meta[name="theme-color"]');
57 |       if (themeColorMeta) {
58 |         themeColorMeta.setAttribute('content', '#ffffff'); // Light background color
59 |       }
60 |     }
61 |   }, [isDarkMode]);
62 | 
63 |   // Listen for system theme changes
64 |   useEffect(() => {
65 |     if (!window.matchMedia) return;
66 | 
67 |     const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)');
68 |     const handleChange = (e) => {
69 |       // Only update if user hasn't manually set a preference
70 |       const savedTheme = localStorage.getItem('theme');
71 |       if (!savedTheme) {
72 |         setIsDarkMode(e.matches);
73 |       }
74 |     };
75 | 
76 |     mediaQuery.addEventListener('change', handleChange);
77 |     return () => mediaQuery.removeEventListener('change', handleChange);
78 |   }, []);
79 | 
80 |   const toggleDarkMode = () => {
81 |     setIsDarkMode(prev => !prev);
82 |   };
83 | 
84 |   const value = {
85 |     isDarkMode,
86 |     toggleDarkMode,
87 |   };
88 | 
89 |   return (
90 |     <ThemeContext.Provider value={value}>
91 |       {children}
92 |     </ThemeContext.Provider>
93 |   );
94 | };


--------------------------------------------------------------------------------
/src/contexts/WebSocketContext.jsx:
--------------------------------------------------------------------------------
 1 | import React, { createContext, useContext } from 'react';
 2 | import { useWebSocket } from '../utils/websocket';
 3 | 
 4 | const WebSocketContext = createContext({
 5 |   ws: null,
 6 |   sendMessage: () => {},
 7 |   messages: [],
 8 |   isConnected: false
 9 | });
10 | 
11 | export const useWebSocketContext = () => {
12 |   const context = useContext(WebSocketContext);
13 |   if (!context) {
14 |     throw new Error('useWebSocketContext must be used within a WebSocketProvider');
15 |   }
16 |   return context;
17 | };
18 | 
19 | export const WebSocketProvider = ({ children }) => {
20 |   const webSocketData = useWebSocket();
21 |   
22 |   return (
23 |     <WebSocketContext.Provider value={webSocketData}>
24 |       {children}
25 |     </WebSocketContext.Provider>
26 |   );
27 | };
28 | 
29 | export default WebSocketContext;


--------------------------------------------------------------------------------
/src/hooks/useAudioRecorder.js:
--------------------------------------------------------------------------------
  1 | import { useState, useRef, useCallback } from 'react';
  2 | 
  3 | export function useAudioRecorder() {
  4 |   const [isRecording, setRecording] = useState(false);
  5 |   const [audioBlob, setAudioBlob] = useState(null);
  6 |   const [error, setError] = useState(null);
  7 |   const mediaRecorderRef = useRef(null);
  8 |   const streamRef = useRef(null);
  9 |   const chunksRef = useRef([]);
 10 | 
 11 |   const start = useCallback(async () => {
 12 |     try {
 13 |       setError(null);
 14 |       setAudioBlob(null);
 15 |       chunksRef.current = [];
 16 | 
 17 |       // Request microphone access
 18 |       const stream = await navigator.mediaDevices.getUserMedia({ 
 19 |         audio: {
 20 |           echoCancellation: true,
 21 |           noiseSuppression: true,
 22 |           sampleRate: 16000,
 23 |         } 
 24 |       });
 25 |       
 26 |       streamRef.current = stream;
 27 | 
 28 |       // Determine supported MIME type
 29 |       const mimeType = MediaRecorder.isTypeSupported('audio/webm') 
 30 |         ? 'audio/webm' 
 31 |         : 'audio/mp4';
 32 |       
 33 |       // Create media recorder
 34 |       const recorder = new MediaRecorder(stream, { mimeType });
 35 |       mediaRecorderRef.current = recorder;
 36 | 
 37 |       // Set up event handlers
 38 |       recorder.ondataavailable = (e) => {
 39 |         if (e.data.size > 0) {
 40 |           chunksRef.current.push(e.data);
 41 |         }
 42 |       };
 43 | 
 44 |       recorder.onstop = () => {
 45 |         // Create blob from chunks
 46 |         const blob = new Blob(chunksRef.current, { type: mimeType });
 47 |         setAudioBlob(blob);
 48 |         
 49 |         // Clean up stream
 50 |         if (streamRef.current) {
 51 |           streamRef.current.getTracks().forEach(track => track.stop());
 52 |           streamRef.current = null;
 53 |         }
 54 |       };
 55 | 
 56 |       recorder.onerror = (event) => {
 57 |         console.error('MediaRecorder error:', event);
 58 |         setError('Recording failed');
 59 |         setRecording(false);
 60 |       };
 61 | 
 62 |       // Start recording
 63 |       recorder.start();
 64 |       setRecording(true);
 65 |       console.log('Recording started');
 66 |     } catch (err) {
 67 |       console.error('Failed to start recording:', err);
 68 |       setError(err.message || 'Failed to start recording');
 69 |       setRecording(false);
 70 |     }
 71 |   }, []);
 72 | 
 73 |   const stop = useCallback(() => {
 74 |     console.log('Stop called, recorder state:', mediaRecorderRef.current?.state);
 75 |     
 76 |     try {
 77 |       if (mediaRecorderRef.current && mediaRecorderRef.current.state === 'recording') {
 78 |         mediaRecorderRef.current.stop();
 79 |         console.log('Recording stopped');
 80 |       }
 81 |     } catch (err) {
 82 |       console.error('Error stopping recorder:', err);
 83 |     }
 84 |     
 85 |     // Always update state
 86 |     setRecording(false);
 87 |     
 88 |     // Clean up stream if still active
 89 |     if (streamRef.current) {
 90 |       streamRef.current.getTracks().forEach(track => track.stop());
 91 |       streamRef.current = null;
 92 |     }
 93 |   }, []);
 94 | 
 95 |   const reset = useCallback(() => {
 96 |     setAudioBlob(null);
 97 |     setError(null);
 98 |     chunksRef.current = [];
 99 |   }, []);
100 | 
101 |   return { 
102 |     isRecording, 
103 |     audioBlob, 
104 |     error,
105 |     start, 
106 |     stop, 
107 |     reset 
108 |   };
109 | }


--------------------------------------------------------------------------------
/src/hooks/useVersionCheck.js:
--------------------------------------------------------------------------------
 1 | // hooks/useVersionCheck.js
 2 | import { useState, useEffect } from 'react';
 3 | import { version } from '../../package.json';
 4 | 
 5 | export const useVersionCheck = (owner, repo) => {
 6 |   const [updateAvailable, setUpdateAvailable] = useState(false);
 7 |   const [latestVersion, setLatestVersion] = useState(null);
 8 | 
 9 |   useEffect(() => {
10 |     const checkVersion = async () => {
11 |       try {
12 |         const response = await fetch(`https://api.github.com/repos/${owner}/${repo}/releases/latest`);
13 |         const data = await response.json();
14 |         
15 |         // Handle the case where there might not be any releases
16 |         if (data.tag_name) {
17 |           const latest = data.tag_name.replace(/^v/, '');
18 |           setLatestVersion(latest);
19 |           setUpdateAvailable(version !== latest);
20 |         } else {
21 |           // No releases found, don't show update notification
22 |           setUpdateAvailable(false);
23 |           setLatestVersion(null);
24 |         }
25 |       } catch (error) {
26 |         console.error('Version check failed:', error);
27 |         // On error, don't show update notification
28 |         setUpdateAvailable(false);
29 |         setLatestVersion(null);
30 |       }
31 |     };
32 | 
33 |     checkVersion();
34 |     const interval = setInterval(checkVersion, 5 * 60 * 1000); // Check every 5 minutes
35 |     return () => clearInterval(interval);
36 |   }, [owner, repo]);
37 | 
38 |   return { updateAvailable, latestVersion, currentVersion: version };
39 | }; 


--------------------------------------------------------------------------------
/src/lib/utils.js:
--------------------------------------------------------------------------------
1 | import { clsx } from "clsx"
2 | import { twMerge } from "tailwind-merge"
3 | 
4 | export function cn(...inputs) {
5 |   return twMerge(clsx(inputs))
6 | }


--------------------------------------------------------------------------------
/src/main.jsx:
--------------------------------------------------------------------------------
 1 | import React from 'react'
 2 | import ReactDOM from 'react-dom/client'
 3 | import App from './App.jsx'
 4 | import './index.css'
 5 | 
 6 | ReactDOM.createRoot(document.getElementById('root')).render(
 7 |   <React.StrictMode>
 8 |     <App />
 9 |   </React.StrictMode>,
10 | )


--------------------------------------------------------------------------------
/src/utils/api.js:
--------------------------------------------------------------------------------
  1 | // Utility function for authenticated API calls
  2 | export const authenticatedFetch = (url, options = {}) => {
  3 |   const token = localStorage.getItem('auth-token');
  4 |   
  5 |   const defaultHeaders = {
  6 |     'Content-Type': 'application/json',
  7 |   };
  8 |   
  9 |   if (token) {
 10 |     defaultHeaders['Authorization'] = `Bearer ${token}`;
 11 |   }
 12 |   
 13 |   return fetch(url, {
 14 |     ...options,
 15 |     headers: {
 16 |       ...defaultHeaders,
 17 |       ...options.headers,
 18 |     },
 19 |   });
 20 | };
 21 | 
 22 | // API endpoints
 23 | export const api = {
 24 |   // Auth endpoints (no token required)
 25 |   auth: {
 26 |     status: () => fetch('/api/auth/status'),
 27 |     login: (username, password) => fetch('/api/auth/login', {
 28 |       method: 'POST',
 29 |       headers: { 'Content-Type': 'application/json' },
 30 |       body: JSON.stringify({ username, password }),
 31 |     }),
 32 |     register: (username, password) => fetch('/api/auth/register', {
 33 |       method: 'POST',
 34 |       headers: { 'Content-Type': 'application/json' },
 35 |       body: JSON.stringify({ username, password }),
 36 |     }),
 37 |     user: () => authenticatedFetch('/api/auth/user'),
 38 |     logout: () => authenticatedFetch('/api/auth/logout', { method: 'POST' }),
 39 |   },
 40 |   
 41 |   // Protected endpoints
 42 |   config: () => authenticatedFetch('/api/config'),
 43 |   projects: () => authenticatedFetch('/api/projects'),
 44 |   sessions: (projectName, limit = 5, offset = 0) => 
 45 |     authenticatedFetch(`/api/projects/${projectName}/sessions?limit=${limit}&offset=${offset}`),
 46 |   sessionMessages: (projectName, sessionId, limit = null, offset = 0) => {
 47 |     const params = new URLSearchParams();
 48 |     if (limit !== null) {
 49 |       params.append('limit', limit);
 50 |       params.append('offset', offset);
 51 |     }
 52 |     const queryString = params.toString();
 53 |     const url = `/api/projects/${projectName}/sessions/${sessionId}/messages${queryString ? `?${queryString}` : ''}`;
 54 |     return authenticatedFetch(url);
 55 |   },
 56 |   renameProject: (projectName, displayName) =>
 57 |     authenticatedFetch(`/api/projects/${projectName}/rename`, {
 58 |       method: 'PUT',
 59 |       body: JSON.stringify({ displayName }),
 60 |     }),
 61 |   deleteSession: (projectName, sessionId) =>
 62 |     authenticatedFetch(`/api/projects/${projectName}/sessions/${sessionId}`, {
 63 |       method: 'DELETE',
 64 |     }),
 65 |   deleteProject: (projectName) =>
 66 |     authenticatedFetch(`/api/projects/${projectName}`, {
 67 |       method: 'DELETE',
 68 |     }),
 69 |   createProject: (path) =>
 70 |     authenticatedFetch('/api/projects/create', {
 71 |       method: 'POST',
 72 |       body: JSON.stringify({ path }),
 73 |     }),
 74 |   readFile: (projectName, filePath) =>
 75 |     authenticatedFetch(`/api/projects/${projectName}/file?filePath=${encodeURIComponent(filePath)}`),
 76 |   saveFile: (projectName, filePath, content) =>
 77 |     authenticatedFetch(`/api/projects/${projectName}/file`, {
 78 |       method: 'PUT',
 79 |       body: JSON.stringify({ filePath, content }),
 80 |     }),
 81 |   getFiles: (projectName) =>
 82 |     authenticatedFetch(`/api/projects/${projectName}/files`),
 83 |   transcribe: (formData) =>
 84 |     authenticatedFetch('/api/transcribe', {
 85 |       method: 'POST',
 86 |       body: formData,
 87 |       headers: {}, // Let browser set Content-Type for FormData
 88 |     }),
 89 | 
 90 |   // TaskMaster endpoints
 91 |   taskmaster: {
 92 |     // Initialize TaskMaster in a project
 93 |     init: (projectName) => 
 94 |       authenticatedFetch(`/api/taskmaster/init/${projectName}`, {
 95 |         method: 'POST',
 96 |       }),
 97 |     
 98 |     // Add a new task
 99 |     addTask: (projectName, { prompt, title, description, priority, dependencies }) =>
100 |       authenticatedFetch(`/api/taskmaster/add-task/${projectName}`, {
101 |         method: 'POST',
102 |         body: JSON.stringify({ prompt, title, description, priority, dependencies }),
103 |       }),
104 |     
105 |     // Parse PRD to generate tasks
106 |     parsePRD: (projectName, { fileName, numTasks, append }) =>
107 |       authenticatedFetch(`/api/taskmaster/parse-prd/${projectName}`, {
108 |         method: 'POST',
109 |         body: JSON.stringify({ fileName, numTasks, append }),
110 |       }),
111 | 
112 |     // Get available PRD templates
113 |     getTemplates: () =>
114 |       authenticatedFetch('/api/taskmaster/prd-templates'),
115 | 
116 |     // Apply a PRD template
117 |     applyTemplate: (projectName, { templateId, fileName, customizations }) =>
118 |       authenticatedFetch(`/api/taskmaster/apply-template/${projectName}`, {
119 |         method: 'POST',
120 |         body: JSON.stringify({ templateId, fileName, customizations }),
121 |       }),
122 | 
123 |     // Update a task
124 |     updateTask: (projectName, taskId, updates) =>
125 |       authenticatedFetch(`/api/taskmaster/update-task/${projectName}/${taskId}`, {
126 |         method: 'PUT',
127 |         body: JSON.stringify(updates),
128 |       }),
129 |   },
130 |   
131 |   // Generic GET method for any endpoint
132 |   get: (endpoint) => authenticatedFetch(`/api${endpoint}`),
133 | };


--------------------------------------------------------------------------------
/src/utils/websocket.js:
--------------------------------------------------------------------------------
  1 | import { useState, useEffect, useRef } from 'react';
  2 | 
  3 | export function useWebSocket() {
  4 |   const [ws, setWs] = useState(null);
  5 |   const [messages, setMessages] = useState([]);
  6 |   const [isConnected, setIsConnected] = useState(false);
  7 |   const reconnectTimeoutRef = useRef(null);
  8 | 
  9 |   useEffect(() => {
 10 |     connect();
 11 |     
 12 |     return () => {
 13 |       if (reconnectTimeoutRef.current) {
 14 |         clearTimeout(reconnectTimeoutRef.current);
 15 |       }
 16 |       if (ws) {
 17 |         ws.close();
 18 |       }
 19 |     };
 20 |   }, []); // Keep dependency array but add proper cleanup
 21 | 
 22 |   const connect = async () => {
 23 |     try {
 24 |       // Get authentication token
 25 |       const token = localStorage.getItem('auth-token');
 26 |       if (!token) {
 27 |         console.warn('No authentication token found for WebSocket connection');
 28 |         return;
 29 |       }
 30 |       
 31 |       // Fetch server configuration to get the correct WebSocket URL
 32 |       let wsBaseUrl;
 33 |       try {
 34 |         const configResponse = await fetch('/api/config', {
 35 |           headers: {
 36 |             'Authorization': `Bearer ${token}`
 37 |           }
 38 |         });
 39 |         const config = await configResponse.json();
 40 |         wsBaseUrl = config.wsUrl;
 41 |         
 42 |         // If the config returns localhost but we're not on localhost, use current host but with API server port
 43 |         if (wsBaseUrl.includes('localhost') && !window.location.hostname.includes('localhost')) {
 44 |           console.warn('Config returned localhost, using current host with API server port instead');
 45 |           const protocol = window.location.protocol === 'https:' ? 'wss:' : 'ws:';
 46 |           // For development, API server is typically on port 3002 when Vite is on 3001
 47 |           const apiPort = window.location.port === '3001' ? '3002' : window.location.port;
 48 |           wsBaseUrl = `${protocol}//${window.location.hostname}:${apiPort}`;
 49 |         }
 50 |       } catch (error) {
 51 |         console.warn('Could not fetch server config, falling back to current host with API server port');
 52 |         const protocol = window.location.protocol === 'https:' ? 'wss:' : 'ws:';
 53 |         // For development, API server is typically on port 3002 when Vite is on 3001
 54 |         const apiPort = window.location.port === '3001' ? '3002' : window.location.port;
 55 |         wsBaseUrl = `${protocol}//${window.location.hostname}:${apiPort}`;
 56 |       }
 57 |       
 58 |       // Include token in WebSocket URL as query parameter
 59 |       const wsUrl = `${wsBaseUrl}/ws?token=${encodeURIComponent(token)}`;
 60 |       const websocket = new WebSocket(wsUrl);
 61 | 
 62 |       websocket.onopen = () => {
 63 |         setIsConnected(true);
 64 |         setWs(websocket);
 65 |       };
 66 | 
 67 |       websocket.onmessage = (event) => {
 68 |         try {
 69 |           const data = JSON.parse(event.data);
 70 |           setMessages(prev => [...prev, data]);
 71 |         } catch (error) {
 72 |           console.error('Error parsing WebSocket message:', error);
 73 |         }
 74 |       };
 75 | 
 76 |       websocket.onclose = () => {
 77 |         setIsConnected(false);
 78 |         setWs(null);
 79 |         
 80 |         // Attempt to reconnect after 3 seconds
 81 |         reconnectTimeoutRef.current = setTimeout(() => {
 82 |           connect();
 83 |         }, 3000);
 84 |       };
 85 | 
 86 |       websocket.onerror = (error) => {
 87 |         console.error('WebSocket error:', error);
 88 |       };
 89 | 
 90 |     } catch (error) {
 91 |       console.error('Error creating WebSocket connection:', error);
 92 |     }
 93 |   };
 94 | 
 95 |   const sendMessage = (message) => {
 96 |     if (ws && isConnected) {
 97 |       ws.send(JSON.stringify(message));
 98 |     } else {
 99 |       console.warn('WebSocket not connected');
100 |     }
101 |   };
102 | 
103 |   return {
104 |     ws,
105 |     sendMessage,
106 |     messages,
107 |     isConnected
108 |   };
109 | }


--------------------------------------------------------------------------------
/src/utils/whisper.js:
--------------------------------------------------------------------------------
 1 | import { api } from './api';
 2 | 
 3 | export async function transcribeWithWhisper(audioBlob, onStatusChange) {
 4 |     const formData = new FormData();
 5 |     const fileName = `recording_${Date.now()}.webm`;
 6 |     const file = new File([audioBlob], fileName, { type: audioBlob.type });
 7 |     
 8 |     formData.append('audio', file);
 9 |     
10 |     const whisperMode = window.localStorage.getItem('whisperMode') || 'default';
11 |     formData.append('mode', whisperMode);
12 |   
13 |     try {
14 |       // Start with transcribing state
15 |       if (onStatusChange) {
16 |         onStatusChange('transcribing');
17 |       }
18 |   
19 |       const response = await api.transcribe(formData);
20 |   
21 |       if (!response.ok) {
22 |         const errorData = await response.json().catch(() => ({}));
23 |         throw new Error(
24 |           errorData.error || 
25 |           `Transcription error: ${response.status} ${response.statusText}`
26 |         );
27 |       }
28 |   
29 |       const data = await response.json();
30 |       return data.text || '';
31 |     } catch (error) {
32 |       if (error.name === 'TypeError' && error.message.includes('fetch')) {
33 |         throw new Error('Cannot connect to server. Please ensure the backend is running.');
34 |       }
35 |       throw error;
36 |     }
37 |   }


--------------------------------------------------------------------------------
/tailwind.config.js:
--------------------------------------------------------------------------------
 1 | /** @type {import('tailwindcss').Config} */
 2 | export default {
 3 |   darkMode: ["class"],
 4 |   content: [
 5 |     "./index.html",
 6 |     "./src/**/*.{js,ts,jsx,tsx}",
 7 |   ],
 8 |   theme: {
 9 |     container: {
10 |       center: true,
11 |       padding: "2rem",
12 |       screens: {
13 |         "2xl": "1400px",
14 |       },
15 |     },
16 |     extend: {
17 |       colors: {
18 |         border: "hsl(var(--border))",
19 |         input: "hsl(var(--input))",
20 |         ring: "hsl(var(--ring))",
21 |         background: "hsl(var(--background))",
22 |         foreground: "hsl(var(--foreground))",
23 |         primary: {
24 |           DEFAULT: "hsl(var(--primary))",
25 |           foreground: "hsl(var(--primary-foreground))",
26 |         },
27 |         secondary: {
28 |           DEFAULT: "hsl(var(--secondary))",
29 |           foreground: "hsl(var(--secondary-foreground))",
30 |         },
31 |         destructive: {
32 |           DEFAULT: "hsl(var(--destructive))",
33 |           foreground: "hsl(var(--destructive-foreground))",
34 |         },
35 |         muted: {
36 |           DEFAULT: "hsl(var(--muted))",
37 |           foreground: "hsl(var(--muted-foreground))",
38 |         },
39 |         accent: {
40 |           DEFAULT: "hsl(var(--accent))",
41 |           foreground: "hsl(var(--accent-foreground))",
42 |         },
43 |         popover: {
44 |           DEFAULT: "hsl(var(--popover))",
45 |           foreground: "hsl(var(--popover-foreground))",
46 |         },
47 |         card: {
48 |           DEFAULT: "hsl(var(--card))",
49 |           foreground: "hsl(var(--card-foreground))",
50 |         },
51 |       },
52 |       borderRadius: {
53 |         lg: "var(--radius)",
54 |         md: "calc(var(--radius) - 2px)",
55 |         sm: "calc(var(--radius) - 4px)",
56 |       },
57 |       spacing: {
58 |         'safe-area-inset-bottom': 'env(safe-area-inset-bottom)',
59 |       },
60 |     },
61 |   },
62 |   plugins: [require('@tailwindcss/typography')],
63 | }


--------------------------------------------------------------------------------
/test.html:
--------------------------------------------------------------------------------
1 | hello world 5
2 | 


--------------------------------------------------------------------------------
/vite.config.js:
--------------------------------------------------------------------------------
 1 | import { defineConfig, loadEnv } from 'vite'
 2 | import react from '@vitejs/plugin-react'
 3 | 
 4 | export default defineConfig(({ command, mode }) => {
 5 |   // Load env file based on `mode` in the current working directory.
 6 |   const env = loadEnv(mode, process.cwd(), '')
 7 |   
 8 |   
 9 |   return {
10 |     plugins: [react()],
11 |     server: {
12 |       port: parseInt(env.VITE_PORT) || 5173,
13 |       proxy: {
14 |         '/api': `http://localhost:${env.PORT || 3001}`,
15 |         '/ws': {
16 |           target: `ws://localhost:${env.PORT || 3001}`,
17 |           ws: true
18 |         },
19 |         '/shell': {
20 |           target: `ws://localhost:${env.PORT || 3002}`,
21 |           ws: true
22 |         }
23 |       }
24 |     },
25 |     build: {
26 |       outDir: 'dist'
27 |     }
28 |   }
29 | })


--------------------------------------------------------------------------------