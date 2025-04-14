
### **Day 32: SystemVerilog Data Types and Structures**

**Concept Overview**  
SystemVerilog introduces a rich set of **data types** that extend Verilog's capabilities, making it easier to write robust, efficient, and modular hardware and verification code. These types help model real-world systems more naturally.

---

### **Key Data Types**

**1. `logic` and `bit`**  
- `logic`: 4-state data type (`0`, `1`, `x`, `z`) used for design modeling.  
- `bit`: 2-state data type (`0`, `1`), typically used in testbenches where unknowns (`x/z`) are unnecessary.

```systemverilog
logic a, b;        // RTL modeling
bit flag;          // 2-state for faster simulation in TB
```

---

**2. Vectors and Arrays**  
- SV supports fixed-size vectors (bit/logic) and arrays (packed and unpacked).
```systemverilog
logic [7:0] byte_val;           // 8-bit packed vector
logic [3:0][7:0] matrix;        // Unpacked 2D array: 4 elements of 8-bit
```

---

**3. Enumerated Types (`enum`)**  
Define meaningful named states or constants.
```systemverilog
typedef enum logic [1:0] {
    IDLE = 2'b00,
    START = 2'b01,
    DATA = 2'b10,
    DONE = 2'b11
} state_t;

state_t current_state;
```

---

**4. Structures (`struct`)**  
Group related variables into a single composite type.
```systemverilog
typedef struct {
    logic [7:0] addr;
    logic [7:0] data;
    bit valid;
} packet_t;

packet_t pkt;
```

---

**5. Typedef**  
Allows aliasing of complex types, improving readability and reuse.
```systemverilog
typedef logic [15:0] word_t;
word_t instruction;
```

---

**6. Constants (`const`) and Parameters**  
```systemverilog
const int MAX_SIZE = 256;
parameter int TIMEOUT = 100;

### **Practical Use Cases**
- `logic` used in RTL designs for wires, regs  
- `bit` and `enum` common in testbenches for compact modeling  
- `struct` used to define packets, bus formats, or interface data  
- `typedef` simplifies large design environments

