
### Struct?

- A **structure** (`struct`) in C is a **user-defined data type** that allows grouping variables of **different data types** under one name.

- It is a **composite data type**

**syntax**
```c
struct StructName {
    data_type member1;
    data_type member2;
    ...
};
```

**Example**

```c
struct StructName {
    data_type member1;
    data_type member2;
    ...
};
```

### Declaration and Initialization

```c
struct Basic student1; // Declaration

// Initialization
student1.id = 101;
student1.grade = 'A';
student1.marks = 87.5;

```

**Designated Initialization**
```c
struct Basic student2 = {102, 'B', 76.5};
```

### Accessing Member

- Using **dot operator (`.`)** for direct objects.
- Using **arrow operator (`->`)** for pointers.

```c
printf("%d %c %.2f\n", student1.id, student1.grade, student1.marks);

struct Basic *ptr = &student1;
printf("%d %c %.2f\n", ptr->id, ptr->grade, ptr->marks);

```

### Memory Layout and padding

```c
struct Basic {
    int id;     // 4 bytes
    char grade; // 1 byte
    float marks;// 4 bytes
};
```

| Byte offset | Content     |
| ----------: | ----------- |
|         0-3 | int id      |
|           4 | char grade  |
|         5-7 | **padding** |
|        8-11 | float marks |
**`sizeof(struct Basic)` = 12 bytes**

#### padding?

- **Padding** is the **extra bytes inserted by the compiler** between structure members to satisfy **CPU alignment requirements**.
- A variable must start at an **address that is a multiple of its alignment** to be accessed efficiently.
- Modern CPUs prefer that **data types are stored at memory addresses that are multiples of their size/alignment**.
	- `int` (4 bytes) → best stored at address divisible by 4
	- `short` (2 bytes) → best stored at address divisible by 2
	- `double`  (8 bytes) → best stored at address divisible by 8

#### Why padding?

- Compiler **inserts padding bytes** so that **each member** in a struct starts at an **address multiple of its natural alignment**.
    
- This makes **memory access faster and safer**.
##### without padding

- CPU may need **multiple memory accesses** for misaligned data.
- Some CPUs **crash** if misaligned access occurs (like older ARM).
##### with padding

- Ensures **fast access** (aligned access).
- Structure size is often **rounded up to a multiple of the largest member's alignment**.

##### Example 1:

```c
struct G {
    char a;  //1
    char b;  //1
    char c;  //1
};

op:
3
```

##### Example 2:

```c
struct I {
    int a;     //4
    double b;  //8
    char c;    //1
};
op:
24
```

**Layout**

```c
0-3   a
4-7   padding (align double to 8)
8-15  b
16    c
17-23 padding (align struct to 8)
```

**while defining last padding we should consider the so far largest alignment , here it is ``double`` so we aligned 8 at end 

##### Example 3 :

```c
struct J {
    char a;       //1
    long long b;  //8
    char c;       //1
};
op:
24
```
**Layout**
```c
0    a
1-7  padding (align long long to 8)
8-15 b
16   c
17-23 padding (struct size multiple of 8)
```

### Application

##### Cab Booking System

```c
#include <stdio.h>
#include <string.h>

// Structure to store Cab details
struct Cab {
    int cabID;
    char driverName[30];
    char cabType[10]; // Mini, Sedan, SUV
    float baseFare;
    int isAvailable;  // 1 = available, 0 = booked
};

// Structure to store Customer details
struct Customer {
    int customerID;
    char name[30];
    char phone[15];
};

// Structure to store Booking details
struct Booking {
    int bookingID;
    struct Customer customer;
    struct Cab cab;
    float distance; // in km
    float totalFare;
};

int main() {
    // Sample Cabs
    struct Cab cabs[3] = {
        {1, "Ramesh", "Mini", 50.0, 1},
        {2, "Suresh", "Sedan", 80.0, 1},
        {3, "Mahesh", "SUV", 100.0, 1}
    };

    struct Booking bookings[5]; // Store up to 5 bookings
    int bookingCount = 0;
    int choice;

    while(1) {
        printf("\n===== CAB BOOKING SYSTEM =====\n");
        printf("1. View Available Cabs\n");
        printf("2. Book a Cab\n");
        printf("3. View All Bookings\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        if(choice == 1) {
            printf("\n--- Available Cabs ---\n");
            for(int i = 0; i < 3; i++) {
                if(cabs[i].isAvailable)
                    printf("ID:%d | Driver:%s | Type:%s | Base Fare:%.2f/km\n",
                           cabs[i].cabID, cabs[i].driverName,
                           cabs[i].cabType, cabs[i].baseFare);
            }

        } else if(choice == 2) {
            if(bookingCount >= 5) {
                printf("\nBooking limit reached!\n");
                continue;
            }

            // Create new booking
            struct Booking newBooking;
            newBooking.bookingID = bookingCount + 1;

            // Get customer details
            printf("Enter Customer Name: ");
            scanf("%s", newBooking.customer.name);
            printf("Enter Phone Number: ");
            scanf("%s", newBooking.customer.phone);
            newBooking.customer.customerID = bookingCount + 100;

            // Choose cab
            int cabChoice;
            printf("\nEnter Cab ID to book: ");
            scanf("%d", &cabChoice);

            int cabIndex = -1;
            for(int i = 0; i < 3; i++) {
                if(cabs[i].cabID == cabChoice && cabs[i].isAvailable) {
                    cabIndex = i;
                    break;
                }
            }

            if(cabIndex == -1) {
                printf("Invalid or Unavailable Cab!\n");
                continue;
            }

            // Distance and fare calculation
            printf("Enter distance in KM: ");
            scanf("%f", &newBooking.distance);
            newBooking.cab = cabs[cabIndex];
            newBooking.totalFare = newBooking.distance * cabs[cabIndex].baseFare;

            // Mark cab as booked
            cabs[cabIndex].isAvailable = 0;

            // Store booking
            bookings[bookingCount++] = newBooking;

            printf("\nBooking Confirmed! ID:%d | Fare: %.2f\n",
                   newBooking.bookingID, newBooking.totalFare);

        } else if(choice == 3) {
            printf("\n--- All Bookings ---\n");
            if(bookingCount == 0) {
                printf("No bookings yet.\n");
            } else {
                for(int i = 0; i < bookingCount; i++) {
                    printf("BookingID:%d | Customer:%s | Cab:%s | Distance:%.2f | Fare:%.2f\n",
                           bookings[i].bookingID,
                           bookings[i].customer.name,
                           bookings[i].cab.cabType,
                           bookings[i].distance,
                           bookings[i].totalFare);
                }
            }

        } else if(choice == 4) {
            printf("Exiting Cab Booking System...\n");
            break;
        } else {
            printf("Invalid choice!\n");
        }
    }

    return 0;
}
```