
# 🏥 **Hospital Patient Connection System** 🌟

## 🚀 **Overview**

Transform hospital management with our **Hospital Patient Connection System**! Simplify patient registration, streamline appointment scheduling, and get real-time updates to cut down wait times and boost efficiency. 

## 🌟 **Features**

- **📝 Patient Registration:** Effortlessly sign up and manage profiles.
- **📅 Appointment Scheduling:** Book and manage your visits with ease.
- **🔔 Real-time Updates:** Instant notifications for confirmations and reminders.
- **⏳ Reduce Wait Times:** Smart scheduling to keep you on track!

## 🛠️ **Technology Stack**

- **Frontend:** HTML, CSS, JavaScript
- **Backend:** Node.js, Express
- **Database:** MySQL
- **Email:** SMTP (nodemailer)
- **Scheduling:** Custom appointment logic

## 🏁 **Setup**

### **Prerequisites**

- Node.js (>= 14.x)
- MySQL
- npm (or yarn)
- SMTP Server credentials

### **Installation**

1. **🔄 Clone the Repository:**

   ```bash
   git clone https://github.com/your-repo/hospital-patient-connection.git
   cd hospital-patient-connection
   ```

2. **📦 Install Backend Dependencies:**

   Navigate to `backend` and install:

   ```bash
   cd backend
   npm install
   ```

3. **🔧 Configure Environment Variables:**

   Set up your `.env` file with:

   ```env
   DB_HOST=your_mysql_host
   DB_USER=your_mysql_user
   DB_PASSWORD=your_mysql_password
   DB_NAME=your_mysql_database
   SMTP_HOST=your_smtp_host
   SMTP_PORT=your_smtp_port
   SMTP_USER=your_smtp_user
   SMTP_PASS=your_smtp_password
   ```

4. **🔄 Set Up the MySQL Database:**

   Create the necessary database and tables:

   ```sql
   CREATE DATABASE hospital;
   USE hospital;
   CREATE TABLE patients (
     id INT AUTO_INCREMENT PRIMARY KEY,
     name VARCHAR(100),
     email VARCHAR(100) UNIQUE,
     phone VARCHAR(15)
   );
   CREATE TABLE appointments (
     id INT AUTO_INCREMENT PRIMARY KEY,
     patient_id INT,
     appointment_time DATETIME,
     FOREIGN KEY (patient_id) REFERENCES patients(id)
   );
   ```

5. **🚀 Start the Backend Server:**

   ```bash
   npm start
   ```

6. **📦 Install Frontend Dependencies:**

   Navigate to `frontend` and install:

   ```bash
   cd ../frontend
   ```

   *Note:* Ensure proper build setup if using tools like webpack.

7. **🚀 Start the Frontend Server:**

   *For development:* 

   ```bash
   npm start
   ```

   *Or deploy static files to a web server.*

### **📧 SMTP Integration**

Configure `sendEmail` in `backend/utils/emailUtils.js`:

```javascript
const nodemailer = require('nodemailer');

const transporter = nodemailer.createTransport({
  host: process.env.SMTP_HOST,
  port: process.env.SMTP_PORT,
  auth: {
    user: process.env.SMTP_USER,
    pass: process.env.SMTP_PASS,
  },
});

exports.sendEmail = function(to, subject, text) {
  const mailOptions = {
    from: 'your_email@example.com',
    to: to,
    subject: subject,
    text: text,
  };

  return transporter.sendMail(mailOptions);
};
```

### **📅 Scheduling**

Implement appointment reminders in `backend/controllers/appointmentController.js`:

```javascript
const schedule = require('node-schedule');
const sendEmail = require('../utils/emailUtils');

// Schedule reminders for the next day
schedule.scheduleJob('0 9 * * *', function() {
  // Logic to fetch appointments for the next day and send reminders
});
```

## 💡 **Usage**

- **📝 Patient Registration:** Create and manage profiles with ease.
- **📅 Appointment Scheduling:** Schedule and manage your appointments seamlessly.
- **🔔 Notifications:** Get timely updates and reminders via email.

## 🤝 **Contributing**

We welcome contributions! Open an issue or submit a pull request to enhance the project.

## 📜 **License**

Licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📬 **Contact**

For questions or support, reach out to [your_email@example.com](mailto:your_email@example.com).

---
