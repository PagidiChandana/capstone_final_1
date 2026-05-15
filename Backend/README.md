# 🔧 BloggApp Backend - The Engine Behind It All

Yo! So you're looking at the backend code? Cool! This is basically the brain of BloggApp. While the frontend is all pretty and flashy, this bad boy does all the heavy lifting - storing your articles, keeping passwords safe, handling user uploads, all that good stuff.

## What's it do?

**In plain English:** It's a Node.js server that handles:
- Letting people create accounts and log in safely
- Storing and managing all those blog articles
- Keeping user data organized
- Making sure only the right people can do certain things (like only authors can write articles)
- Taking care of image uploads to the cloud

Pretty straightforward, really. It's like a filing system, but for the internet.

## Tech we're using

- **Node.js** - The JavaScript runtime (makes JavaScript work outside the browser)
- **Express.js** - The web framework (handles requests and responses)
- **MongoDB** - The database (where all the data lives)
- **Mongoose** - Makes talking to MongoDB easier
- **JWT** - Tokens for secure authentication
- **bcryptjs** - Makes sure passwords aren't stored as plain text (that would be terrible)
- **Cloudinary** - Hosts our images in the cloud
- **Multer** - Handles file uploads

## Before you get started

You'll need:
- Node.js installed (grab it from [nodejs.org](https://nodejs.org/))
- npm (comes with Node)
- A MongoDB account (free tier is fine - go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas))
- A Cloudinary account for image hosting ([sign up free](https://cloudinary.com/))

## Getting it set up

### Step 1: Clone and install
```bash
git clone https://github.com/PagidiChandana/week-7_Blog_app.git
cd week-7_Blog_app/ATP_24EG105G34_BloggApp-main/Backend
npm install
```

### Step 2: Make a `.env` file
Copy the example and fill in your own values:
```bash
cp .env.example .env
```

Then open `.env` and add your stuff:
```
# MongoDB - grab this from MongoDB Atlas
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/blogapp

# Random secret key (make it long and random!)
JWT_SECRET=put_something_super_secret_here_ok

# Cloudinary stuff - find this on your Cloudinary dashboard
CLOUDINARY_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# What port to run on
PORT=5000
```

**Don't share your `.env` file with anyone!** It has sensitive stuff.

### Step 3: Fire it up
```bash
npm run dev
```

You should see something like:
```
Server running on http://localhost:5000
✓ Connected to MongoDB
Ready to rock!
```

## How it's organized

```
Backend/
├── APIs/                    # The actual route handlers
│   ├── CommonAPI.js        # Login, signup, get articles
│   ├── AuthorAPI.js        # Author stuff (write articles)
│   ├── UserAPI.js          # User profiles
│   └── AdminAPI.js         # Admin only features
│
├── models/                  # Database structure
│   ├── UserModel.js        # What a user looks like
│   └── ArticleModel.js     # What an article looks like
│
├── config/                  # Settings
│   ├── cloudinary.js       # Cloudinary setup
│   └── multer.js           # File upload settings
│
├── middlewares/             # Security checks
│   └── verifyToken.js      # Makes sure you're logged in
│
└── server.js               # Where everything starts
```

## Using the API

All requests go to `http://localhost:5000/api`

### Logging in
```
POST /auth/login

Send:
{
  "email": "you@example.com",
  "password": "yourpassword"
}

Get back:
{
  "success": true,
  "token": "some_long_token_here",
  "user": { name, email, role, ... }
}
```

### Getting all articles
```
GET /articles

You'll get:
{
  "success": true,
  "articles": [ ... array of articles ... ],
  "total": 42
}
```

### Writing an article (need to be logged in!)
```
POST /articles
Headers: Authorization: Bearer YOUR_TOKEN_HERE
Content-Type: multipart/form-data

Send:
{
  "title": "My Awesome Article",
  "content": "This is where the article content goes...",
  "image": <pick a file>,
  "category": "tech"
}
```

### Getting one specific article
```
GET /articles/:id

You'll get the full article with all details
```

### Editing your article
```
PUT /articles/:id
Headers: Authorization: Bearer YOUR_TOKEN_HERE

Send:
{
  "title": "Updated title",
  "content": "Updated content"
}
```

### Deleting your article
```
DELETE /articles/:id
Headers: Authorization: Bearer YOUR_TOKEN_HERE

And it's gone!
```

Check out the `.http` files in this folder for more examples you can test directly!

## Database stuff

### User data looks like:
```
{
  name: "John Doe",
  email: "john@example.com",
  password: "encrypted_password_here",
  role: "author", // or "user" or "admin"
  bio: "I like writing",
  profileImage: "https://cloudinary.com/...",
  createdAt: "2024-05-14T10:30:00Z"
}
```

### Article data looks like:
```
{
  title: "How to code",
  content: "First you open your editor...",
  author: "userid_goes_here",
  image: "https://cloudinary.com/...",
  views: 150,
  likes: 23,
  status: "published",
  createdAt: "2024-05-14T10:30:00Z"
}
```

## Common stuff you might run into

**"Can't connect to MongoDB"**
- Make sure your MongoDB URI is right in `.env`
- Check that you've whitelisted your IP on MongoDB Atlas
- Make sure MongoDB is actually running

**"Token is invalid"**
- Your token might have expired (try logging in again)
- Make sure you're sending it in the header correctly: `Authorization: Bearer YOUR_TOKEN`
- Check that JWT_SECRET hasn't changed

**"Image upload failed"**
- File too big? Keep it under 5MB
- Wrong file type? Use jpg, jpeg, png, or gif
- Check your Cloudinary credentials

**"Getting 403 Forbidden"**
- You might not be logged in
- Or you might not have permission to do that thing
- Only authors can write articles, only admins can delete users, etc.

## Tips and tricks

- Always set a strong JWT_SECRET in production (not something easy to guess)
- Keep your `.env` file in `.gitignore` (don't push it to GitHub!)
- Test your endpoints before using them in the frontend
- If something's weird, check the server console for error messages

## Stuck? Need help?

- Check the error message in the terminal
- Look at the actual HTTP response (status code and message)
- Make sure all your environment variables are set
- Try restarting the server
- If all else fails, open an issue on GitHub!

---

**Now go forth and build! 🚀**
