
# LangkahPemula API Documentation

## Base URL

**Base URL:** `https://amp.academychan.my.id/api/`

---

## Authentication

API ini menggunakan **Laravel Sanctum** untuk autentikasi berbasis token. Pastikan Anda mendapatkan token autentikasi setelah login dan menggunakannya dalam setiap request yang memerlukan autentikasi.

---

## Endpoints

### 1. **Register User**

**URL:** `/register`  
**Method:** `POST`  
**Description:** Mendaftarkan user baru.  
**Authorization:** Tidak diperlukan.

#### Request Body (JSON):
```json
{
    "name": "John Doe",
    "email": "johndoe@example.com",
    "password": "password123"
}
```

#### Response (Success):
```json
{
    "status": 200,
    "message": "success",
    "data": {
        "id": "id_user",
        "name": "name_user",
        "email": "email_user"
    }
}
```

---

### 2. **Login**

**URL:** `/login`  
**Method:** `POST`  
**Description:** Login user untuk mendapatkan token.  
**Authorization:** Tidak diperlukan.

#### Request Body (JSON):
```json
{
    "email": "johndoe@example.com",
    "password": "password123"
}
```

#### Response (Success):
```json
{
    "status": 200,
    "message": "success",
    "data": {
        "token": "isi_token"
    }
}
```

---

### 3. **Logout**

**URL:** `/logout`  
**Method:** `POST`  
**Description:** Logout user dengan menghapus token.  
**Authorization:** Bearer token (Login required).

#### Headers:
- `Authorization: Bearer <token>`

#### Response (Success):
```json
{
    "status": 200,
    "message": "Logged out successfully"
}
```

---

### 4. **Get User Dashboard (Customer, Mentor, Administrator)**

**URL:** `/dashboard`  
**Method:** `GET`  
**Description:** Mengambil data dashboard user sesuai dengan perannya (Customer, Mentor, atau Administrator).  
**Authorization:** Bearer token (Login required).

#### Headers:
- `Authorization: Bearer <token>`

#### Response (Success):
```json
{
    "status": 200,
    "message": "success",
    "data": {
        "role": "customer/mentor/administrator",
        "courses": [...]
    }
}
```

---

### 5. **CRUD Courses (Administrator & Mentor)**

#### a. **Create Course**

**URL:** `/courses`  
**Method:** `POST`  
**Description:** Menambahkan course baru (Hanya untuk Administrator dan Mentor).  
**Authorization:** Bearer token & role-based access control.

#### Headers:
- `Authorization: Bearer <token>`

#### Request Body (JSON):
```json
{
    "title": "Course Title",
    "description": "Course Description",
    "category_id": 1
}
```

#### Response (Success):
```json
{
    "status": 200,
    "message": "Course created successfully",
    "data": {
        "id": 1,
        "title": "Course Title",
        "description": "Course Description",
        "category_id": 1
    }
}
```

---

#### b. **Update Course**

**URL:** `/courses/{id}`  
**Method:** `PUT`  
**Description:** Mengubah course yang sudah ada (Hanya untuk Administrator dan Mentor).  
**Authorization:** Bearer token & role-based access control.

#### Headers:
- `Authorization: Bearer <token>`

#### Request Body (JSON):
```json
{
    "title": "Updated Course Title",
    "description": "Updated Course Description",
    "category_id": 2
}
```

#### Response (Success):
```json
{
    "status": 200,
    "message": "Course updated successfully",
    "data": {
        "id": 1,
        "title": "Updated Course Title",
        "description": "Updated Course Description",
        "category_id": 2
    }
}
```

---

#### c. **Delete Course**

**URL:** `/courses/{id}`  
**Method:** `DELETE`  
**Description:** Menghapus course berdasarkan ID (Hanya untuk Administrator).  
**Authorization:** Bearer token & role-based access control.

#### Headers:
- `Authorization: Bearer <token>`

#### Response (Success):
```json
{
    "status": 200,
    "message": "Course deleted successfully"
}
```

---

### 6. **CRUD Categories (Administrator Only)**

#### a. **Create Category**

**URL:** `/categories`  
**Method:** `POST`  
**Description:** Menambahkan kategori baru (Hanya untuk Administrator).  
**Authorization:** Bearer token & role-based access control.

#### Headers:
- `Authorization: Bearer <token>`

#### Request Body (JSON):
```json
{
    "name": "Category Name"
}
```

#### Response (Success):
```json
{
    "status": 200,
    "message": "Category created successfully",
    "data": {
        "id": 1,
        "name": "Category Name"
    }
}
```

---

#### b. **Update Category**

**URL:** `/categories/{id}`  
**Method:** `PUT`  
**Description:** Mengubah kategori yang sudah ada (Hanya untuk Administrator).  
**Authorization:** Bearer token & role-based access control.

#### Headers:
- `Authorization: Bearer <token>`

#### Request Body (JSON):
```json
{
    "name": "Updated Category Name"
}
```

#### Response (Success):
```json
{
    "status": 200,
    "message": "Category updated successfully",
    "data": {
        "id": 1,
        "name": "Updated Category Name"
    }
}
```

---

#### c. **Delete Category**

**URL:** `/categories/{id}`  
**Method:** `DELETE`  
**Description:** Menghapus kategori berdasarkan ID (Hanya untuk Administrator).  
**Authorization:** Bearer token & role-based access control.

#### Headers:
- `Authorization: Bearer <token>`

#### Response (Success):
```json
{
    "status": 200,
    "message": "Category deleted successfully"
}
```

---

### 7. **CRUD Users (Administrator Only)**

#### a. **Create User**

**URL:** `/users`  
**Method:** `POST`  
**Description:** Menambahkan user baru (Hanya untuk Administrator).  
**Authorization:** Bearer token & role-based access control.

#### Headers:
- `Authorization: Bearer <token>`

#### Request Body (JSON):
```json
{
    "name": "New User",
    "email": "newuser@example.com",
    "password": "password123",
    "role": "customer/mentor/administrator"
}
```

#### Response (Success):
```json
{
    "status": 200,
    "message": "User created successfully",
    "data": {
        "id": 1,
        "name": "New User",
        "email": "newuser@example.com",
        "role": "customer/mentor/administrator"
    }
}
```

---

#### b. **Update User**

**URL:** `/users/{id}`  
**Method:** `PUT`  
**Description:** Mengubah user yang sudah ada (Hanya untuk Administrator).  
**Authorization:** Bearer token & role-based access control.

#### Headers:
- `Authorization: Bearer <token>`

#### Request Body (JSON):
```json
{
    "name": "Updated User Name",
    "email": "updateduser@example.com",
    "role": "customer/mentor/administrator"
}
```

#### Response (Success):
```json
{
    "status": 200,
    "message": "User updated successfully",
    "data": {
        "id": 1,
        "name": "Updated User Name",
        "email": "updateduser@example.com",
        "role": "customer/mentor/administrator"
    }
}
```

---

#### c. **Delete User**

**URL:** `/users/{id}`  
**Method:** `DELETE`  
**Description:** Menghapus user berdasarkan ID (Hanya untuk Administrator).  
**Authorization:** Bearer token & role-based access control.

#### Headers:
- `Authorization: Bearer <token>`

#### Response (Success):
```json
{
    "status": 200,
    "message": "User deleted successfully"
}
```

---

Dengan mengikuti dokumentasi ini, Anda dapat menggunakan Postman atau alat lainnya untuk berinteraksi dengan API **LangkahPemula**. Jangan lupa untuk selalu menambahkan token di header pada setiap request yang membutuhkan autentikasi.
