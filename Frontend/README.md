# 🎨 BloggApp Frontend - Where the magic looks good

Alright, so this is the pretty part of BloggApp! This is what people actually see when they visit the site. We built it with React and Vite, which basically means it loads super fast and feels smooth to use.

Think of it as the face of the application. The backend does all the thinking, but this is what makes people go "ooh, nice!"

## What you get

- ⚡ **Super fast** - Built with Vite, loads in milliseconds
- 📱 **Works everywhere** - Desktop, tablet, phone, it all looks good
- 🎨 **Looks nice** - Tailwind CSS makes everything pretty
- 🔐 **Secure login** - Uses the same auth as the backend
- ✍️ **Write articles** - Rich editor for creating content
- 📖 **Read articles** - Browse and discover blog posts
- 👤 **User profiles** - See who's writing what
- 🖼️ **Image uploads** - Add pictures to your articles
- 📱 **Responsive** - Works on any screen size

## What we're using

- **React 19** - The UI library
- **Vite** - Super fast build tool
- **Tailwind CSS** - For styling (looks amazing)
- **React Router** - Navigation between pages
- **Zustand** - Keeps track of stuff (state management)
- **Axios** - Talks to the backend
- **React Hook Form** - Makes forms not annoying
- **React Hot Toast** - Little notifications

## Before you start

