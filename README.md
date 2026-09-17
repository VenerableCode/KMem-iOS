# KMem-iOS
lightweight ios mach memory utility header

## Usage

### Find the First Base

Find the first base:

```cpp
uintptr_t base = KMEM::scanner::FindFirstBase();
```

### Return Base

Reinterpret cast `_dyld_get_image_header(0)`:

```cpp
uintptr_t base = KMEM::scanner::ReturnBase();
```

### Get Base From Name

Get the base from a framework name:

```cpp
uintptr_t base = KMEM::scanner::GetImageBase("UnityFramework");
```

### Get Address From First Base + Offset

Only works if `FindFirstBase` is successful:

```cpp
uintptr_t address = KMEM::io::GetAddress(0x123);
```

### Get Address From Chosen Base + Offset

```cpp
uintptr_t address = KMEM::io::GetAddress("framework", 0x123);
```

### Validate Pointer

```cpp
if (KMEM::io::IsValidPointer(address)) { }
```

### Read

```cpp
int value = KMEM::io::ReadMem<int>(address);
```

### Write

```cpp
KMEM::io::WriteMem<int>(address, 100);
```

### Read String

```cpp
std::string text = KMEM::io::ReadString(address, 64);
```

### Raw Read

```cpp
uintptr_t rawValue = KMEM::io::ReadRaw(address);
```

### Raw Write

```cpp
KMEM::io::WriteRaw<int>(address, 100);
```

### Read Bytes

```cpp
uint8_t buffer[32]{};
KMEM::io::ReadBytes(address, buffer, sizeof(buffer));
```

### Write Bytes

```cpp
const uint8_t bytes[] = { 0x90, 0x90, 0x90 };
KMEM::io::WriteBytes(address, bytes, sizeof(bytes));
```
