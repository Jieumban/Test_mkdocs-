# AISLAB專題方向

## 主題

- 主持人 峻豪

討論專題的幾個方向，包含指令集模擬器、系統模擬器、OS、CPU設計

**提到的主題**
1. ISA Simulator
2. System Emulator
3. Cache Simulator and DRAM Simulator
4. Operating System for RISC-V
5. Superscalar In-order RISC-V CPU
6. Out-of-Order (OoO) RISC-V CPU
7. RISC-V Vector Extension Related Topics



### 1. ISA Simulator (ISS)

- 專注於指令集模擬，像是single cycle CPU
- 基本上會希望做到至少支援 RV32(64)IMAC_Zicsr_Zifencei，除了基本的指令以外，包含 M-extension 和 C-extension 和 A-extension，跟 Zicsr extension，所以要實做部份的 Control-and-Status (CSR) registers。然後在上面去開發各種 infrastructure，讓我們這個工具更具實用和研究價值
- M extension 為加上乘法除法相關的指令
- F, D, Q為浮點數相關的simulation ，

### 2. System Emulator 

- 這個是做整個系統的模擬。
- 加入更多模擬關於系統元件的部分，例如 UART、MMU、CLINT、PLIC、VirtIO，支援 SBI，甚至把 Linux 開起來
- 可以去想要寫什麼模擬的裝置。

**延伸主題：differential testing**

>拿ISS作為golden model，驗證後面用verilog 寫出來的single cycle CPU，如果專題想做ISS，可以改善store指令模擬錯誤但抓不到的問題。

ISS和系統模擬使用C語言或rust來進行


參考資料
- [Virtio: An I/O virtualization framework for Linux](https://developer.ibm.com/articles/l-virtio/)


### 3. Cache Simulator and DRAM Simulator

- 教育部計畫相關
 - 建立可參數化配置的 Cache Simulator，希望應該是至少要做到 multi-level，然後要整合 ramulator2.0，在上面探索 Cache Performance & Optimization
 - 觀察Cache設計與高階語言寫法之間的影響。

**延伸主題：嘗試把Cache Simulator 把 Ramulater 整合起來**


**基本上與教育部計畫有直接關聯，Ramulator為DRAM的開源模擬器**


### 4. Operating System for RISC-V

- 作業系統相關的題目，例如rCore和xV6
**rCore**: 使用rust寫的作業系統，如果要看rCore，必須要先看懂Rust的語法。
**xV6**: 針對x86寫的作業系統，xV6程式碼約七千多行，不像是Linux有幾千萬行的功能。
>如果要做作業系統的題目，也會於指令集有關，向上管理系統程式，向下管理CPU等硬體的處理。
Virtual memory 也跟作業系統相關，除了嵌入式裝置，作業系統基本上都會有虛擬記憶體的裝置。
> - **需要了解中斷和異常處理兩個重要觀念**

**可以考慮拿現有的Linux等的功能加到xV6或是rCore**

參考資料
- [rCore OS (github.com)](https://github.com/rcore-os)
- [Xv6 for RISC-V (github.com)](https://github.com/mit-pdos/xv6-riscv)
- [作業系統 RISCV xv6 (Medium)](https://medium.com/@igimast5088/mit-6-1810-ch2-operating-system-organization-3afc106cfcda)


### 5. Superscalar In-order RISC-V CPU

**In-order vs. Out-of-order**
- In-order
 CPU執行指令順序會跟編譯出來的指令順序相同
- out of order
在兩條指令不會產生data hazard的情況，指令執行先後順序可以交換，可以提升指令執行效率。

**Superscalar** 
- 在一個Clock 裡面執行超過一個指令，透過新增memory的port，或增加ALU的數量，就可以並行使用，只是會增加功耗和面積的使用。


- 不一定要實作Superscalar In-order Core，也可以是Superscalar Out-of-order Core
- 探討更高效能的 pipeline 設計，像是更深的流水線，還有設計對應的 cache、MMU

### 6. Out-of-Order (OoO) RISC-V CPU

- 實作Out-of-Order的CPU本身就有難度，故可以不用做Superscalar

這兩個CPU Core design 的題目可以使用Verilog或是Chisel來寫，偏計組與數位IC相關，也就是進行RTL design。
也會以可以開作業系統（不論大小）為目標

### 7. RISC-V Vector Extension Related Topics
 
- 使用SIMD的概念，使用一個指令來同時進行多筆資料的運算
- V extension 就是SIMD的指令架構，因難度較高，可以嘗試進行指令模擬就好，也有可能可以運用到AI加速器。

> 補充：GPU使用的不是SIMD而是SIMT
> - [GPU Flynn概念(Medium)](https://johnnybboy.medium.com/gpu-flynn%E6%A6%82%E5%BF%B5-ed19ed1b3e61)

## 補充資源

### TinyEMU
- 對應到System Emulator ，模擬RISC-V或x86的系統模擬器，可能會掛上VirtIO、network 等等
- 系統模擬器就像是ISS的擴充版
> 補充: [RISCV with TinyEMU](/iU7V_UVxRtKvv1eGYhhYOQ)

### Spike RISC-V ISA Simulator 

- RISC-V是模組化的設計，Spike支援幾乎所有的extension 的指令，因為它是官方維護的指令集模擬器。
- Spike就不像TinyEMU會去模擬與其他輸出輸入的互動，

### RISC-V 規格書

- 裡面有ISA Specification，分為Unprivileged 和Privileged 兩部分，所以也需要了解特權等級的觀念

