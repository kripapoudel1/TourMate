# Introduction
The "TourMate" project proposes the development of a web application to
revolutionize the travel planning/tour booking experience. In response to the
growing demand for convenient, user-friendly platforms, this project will offer users
with a full solution to explore, and book travel experiences effortlessly. Using the
Laravel framework, the project will deliver a robust, scalable, and easily
maintainable architecture. The application will include essential features such as
tour browsing, planning, secure booking, payment integration, and real-time
communication with service providers. It also includes several administrative tasks
for managing tours, turning travelers dream journeys into unforgettable realities.

# Business Rules
### **1. Users**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **Username**: Unique, valid username (mandatory).
    - **Password**: Secure login password (mandatory).
    - **Email**: Unique, valid email address (mandatory).
    - **Role**: Defines whether the user is a **CUSTOMER** or **ADMIN** (mandatory).
    - **Name**: Full name of the user (mandatory).
    - **Phone Number**: Contact number for the user (mandatory).
    - **Address**: User's primary address (mandatory).
- **Uniqueness**:
    - Each user has a **unique username** and **unique email**.
- **Optional/Mandatory**:
    - All fields (ID, username, password, email, role, name, phone number, address) are **mandatory**.
- **Relationships**:
    - Users can **create** and **manage multiple wishlists**.
    - Verified registered users can **make bookings**, **write blog posts**, **comment**, **rate and review tours**.
    - Users **can update their profile**.
    - Users can **reset their password** via a secure email link.

### **2. Tour Categories**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **Name**: Unique name (e.g., Adventure, Cultural) (mandatory).
- **Uniqueness**:
    - Each category has a **unique name**.
- **Optional/Mandatory**:
    - **ID** and **Name** are **mandatory**.
- **Relationships**:
    - A category can have **multiple tours** associated with it.

### **3. Tours**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **Name**: Unique name for each tour (mandatory).
    - **Description**: Details about the tour (mandatory).
    - **Location**: Geographic location of the tour (mandatory).
    - **Price**: Price of the tour (mandatory).
    - **Availability Status**: Current availability, e.g., **available** or **sold out** (mandatory).
    - **Category**: Tour category association, e.g., Adventure, Cultural (mandatory).
    
- **Uniqueness**:
    - Each tour has a **unique name**.
- **Optional/Mandatory**:
    - Description is optional all other fields are **mandatory**.
- **Relationships**:
    - Tours **must belong to one category**.
    - Tours can have **one or many bookings**.
    - Tours can have **one or many ratings**.

### **4. Wishlists**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - Tour_id
    - User_id
- **Uniqueness**:
    - Each wishlist has a **unique name** within a user’s account.
- **Optional/Mandatory**:
    - All are **mandatory**.
- **Relationships**:
    - Users can have **multiple wishlists**.
    - Wishlists can contain **multiple tours**.
    

### **5. Bookings**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **User_id**
    - **Tour_id**
    - **Number of Travelers**: Number of travelers for the booking (mandatory).
    - **Status**: Status of the booking (Confirmed, Pending, or Canceled) (mandatory).
- **Uniqueness**:
    - Each booking is **unique** to its combination of user, tour, and date.
- **Optional/Mandatory**:
    - All properties are **mandatory**.
- **Relationships**:
    - Each booking is associated with **one tour** and **one user**.
    - Bookings require a **confirmed payment**.

### **6. Payments**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **Amount**: Payment amount (mandatory).
    - **Booking_id**
    - **Payment Method**: (e.g., eSewa, Khalti) (mandatory).
    - **Status**: Status of the payment (Pending, Completed, Failed) (mandatory).
- **Uniqueness**:
    - Each payment is **unique to its booking**.
- **Optional/Mandatory**:
    - All properties are **mandatory**.
- **Relationships**:
    - A payment **is associated with one booking** only.

### **7. Blog Posts**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **Title**: Unique title for the blog post (mandatory).
    - **Content**: Content of the blog post (mandatory).
    - **Publication Date**: Date of publication (mandatory).
- **Uniqueness**:
    - Each post has a **unique title**.
- **Optional/Mandatory**:
    - All properties are **mandatory**; media attachments are **optional**.
- **Relationships**:
    - User can create multiple blogs.
    - Blog posts can have **multiple comments**.

### **8. Blog Comments**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **Content**: Comment content (mandatory).
- **Optional/Mandatory**:
    - **ID** and **Content** are **mandatory**.
- **Relationships**:
    - Each comment is associated with **one blog post**.
    - Users can make **multiple comments** on posts.

### **9. Ratings**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **Score**: Rating score (1-5 stars) (mandatory).
    - **Review**: Text review (optional).
- **Uniqueness**:
    - Each user can only provide **one rating per tour**.
- **Optional/Mandatory**:
    - Score is **mandatory**; the review text is **optional**.
- **Relationships**:
    - Ratings are **associated with both a tour and a user**.

### **10. Search**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **Query**: Search query terms (mandatory).
- **Optional/Mandatory**:
    - **ID** and **Query** are **mandatory**.
- **Relationships**:
    - Searches **are stored for registered users** to save history.

### **11. Traveler Info**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **Name**: Traveler's name (mandatory).
    - **Booking ID**: Reference to the associated booking (mandatory).
    - **Age**: Traveler's age (mandatory).
    - **Gender**: Traveler's gender (mandatory).
    - **Created At**: Date and time of record creation (auto-generated, mandatory).
- **Optional/Mandatory**:
    - **ID**, **Name**, **Booking ID**, **Age**, **Gender**, and **Created At** are **mandatory**.
- **Relationships**:
    - Each booking can be associated with **one or more travelers** (1-to-many relationship).
    - Each traveler must be associated with exactly **one booking**.

### **12. Tour Gallery**

- **Properties**:
    - **ID**: Unique identifier (auto-generated, mandatory).
    - **Tour ID**: Reference to the associated tour (mandatory).
    - **Image**: Tour image (mandatory).
- **Optional/Mandatory**:
    - **ID**, **Tour ID**, and **Image** are **mandatory**.
- **Relationships**:
    - Each tour can have **multiple images** associated with it (1-to-many relationship).
    - Each image is associated with exactly **one tour**.