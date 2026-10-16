# nucleo-can-diagnostic-system
nucleo-can-diagnostic-system

# STM32 CAN-based Diagnostic System (SDV ECU Simulator)

## 📡 CAN Message Matrix

### 1. Periodic Broadcast Message (STM32 -> PC)
- **CAN ID:** `0x100`
- **DLC:** 8 Bytes
- **Cycle:** 100ms

| Byte | Field | Data Range / Values | Description |
| :---: | :--- | :--- | :--- |
| **Byte 0** | Light Sensor (Lux) | `0 ~ 100` (%) | 조도 센서 측정값 |
| **Byte 1** | Temperature | `0 ~ 100` (°C) | 현재 온도 |
| **Byte 2** | Humidity | `0 ~ 100` (%) | 현재 습도 |
| **Byte 3** | Wiper Status | `0`: OFF<br>`1`: LOW (천천히)<br>`2`: HIGH (빠르게) | 와이퍼 작동 단계 |
| **Byte 4** | Auto-Light LED | `0`: OFF<br>`1`: ON | 오토라이트 LED 상태 |
| **Byte 5** | DTC Flag | `0`: Normal<br>`1`: Fault Detected | 센서 고장 발생 여부 |
| **Byte 6~7**| Reserved | `0x00` | 예비 영역 |

---

### 2. UDS Diagnostic Messages
- **Request ID (PC -> STM32):** `0x7E0`
- **Response ID (STM32 -> PC):** `0x7E8`
- **DLC:** 8 Bytes
