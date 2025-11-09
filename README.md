Excellent choice, Akash 👏
**“AES-128 Hardware Encryption Core”** is a *strong, industry-relevant VLSI project* — simple enough to complete, but deep enough to show *real digital design skill*.

Below is a **complete project description + professional README.md** file you can directly use in your GitHub repository or final-year submission folder.

---

# 🧠 **Project Title:** AES-128 Hardware Encryption Core

---

## 🔹 **Project Description**

The **AES-128 Hardware Encryption Core** is a **Verilog-based implementation** of the **Advanced Encryption Standard (AES)** algorithm designed to perform **block-level data encryption** using a **128-bit key**.

This project demonstrates how symmetric-key encryption can be implemented in **hardware logic** to achieve **high performance and data security**, making it suitable for **FPGA**, **SoC**, and **embedded security applications**.

The AES-128 core performs **10 rounds** of transformation operations — each consisting of **SubBytes**, **ShiftRows**, **MixColumns**, and **AddRoundKey** — controlled by a **Finite State Machine (FSM)**.
The design also includes a **Key Expansion Unit** that generates all **round keys** from the initial 128-bit secret key.

---

## 🔸 **Objectives**

* To design and implement a **fully functional AES-128 encryption module** using Verilog HDL.
* To understand the **datapath and control logic** of modern cryptographic algorithms.
* To **simulate and verify** AES functionality using **ModelSim or Vivado Simulator**.
* (Optional) To **synthesize and test** the AES core on an **FPGA board** (Basys 3 / Nexys A7).

---

## 🔹 **Features**

* Implements **AES-128 encryption** (128-bit key and block size).
* Modular design: individual RTL modules for each AES stage.
* FSM-based control unit for round sequencing.
* Supports simulation-based testing with plaintext and key inputs.
* Easily extensible to AES-192 / AES-256.
* Synthesizable for **FPGA hardware acceleration**.

---

## 🔸 **System Architecture**

### 🔹 AES-128 Block Diagram

```
                ┌──────────────────────────────────────┐
                │            AES-128 Core              │
                │──────────────────────────────────────│
                │  ┌──────────────┐  ┌──────────────┐  │
Plaintext  ───► │  AddRoundKey   │►►│   SubBytes    │  │
                │  (Round 0)      │  └──────────────┘  │
                │          │             │              │
                │          ▼             ▼              │
                │     ┌──────────────┐ ┌──────────────┐ │
                │     │ ShiftRows    │ │ MixColumns   │ │
                │     └──────────────┘ └──────────────┘ │
                │          │             │              │
                │          ▼             ▼              │
                │     ┌───────────────────────────────┐ │
                │     │        AddRoundKey            │ │
                │     └───────────────────────────────┘ │
                │          ▲                            │
                │          │                            │
                │     ┌──────────────┐                  │
                │     │ Key Expansion│◄─────────────────┘
                │     └──────────────┘
                └──────────────────────────────────────┘
                                 │
                                 ▼
                          Ciphertext Output
```

---

## 🔹 **Design Modules**

| **Module Name**      | **Description**                                     |
| -------------------- | --------------------------------------------------- |
| `aes_top.v`          | Top-level integration module for all AES submodules |
| `aes_fsm.v`          | Control FSM to handle 10 rounds and timing          |
| `aes_subbytes.v`     | Implements S-box substitution using lookup table    |
| `aes_shiftrows.v`    | Performs cyclic shifting of matrix rows             |
| `aes_mixcolumns.v`   | Performs matrix multiplication in GF(2^8)           |
| `aes_addroundkey.v`  | XOR operation between key and data state            |
| `aes_keyexpansion.v` | Generates 11 round keys from input key              |
| `aes_testbench.v`    | Testbench to verify encryption output               |

---

## 🔸 **Data Flow**

1. **Input:**

   * 128-bit Plaintext
   * 128-bit Secret Key

2. **Processing:**

   * Key Expansion → Round 0: AddRoundKey →
   * 9 Main Rounds: SubBytes → ShiftRows → MixColumns → AddRoundKey →
   * Final Round: SubBytes → ShiftRows → AddRoundKey