Make sure you have:
- Node.js ([get it here](https://nodejs.org/))
- npm (comes with Node)
- A modern browser (Chrome, Firefox, Safari, Edge - basically anything modern)

## Getting it running

### Step 1: Clone and install
```bash
git clone https://github.com/PagidiChandana/week-7_Blog_app.git
cd week-7_Blog_app/ATP_24EG105G34_BloggApp-main/Frontend
npm install
```

### Step 2: Create `.env.local`
```
VITE_API_URL=http://localhost:5000
```

This tells React where the backend is running. If your backend is somewhere else, change this!

### Step 3: Start developing
```bash
npm run dev
```

It'll usually start on `http://localhost:5173`. The cool thing is, whenever you change code, the page automatically refreshes. No manual refreshing needed!

### When you're ready to deploy
```bash
npm run build
```

This creates an optimized version ready for the internet.

## What's inside?

```
Frontend/
├── components/              # The different pages and pieces
│   ├── Home.jsx            # Landing page
│   ├── Articles.jsx        # Browse all articles
│   ├── ArticleById.jsx     # Read one article
│   ├── WriteArticles.jsx   # Create a new article
│   ├── EditArticle.jsx     # Edit your article
│   ├── Login.jsx           # Login page
│   ├── Register.jsx        # Sign up page
│   ├── UserProfile.jsx     # Your profile
│   ├── AuthorProfile.jsx   # Someone else's profile
│   ├── Header.jsx          # Navigation bar
│   ├── Footer.jsx          # Bottom of page
│   └── ... more components
│
├── store/                   # Where we keep track of stuff
│   └── authStore.js        # Remembers if you're logged in
│
├── styles/                  # CSS stuff
│   └── common.js           # Shared styles
│
├── App.jsx                 # The main component
└── main.jsx                # Where everything starts
```

## Main pages

### Home page
The first thing people see. Has a hero section, featured articles, and buttons to get started. Pretty straightforward.

### Articles page
Shows a list of all blog posts. You can scroll through, search for stuff, filter by category, all that good stuff.

### Article detail page
Click an article and see the full thing. Shows the author, publication date, and the full content. Also links to the author's profile so you can see what else they've written.

### Write article
If you're logged in as an author, you can write new articles. Just type the title, content, upload a picture, and boom - you're published!

### Profiles
Every user has a profile showing their bio, picture, and all the articles they've written. You can follow people too (if that feature's enabled).

### Admin dashboard
If you're an admin, you get a special page where you can manage users, delete bad content, see statistics, that kind of thing.

## How it talks to the backend

We use Axios to send requests to the backend. It's pretty straightforward:

```javascript
// Get all articles
axios.get('/api/articles')

// Create a new article
axios.post('/api/articles', {
  title: "My article",
  content: "...",
})

// Update an article
axios.put(`/api/articles/${id}`, {
  title: "Updated title"
})

// Delete an article
axios.delete(`/api/articles/${id}`)
```

The frontend automatically adds your login token to every request, so the backend knows who you are.

## Routing (how you get from page to page)

- `/` - Home
- `/articles` - All articles
- `/articles/:id` - Read one article
- `/write` - Create article (need to be logged in)
- `/edit/:id` - Edit article (need to own it)
- `/login` - Login page
- `/register` - Sign up
- `/profile/:id` - User profile
- `/author/:id` - Author profile

## State management with Zustand

We use this thing called Zustand to remember stuff. Like, if you log in, we need to remember that across all pages. Here's how it works:

```javascript
// In a component
import authStore from '../store/authStore';

function MyComponent() {
  const { user, isLoggedIn, login, logout } = authStore();
  
  return (
    <div>
      {isLoggedIn ? <p>Hi {user.name}!</p> : <p>Please log in</p>}
    </div>
  );
}
```

It's way simpler than it sounds, I promise.

## Styling with Tailwind

We use Tailwind CSS which means instead of writing a bunch of CSS, we just add class names:

```jsx
// Instead of:
// <style>
//   .card { padding: 20px; background: white; border-radius: 8px; }
// </style>
// <div class="card">

// We do:
<div className="p-5 bg-white rounded-lg">
```

It takes a minute to get used to, but once you do, it's way faster. Plus the page loads way faster too.

## Form handling

We use React Hook Form to handle forms (login, signup, write article, etc). It handles validation, error messages, and all the annoying form stuff automatically. Much better than manually managing form state.

## Common things you might want to do

### Add a new page
1. Create a new component file in `components/`
2. Add a new route in `App.jsx`
3. Add a link in the Header or wherever makes sense

### Change colors
Look in `tailwind.config.js` and customize the theme. Want everything blue instead of green? Change it there.

### Make an API call
Use Axios. Check existing components to see how it's done.

### Add a new form field
Use React Hook Form. Look at the LoginForm or RegisterForm to see the pattern.

### Fix a bug
1. Open the browser dev tools (F12)
2. Check the console for errors
3. Use the Network tab to see if API calls are working
4. React DevTools extension is super helpful

## Troubleshooting

**"Can't connect to backend"**
- Is the backend running? (check terminal)
- Is `VITE_API_URL` pointing to the right place?
- Check the Network tab in dev tools

**"Page won't refresh after I make changes"**
- That's weird, Vite usually auto-refreshes
- Try saving the file again
- Might need to restart the dev server

**"Getting a white screen"**
- Check console for errors (F12)
- Make sure the backend is running
- Try a hard refresh (Ctrl+Shift+R)

**"Login keeps logging me out"**
- Token might be expiring
- Check if the backend is running
- Clear localStorage: `localStorage.clear()` in console

## Tips

- Use the browser dev tools A LOT. F12 is your friend
- The React DevTools browser extension is super helpful
- When making changes to components, save the file and it automatically refreshes
- Keep components small and focused - easier to debug
- If something seems slow, check the Network tab to see what's taking forever

## Building for the real world

When you're ready to put this on the internet:

```bash
npm run build
```

This creates a `dist/` folder with everything optimized. You can deploy this to Netlify, Vercel, GitHub Pages, or wherever. Just upload the contents of `dist/`.

## Want to help?

Got ideas? Found a bug? Want to add a feature?
1. Make a new branch (`git checkout -b my-feature`)
2. Make your changes
3. Test it
4. Send a pull request

We'd love the help!

---

**Have fun building! 🚀** If you get stuck, just ask. We're all learning here!
