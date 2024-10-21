Berikut adalah dokumentasi API **LangkahPemula**

---

# LangkahPemula API Documentation

**Base URL:** `https://amp.academychan.my.id/api/`

---

## Table of Contents

- [Register User](#register-user)
- [Login](#login)
- [Logout](#logout)
- [Get User Dashboard](#get-user-dashboard)
- [CRUD Courses (Administrator & Mentor)](#crud-courses-administrator--mentor)
  - [Create Course](#create-course)
  - [Update Course](#update-course)
  - [Delete Course](#delete-course)
- [CRUD Categories (Administrator Only)](#crud-categories-administrator-only)
  - [Create Category](#create-category)
  - [Update Category](#update-category)
  - [Delete Category](#delete-category)
- [CRUD Users (Administrator Only)](#crud-users-administrator-only)
  - [Create User](#create-user)
  - [Update User](#update-user)
  - [Delete User](#delete-user)

---

## Register User

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

## Login

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

## Logout

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

## Get User Dashboard

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

## CRUD Courses (Administrator & Mentor)

### Create Course

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

### Update Course

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

### Delete Course

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

## CRUD Categories (Administrator Only)

### Create Category

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

### Update Category

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

### Delete Category

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

## CRUD Users (Administrator Only)

### Create User

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

### Update User

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

### Delete User

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

Selamat Mencoba...
