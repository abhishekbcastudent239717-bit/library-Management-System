# Library Management System

A complete **Library Management System** built with **PHP, MySQL, HTML, CSS, and JavaScript** featuring separate admin and student panels with modern UI design.

## 📋 Features

### Admin Panel

- ✅ Dashboard with gradient statistics cards
- ✅ Manage Books (Add, Edit, Delete with image upload)
- ✅ Manage Students (Add, Edit, Delete)
- ✅ Manage Categories
- ✅ Issue books to students
- ✅ Track issued books and returns
- ✅ Automatic overdue detection
- ✅ Fine calculation (₹5 per day)
- ✅ Search and filter functionality
- ✅ Announcements system (create, edit, delete)
- ✅ Contact messages viewer with filters
- ✅ Profile management with password change

### Student Panel

- ✅ View personal dashboard with gradient cards
- ✅ View issued books with due dates
- ✅ Check overdue status and fines
- ✅ Browse available books with images
- ✅ Search books by title, author, or ISBN
- ✅ Filter books by category
- ✅ View announcements from admin
- ✅ Contact library (pre-filled form)
- ✅ Profile management with password change

### Security Features

- ✅ Password hashing using bcrypt
- ✅ SQL injection prevention (prepared statements)
- ✅ Session management with role-based access
- ✅ Input sanitization
- ✅ XSS protection
- ✅ Secure password change functionality
- ✅ Auto-detect user type (admin/student)

## 📁 Project Structure

```
library_system/
│
├── admin/                      # Admin panel files
│   ├── dashboard.php          # Admin dashboard
│   ├── books.php              # Manage books
│   ├── students.php           # Manage students
│   ├── categories.php         # Manage categories
│   ├── issue_book.php         # Issue book to student
│   ├── issued_books.php       # View issued books
│   └── logout.php             # Admin logout
│
├── student/                    # Student panel files
│   ├── dashboard.php          # Student dashboard
│   ├── my_books.php           # View issued books
│   ├── available_books.php    # Browse available books
│   └── logout.php             # Student logout
│
├── includes/                   # PHP includes
│   ├── db_connect.php         # Database connection
│   └── functions.php          # Common functions
│
├── assets/                     # Static assets
│   ├── css/
│   │   └── style.css          # Custom CSS
│   └── js/
│       └── script.js          # JavaScript validations
│
├── database.sql               # Database schema with sample data
├── index.php                  # Redirects to login
├── login.php                  # Login page for admin/student
└── README.md                  # This file
```

## 🚀 Installation & Setup

### Prerequisites

- **XAMPP** (or any PHP 7.4+ with MySQL)
- Web browser (Chrome, Firefox, etc.)

### Step-by-Step Installation

#### 1. Clone/Download the Project

```bash
# Place the library_system folder in your htdocs directory
# Example: C:\xampp\htdocs\library_system
```

#### 2. Start XAMPP

- Start **Apache** and **MySQL** services from XAMPP Control Panel

#### 3. Create Database

- Open **phpMyAdmin**: http://localhost/phpmyadmin
- Click on "New" to create a new database
- Name it: `library_management`
- Click "Create"

#### 4. Import Database

- Select the `library_management` database
- Click on "Import" tab
- Click "Choose File" and select `database.sql` from the project folder
- Click "Go" to import

#### 5. Configure Database Connection (if needed)

Edit `includes/db_connect.php` if your database credentials are different:

```php
define('DB_HOST', 'localhost');
define('DB_USER', 'root');
define('DB_PASS', '');  // Change if you have a password
define('DB_NAME', 'library_management');
```

#### 6. Access the Application

Open your browser and navigate to:

```
http://localhost/library_system
```

## 🔑 Login Credentials

### Admin Login

- **Email:** admin@library.com
- **Password:** password

### Student Login

- **Email:** john@student.com
- **Password:** password

**OR**

- **Email:** jane@student.com
- **Password:** password

## 📊 Database Schema

### Tables

1. **admin** - Admin user accounts
2. **students** - Student user accounts
3. **categories** - Book categories
4. **books** - Book inventory with image support
5. **issued_books** - Book issue/return tracking
6. **announcements** - System-wide announcements
7. **contact_messages** - Contact form submissions

### Sample Data Included

- 1 Admin account
- 2 Student accounts
- 5 Categories (Fiction, Science, History, Programming, Mathematics)
- 5 Sample books
- Pre-configured relationships

## 💡 Usage Guide

### Admin Operations

#### Managing Books

