# Habit Tracker

> **Forked from:** [nicopanozo/habit-tracker](https://github.com/nicopanozo/habit-tracker)  
> **Deployed at:** [http://38.242.140.239:8080](http://38.242.140.239:8080)  
> **CI/CD:** GitHub Actions → Docker → VPS

A modern, responsive habit tracking application built with React and TypeScript. Track your daily habits, monitor progress, and build consistency with an intuitive and visually appealing interface.

## 🔄 This Fork

This fork adds:
- **CI/CD Pipeline:** Automated Docker builds and deployment to VPS
- **Security Scanning:** Trivy vulnerability scanning on every push
- **Production Deployment:** Containerized app running on personal VPS
- **GitHub Container Registry:** Images stored at `ghcr.io/lawrencemwangi496-design/react-habit-tracker`

## 🚀 Deployment

### Automatic (via GitHub Actions)
On every push to `main` or `master`:
1. Builds Docker image
2. Pushes to GitHub Container Registry
3. Deploys to VPS (port 8080)
4. Runs security scan

### Manual
```bash
# Build locally
npm run build
docker build -t react-habit-tracker .

# Run container
docker run -d -p 8080:80 --name habit-tracker react-habit-tracker
```

## 🔒 Security

Daily security scans via GitHub Actions (Trivy). Current vulnerabilities tracked in [security_reports](https://github.com/lawrencemwangi496-design/security_reports).

---
*Original project below*

Habit Tracker Preview

## 🌟 Features
- Habit Management: Create, edit, and delete habits with custom names and colors
- Weekly Tracking: Track habits on a 7-day weekly basis with visual checkboxes
- Progress Visualization: Progress bars and completion percentages for each habit
- Streak Tracking: Monitor consecutive days of habit completion
- Filtering & Search: Filter habits by completion status and search by name
- Sorting Options: Sort habits by name, streak length, or creation date
- Dark/Light Theme: Toggle between dark and light themes
- Responsive Design: Fully responsive design that works on all devices
- Local Storage: Automatically saves your progress locally
- Accessibility: WCAG compliant with keyboard navigation and screen reader support

## 🏗️ Tech Stack

- **React 19** - UI library
- **TypeScript** - Type safety
- **Vite** - Build tool and dev server
- **CSS3** - Styling
- **Lucide React** - Icons
- **ESLint** - Code linting
- **Prettier** - Code formatting

## 🔧 Development Guidelines

This project uses ESLint and Prettier for code quality and formatting:

- Code is automatically formatted on save
- Run `npm run lint` to check for issues
- Run `npm run format` to format all files
- Follow the established TypeScript and React best practices

## 📱 Screenshots

### Light Theme (Desktop)

<img src="./habit-tracker/public/screenshots/image.png" alt="App screenshot 1" width="600" />

### Dark Theme (Desktop)

<img src="./habit-tracker/public/screenshots/image1.png" alt="App screenshot 2" width="600" />

### Mobile View (Pixel 7 412x915)

<img src="./habit-tracker/public/screenshots/image2.png" alt="App screenshot 3" width="600" />

### Tablet View (iPad Pro 1024x1366)

<img src="./habit-tracker/public/screenshots/image3.png" alt="App screenshot 4" width="600" />

## 🛠️ Installation
1. Clone the repository
```bash
git clone https://github.com/yourusername/habit-tracker.git
cd habit-tracker
```
2. Install dependencies
```bash
npm install
```
3. Start the development server
``` bash
npm run dev
```
4. Open your browser and navigate to http://localhost:5173
📦 Build for Production

``` bash
npm run build
```

The built files will be in the dist directory.

## 🛠️ Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Check code for linting errors
- `npm run lint:fix` - Fix linting errors automatically
- `npm run format` - Format code with Prettier
- `npm run format:check` - Check if code is properly formatted

## 🎯 Usage
Adding a Habit
1. Click the "+" button in the "Add New Habit" section
2. Enter a habit name
3. Choose a color from the color picker
4. Click "Add Habit"

### Tracking Progress
- Click on the day checkboxes to mark habits as complete
- Progress bars show weekly completion percentage
- Streak badges display consecutive completion days
- Managing Habits
- Edit: Click the "Edit" button on any habit card
- Delete: Hover over a habit card and click "Delete"
- Reset Progress: Use the "Reset Progress" button in the header
- Filtering and Sorting
- Search: Use the search bar to find specific habits
- Filter: Choose between "All", "Completed", or "Incomplete" habits
- Sort: Sort by creation date, name, or streak length

## 🏗️ Project Structure
```bash
habit-tracker/
├── src/
│   ├── components/          # React components
│   │   ├── AddHabitForm.tsx
│   │   ├── ColorPicker.tsx
│   │   ├── EditHabitModal.tsx
│   │   ├── HabitCard.tsx
│   │   ├── HabitsFilter.tsx
│   │   ├── HabitsList.tsx
│   │   ├── Header.tsx
│   │   └── ProgressBar.tsx
│   ├── constants/           # Application constants
│   │   └── colors.ts
│   ├── styles/              # CSS modules
│   │   ├── components/      # Component-specific styles
│   │   ├── accessibility.css
│   │   ├── responsive.css
│   │   └── reset.css
│   ├── types/               # TypeScript type definitions
│   │   └── Habit.ts
│   ├── utils/               # Utility functions
│   │   └── habitUtils.ts
│   ├── App.tsx              # Main application component
│   └── main.tsx             # Application entry point
├── public/                  # Static assets
├── package.json
└── vite.config.ts
```
## 🎨 Design Features
Modern UI: Clean, minimalist design with smooth animations
Color-Coded Habits: 5 predefined colors to categorize habits
Visual Progress: Progress bars and completion badges
Responsive Grid: Adaptive layout for different screen sizes
Hover Effects: Interactive elements with visual feedback

## ♿ Accessibility
Full keyboard navigation support
ARIA labels and descriptions
High contrast mode support
Reduced motion preferences
Screen reader compatibility
Focus management for modals

## 🌐 Browser Support
Chrome/Chromium 88+
Firefox 85+
Safari 14+
Edge 88+

## 📈 Performance
Lightweight: Minimal bundle size with tree-shaking
Fast Loading: Vite's optimized build process
Efficient Rendering: React 19's concurrent features
Local Storage: No external API calls required

## Run a Docker container locally
```bash
npm run build
docker build -t react-habit-tracker .
docker rm -f habit-tracker
docker run -d -p 8080:80 --name habit-tracker react-habit-tracker
```

## 🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.
1. Fork the project
2. Create your feature branch (git checkout -b feature/AmazingFeature)
3. Commit your changes (git commit -m 'Add some AmazingFeature')
4. Push to the branch (git push origin feature/AmazingFeature)
5. Open a Pull Request

## 📝 License
This project is licensed under the MIT License

## 🔮 Future Enhancements
Monthly/yearly habit tracking views
Habit categories and tags
Export/import functionality
Habit statistics and analytics
Reminder notifications
Multiple habit templates
Social sharing features
Backend integration for cloud sync

## 👨‍💻 Author

Nicolas Panozo - Digital Academy Frontend Development

Portfolio: [React Portfolio URL](https://portfolio-react-node-npanozo.vercel.app/)

LinkedIn: [LinkedIn](https://linkedin.com/in/nicolas-panozo)

GitHub: @nicopanozo
---

Made with ❤️ and React