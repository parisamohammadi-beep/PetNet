# Class Diagram — پت نت

## ۱. مقدمه

این دیاگرام ساختار کلاس‌های اصلی سیستم را نشان می‌دهد.

## ۲. کلاس‌ها

### ۲.۱ user
| ویژگی | نوع |
|--------|------|
| id | int |
| fullname | string |
| email | string |
| phone | int |
| isActive | boolean |
| role | UserRole (enum) |
| passwordHash | string |

### ۲.۲ customer
| ویژگی | نوع |
|--------|------|
| nationalcode | long |
| email | string |
|phone number| int |

### ۲.۳ Veterinarian
| ویژگی | نوع |
|--------|------|
| licenseNumber | int |
| bio | string |
| rating | int |

### ۲.۴ Address
| ویژگی | نوع |
|--------|------|
| id | int |
| province | string |
| city | string |
| street | string |
| postalcode | string |

### ۲.۵ pet
| ویژگی | نوع |
|--------|------|
| id | int |
| name | string |
| species | string |
| agemonth | int |
| gender| gender(enum)|
| vaccinated | boolean |
| medicalNotes | string |
| imageUrl | string |

### ۲.۶ clinic
| ویژگی | نوع |
|--------|------|
| id | int |
| name | string |
| address| string |
| phone | string |
| description | string |

### ۲.۷ timeslot
| ویژگی | نوع |
|--------|------|
| id | long |
| startTime | Date time |
| endTime | Date time |
| isAvailable | boolean |

### ۲.۸ AdoptionPost
| ویژگی | نوع |
|--------|------|
| id | long |
| title | string |
| type |adobtionpost type |
| description | string |
| status | postStatus |
| city | string |
| createdAt| data time |

### ۲.۹ AdoptionRequest
| ویژگی | نوع |
|--------|------|
| id | int |
| Message | string |
| status | AdoptionStatus (enum) |
|RequestedAt| Datetime |

### ۲.۱۰ Article
| ویژگی | نوع |
|--------|------|
| title | string |
| slug | string |
| content | string |
| status | postStatus |
| publishedAt | DateTime |
| views | int |

### ۲.۱۱ product
| ویژگی | نوع |
|--------|------|
| id | int |
| name | string |
| Description | string |
| price | decimal |
| stock | int |
| imageUrl | string |
|isActive | boolean | 

### ۲.۱۲ order
| ویژگی | نوع |
|--------|------|
| id | long |
| status | postStatus |
| totalprice | decimal |
|orderDate| Datetime |

## ۳. روابط

# رابطه

- User 1:N Customer 
- User 1:N Veterinarian 
- User 1:N Admin 
- Customer 1:N Address
- Customer 1:N Pet

- Veterinarian  N:1  Clinic
- Clinic        1:N  TimeSlot
- Veterinarian  1:N  TimeSlot
- Customer      1:N  Appointment
- Pet           1:N  Appointment

- Customer       1:N  AdoptionPost
- Pet            1:N  AdoptionPost
- AdoptionPost   1:N  AdoptionRequest
- Customer       1:N  AdoptionRequest

- Category   1:N  Article
- User       1:N  Article
- Customer   1:N  Order