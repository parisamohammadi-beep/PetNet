# Class Specification — پت نت

### user
| بخش | توضیح |
|------|-------|
| مسئولیت |مسئولیت نگهداری اطلاعات پایه و مشترک همه کاربران، مدیریت احراز هویت و نقشها. این کلاس هیچ دانشی از رفتار اختصاصی نقشها ندارد و فقط قرارداد مشترک را تعریف میکند. |
| ویژگی‌ها | id, fullName, email, phone, passwordHash, role, isActive, createdAt |
| متدها | login(), logout(), updateProfile(), changePassword() |
| روابط | User 1:N Customer, User 1:N Veterinarian |

## customer
| بخش | توضیح |
|------|-------|
| مسئولیت | مسئولیت نمایندهی کاربر عادی سایت؛ صاحب پت، خریدار فروشگاه، سازنده آگهی واگذاری و متقاضی سرپرستی. مسئول نگهداری اطلاعات هویتی تکمیلی (کد ملی، تاریخ تولد) و ارتباط با آدرسها، پتها، سفارشها و آگهی هااست |
| ویژگی‌ها | nationalCode, birthDate, email |
| روابط | Customer 1:N Address, Customer 1:N Pet |

## Veterinarian
| بخش | توضیح |
|------|-------|
| مسئولیت | مسئولیت نمایندهی دامپزشک؛ مدیریت پروفایل حرفهای، تعریف بازههای زمانی قابل رزرو، ویزیت نوبتها و نوشتن نسخه/مقاله. |
| ویژگی‌ها | licenseNumber, specialty, bio, rating |
| متدها | setAvailability(), addTimeSlot() |
| روابط | Veterinarian N:1 Clinic, Veterinarian 1:N TimeSlot, User 1:N Veterinarian |

## Address
| بخش | توضیح |
|------|-------|
| مسئولیت | مسئولیت نگهداری آدرسهای ارسال سفارش برای هر مشتری. همراه با حذف مشتری حذف میشود |
| ویژگی‌ها | province, city, street, postalCode |
| متدها | ـــ |
| روابط | Customer 1:N Address |

## pet
| بخش | توضیح |
|------|-------|
| مسئولیت | یک پت با اطلاعات زیستی و پزشکی پایه. مستقل از مالکیت است |
| ویژگی‌ها | name, species, breed, ageMonths, gender, vaccinated, medicalNotes |
| متدها | calculateAge(), isVaccinated() |
| روابط | Customer 1:N Pet, Pet 1:N Appointment, Pet 1:N AdoptionPost |

## clinic
| بخش | توضیح |
|------|-------|
| مسئولیت | مسئولیت نمایش درمانگاه/مطب؛ مدیریت لیست دامپزشکان و بازههای زمانی قابل رزرو |
| ویژگی‌ها |  name, address, phone, description |
| متدها | getAvailableSlots(date) |
| روابط | Veterinarian N:1 Clinic, Clinic 1:N TimeSlot |

## timeslot
| بخش | توضیح |
|------|-------|
| مسئولیت | مسئولیت نگهداری یک بازهی زمانی مشخص که یا آزاد است یا به نوبت اختصاص یافته |
| ویژگی‌ها | startTime, endTime, isAvailable |
| متدها | reserve(), release() |
| روابط | Clinic 1:N TimeSlot, Veterinarian 1:N TimeSlot |

## AdoptionPost
| بخش | توضیح |
|------|-------|
| مسئولیت | مسئولیت مدیریت آگهی واگذاری یا درخواست سرپرستی |
| ویژگی‌ها | type, title, description, status, createdAt, city |
| متدها | publish(), close(), reject() |
| روابط | Customer 1:N AdoptionPost, Pet 1:N AdoptionPost, AdoptionPost 1:N AdoptionRequest |

## AdoptionRequest
| بخش | توضیح |
|------|-------|
| مسئولیت | نگهداری درخواست یک کاربر برای گرفتن پت از یک آگهی خاص |
| ویژگی‌ها | message, status, requestedAt |
| متدها | approve(), reject() |
| روابط | AdoptionPost 1:N AdoptionRequest, Customer 1:N AdoptionRequest |

## Article
| بخش | توضیح |
|------|-------|
| مسئولیت | مسئولیت مدیریت محتوای مقالات |
| ویژگی‌ها | title, slug, content, coverImageUrl, status, publishedAt, views |
| متدها | publish(), incrementView() |
| روابط | Category 1:N Article, User 1:N Article |

## product
| بخش | توضیح |
|------|-------|
| مسئولیت | مسئولیت نگهداری کاتالوگ محصولات، قیمت و موجودی |
| ویژگی‌ها | name, description, price, stock, imageUrl, isActive |
| متدها | isInStock(), decreaseStock(qty) |
| روابط | ___ |

## order
| بخش | توضیح |
|------|-------|
| مسئولیت | مسئولیت مدیریت چرخهی سفارش از ثبت تا تحویل/لغو |
| ویژگی‌ها | orderDate, status, totalPrice |
| متدها | checkout(), cancel() |
| روابط | Customer   1:N  Order |

