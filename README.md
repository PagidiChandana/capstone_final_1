# 📝 BloggApp - A Modern Blogging Platform

Welcome to **BloggApp**! A beautiful, full-stack blogging application built with modern web technologies. Share your stories, ideas, and expertise with the world! 🚀

## ✨ Features

### 🎯 Core Functionality
- **User Authentication** - Secure signup and login with JWT-based authentication
- **Create & Publish** - Write and publish your own blog articles with rich content
- **Edit & Delete** - Manage your published articles with ease
- **Browse Articles** - Discover and read articles from other authors
- **User Profiles** - View author profiles and their contributions
- **Image Uploads** - Add beautiful images to your articles using Cloudinary

### 👥 User Roles
- **Regular Users** - Read articles and explore the platform
- **Authors** - Create, edit, and manage their own articles
- **Admins** - Manage users, articles, and platform content

### 🛠️ Technical Highlights
- **Responsive Design** - Beautiful UI with Tailwind CSS that works on all devices
- **Fast Performance** - Built with Vite for blazing-fast load times
- **Secure API** - RESTful backend with proper authentication and authorization
- **Database-Driven** - MongoDB for scalable data storage
- **Image Optimization** - Cloudinary integration for efficient image management

---

## 🏗️ Project Structure

```
BloggApp/
├── Backend/                 # Node.js + Express server
│   ├── APIs/               # Route handlers
│   │   ├── AdminAPI.js
│   │   ├── AuthorAPI.js
│   │   ├── UserAPI.js
│   │   └── CommonAPI.js
│   ├── config/             # Configuration files
│   │   ├── cloudinary.js
│   │   └── multer.js
│   ├── models/             # MongoDB schemas
│   │   ├── UserModel.js
│   │   └── ArticleModel.js
│   ├── middlewares/        # Custom middleware
│   │   └── verifyToken.js
│   └── server.js           # Entry point
│
└── Frontend/               # React + Vite application
    ├── src/
    │   ├── components/     # React components
    │   ├── store/          # Zustand state management
    │   ├── styles/         # Tailwind styles
    │   ├── App.jsx
    │   └── main.jsx
    └── vite.config.js
```

---

## 🚀 Getting Started

### Prerequisites
Make sure you have the following installed on your system:
- **Node.js** (v16 or higher)
- **npm** or **yarn**
- **MongoDB** (local or cloud - we recommend MongoDB Atlas)
- **Git**

### 📦 Installation

#### 1. Clone the Repository
```bash
git clone https://github.com/PagidiChandana/week-7_Blog_app.git
cd week-7_Blog_app/ATP_24EG105G34_BloggApp-main
```

#### 2. Setup Backend

Navigate to the Backend folder:
```bash
cd Backend
npm install
```

Create a `.env` file in the Backend directory:
```bash
cp .env.example .env
```

Fill in your environment variables:
```env
# Database
MONGODB_URI=your_mongodb_connection_string

# JWT Secret
JWT_SECRET=your_secret_key_here

# Cloudinary (for image uploads)
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Server Port
PORT=5000
```

Start the backend server:
```bash
npm run dev
```

The backend will run on `http://localhost:5000`

#### 3. Setup Frontend

Open a new terminal and navigate to the Frontend folder:
```bash
cd Frontend
npm install
```

Create a `.env` file in the Frontend directory (if needed):
```env
VITE_API_URL=http://localhost:5000
```

Start the development server:
```bash
npm run dev
```

The frontend will typically run on `http://localhost:5173`

---

## 📚 API Endpoints

### Authentication
- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Login user
- `POST /api/auth/logout` - Logout user

### Articles
- `GET /api/articles` - Get all articles
- `GET /api/articles/:id` - Get article by ID
- `POST /api/articles` - Create new article (Authenticated)
- `PUT /api/articles/:id` - Update article (Author/Admin)
- `DELETE /api/articles/:id` - Delete article (Author/Admin)

### Users
- `GET /api/users` - Get all users
- `GET /api/users/:id` - Get user profile
- `PUT /api/users/:id` - Update user profile

### Admin
- `GET /api/admin/users` - Get all users (Admin only)
- `DELETE /api/admin/users/:id` - Delete user (Admin only)

For complete API documentation, check the `.http` files in the Backend folder.

---

## 🛠️ Tech Stack

### Frontend
- **React 19** - UI library
- **Vite** - Build tool and dev server
- **Tailwind CSS** - Utility-first CSS framework
- **React Router** - Client-side routing
- **Zustand** - State management
- **Axios** - HTTP client
- **React Hook Form** - Form management
- **React Hot Toast** - Toast notifications

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM
- **JWT** - Authentication
- **bcryptjs** - Password hashing
- **Multer** - File upload middleware
- **Cloudinary** - Image hosting service

---

## 🎮 Usage

1. **Sign Up** - Create a new account on the platform
2. **Browse Articles** - Check out articles from other authors
3. **Write Articles** - Click "Write" to create your own article
4. **Add Images** - Upload images to make your articles more engaging
5. **Publish** - Share your article with the community
6. **Edit/Delete** - Manage your own articles anytime
7. **View Profiles** - Check out author profiles and their work

---

## 🔒 Security Features

- ✅ Password hashing with bcryptjs
- ✅ JWT-based authentication
- ✅ Protected routes and endpoints
- ✅ CORS enabled for secure cross-origin requests
- ✅ Input validation and sanitization
- ✅ Secure cookie handling

---

## 📝 Available Scripts

### Backend
```bash
npm run dev    # Start development server with nodemon
npm start      # Start production server
```

### Frontend
```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run preview  # Preview production build
npm run lint     # Run ESLint
```

---

## 🤝 Contributing

We love contributions! Here's how you can help:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

Please make sure to follow our coding standards and add tests for new features.

---

## 📧 Support & Feedback

Have questions or suggestions? Feel free to:
- Open an issue on GitHub
- Send us an email
- Check out our documentation

---

## 📄 License

This project is licensed under the ISC License - see the LICENSE file for details.

---

## 🙏 Acknowledgments

- Thanks to all contributors who have helped with the project
- Built as part of the ATP_24EG105G34 assignment
- Special thanks to the open-source community

---

## 🌟 Show Your Support

If you find this project helpful, please give it a star! ⭐ Your support means a lot to us!

---

**Happy Blogging! 📝✨**

For more information and updates, visit our [GitHub repository](https://github.com/PagidiChandana/week-7_Blog_app)