3. **Output:**

   * 128-bit Ciphertext

---

## 🔹 **Algorithm Overview**

| **AES Step**    | **Operation**                 | **Purpose** |
| --------------- | ----------------------------- | ----------- |
| **SubBytes**    | Byte substitution using S-box | Confusion   |
| **ShiftRows**   | Cyclic row shifting           | Diffusion   |
| **MixColumns**  | Column-wise transformation    | Diffusion   |
| **AddRoundKey** | XOR with round key            | Key mixing  |

---

## 🔸 **Tools and Technologies**

| **Tool / Language**               | **Purpose**                       |
| --------------------------------- | --------------------------------- |
| **Verilog HDL**                   | Design and implementation         |
| **ModelSim / Vivado Simulator**   | Functional simulation             |
| **Xilinx Vivado / Quartus**       | Synthesis and FPGA implementation |
| **Basys 3 / Nexys A7 FPGA Board** | Hardware testing (optional)       |

---

## 🔹 **Simulation Example**

**Input:**

* Plaintext: `00112233445566778899AABBCCDDEEFF`
* Key: `000102030405060708090A0B0C0D0E0F`

**Expected Output (Ciphertext):**
`69C4E0D86A7B0430D8CDB78070B4C55A`

---

## 🔸 **Project Folder Structure**

```
AES_128_Hardware_Encryption_Core/
│
├── src/
│   ├── aes_top.v
│   ├── aes_subbytes.v
│   ├── aes_shiftrows.v
│   ├── aes_mixcolumns.v
│   ├── aes_addroundkey.v
│   ├── aes_keyexpansion.v
│   ├── aes_fsm.v
│
├── testbench/
│   ├── aes_testbench.v
│
├── docs/
│   ├── AES_Block_Diagram.png
│   ├── Simulation_Waveforms.png
│
├── README.md
└── report/
    ├── AES_Report.pdf
```

---

## 🔹 **How to Run the Project**

### 🔸 **Simulation**

1. Open **Vivado / ModelSim**.
2. Create a new project and add all `.v` files from the `/src` folder.
3. Add `aes_testbench.v` as the simulation source.
4. Run the simulation and observe the ciphertext output.

### 🔸 **FPGA Implementation (Optional)**

1. Create a new Vivado project for your FPGA board.
2. Add top-level `aes_top.v` and synthesize.
3. Map 128-bit inputs/outputs to switches and LEDs or UART for testing.

---

## 🔹 **Performance Metrics**

| **Parameter** | **Result (Typical)**        |
| ------------- | --------------------------- |
| Frequency     | ~100–150 MHz (Basys 3 FPGA) |
| Latency       | 10 rounds × clock cycles    |
| Power         | ~25–40 mW (synthesized)     |
| Area          | ~3000–5000 LUTs (approx.)   |

---

## 🔸 **Possible Extensions**

| **Extension**             | **Description**                                        |
| ------------------------- | ------------------------------------------------------ |
| 🔋 Low-Power AES          | Add clock gating to reduce dynamic power               |
| ⚡ Pipelined AES           | Add round-level pipeline registers for higher speed    |
| 🔁 AES Decryption         | Implement inverse rounds for full encrypt/decrypt core |
| 🔐 Random Key Generator   | Integrate LFSR for key randomization                   |
| 🧠 AES-RISC-V Accelerator | Integrate as co-processor in a CPU design              |

---

## 🔹 **Applications**

* Secure IoT communication
* Data encryption in embedded systems
* FPGA-based cryptographic accelerators
* Hardware Security Modules (HSMs)
* Secure wireless communication devices

---

## 🏁 **Conclusion**

This project demonstrates a complete **hardware realization of AES-128 encryption**, achieving **fast and secure data processing** through efficient RTL design. It showcases skills in **digital logic, FSM design, and FPGA implementation**, making it a strong addition to any **VLSI design or hardware security resume**.

---

## 👨‍💻 **Author**

**Akash Sasmal**
Backend & Hardware Design Engineer | VLSI & FPGA Enthusiast
📧 *[[akash.aios.10@gmail.com](mailto:your.email@example.com)]*
🔗 GitHub: *github.com/Akash-10-h*

---