1. Login as admin
2. Click "Manage Books"
3. Click "+ Add New Book" to add a book
4. Fill in book details (Title, Author, ISBN, Category, Quantity, etc.)
5. Click "Add Book"
6. To edit, click "Edit" button on any book
7. To delete, click "Delete" (only if not currently issued)

#### Managing Students

1. Click "Manage Students"
2. Click "+ Add New Student"
3. Fill in student details (Name, Email, Password, Phone, Address)
4. Click "Add Student"
5. Edit/Delete as needed

#### Issuing Books

1. Click "Issue Book"
2. Select student from dropdown
3. Select available book
4. Set return date (must be future date)
5. Click "Issue Book"

#### Returning Books

1. Click "Issued Books"
2. Find the book to return
3. Click "Return" button
4. System automatically calculates fine if overdue (₹5/day)

### Student Operations

#### Viewing Books

1. Login as student
2. Dashboard shows current issued books
3. Click "My Books" to see all history
4. Click "Available Books" to browse library

#### Searching Books

1. Go to "Available Books"
2. Use search box to find by title, author, or ISBN
3. Filter by category using dropdown
4. Click "Search"

## 🎨 Features Breakdown

### Form Validations

- Client-side validation using JavaScript
- Server-side validation in PHP
- Email format validation
- Password strength (minimum 6 characters)
- Phone number format (10 digits)
- ISBN uniqueness check
- Quantity validations

### Security Measures

1. **Password Hashing:** Uses PHP `password_hash()` with bcrypt
2. **SQL Injection Prevention:** All queries use mysqli_real_escape_string()
3. **XSS Prevention:** Output escaped with htmlspecialchars()
4. **Session Management:** Secure session handling for both roles
5. **Access Control:** Role-based access restrictions

### Fine Calculation

- Automatic overdue detection
- ₹5 per day overdue fine
- Fine displayed in student and admin panels
- Calculated on return

### UI/UX Features

- **Responsive Design:** Works on desktop and mobile
- **Modern Gradients:** Beautiful color schemes
- **Search Functionality:** Real-time table search
- **Modal Popups:** For add/edit forms
- **Status Badges:** Visual indicators for book status
- **Auto-hide Messages:** Success/error messages fade after 5 seconds
- **Loading States:** Visual feedback for actions

## 🛠 Customization

### Changing Fine Amount

Edit `includes/functions.php`:

```php
function calculate_fine($overdue_days) {
    return $overdue_days * 5;  // Change 5$ to your desired amount
}
```

### Modifying Colors

Edit `assets/css/style.css`:

```css
/* Main theme color */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

### Adding More Categories

1. Login as admin
2. Go to "Categories"
3. Click "+ Add New Category"

## 📝 API Endpoints (Form Actions)

### Admin

- `POST /admin/books.php?action=add` - Add book
- `POST /admin/books.php?action=edit` - Edit book
- `GET /admin/books.php?delete=ID` - Delete book
- `POST /admin/students.php?action=add` - Add student
- `POST /admin/issue_book.php` - Issue book
- `GET /admin/issued_books.php?return=ID` - Return book

### Authentication

- `POST /login.php` - Login (admin/student)
- `GET /admin/logout.php` - Logout (admin)
- `GET /student/logout.php` - Logout (student)

## 🐛 Troubleshooting

### Database Connection Error

- Check if MySQL is running in XAMPP
- Verify database credentials in `db_connect.php`
- Ensure `library_management` database exists

### Login Not Working

- Check if `admin` or `students` table has data
- Verify password is: `password` (default)
- Clear browser cookies/cache

### Books Not Showing

- Check if books exist in database with `available_quantity > 0`
- Verify foreign key relationships are intact

### CSS Not Loading

- Check file path in HTML: `../assets/css/style.css`
- Ensure files are in correct directory structure
- Clear browser cache

## 📧 Support

For issues or questions:

1. Check the database import was successful
2. Verify all files are in correct directories
3. Check PHP error logs in XAMPP
4. Ensure MySQL and Apache are running

## 🎓 Learning Resources

This project demonstrates:

- PHP procedural programming
- MySQL database design
- CRUD operations
- Session management
- Form validation (client & server)
- Responsive CSS design
- JavaScript DOM manipulation
- Security best practices

## 📜 License

This project is open-source and available for educational purposes.

## 🚀 Future Enhancements (Optional)

- Email notifications for due dates
- Export reports to PDF/Excel
- Book reservation system
- Advanced search filters
- User profile management
- Book reviews and ratings
- QR code for book scanning
- Mobile app integration

---

**Built with ❤️ by Abhishek Kumar using PHP, MySQL, HTML, CSS, and JavaScript**
