
### Union?

- A **union** is a **user-defined data type** like a `struct`.
- **All members share the same memory location**.
- **Size of union = size of largest member**.
- **At any point in time, only one member can hold a meaningful value**.

**syntax**
```c
union UnionName {
    data_type member1;
    data_type member2;
    ...
};
```

**Example**
```c
union Data {
    int i;
    float f;
    char str[20];
};
```

### Declaration and Initialization

```c
union Data d1;   // Declare

d1.i = 10;       // Assign integer
printf("%d\n", d1.i);

d1.f = 5.5;      // Assign float (overwrites int)
printf("%.2f\n", d1.f);

```

**Important:**
- All members **share memory**, so writing to one **overwrites the others**.

### Memory Layout & Size Calculation

**Key Rule:**

- **Union memory = size of largest member**
- **Alignment = alignment of largest member**

```c
union Example {
    char a;     // 1 byte
    int b;      // 4 bytes
};
```

- Size = 4 bytes (largest is `int`)
- **All members share the same memory.**

